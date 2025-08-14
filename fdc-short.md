# Firebase Data Connect

Firebase Data Connect is a relational database solution that integrates Cloud SQL for PostgreSQL with type-safe mobile and web SDKs. It allows developers to define an application's data model, automatically generates PostgreSQL schema, secure server endpoints (GraphQL APIs), and type-safe SDKs for client applications.

## Key Concepts

*   **Service**: A managed GraphQL API defined by developers and called by end-users. A project can have multiple services.
*   **Schema**: The app data model for a service, primarily defined in GraphQL source files (`.gql`) and configuration for attached datasources (like Cloud SQL). Each service has one schema.
*   **Connectors**: Collections of predefined queries and mutations that operate against a service's schema. A service can have multiple connectors (e.g., for different client applications).
*   **Generated SDKs**: Strongly-typed SDKs for client applications (Android Kotlin, iOS Swift, Flutter Dart, Web JavaScript, React, Angular) automatically generated based on the defined data model and operations.
*   **Local Emulator Suite**: Provides a local PGLite database instance for end-to-end prototyping and CI/CD workflows, mimicking production behavior.

## Installation and Setup

### Firebase CLI Installation

1.  Install Node.js (v18.0 or higher).
2.  Install the Firebase CLI: `npm install -g firebase-tools`
3.  Initialize a Firebase project in your local directory: `firebase init`
    *   Select `dataconnect` for product setup.
    *   Choose a new service name and location.
    *   Link an existing Cloud SQL for PostgreSQL instance or create a new one (can take up to 15 minutes).
    *   Optionally, install the Data Connect emulator.

### Local Development Environment Setup (VS Code Extension)

1.  Create a new local project directory.
2.  Run the auto-installation script: `curl -sL https://firebase.tools/init/dataconnect | editor=true bash`
    *   This sets up the Data Connect VS Code extension, syncs assets from the Firebase console, and generates client SDKs.
    *   If the script fails, proceed with manual installation steps.

### Project Configuration Files

*   **`firebase.json`**:
    *   `dataconnect.source`: Path to the directory containing `dataconnect.yaml`.
    *   `emulators.dataconnect.dataDir`: (Optional) Path for automatic local PostgreSQL data export/import.
*   **`dataconnect.yaml`**:
    *   `specVersion`: Firebase Data Connect API version. (Optional, defaults to latest)
    *   `serviceId`: ID of the Data Connect service. (Required)
    *   `location`: Location of the Data Connect service. (Required)
    *   `schema.source`: Relative path to the directory for schema definitions (`.gql` files). (Optional, defaults to `./schema`)
    *   `datasource.postgresql.database`: Name of the PostgreSQL database. (Required)
    *   `datasource.postgresql.cloudSql.instanceId`: ID of the Cloud SQL instance. (Required)
    *   `schemaValidation`: Schema validation mode for migrations (`STRICT` or `COMPATIBLE`). (Optional, defaults to prompting for strict changes).
    *   `connectorDirs`: List of relative paths to directories for connector definitions (`.gql` and `connector.yaml` files). (Required)
*   **`connector.yaml`**:
    *   `connectorId`: Name of the Data Connect connector resource. (Required)
    *   `generate`:
        *   `javascriptSdk`: Configuration for web JavaScript SDK generation.
            *   `outputDir`: Path for generated web SDK. (Required)
            *   `packageJsonDir`: Path to `package.json` for auto-installation. (Optional)
            *   `package`: Package name. (Optional, defaults to `@firebasegen/`)
            *   `react`: `true` to generate React hooks.
            *   `angular`: `true` to generate Angular injectables.
        *   `swiftSdk`: Configuration for iOS Swift SDK generation.
            *   `outputDir`: Path for generated iOS Swift SDK. (Required)
            *   `package`: Package name.
            *   `observablePublisher`: `observableMacro` (iOS 17+) or `observableObject` (pre-iOS 17). (Optional, defaults to `observableMacro`)
        *   `kotlinSdk`: Configuration for Android Kotlin SDK generation.
            *   `outputDir`: Path for generated Android Kotlin SDK. (Required)
            *   `package`: Package name.
        *   `dartSdk`: Configuration for Flutter Dart SDK generation.
            *   `outputDir`: Path for generated Flutter Dart SDK. (Required)
            *   `package`: Package name.

## Schema Design

Firebase Data Connect uses GraphQL Schema Definition Language (`.gql` files) to define the data model.
*   **`type TypeName @table(...)`**: Maps GraphQL types to PostgreSQL tables.
    *   `@table(name: "sql_table_name")`: Customize the SQL table name (defaults to snake\_case).
    *   `@table(key: "field_name")` or `@table(key: ["field1", "field2"])`: Define primary keys.
*   **`field: Type! @col(...)`**: Maps GraphQL fields to SQL columns.
    *   `@col(name: "sql_column_name")`: Customize the SQL column name.
    *   `@col(dataType: "sql_data_type")`: Customize the SQL column type (e.g., `varchar(50)`, `serial`).
    *   `@col(size: X)`: Required for `Vector` types to specify dimensions (e.g., `Vector! @col(size: 768)`).
*   **`@default(expr: "CEL_expression")`**: Configures SQL column default values during insert using Common Expression Language (CEL).
    *   `@default(expr: "uuidV4()")`: Auto-generates UUIDs.
    *   `@default(expr: "auth.uid")`: Populates with Firebase Auth UID.
    *   `@default(expr: "request.time")`: Populates with request timestamp.
*   **`@ref(fields: "fk_field", references: "pk_field")`**: Customizes foreign key constraints for relationships.
*   **Relationships**:
    *   One-to-one (`@unique` on `@ref` field).
    *   Many-to-many (through join tables). Data Connect automatically generates reverse mapping fields (e.g., `_on_`, `_via_`).

### Supported Data Types

| Data Connect Type | GraphQL built-in/Custom Type | Default PostgreSQL Type | Supported PostgreSQL Types (aliases)                                                                               |
| :---------------- | :--------------------------- | :---------------------- | :----------------------------------------------------------------------------------------------------------------- |
| String            | GraphQL                      | `text`                  | `text`, `bit(n)`, `varbit(n)`, `char(n)`, `varchar(n)`                                                            |
| Int               | GraphQL                      | `int`                   | `int2` (smallint, smallserial), `int4` (integer, int, serial)                                                      |
| Float             | GraphQL                      | `float8`                | `float4` (real), `float8` (double precision), `numeric` (decimal)                                                  |
| Boolean           | GraphQL                      | `boolean`               | `boolean`                                                                                                          |
| UUID              | Custom                       | `uuid`                  | `uuid`                                                                                                             |
| Int64             | Custom                       | `bigint`                | `int8` (bigint, bigserial), `numeric` (decimal)                                                                    |
| Date              | Custom                       | `date`                  | `date`                                                                                                             |
| Timestamp         | Custom                       | `timestamptz`           | `timestamptz` (stores as UTC)                                                                                      |
| Vector            | Custom                       | `vector`                | `vector` (requires `pgvector` extension; see Vector Similarity Search section)                                     |
*   GraphQL `List` maps to a one-dimensional array (e.g., `[Int]` to `int[]`).
*   Nested arrays are not supported.

## Queries

Queries define how clients retrieve data from the Data Connect service.
*   **Generated Fields**: Data Connect automatically generates query fields based on schema types and relationships (e.g., `movie`, `movies`, `actors_on_movies`).
*   **Key Scalars**: Concise object identifiers `{TableType}_Key` used for efficient record identification.
*   **Arguments**:
    *   `where`: Filter results using various operators (`eq`, `ne`, `gt`, `lt`, `ge`, `le`, `isNull`, `includes`, `excludes`, `startsWith`, `endsWith`, `contains`, regular expressions, `_or`, `_and`, `_not`).
    *   `orderBy`: Sort results (e.g., `{ rating: DESC }`).
    *   `limit`: Restrict the number of results.
    *   `offset`: Skip a number of results for pagination.
*   **Aliases**: Rename fields in query results to avoid name collisions when performing multiple sub-queries.
*   **Relational Queries**: Access data across related tables using generated `_on_` (one-to-one, many-to-one) and `_via_` (many-to-many) syntax.
*   **Aggregation Queries**: Perform server-side calculations on result sets.
    *   `_count`: Counts rows (or non-null values for a specific field).
    *   `_min`, `_max`, `_sum`, `_avg`: For numeric fields.
    *   `_min`, `_max`: For date and timestamp fields.
    *   `distinct`: Get unique values for a field or group aggregates by distinct values.
    *   Grouped Aggregates: Select a mix of aggregate and non-aggregate fields to group results.
    *   `having`: Filter groups by their aggregate fields.
    *   `where`: Filter rows based on non-aggregate fields.

### Example Queries

```graphql
# Retrieve an individual movie by ID
query GetMovieById($id: UUID!) @auth(level: PUBLIC) {
  movie(id: $id) {
    id
    title
    imageUrl
    genre
  }
}

# List all movies
query ListMovies @auth(level: PUBLIC) {
  movies {
    id
    title
    imageUrl
    genre
  }
}

# Get top 10 movies by rating
query MoviesTop10 {
  movies(orderBy: [{ rating: DESC }], limit: 10) {
    title
  }
}

# List movies without description
query ListMoviesWithoutDescription {
  movies(where: { description: { isNull: true }}) {
    id
    title
  }
}

# Query movies by genre and rating range
query ListMoviesByRating($minRating: Int!, $maxRating: Int!) {
  movies(where: { rating: { ge: $minRating, lt: $maxRating }}) {
    id
    title
  }
}

# Query movies by tag inclusion
query ListMoviesByTag($tag: String!) {
  movies(where: { tags: { includes: $tag }}) {
    id
    title
  }
}

# Query movie reviews with nested movie and user details
query MyReviews @auth(level: USER) {
  user(key: {id_expr: "auth.uid"}) {
    reviews: reviews_on_user {
      movie {
        name
      }
      rating
    }
  }
}

# Aggregate: Count all products
query CountProducts {
  products {
    _count
  }
}

# Aggregate: Max quantity and min/avg/sum price grouped by manufacturer
query MostExpensiveProductByManufacturer {
  products {
    manufacturer
    price_max
  }
}
```

## Mutations

Mutations define how clients modify data in the Data Connect service (Create, Read, Update, Delete).
*   **Generated Fields**: Data Connect automatically generates mutation fields (e.g., `movie_insert`, `movie_update`, `movie_delete`).
*   **Key Scalars**: Used to identify records for mutations.
*   **Server Values (`_expr`)**: Dynamically populate fields using server-side CEL expressions (e.g., `id_expr: "uuidV4()"`, `userId_expr: "auth.uid"`).
*   **Operators for Updates**:
    *   `inc`: Increment numeric, Date, Timestamp fields.
    *   `dec`: Decrement numeric, Date, Timestamp fields.
    *   `add`: Append items to list types (if not present).
    *   `remove`: Remove items from list types.
    *   `append`: Append items to list types.
    *   `prepend`: Prepend items to list types.
*   **Multi-step Operations**:
    *   Include multiple write fields in one mutation.
    *   Include multiple read fields (`query` keyword) to lookup data before performing writes.
    *   `@transaction` directive: Ensures atomicity (all succeed or all fail).
    *   `@check` directive: Verifies specified fields in query results using CEL expressions. Can include `message` for client feedback.
    *   `@redact` directive: Omits query field results from client response, but still available for server-side logic (`@check`, `response` binding).
    *   `response` binding: Stores accumulated results of all previous mutations and queries in a multi-step operation, accessible in subsequent steps and `@check` directives.

### Example Mutations

```graphql
# Create a movie
mutation CreateMovie($title: String!, $releaseYear: Int!, $genre: String!, $rating: Int!) {
  movie_insert(data: { title: $title, releaseYear: $releaseYear, genre: $genre, rating: $rating })
}

# Upsert a movie
mutation UpsertMovie($title: String!) {
  movie_upsert(data: { title: $title, releaseYear: 2009, genre: "Mystery", rating: 5 })
}

# Update a movie by ID
mutation UpdateMovie($id: UUID!, $genre: String!, $rating: Int!, $description: String!) {
  movie_update(id: $id, data: { genre: $genre, rating: $rating, description: $description })
}

# Increment movie rating
mutation UpdateMovie($id: UUID!, $ratingIncrement: Int!) {
  movie_update(id: $id, data: { rating_update: { inc: $ratingIncrement } })
}

# Delete a movie by ID
mutation DeleteMovie($id: UUID!) {
  movie_delete(id: $id)
}

# Delete multiple movies based on a condition
mutation DeleteUnpopularMovies($minRating: Int!) {
  movie_deleteMany(where: { rating: { le: $minRating } })
}

# Create or update a one-to-one relation (MovieMetadata)
mutation MovieMetadataUpsert($movieId: UUID!, $director: String!) {
  movieMetadata_upsert(data: { movie: { id: $movieId }, director: $director })
}

# Add a movie to user's favorites list (uses auth.uid server value)
mutation AddFavoritedMovie($movieId: UUID!) @auth(level: USER) {
  favorite_movie_upsert(data: { userId_expr: "auth.uid", movieId: $movieId })
}

# Multi-step mutation with transaction and response binding
mutation CreateTodoListWithFirstItem( $listName: String!, $itemContent: String! ) @transaction {
  # Step 1: Create a todo list, auto-generating ID
  todoList_insert(data: { id_expr: "uuidV4()", name: $listName })
  # Step 2: Create a todo item, using ID from previous step
  todo_insert(data: { listId_expr: "response.todoList_insert.id", content: $itemContent })
}

# Multi-step mutation with query, check, and redact for authorization
mutation UpdateMovieTitle($movieId: UUID!, $newTitle: String!) @auth(level: USER) @transaction {
  query @redact {
    moviePermission(key: {movieId: $movieId, userId_expr: "auth.uid"})
    @check(expr: "this != null", message: "You do not have access to this movie") {
      role @check(expr: "this == 'editor'", message: "You must be an editor of this movie to update title")
    }
  }
  movie_update(id: $movieId, data: { title: $newTitle })
}
```

## Authorization and Attestation

Data Connect integrates with Firebase Authentication and App Check for robust security.
*   **`@auth` directive**: Sets the authentication level required for an operation.
    *   `level`: Preset access levels (e.g., `PUBLIC`, `USER`, `USER_ANON`, `USER_EMAIL_VERIFIED`, `NO_ACCESS`). `NO_ACCESS` is default if not specified.
    *   `expr`: Common Expression Language (CEL) expression for fine-grained control based on request variables (`vars`), authentication data (`auth`), and other factors.
    *   `insecureReason`: Suppresses CLI warnings for specific operations deemed safe.
*   **`@check` directive**: Used within mutations to validate conditions using CEL expressions. If the check fails, the operation terminates.
*   **`@redact` directive**: Hides fields from client responses while still allowing their evaluation on the server for side effects (e.g., authorization checks).
*   **CEL Bindings**:
    *   `request.operationName`: Type of operation (query/mutation).
    *   `vars` (alias for `request.variables`): Access to all variables passed in the operation.
    *   `auth` (alias for `request.auth`):
        *   `uid`: Unique user ID.
        *   `token`: Map of values from the authentication token (e.g., `auth.token.email`, `auth.token.email_verified`, custom claims like `auth.token.plan`).
    *   `response`: (Mutations only) Contains partial response data from successfully completed steps in a multi-step operation.
    *   `this`: (Within `@check` expressions only) Refers to the value of the field the `@check` directive is attached to.
*   **Antipatterns to Avoid**:
    *   Passing user IDs/auth token parameters directly in query/mutation arguments.
    *   Using `USER` (or `USER_ANON`, `USER_EMAIL_VERIFIED`) levels without additional filters.
    *   Using `PUBLIC` or `USER` levels for prototyping without robust security logic before deployment.
    *   Basing authorization on unverified email addresses (`auth.token.email_verified` should be checked).
*   **Firebase App Check**: Provides app/device attestation to ensure requests originate from authentic, untampered apps.

## Firebase CLI Commands

The Firebase CLI is essential for managing Data Connect projects.
*   `firebase init`: Sets up a new local project, including Data Connect service and database configuration.
*   `firebase emulators:start`/`firebase emulators:exec`: Starts the Data Connect emulator (interactive/non-interactive).
*   `firebase emulators:export --only dataconnect`: Exports local PostgreSQL data snapshots.
*   `firebase emulators:start/exec --import`: Imports PostgreSQL data from a snapshot.
*   `firebase dataconnect:services:list`: Lists deployed Data Connect services, schemas, and connectors.
*   `firebase deploy [--only dataconnect]`: Deploys Data Connect resources (schemas, connectors).
    *   `--only dataconnect:serviceId:schema`: Deploys only schema changes for a service.
    *   `--only dataconnect:serviceId:connectorId`: Deploys resources for a specific connector.
    *   `--only dataconnect:serviceId`: Deploys schema and all connectors for a service.
    *   `--force`: Skips interactive prompts for schema and connector validation warnings.
*   `firebase dataconnect:sql:diff`: Compares local schema with Cloud SQL database schema and prints migration commands.
*   `firebase dataconnect:sql:migrate [serviceId]`: Applies local schema changes to the Cloud SQL database. Prompts for approval in interactive mode.
*   `firebase dataconnect:sdk:generate [--watch] [--only connector1,connector1:kotlin]`: Generates typed SDKs. `--watch` for automatic regeneration on `.gql` changes.
*   `firebase dataconnect:sql:setup`: Configures initial global permissions to tables in your database. Crucial for integrating existing databases.
*   `firebase dataconnect:sql:grant --role writer`: Grants predefined PostgreSQL roles (e.g., `writer`, `reader`) to users/service accounts.
*   `--json`: Switches CLI output to JSON.
*   `--noninteractive`/`--interactive`: Overrides automatic TTY detection.

## SDKs

Firebase Data Connect provides generated, type-safe SDKs for various platforms.
*   **Generated SDKs**: Automatically created based on your defined schema, queries, and mutations. They wrap core SDKs for type safety and ergonomics.
*   **Workflow**:
    1.  Add Firebase to your app.
    2.  Configure Data Connect SDK as a dependency (Gradle for Android, Xcode for iOS, pub for Flutter, npm for Web).
    3.  Develop your app schema (`.gql` files).
    4.  Set up SDK generation via VS Code extension or `connector.yaml`.
    5.  Initialize client code and import libraries.
    6.  Implement calls to generated queries and mutations.
    7.  Use the Data Connect emulator for prototyping and testing.

### Web (JavaScript/TypeScript) SDK

*   **Installation**: `npm i --save @tanstack/react-query @tanstack-query-firebase/react` (for React) or `@angular/fire` (for Angular). Install `firebase@latest`.
*   **Initialization**:
    ```javascript
    import { initializeApp } from 'firebase/app';
    import { DataConnect, getDataConnect, connectDataConnectEmulator } from 'firebase/data-connect';
    import { connectorConfig, listMovies, createMovie } from '@myorg/myconnector'; // Generated SDK

    const app = initializeApp({});
    const dataConnect = getDataConnect(connectorConfig); // Use this for emulator connection
    connectDataConnectEmulator(dataConnect, 'localhost', 9399);
    ```
*   **Usage**:
    ```javascript
    // Using generated query action shortcut
    listMovies().then(data => console.log(data.movies));

    // Using QueryRef
    import { executeQuery, QueryRef } from 'firebase/data-connect';
    import { listMoviesRef } from '@movie-app/movies';
    const ref = listMoviesRef();
    const { data } = await executeQuery(ref);
    console.log(data.movies);

    // Subscribing to changes (not real-time, updates on execute)
    subscribe(listRef, ({ data }) => { /* update UI */ });
    await createMovie(...);
    await listRef.execute(); // Triggers subscription update

    // Mutations
    import { executeMutation } from 'firebase/data-connect';
    import { createMovieRef } from '@movie-app/movies';
    const { data } = await executeMutation(createMovieRef({ movie: '...' }));
    ```
*   **React/Angular Integration**: Generated SDK provides hooks (`useListAllMovies` for React) or injectables (`injectListAllMovies` for Angular) that wrap TanStack Query bindings.
    *   Queries use `useDataConnectQuery`.
    *   Mutations use `useDataConnectMutation`.
    *   `invalidate: [listAllMoviesRef()]` can be used with mutations to automatically re-fetch queries.
*   **Path Configuration**: Output directory for generated JS SDK needs to be accessible to `node_modules` (e.g., `../../js-email-generated` if `node_modules` is at project root).

### Android (Kotlin) SDK

*   **Dependencies (`app/build.gradle.kts`)**:
    ```kotlin
    plugins {
      kotlin("plugin.serialization") version "1.8.22"
    }
    dependencies {
      implementation(platform("com.google.firebase:firebase-bom:33.16.0"))
      implementation("com.google.firebase:firebase-dataconnect")
      implementation("org.jetbrains.kotlinx:kotlinx-serialization-core:1.5.1")
      // ... other dependencies like coroutines, appcompat
    }
    ```
*   **Initialization**:
    ```kotlin
    import com.myapplication.MoviesConnector
    val connector = MoviesConnector.instance
    connector.dataConnect.useEmulator() // Connect to emulator (default port 9399)
    // Or: connector.dataConnect.useEmulator(port = 9999)
    ```
*   **Usage**:
    ```kotlin
    val connector = MoviesConnector.instance
    val addMovieResult = connector.createMovie.execute(title = "...", releaseYear = ..., genre = "...", rating = ...)
    val movie = connector.getMovieByKey.execute(addMovieResult.data.key)
    val listMoviesResult = connector.listMoviesByGenre.execute(genre = "Sci-Fi")

    // Flow for observing changes (not real-time, updates on execute)
    connector.listMoviesByGenre.flow(genre = "Sci-Fi").collect { data -> println(data.movies) }
    connector.createMovie.execute(...)
    connector.listMoviesByGenre.execute(genre = "Sci-Fi") // Triggers flow notification
    ```
*   **Data Types**: `String`, `Int` (32-bit), `Double` (64-bit), `Boolean`, `java.util.UUID`, `com.google.firebase.dataconnect.LocalDate`, `com.google.firebase.Timestamp`, `Long`, `com.google.firebase.dataconnect.AnyValue`.

### iOS (Swift) SDK

*   **Dependencies**: In Xcode, `File > Add Package Dependencies > Add Local`, choose folder with generated `Package.swift`.
*   **Initialization**:
    ```swift
    import FirebaseDataConnect
    let connector = DataConnect.moviesConnector
    connector.useEmulator() // Connect to emulator (default port 9399)
    // Or: connector.useEmulator(port: 9999)
    ```
*   **Usage**:
    ```swift
    let mutationResult = try await connector.createMovieMutation.execute(title: "...", releaseYear: ..., genre: "...", rating: ...)
    print("Movie ID: \(mutationResult.data.movie_insert.id)")

    // Query with Observable Publisher (for SwiftUI views)
    struct ListMovieView: View {
      @StateObject private var queryRef = connector.listMoviesByGenreQuery.ref(genre: "Sci-Fi")
      // ... body and refresh method
    }

    // One-shot query execution
    let resultData = try await DataConnect.moviesConnector.listMoviesByGenreQuery.execute(genre: "Sci-Fi")
    ```
*   **`observablePublisher`**: Configurable in `connector.yaml` to use `@Observable` macro (iOS 17+) or `ObservableObject` protocol (pre-iOS 17).
*   **Data Types**: (Documentation incomplete, but similar mapping to other SDKs expected).

### Flutter (Dart) SDK

*   **Installation**:
    1.  `flutter pub add firebase_data_connect`
    2.  `dart pub global activate flutterfire_cli`
    3.  `flutterfire configure`
*   **Initialization**:
    ```dart
    import 'package:firebase_core/firebase_core.dart';
    import 'package:firebase_data_connect/firebase_data_connect.dart';
    import 'generated/movies.dart'; // Generated SDK

    void main() async {
      WidgetsFlutterBinding.ensureInitialized();
      await Firebase.initializeApp(options: DefaultFirebaseOptions.currentPlatform);
      MoviesConnector.instance.dataConnect.useDataConnectEmulator('127.0.0.1', 9399); // Connect to emulator
      runApp(const MyApp());
    }
    ```
*   **Usage**:
    ```dart
    await MoviesConnector.instance.listMovies().execute();
    await MoviesConnector.instance.createMovie(
      title: 'Empire Strikes Back',
      releaseYear: 1980,
      genre: "Sci-Fi",
    ).rating(5).execute(); // Optional fields use builder pattern

    // Subscribe to changes (not real-time, updates on execute)
    QueryRef listRef = MoviesConnector.instance.listMovies().ref();
    listRef.subscribe().listen((data) { /* update UI */ });
    await MoviesConnector.instance.createMovie(...);
    await listRef.execute(); // Triggers subscription update
    ```
*   **Data Types**: `Timestamp` (`firebase_data_connect.Timestamp`), `int` (32-bit and 64-bit), `DateTime`, `String` (for UUID), `double`, `bool`, `firebase_data_connect.AnyValue`.

## Data Seeding and Bulk Operations

*   **Local Development**:
    *   Use GraphQL mutations with `_insertMany` (for multi-table relationships) or `_upsertMany` to seed initial data or reset data for testing.
    *   Alternatively, `_deleteMany(all:true)` followed by `_insertMany` can reset data.
*   **Production**:
    *   **Firebase Admin SDK**: Recommended for bulk data operations due to privileged environment access.
        *   **Setup**: Install and set up the Admin SDK for Node.js.
        ```javascript
        import { initializeApp } from 'firebase-admin/app';
        import { getDataConnect } from 'firebase-admin/data-connect';
        const app = initializeApp();
        const dataConnect = getDataConnect({ serviceId: 'serviceId', location: 'us-west2' });
        ```
        *   **Emulator Integration**: Admin SDK automatically connects to Data Connect emulator if `DATA_CONNECT_EMULATOR_HOST` environment variable is set.
        *   **GraphQL Execution**: Use `dataConnect.executeGraphql(query, options)` for read/write or `dataConnect.executeGraphqlRead(query, options)` for read-only.
            *   Admin SDK ignores `@auth` directives, including `NO_ACCESS`.
            *   Can impersonate user credentials using `impersonate: { authClaims: { sub: 'uid' } }` or unauthenticated user using `impersonate: { unauthenticated: true }`.
        *   **Bulk Operations API**: Specialized methods for bulk mutations, constructing GraphQL mutations internally.
            ```javascript
            const dc = getDataConnect({ location: "us-west2", serviceId: "my-service" });
            await dc.insert("movie", data[0]);
            await dc.insertMany("movie", data);
            await dc.upsert("movie", data[0]);
            await dc.upsertMany("movie", data);
            ```
            *   Performance: Batching increases throughput, but too large batches can hit PostgreSQL statement length limits.
    *   **Direct SQL**: For stable production schemas where no schema modification is needed, direct SQL tools can be used with the Cloud SQL instance. **Caution**: Modifying schema directly can break Data Connect schema/connectors.

## Vector Similarity Search with Vertex AI

Firebase Data Connect supports vector similarity search using PostgreSQL's `pgvector` extension and Vertex AI's Embeddings API.
*   **Prerequisites**:
    *   Data Connect project setup.
    *   Supported Cloud SQL for PostgreSQL location (check limitations list).
    *   Vertex AI APIs enabled.
    *   Local PostgreSQL: `pgvector` extension installed and enabled (`CREATE EXTENSION vector`).
    *   IDX: `pgvector` extension enabled.
    *   Grant Vertex AI user IAM role (`roles/aiplatform.user`).
    *   Set up Google Cloud Application Default Credentials for local integration.
*   **Schema Design**: Add a `Vector` type field to your schema, specifying dimensions with `@col(size: X)`.
    ```graphql
    type Movie @table {
      id: ID! @col(name: "movie_id") @default(expr: "uuidV4()")
      title: String!
      description: String
      descriptionEmbedding: Vector! @col(size:768)
    }
    ```
*   **Embedding Generation (`_embed` server value)**: Directs Data Connect to call Vertex AI's Embedding APIs.
    ```graphql
    # Mutation to insert movie with auto-generated embedding
    mutation createMovie($title: String!, $description: String!) {
      movie_insert(data: {
        title: $title,
        description: $description,
        descriptionEmbedding_embed: {model: "textembedding-gecko@003", text: $description}
      })
    }
    ```
*   **Similarity Search Query**: Data Connect generates `${pluralType}_${vectorFieldName}_similarity` function.
    ```graphql
    query searchMovieDescriptionUsingL2Similarity ($query: String!) @auth(level: PUBLIC) {
      movies_descriptionEmbedding_similarity(
        compare_embed: {model: "textembedding-gecko@003", text: $query},
        where: {content: {ne: "No info available for this movie."}},
        limit: 5
      ) {
        id title description
        _metadata { distance } # Optional: retrieve distance
      }
    }
    ```
    *   **Parameters**:
        *   `compare_embed`: Generates embedding from text for comparison.
        *   `compare`: Use a custom `Vector` directly for comparison.
        *   `method`: Distance function (`COSINE`, `INNER_PRODUCT`, `L2`).
        *   `within`: Constraint on distance for results.
        *   `where`: Standard filter condition.
        *   `limit`: Number of results.
*   **Custom Embeddings**: Can store and use pre-generated `Vector` values directly.

## Deployment and Management

*   **Deployment Concepts**:
    *   **Schema Deployments**: Affects the Cloud SQL database's SQL schema.
        *   **Strict Mode**: Database schema *must exactly match* application schema. Tables/columns not in Data Connect schema are deleted.
        *   **Compatible Mode**: Database schema *must be compatible* (elements not used by app schema are left unmodified). Default behavior is to apply compatible changes and prompt for strict ones.
    *   **Connector Deployments**: Data Connect operations are stored on the server. CLI analyzes changes for potential breaking changes or altered client behavior.
*   **Deployment Workflow**:
    1.  List deployed resources: `firebase dataconnect:services:list`.
    2.  Manage schema updates:
        *   Check diffs: `firebase dataconnect:sql:diff`.
        *   Apply migrations: `firebase dataconnect:sql:migrate`.
    3.  Perform schema and connector deployments: `firebase deploy --only dataconnect`.
*   **Rollback**: Manual process by deploying a previous code version. Destructive changes may lead to data loss.
*   **Best Practices**:
    *   Source control schema/connector files.
    *   Minimize breaking changes (e.g., removing/renaming fields, changing nullability/data types).
    *   When removing fields: first remove references in connectors, deploy, update clients, then remove field from schema and migrate.
    *   Use `STRICT` mode for new databases to keep schemas aligned.
    *   Use `COMPATIBLE` mode for production databases with existing data to prevent unintended data loss.

## Service and Database Management

*   **Regions**: Data Connect services and associated Cloud SQL for PostgreSQL instances must be in the same region.
*   **Service Instances**: Created via Firebase console or `firebase init`.
*   **User Management**: Use Firebase IAM roles to control access to Data Connect services and Cloud SQL instances.
    *   `firebasedataconnect.*`: For Data Connect specific permissions.
    *   `roles/cloudsql.admin`: For Cloud SQL administrative tasks.
    *   `roles/cloudsql.client`: For connecting to Cloud SQL instances.
*   **Performance Monitoring**:
    *   Cloud SQL: Refer to Cloud SQL documentation for quotas and observability.
    *   Data Connect: Quotas for GraphQL requests (per-project and per-user limits).
*   **Cloud SQL Instance Administration**:
    *   Managed through Google Cloud console (stop/restart, create/delete databases, flags, extensions, monitoring, IAM, security).
    *   Free trial limitations (PostgreSQL 15.x, db-f1-micro, single-zone, no automatic backups/storage increase).
*   **Integrating Existing Databases**:
    1.  Select existing instance during Data Connect setup.
    2.  Run `firebase dataconnect:sql:setup` and *decline* Data Connect handling SQL migrations.
    3.  Write GraphQL schema to match existing database schema (use `firebase dataconnect:sql:diff` to help).
    4.  Apply SQL migrations using your custom tooling.

## Audit Logging

Firebase Data Connect integrates with Cloud Audit Logs.
*   **Log Types**:
    *   **Admin Activity**: Always enabled, logs metadata/configuration writes.
    *   **Data Access**: Disabled by default, logs metadata/configuration reads and user data reads/writes.
*   **Log Format**: `LogEntry` objects containing `AuditLog` data.
*   **Service Name**: `firebasedataconnect.googleapis.com`.
*   **Resource Type**: `audited_resource`.
*   **Viewing Logs**:
    *   **Cloud Logging Logs Explorer**: Filter by `Resource type` and `Log name`.
    *   `gcloud` CLI: `gcloud logging read "logName : projects/PROJECT_ID/logs/cloudaudit.googleapis.com"`.
    *   Logging API: `entries.list` method.
*   **Routing Logs**: Can route to Cloud Storage, BigQuery, Pub/Sub for longer retention, advanced search, or organization-wide aggregation.
