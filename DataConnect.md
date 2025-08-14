--- START OF FILE Pasted Text August 14, 2025 - 5:22PM ---

# Firebase Data Connect

Firebase's first relational database solution for developers who want to create secure and scalable apps with Cloud SQL for PostgreSQL and type-safe mobile and web SDKs. Learn more.

## Docs

*   [Firebase Data Connect](https://firebase.google.com/docs/data-connect.md.txt): Firebase's first relational database solution for developers who want to create secure and scalable apps with Cloud SQL for PostgreSQL and type-safe mobile and web SDKs. Learn more.
*   [Use the Admin SDK with Data Connect](https://firebase.google.com/docs/data-connect/admin-sdk.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Use generated Android SDKs](https://firebase.google.com/docs/data-connect/android-sdk.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Firebase CLI command reference for Data Connect](https://firebase.google.com/docs/data-connect/cli-reference.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Configuration and security reference](https://firebase.google.com/docs/data-connect/configuration-reference.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Seed data and perform bulk data operations](https://firebase.google.com/docs/data-connect/data-seeding-bulk-operations.md.txt): The Admin SDK is a set of server libraries that lets you interact with Firebase from privileged environments.
*   [Use generated iOS SDKs](https://firebase.google.com/docs/data-connect/ios-sdk.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Implement Data Connect mutations](https://firebase.google.com/docs/data-connect/mutations-guide.md.txt): Developer documentation for Firebase
*   [Implement Data Connect queries](https://firebase.google.com/docs/data-connect/queries-guide.md.txt): Developer documentation for Firebase
*   [Design Data Connect schemas](https://firebase.google.com/docs/data-connect/schemas-guide.md.txt): Developer documentation for Firebase
*   [Perform vector similarity search with Vertex AI](https://firebase.google.com/docs/data-connect/solutions-vector-similarity-search.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Use generated web SDKs](https://firebase.google.com/docs/data-connect/web-sdk.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Use AI assistance for Firebase Data Connect schemas, queries and mutations](https://firebase.google.com/docs/data-connect/ai-assistance.md.txt): Developer documentation for Firebase
*   [Secure Data Connect with authorization and attestation](https://firebase.google.com/docs/data-connect/authorization-and-security.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Common Expression Language syntax reference for Data Connect](https://firebase.google.com/docs/data-connect/cel-reference.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Audit logging for Firebase Data Connect](https://firebase.google.com/docs/data-connect/cloud-audit-logging.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Use the Data Connect emulator for CI/CD](https://firebase.google.com/docs/data-connect/data-connect-emulator-suite.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Use generated Flutter SDKs](https://firebase.google.com/docs/data-connect/flutter-sdk.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Deploy and manage Data Connect schemas and connectors](https://firebase.google.com/docs/data-connect/manage-schemas-and-connectors.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Manage Data Connect services and databases](https://firebase.google.com/docs/data-connect/manage-services-and-databases.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Firebase Data Connect pricing](https://firebase.google.com/docs/data-connect/pricing.md.txt): Firebase's first relational database solution for app developers to build mobile and web applications using a fully managed PostgreSQL database powered by Cloud SQL.
*   [Get started with Firebase Data Connect](https://firebase.google.com/docs/data-connect/quickstart.md.txt): Developer documentation for Firebase
*   [Get started with Firebase Data Connect locally](https://firebase.google.com/docs/data-connect/quickstart-local.md.txt): Developer documentation for Firebase

# Firebase Data Connect

Firebase Data Connect plat_ios plat_android plat_web plat_flutter

Firebase's first relational database solution for developers who want to create secure and scalable apps with Cloud SQL for PostgreSQL and type-safe mobile and web SDKs. [Learn more](https://firebase.google.com/products/data-connect).

Firebase Data Connect is a relational database service for mobile and web apps that lets you build and scale using a fully-managed PostgreSQL database powered by Cloud SQL. It provides secure schema, query and mutation management using GraphQL technology that integrates well with Firebase Authentication. You can quickly integrate this product into your mobile and web apps with SDK support in Kotlin Android, iOS, Flutter, and web.

Data Connect lets you declare your application's data model and the exact queries needed by your application. Using your data model we automatically create a PostgreSQL database schema to fit your data model, secure server endpoints that talk to the database, and type-safe SDKs for your client application that talk to the server endpoints. It's like a "self-driving app server" made-to-order for your specific application.

Key capabilities

How does it work?

The top-level resource for Firebase Data Connect is a *service*, which represents a managed GraphQL API that can be defined by developers and called by end users. Your *schema* is the app data model for a service, represented primarily as a collection of GraphQL source files, as well as specific configuration for attached datasources (such as Cloud SQL instances). There can be only one schema per service. Finally, your *connectors* are collections of queries and mutations that have been defined to operate against a service's schema. There can be many connectors per service (for instance if you have a "rider" app and a "driver" app for your rideshare company).

Your Data Connect schema maps explicitly to a specific underlying PostgreSQL database schema. Data Connect includes tooling to automatically generate the SQL DDL needed to perform schema migrations based on changes to the app schema. Based on your app schema, Data Connect automatically generates additional GraphQL schema to query and manipulate the data model.

Once your app schema is defined, you can write predefined queries and mutations that are executed to read and write data in the application. Data Connect queries and mutations are not submitted by client code and executed on the server. Instead, when deployed, these Data Connect operations are stored on the server, like Cloud Functions. This simplifies code management, and development of your client code. In privileged environments, like the Firebase console and using our Data Connect VS Code extension, you can execute ad hoc operations with appropriate Google IAM credentials for administrative operations.

For client code, each supported platform has a *core SDK* that handles connecting to the backend, issuing requests, and processing responses. These SDKs are not schema-aware and must be supplied with operation names and variables as unstructured data. Each supported platform also has a *generated SDK*. As you define your data model and operations, tooling on your machine will automatically generate strongly-typed SDKs specific to the application. These SDKs will "wrap" the core SDKs for type safety, ergonomics, and other features such as data validation and more down the road.

Implementation path

Next steps

*   Try out Data Connect right now: explore a quickstart app repository and build a fully-featured Data Connect app by following our [codelab for web](/codelabs/firebase-dataconnect-web), [codelab for iOS](/codelabs/firebase-dataconnect-ios), or [codelab for Android](/codelabs/firebase-dataconnect-android).
*   If you'd like to see the Firebase Data Connect development flow in action, read through the [Get started guide](/docs/data-connect/quickstart).
*   Learn about Data Connect [pricing and billing](/docs/data-connect/pricing).

# Use the Admin SDK with Data Connect

The Firebase Admin SDK is a set of server libraries that lets you interact with Firebase from privileged environments to perform actions like performing queries and mutations on a Firebase Data Connect service for bulk data management and other operations with elevated privileges and impersonated credentials.

The Admin SDK provides you with an API to call operations in both read/write and read-only modes. With the read-only operations, you have the peace of mind of implementing administrative functions that cannot modify data in your databases.

Admin SDK Setup

To get started using the with Firebase Data Connect on your server, you'll first need to [install and set up the Admin SDK for Node.js](/docs/admin/setup).

Initialize the Admin SDK in your scripts

To initialize the SDK, import the Data Connect extensions and declare your project service ID and location.

```javascript
import { initializeApp } from 'firebase-admin/app';
import { getDataConnect } from 'firebase-admin/data-connect';

// If you'd like to use OAuth2 flows and other credentials to log in,
// visit https://firebase.google.com/docs/admin/setup#initialize-sdk
// for alternative ways to initialize the SDK.

const app = initializeApp();

const dataConnect = getDataConnect({
    serviceId: 'serviceId',
    location: 'us-west2'
});
```

Design queries and mutations to use with the Admin SDK

The Admin SDK is useful for testing Data Connect operations, given the following considerations.

Understand the SDK and `@auth(level: NO_ACCESS)` operation directive

Since the Admin SDK operates with privileges, it can execute any of your queries and mutations regardless of access levels set using [`@auth` directives](/docs/data-connect/authorization-and-security), including the `NO_ACCESS` level.

> **Note:** If you do not set an access level for an operation, it is `NO_ACCESS` by default.

If alongside your client operations, you organize your administrative queries and mutations in `.gql` source files for import into administrative scripts, Firebase recommends that you mark the administrative operations without any authorization access level, or perhaps be more explicit and set them as `NO_ACCESS`. Either way, this prevents such operations from being executed from clients or in other non-privileged contexts.

Use the SDK with the Data Connect emulator

In prototype and test environments, it can be useful to perform data seeding and other operations on local data. The Admin SDK lets you simplify your workflows since it ignores authentication and authorization for local flows.

The Firebase Admin SDKs automatically connects to the Data Connect emulator when the `DATA_CONNECT_EMULATOR_HOST` environment variable is set:

```bash
export DATA_CONNECT_EMULATOR_HOST="127.0.0.1:9399"
```

For more information, see:

*   The [guide for data seeding in local development](/docs/data-connect/data-seeding-bulk-operations)
*   The [Data Connect emulator documentation](/docs/data-connect/data-connect-emulator-suite).

Implement common use cases

The Admin SDK is provided for privileged operations on your critical data.

The Admin SDK provides two interfaces:

*   A general interface for most read-write or read-only operations, in which your code implements queries and mutations and passes them to the read-write `executeGraphql` method or the read-only `executeGraphqlRead` method.
*   A specialized interface for bulk data operations, which instead of generic `executeGraphql` methods, exposes dedicated methods for mutation operations: `insert`, `insertMany`, `upsert`, and `upsertMany`.

Manage user data with `executeGraphql` methods

A typical use case for the Admin SDK is managing user data.

Use administrative credentials

The most straightforward approach is to access user data using administrative credentials.

```javascript
// User can be publicly accessible, or restricted to admins
const query = "query getProfile(id: AuthID) { user(id: $id) { id name } }";

interface UserData {
  user: {
    id: string;
    name: string;
  };
}

export interface UserVariables {
  id: string;
}

const options:GraphqlOptions<UserVariables> = { variables: { id: "QVBJcy5ndXJ1" } };

// executeGraphql
const gqlResponse = await dataConnect.executeGraphql<UserData, UserVariables>(query, options);

// executeGraphqlRead (similar to previous sample but only for read operations)
const gqlResponse = await dataConnect.executeGraphqlRead<UserData, UserVariables>(query, options);

// gqlResponse -> { "data": { "user": { "id": "QVBJcy5ndXJ1", "name": "Fred" } } }
```

Impersonate user credentials

There are also use cases where you want your scripts to modify user data based on limited credentials, on behalf of a specific user. This approach honors the principle of least privilege.

To use this interface, gather information from a customized JWT auth token that follows the [Authentication token format](/docs/data-connect/cel-reference#auth-token-contents). Also see the [custom tokens guide](https://firebase.google.com/docs/auth/admin/create-custom-tokens).

```javascript
// Get the current user's data
const queryGetUserImpersonation = `
    query getUser @auth(level: USER) {
        user(key: {uid_expr: "auth.uid"}) {
            id,
            name
        }
    }`;

// Impersonate a user with the specified auth claims
const optionsAuthenticated: GraphqlOptions<undefined> = {
    impersonate: {
        authClaims: {
            sub: 'QVBJcy5ndXJ1'
        }
    }
};

// executeGraphql with impersonated authenticated user scope
const gqlResponse = await dataConnect.executeGraphql<UserData, undefined>(queryGetUserImpersonation, optionsAuthenticated);

// gqlResponse -> { "data": { "user": { "id": "QVBJcy5ndXJ1", "name": "Fred" } } }
```

Manage public data with `executeGraphql` methods

You can work with publicly-acessible data using the SDK, impersonating an unauthenticated user.

```javascript
// Query to get posts, with authentication level PUBLIC
const queryGetPostsImpersonation = `
    query getPosts @auth(level: PUBLIC) {
        posts {
          description
        }
    }`;

// Attempt to access data as an unauthenticated user
const optionsUnauthenticated: GraphqlOptions<undefined> = {
    impersonate: {
        unauthenticated: true
    }
};

// executeGraphql with impersonated unauthenticated user scope
const gqlResponse = await dataConnect.executeGraphql<UserData, undefined>(queryGetPostsImpersonation, optionsUnauthenticated);

// gqlResponse -> { "data": { "user": { "id": "QVBJcy5ndXJ1", "name": "Fred" } } }
```

Perform bulk data operations

Firebase recommends you use the Admin SDK for bulk data operations on production databases.

The SDK provides the following methods for working with bulk data. From the provided arguments, each method constructs and executes a GraphQL mutation.

> **Note:** Specific workflows are described in more detail in the [Data seeding and bulk data management guide](/docs/data-connect/data-seeding-bulk-operations#bulk-data-adminsdk).

```javascript
// Methods of the bulk operations API
// dc is a Data Connect admin instance from getDataConnect

const resp = await dc.insert("movie" /*table name*/, data[0]);
const resp = await dc.insertMany("movie" /*table name*/, data);
const resp = await dc.upsert("movie" /*table name*/, data[0]);
const resp = await dc.upsertMany("movie" /*table name*/, data);
```

Performance notes for bulk operations

Each request to the backend will incur one round trip to Cloud SQL, so the more you batch, the higher the throughput is.

However, the larger the batch size, the longer the generated SQL statement is. When the PostgreSQL SQL statement length limit is reached, you will encounter an error.

In practice, experiment to find the appropriate batch size for your workload.

What's next?

*   Learn about [seeding your databases with data using the Admin SDK](/docs/data-connect/data-seeding-bulk-operations).
*   Review the [API for the Admin SDK](/docs/reference/admin/node/firebase-admin.data-connect).
*   Use the Firebase CLI and Google Cloud console for other project management operations, like [managing schemas and connectors](/docs/data-connect/manage-schemas-and-connectors) and [managing services and databases](/docs/data-connect/manage-services-and-databases).

# Use generated Android SDKs

Firebase Data Connect client SDKs let you call your server-side queries and mutations directly from a Firebase app. You generate a custom client SDK in parallel as you design the schemas, queries and mutations you deploy to your Data Connect service. Then, you integrate methods from this SDK into your client logic.

As we've mentioned elsewhere, it's important to note that Data Connect queries and mutations are not submitted by client code and executed on the server. Instead, when deployed, Data Connect operations are stored on the server like Cloud Functions. This means you need to deploy corresponding client-side changes to avoid breaking existing users (for example, on older app versions).

That's why Data Connect provides you with a developer environment and tooling that lets you prototype your server-deployed schemas, queries and mutations. It also generates client-side SDKs automatically, while you prototype.

When you've iterated updates to your service and client apps, both server- and client-side updates are ready to deploy.

What is the client development workflow?

If you followed the [Get started](/docs/data-connect/quickstart), you were introduced to the overall development flow for Data Connect. In this guide, you'll find more detailed information about generating Android SDKs from your schema and working with client queries and mutations.

> You can learn client development with a quickstart app repository and build a fully-featured Data Connect app by following our [codelab for Android](/codelabs/firebase-dataconnect-android).

To summarize, to use generated Android SDKs in your client apps, you'll follow these prerequisite steps:

1.  Add Firebase to your [Android](/docs/android/setup) app.
2.  Configure Data Connect as a dependency in Gradle.
3.  Add the Kotlin Serialization Gradle plugin and Gradle dependency.

Then:

1.  Develop your app schema.
2.  Set up SDK generation:
    *   With the **Add SDK to app** button in our Data Connect VS Code extension
    *   By [updating your `connector.yaml`](#generate-kotlin)
3.  [Initialize your client code and import libraries](#set-client).
4.  [Implement calls to queries and mutations](#queries-mutations).
5.  [Set up and use the Data Connect emulator](#prototype-and) and iterate.

Generate your Kotlin SDK

As with most Firebase projects, work on your Firebase Data Connect client code takes place in a local project directory. Both the Data Connect VS Code extension and the Firebase CLI are important local tools for generating and managing client code.

SDK generation options are keyed to several entries in the `dataconnect.yaml` file generated when you initialized your project.

Initialize SDK generation In your `connector.yaml`, add your `outputDir`, `package` and (for the web SDK) `packageJsonDir`.

```yaml
connectorId: movies
generate:
  kotlinSdk:
    outputDir: ../../../src/main/java/com/myapplication
    package: com.myapplication
```

Replace `outputDir` with the path of the directory into which the generated code will be placed; this path is relative to the directory that contains the `connector.yaml` file itself. Replace `package` with the Kotlin package statement to be used in the generated files, or omit `package` to use a default package.

> **Note:** Data Connect generates a default package with a name derived from the connector ID.
> **Note:** You can provide an absolute path to directories if your project is set up in a separate directory structure.

Update SDKs while prototyping

If you're prototyping interactively with the Data Connect VS Code extension and its Data Connect emulator, SDK source files are automatically generated and updated while you modify `.gql` files defining schemas, queries and mutations. This can be a useful feature in hot (re)loading workflows. In other scenarios, if you're using the Data Connect emulator from the Firebase CLI, you can set a watch on `.gql` updates and also have SDK sources automatically updated.

Alternatively, you can use the CLI to regenerate SDKs whenever .gql files are changed:

```bash
firebase dataconnect:sdk:generate --watch
```

Generate SDKs for integration and for production releases

In some scenarios, such as preparing project sources to submit for CI tests, you can call the Firebase CLI for a batch update.

In these cases, use `firebase dataconnect:sdk:generate`.

Set up client code

Incorporate Data Connect into your client code

To set up your client code to use Data Connect and your generated SDK, first follow the [standard Firebase setup instructions](//firebase.google.com/docs/android/setup).

Then, add the following into the `plugins` section in `app/build.gradle.kts`:

```kotlin
// The Firebase team tests with version 1.8.22; however, other 1.8 versions,
// and all newer versions are expected work too.
kotlin("plugin.serialization") version "1.8.22" // MUST match the version of the Kotlin compiler
```

Then, add the following into the `dependencies` section in `app/build.gradle.kts`:

```kotlin
implementation(platform("com.google.firebase:firebase-bom:33.16.0"))
implementation("com.google.firebase:firebase-dataconnect")
implementation("com.google.firebase:firebase-auth") // Optional
implementation("com.google.firebase:firebase-appcheck") // Optional
implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.7.3") // Newer versions should work too
implementation("org.jetbrains.kotlinx:kotlinx-serialization-core:1.5.1") // Newer versions should work too
```

Initialize the Data Connect Android SDK

Initialize your Data Connect instance using the information you used to set up Data Connect (all available in the Firebase console Data Connect tab).

The ConnectorConfig object

The SDK requires a connector configuration object.

This object is automatically generated from `serviceId` and `location` in `dataconnect.yaml`, and `connectorId` in `connector.yaml`.

Getting a connector instance

Now that you've set up a configuration object, get a Data Connect connector instance. The code for your connector will be generated by the Data Connect emulator. If your connector name is `movies` and the Kotlin package is `com.myapplication`, as specified in `connector.yaml`, then retrieve the connector object by calling:

```kotlin
val connector = com.myapplication.MoviesConnector.instance
```

Use queries and mutations from your Android SDK

With the connector object, you can run queries and mutations as defined in the GraphQL source code. Suppose your connector has these operations defined:

```graphql
mutation createMovie($title: String!, $releaseYear: Int!, $genre: String!, $rating: Int!) {
  movie_insert(data: {
    title: $title
    releaseYear: $releaseYear
    genre: $genre
    rating: $rating
  })
}

query getMovieByKey($key: Movie_Key!) {
  movie(key: $key) { id title }
}

query listMoviesByGenre($genre: String!) {
  movies(where: {genre: {eq: $genre}}) {
    id
    title
  }
}
```

then you could create and retrieve a movie as follows:

```kotlin
val connector = MoviesConnector.instance

val addMovieResult1 = connector.createMovie.execute(
  title = "Empire Strikes Back",
  releaseYear = 1980,
  genre = "Sci-Fi",
  rating = 5
)

val movie1 = connector.getMovieByKey.execute(addMovieResult1.data.key)

println("Empire Strikes Back: ${movie1.data.movie}")
```

You can also retrieve multiple movies:

```kotlin
val connector = MoviesConnector.instance

val addMovieResult2 = connector.createMovie.execute(
  title="Attack of the Clones",
  releaseYear = 2002,
  genre = "Sci-Fi",
  rating = 5
)

val listMoviesResult = connector.listMoviesByGenre.execute(genre = "Sci-Fi")

println(listMoviesResult.data.movies)
```

You can also collect a `Flow` that will only produce a result when a new query result is retrieved using a call to the query's `execute()` method.

> **Note:** This Flow is not updated in realtime.

```kotlin
val connector = MoviesConnector.instance

connector.listMoviesByGenre.flow(genre = "Sci-Fi").collect { data ->
  println(data.movies)
}

connector.createMovie.execute(
  title="A New Hope",
  releaseYear = 1977,
  genre = "Sci-Fi",
  rating = 5
)

connector.listMoviesByGenre.execute(genre = "Sci-Fi") // will cause the Flow to get notified
```

Prototype and test your Android application

Instrument clients to use a local emulator

You can use the Data Connect emulator, whether from the Data Connect VS Code extension or from the CLI.

Instrumenting the app to connect to the emulator is the same for both scenarios.

```kotlin
val connector = MoviesConnector.instance

// Connect to the emulator on "10.0.2.2:9399"
connector.dataConnect.useEmulator()

// (alternatively) if you're running your emulator on non-default port:
connector.dataConnect.useEmulator(port = 9999)

// Make calls from your app
```

To switch to production resources, comment out lines for connecting to the emulator.

Data types in Data Connect SDKs

The Data Connect server represents common and custom GraphQL data types. These are represented in the SDK as follows.

| Data Connect Type | Kotlin                                                     |
| :---------------- | :--------------------------------------------------------- |
| String            | String                                                     |
| Int               | Int (32-bit integer)                                       |
| Float             | Double (64-bit float)                                      |
| Boolean           | Boolean                                                    |
| UUID              | `java.util.UUID`                                           |
| Date              | `com.google.firebase.dataconnect.LocalDate` (was `java.util.Date` until 16.0.0-beta03) |
| Timestamp         | `com.google.firebase.Timestamp`                            |
| Int64             | Long                                                       |
| Any               | `com.google.firebase.dataconnect.AnyValue`                 |

# Firebase CLI command reference for Data Connect

The Firebase CLI is a tool that lets you to manage and configure Firebase products and services from the command line.

The CLI provides commands that can be used to perform a variety of Data Connect tasks, like creating a new Data Connect project, initializing a corresponding local working directory, setting up the Data Connect emulator, listing Data Connect resources, generating client SDKs and more.

Setup commands

Add Data Connect to a Firebase project

`firebase init`

Use `firebase init` to set up a new local project configuration. This workflow creates or updates [Firebase configuration files](./configuration-reference) in your directory.

```bash
firebase init
```

The `firebase init` flow guides you through setting up a service and database, and optionally installing the Data Connect emulator and configuring generated SDKs.

Service and database setup

If you select `dataconnect` for product setup, the CLI prompts you for a new service name and location, and whether to link an existing Cloud SQL for PostgreSQL instance or create a new instance.

If an existing instance is linked, the CLI checks for compatible settings, such as IAM authentication and public IP addresses.

> **Note:** Provisioning a new Cloud SQL instance during the flow can take up to 15 minutes.
> **Note:** If you would like to use customer-managed encryption keys (CMEK) make sure you link an existing Cloud SQL database with CMEK.

Local Emulator Suite setup

The CLI flow offers to set up emulators, including the Data Connect emulator.

Data Connect emulator commands

Start the Data Connect emulator

`emulators:start/exec`

```bash
firebase emulators:start/exec
```

Use the Local Emulator Suite version of the Data Connect emulator in interactive mode with `start` or script-driven, non-interactive mode with `exec`.

Export and import local PostgreSQL data

To support local prototyping and testing, and continuous integration, you can export the data stored in a local database instance and import it between development iterations and test runs.

Exports are stored as snapshots of your local PostgreSQL database.

Data Connect offers three approaches to export/import:

*   Automatic export/import configured in your `firebase.json` to provide snapshot backups on emulator shutdown and startup
*   Manual export/import using the CLI
*   Manual export/import using the VS Code extension interface

Automatic export and import configured in your `firebase.json`

To backup data between development sessions, specify an automatic backup location during the `firebase init` sequence. This location is stored in your `firebase.json` in the `emulators.dataconnect.dataDir` field. Any data changes you make will automatically be saved here between emulator runs, so it is useful during local testing and exploration.

Manual export: `emulators:export` and `emulators:start/exec --import`

While the Data Connect emulator is running, in a separate terminal, run the `firebase emulators:export` command to save a snapshot of your data. Then, you can start the emulator from that snapshot by using the `--import` flag.

```bash
# Export data from local emulator from a separate terminal
firebase emulators:export --only dataconnect <export_directory>

# Import data from local directory, here using emulators:exec
firebase emulators:exec ./<your-test-script>.sh --only dataconnect --import <import_directory>
```

> **Note:** An import directory you specify during manual import with the CLI `emulators:start --import` flag takes precedence over the default backup directory configured in `firebase.json`.
> **Note:** Manual import and export is a good way to seed tests with data in CI/CD.

Manual export/import: VS Code extension

In the VS Code extension UI, while the emulator is running, use the **Export emulator data** button to export data to export the current database contents. The default export location is the `exportedData` directory at the root of your project directory.

> **Note:** To modify this export location, before you start the emulator using the extension, click the **Configure emulator** link.

You can import this data using the CLI, as described in the previous section. You can also import this data before starting the emulator through VS Code by clicking the **Configure emulator** link and setting **Import Path**.

Schema and connector management commands

This section contains CLI reference information for commands you use to manage schemas and connectors.

> **Note:** You can limit access to PostgreSQL databases by granting more or less elevated roles to individual users. Behavior of the following commands may vary depending on the role the current user has. See [Cloud SQL management commands](#cloudsql-management-commands).

For how-to use cases and recommended practices related to these commands, see the [schema and connector management guide](/docs/data-connect/manage-schemas-and-connectors).

Deploy schemas and connectors

`deploy`

```bash
firebase deploy
```

This command deploys resources for Data Connect services indexed in [firebase.json](./configuration-reference). A [schema migration](#manage-cloudsql-schemas) and [connector update](#update-connectors) are performed if necessary.

With the `---only` flags, you can pass comma-separated values to deploy any subset of resources you want.

```bash
firebase deploy --only dataconnect:service1:schema,dataconnect:service2
```

List Data Connect services, schemas and connectors

`dataconnect:services:list`

```bash
firebase dataconnect:services:list
```

This command prints out basic info about the services, schemas, and connectors deployed on a project.

Compare and migrate SQL schemas

When you run [`firebase deploy`](#deploy-schema), the CLI performs a SQL schema comparison before deploying updates. You can also perform the comparison and update directly with a set of `dataconnect:sql` commands.

`dataconnect:sql:diff`

```bash
firebase dataconnect:sql:diff
```

This command compares local schema for a service with the current schema of the corresponding Cloud SQL database. It prints out the commands that would be run to migrate the database to your new schema.

`dataconnect:sql:migrate`

```bash
firebase dataconnect:sql:migrate
```

This command applies local schema changes to a service's Cloud SQL database.

When you set up a new local Data Connect project, with the default `dataconnect.yaml` file, the behavior of the `dataconnect:sql:migrate` command is to prompt you for any required changes, and then prompt for any optional changes, before executing the changes. You can modify this behavior to always include or ignore optional changes by updating your `dataconnect.yaml` configuration, as discussed in [migrate a schema in strict or compatible mode](#migrate-compat-strict-modes).

In interactive environments, the CLI displays each migration SQL statement (and whether it is destructive) and prompts for the changes you want to apply. Passing the `--force` flag is equivalent to accepting all prompts.

In noninteractive environments:

*   Without `--force`, only non-destructive changes are made. If there are destructive changes, the CLI aborts with no changes made.
*   With `--force`, all changes are made. If this includes any destructive changes, they are printed and you are prompted whether you want to continue, unless the `--force` flag is provided.

As with other `--only` flags, you can provide multiple services separated by commas.

Migrate a schema in strict or compatible mode

Data Connect schema migrations have two different schema validation modes: *strict* and *compatible*. Strict mode validation requires that the database schema exactly match the application schema before the application schema can be deployed. Compatible mode validation requires that the database schema be *compatible* with the application schema, meaning elements in your database that are not used by your application schema are left unmodified.

These schema validation modes and best practices for schema migration are covered in the [schema and connector management guide](/docs/data-connect/manage-schemas-and-connectors).

The validation mode is defined using the `schemaValidation` key in your `dataconnect.yaml` file. If `schemaValidation` is unspecified, the CLI applies compatible changes and prompts you before executing any strict changes. See the [configuration reference](/docs/data-connect/configuration-reference).

Manage changes to connectors

When you run [`firebase deploy`](#deploy-schema), the CLI initiates an update of the applicable connectors. The CLI analyzes changes to each connector and issues a set of assessment messages with respect to connector changes that may cause unexpected behavior (messages are warning-level) or breakages (messages are breaking-level) in previous versions of client code.

> **Note:** The following lists are not exhaustive. Refer to the CLI output messages for warnings and errors applicable to your connector.

In interactive environments, the CLI displays each connector assessment and prompts for the changes you want to apply. Passing the `--force` flag is equivalent to accepting all assessments.

In non-interactive environments:

*   if only warning-level assessments (possible behavior changes) occur, all connectors will be deployed and warnings will be logged to terminal.
*   if any breaking-level assessments occur, no connectors will be deployed and warnings will be logged to terminal. You can override with the `--force` flag.

Audit authorization code

Data Connect helps you audit your authorization strategy by analyzing your connector code when you deploy to the server using `firebase deploy` from the Firebase CLI. You can use this audit to help you review your codebase.

When you deploy your connectors, the CLI will output assessments for existing, modified and new operation code in your connector.

For modified and new operations, the CLI issues warnings and prompts you for confirmation when you use certain access levels in your new operations, or when you modify existing operations to use those access levels.

> **Note:** Insecure operation warnings are suppressed if you annotate the `@auth` directive in the operation with the [`insecureReason` argument](/docs/data-connect/authorization-and-security#insecureReasons).

Warnings and prompts always occur for:

*   `PUBLIC`

And, warnings and prompts occur on the following access levels when you *don't augment them* with filters using `auth.uid`:

*   `USER`
*   `USER_ANON`
*   `USER_EMAIL_VERIFIED`

For more information about authorization, refer to the [authorization and attestation guide](/docs/data-connect/authorization-and-security).

SDK commands

Generate SDKs

`dataconnect:sdk:generate`

```bash
firebase dataconnect:sdk:generate
```

This command generates the typed SDKs declared in [connector.yaml](./configuration-reference#connector.yaml-configuration).

Also see the guides for working with [the web SDKs](./web-sdk), [the Android SDKs](./android-sdk) and [the iOS SDKs](./ios-sdk).

With the `--only` flags, you can pass comma-separated values.

```bash
firebase dataconnect:sdk:generate ---only connector1, connector1:kotlin
```

Cloud SQL management commands

Grant SQL roles for Cloud SQL

Data Connect operates on top of your own PostgreSQL instance hosted on Cloud SQL. SQL role commands help you manage permissions on your database tables.

`dataconnect:sql:setup`

```bash
firebase dataconnect:sql:setup
```

This command configures initial, global permissions to tables in your database.

The default database provisioning and management flow assumes your project uses a new (greenfield) database, and when you invoke `firebase deploy`, Data Connect will display database schema changes to be made and performs any migrations after you approve. If this is your preferred flow, `dataconnect:sql:setup` prompts you to grant permissions including `superuser` schema ownerships.

For existing (brownfield) databases, you may have your own workflow for migrating schemas and want to maintain schema ownership yourself. If this is your preferred flow, make sure to **decline** at the `dataconnect:sql:setup` prompt for whether Data Connect should handle SQL migrations for you. As a result of declining, Data Connect will only take `read` and `write` access to your database tables, but schema ownerships and migrations will remain your responsibility.

For more discussion and use cases, see [Manage services and databases](/docs/data-connect/manage-services-and-databases#integrate-existing-databases).

`dataconnect:sql:grant`

```bash
firebase dataconnect:sql:grant
```

In some cases, you might want to access your database directly to query or update the data generated by your Data Connect apps. To do this, you will need to grant one of the roles defined in this section to the needed user or service account.

For details on the granted roles, see [PostgreSQL user roles](https://www.postgresql.org/docs/current/user-manag.html).

> **Note:** In addition to setting PostgreSQL roles with the Firebase CLI, you will need to assign the IAM role `roles/cloudsql.client`. See the [guide for managing services and databases](/docs/data-connect/manage-services-and-databases#sql-roles-cloudsql-iam).
> **Note:** These SQL roles are distinct from Cloud SQL IAM roles. IAM roles control who can access a database. SQL roles control which operations you can perform with such access, and which tables you can modify.

Global options

The following global options apply to all commands:

*   `--json` switches CLI output to JSON for parsing by other tools.
*   `--noninteractive` and `--interactive` override, as needed, automatic detection of non-TTY environments.

# Configuration and security reference

The Firebase CLI lets you manage your Firebase projects in a local, version-controllable project directory. This includes Data Connect services in your projects, connectors for those services, and resources like schema, query and mutation sources for each connector. The CLI also lets you install and operate the Firebase Data Connect emulator. The CLI is an efficient alternative to working in the Firebase console.

For instructions on installing the Firebase CLI experiment for Private Preview program, and Data Connect-related CLI commands, see the [CLI reference](./cli-reference).

> **Note:** Project configuration changes you make in the Firebase console are not automatically synchronized with configurations stored in a local project directory.

This reference guide documents:

*   Data Connect-specific entries in your `firebase.json` project configuration file.
*   Data Connect configurations in `dataconnect.yaml` and `connector.yaml`.
*   IAM roles you'll need to configure for your projects that use Data Connect.

Firebase project configuration files

`firebase.json` configuration reference

Use the `dataconnect` keys to configure one or more Data Connect services in your project.

```json
dataconnect: {
   source: string // Path to the directory containing the dataconnect.yaml service file.
}
```

`dataconnect.yaml` configuration reference

The `dataconnect.yaml` file stores configuration information about the locations of application schema sources, connector sources, and data source connection information. The file also serves as a project directory signifier for the Firebase CLI.

The `schemaValidation` key controls the level of schema validation performed when schemas are migrated during deployment. With no value set, the behavior of the `dataconect:sql:migrate` command is to apply compatible changes and prompt you before executing any strict changes. When set, the behavior is as follows:

*   `STRICT` mode. The database schema must exactly match the application schema before the application schema can be deployed. Any tables or columns that are not used in your Data Connect schema will be deleted from the database.
*   `COMPATIBLE` mode. The database schema must be compatible with the application schema before the application schema can be deployed; any additional changes are considered optional. Compatible means that schema migrations are based on the application schema you write. Elements in your database that are not used by your application schema are left unmodified. Therefore, after deployment, your backend may contain unused schemas, tables, and columns.

Values for other keys in this file are explained in the comments below.

```yaml
# The top-level Firebase Data Connect YAML file.

# The Firebase Data Connect API version to target.
# Optional. Defaults to the latest version.
specVersion: string

# The ID of the Firebase Data Connect service resource.
# Required.
serviceId: string

# The location of the Firebase Data Connect service.
# Required.
location: string

# Required.
schema:
  # Relative path to directory for schema definitions.
  # Recursively loads all .gql files in this directory.
  # Optional. If not present, defaults to ./schema.
  source: string
  # Datasource connection information.
  # Required.
  datasource:
    # Required.
    postgresql:
      # The name of the PostgreSQL database.
      # Required.
      database: string
      cloudSql:
        # The ID of the CloudSQL instance resource.
        # Required.
        instanceId: string
        # Schema validation mode for schema migrations.
        # Defaults to unspecified/commented out, meaning you are prompted to
        # review all changes during migration.
        # If desired, uncomment and indicate one of "STRICT" or "COMPATIBLE".
        schemaValidation: string

# Required.
# Relative paths to directories for connector definitions.
# Recursively loads all .gql files in the listed directories.
# All directories specified MUST contain a connector.yaml file.
connectorDirs: [string]
```

The YAML file assumes a default (but configurable) directory structure of:

```
./(project root)
   /dataconnect
      dataconnect.yaml
      /schema
        *.gql
      /connector
        connector.yaml
        *.gql
```

`connector.yaml` configuration reference

Use `connector.yaml` to configure default authentication mode and SDK generation options.

```yaml
# The connector-level YAML file.

# Required. The connector name of the Firebase Data Connect connector resource.
connectorId: string

# Optional. If not specified, no generated libraries (i.e. type-safe SDKs) will be generated.
generate:
    # Optional.
    javascriptSdk:
        # Path to the directory that will be updated with the latest generated
        # web SDK.
        # Required.
      - outputDir: string
        # Path to your package.json directory. If specified, the new generated sdk will be installed in this path.
        # Optional. If not provided, the package will not be auto-installed for you.
      - packageJsonDir: string
        # Name of the package to be created.
        # Optional. Defaults to @firebasegen/<connectorID>
      - package: string
        <option>: string
    # Optional.
    swiftSdk:
        # Path to the directory that will be updated with the latest generated
        # iOS Swift SDK.
        # Required.
      - outputDir: string
        # Name of the package to be created.
      - package: string
        <option>: string
    # Optional.
    kotlinSdk:
        # Path to the directory that will be updated with the latest generated
        # Android SDK.
        # Required.
      - outputDir: string
        # Name of the package to be created.
      - package: string
        <option>: string
```

IAM configuration for Data Connect projects

Granular IAM roles for Data Connect

Firebase basic roles and predefined roles map to lower-level Data Connect roles. Refer to the table for the mapping.

To manage individual IAM role assignments for Data Connect at a more granular level, use the [Google Cloud console](https://console.cloud.google.com).

> **Note:** For workflows associated with these IAM roles, see the [guide to managing services and databases](/docs/data-connect/manage-services-and-databases#manage-data-connect-users).

| IAM role                                                                                                                                              | Permissions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           ## Seed Data for Multi-Table Relationships with `_insertMany`

```graphql
mutation @transaction {
  movie_insertMany(data: [
    {
      id: "550e8400-e29b-41d4-a716-446655440000",
      title: "Inception",
      imageUrl: "https://firebasestorage.googleapis.com/v0/b/fdc-quickstart-web.appspot.com/o/movies%2Finception.jpg?alt=media&token=07b09781-b302-4623-a5c3-1956d0143168",
      genre: "sci-fi",
    },
    {
      id: "550e8400-e29b-41d4-a716-446655440001",
      title: "The Matrix",
      imageUrl: "https://firebasestorage.googleapis.com/v0/b/fdc-quickstart-web.appspot.com/o/movies%2Fthe_matrix.jpg?alt=media&token=4975645d-fef8-409e-84a5-bcc1046e2059",
      genre: "action",
    }
  ])

  actor_insertMany(data: [
    {
      id: "123e4567-e89b-12d3-a456-426614174000",
      imageUrl: "https://firebasestorage.googleapis.com/v0/b/fdc-quickstart-web.appspot.com/o/actors%2Fdicaprio.jpeg?alt=media&token=452e030a-efa5-4ef4-bb81-502b23241316",
      name: "Leonardo DiCaprio"
    },
    {
      id: "123e4567-e89b-12d3-a456-426614174001",
      imageUrl: "https://firebasestorage.googleapis.com/v0/b/fdc-quickstart-web.appspot.com/o/actors%2Fkeanu.jpg?alt=media&token=6056520c-ef3e-4823-aad0-108aab163115",
      name: "Keanu Reeves"
    }
   ])
}
```

Write a mutation to reset seed data

While prototyping and performing CI/CD, resetting the data to a zero state for executing a new series of tests on a new set of data can be useful.

To do so, if your prototype code does't add records to your tables, use the `_upsertMany` mutation provided by Data Connect.

> **Note:** Alternatively, you can call `_deleteMany(all:true)` followed by `_insertMany` to reset your data.

In the following example, `movie_upsertMany` is called with the initial values to update movie records to their original state.

```graphql
mutation {
  # Execute an upsertMany operation to update the Movie table
  movie_upsertMany(data: [
    {
      id: "550e8400-e29b-41d4-a716-446655440000",
      title: "Inception",
      imageUrl: "https://firebasestorage.googleapis.com/v0/b/fdc-quickstart-web.appspot.com/o/movies%2Finception.jpg?alt=media&token=07b09781-b302-4623-a5c3-1956d0143168",
      genre: "sci-fi",
    },
    {
      id: "550e8400-e29b-41d4-a716-446655440001",
      title: "The Matrix",
      imageUrl: "https://firebasestorage.googleapis.com/v0/b/fdc-quickstart-web.appspot.com/o/movies%2Fthe_matrix.jpg?alt=media&token=4975645d-fef8-409e-84a5-bcc1046e2059",
      genre: "action",
    }
   // ...
])
}
```

Production development: use the Admin SDK to populate and update

The Firebase Admin SDK is available for when you want to work from privileged environments. This is an important use case when you want to load thousands of records, given the critical nature of bulk data operations on your production data.

Install the Firebase Admin SDK

Even if you mainly work locally, Firebase recommends setting up the Admin SDK so you can use Firebase Data Connect from a privileged environment, including your local environment. You'll need to [set up the Admin SDK](/docs/admin/setup) for Node.js.

You can learn more about [using the Admin SDK in other Data Connect use cases](/docs/data-connect/admin-sdk).

Perform bulk loads and updates of production data

The API for bulk data management builds GraphQL mutations on your behalf, rather than asking you to build `mutation {...}` strings with the `executeGraphQL` API described earlier for adding a few rows here and there locally.

A major benefit of the administrative API is the ability to separately manage and re-use arrays of data for CI/CD flows, or set up large bulk data files for production data.

The following snippets demonstrate how to set up a bulk-data script.

```javascript
import { initializeApp } from 'firebase-admin/app';
import { getDataConnect } from 'firebase-admin/data-connect';

const app = initializeApp();

const dc = getDataConnect({ location: "us-west2", serviceId: "my-service" });

const data = [
 {
      id: "550e8400-e29b-41d4-a716-446655440000",
      title: "Inception",
      imageUrl: "https://firebasestorage.googleapis.com/v0/b/fdc-quickstart-web.appspot.com/o/movies%2Finception.jpg?alt=media&token=07b09781-b302-4623-a5c3-1956d0143168",
      genre: "sci-fi",
  },
  {
      id: "550e8400-e29b-41d4-a716-446655440001",
      title: "The Matrix",
      imageUrl: "https://firebasestorage.googleapis.com/v0/b/fdc-quickstart-web.appspot.com/o/movies%2Fthe_matrix.jpg?alt=media&token=4975645d-fef8-409e-84a5-bcc1046e2059",
      genre: "action",
    }
];

// Methods of the bulk operations API
const resp = await dc.insert("movie" /*table name*/, data[0]);
// Or
const resp = await dc.insertMany("movie" /*table name*/, data);

// Or
const resp = await dc.upsert("movie" /*table name*/, data[0]);
// Or
const resp = await dc.upsertMany("movie" /*table name*/, data);
```

Production development: use SQL for bulk data updates

When you're working with a stable schema in production, and are not modifying your schema, you can work in your Cloud SQL instance to manage data loads and updates.

> **Note:** Modifying your database *schema* directly with SQL tools can break your Data Connect schema and connectors.

Refer to the [Cloud SQL for PostgreSQL guide for importing data](//cloud.google.com/sql/docs/postgres/import-export/import-export-dmp).

What's next?

*   Learn about [integrating the Admin SDK into your Data Connect projects](/docs/data-connect/admin-sdk).

# Use generated iOS SDKs

Firebase Data Connect client SDKs let you call your server-side queries and mutations directly from a Firebase app. You generate a custom client SDK in parallel as you design the schemas, queries and mutations you deploy to your Data Connect service. Then, you integrate methods from this SDK into your client logic.

As we've mentioned elsewhere, it's important to note that Data Connect queries and mutations are not submitted by client code and executed on the server. Instead, when deployed, Data Connect operations are stored on the server like Cloud Functions. This means you need to deploy corresponding client-side changes to avoid breaking existing users (for example, on older app versions).

That's why Data Connect provides you with a developer environment and tooling that lets you prototype your server-deployed schemas, queries and mutations. It also generates client-side SDKs automatically, while you prototype.

When you've iterated updates to your service and client apps, both server- and client-side updates are ready to deploy.

What is the client development workflow?

If you followed the [Get started](/docs/data-connect/quickstart), you were introduced to the overall development flow for Data Connect. In this guide, you'll find more detailed information about generating Swift SDKs from your schema and working with client queries and mutations.

> You can learn client development with a quickstart app repository and build a fully-featured Data Connect app by following our [codelab for iOS](/codelabs/firebase-dataconnect-ios).

To summarize, to use generated Swift SDKs in your client apps, you'll follow these prerequisite steps:

1.  Add Firebase to your [iOS](/docs/ios/setup) app.
2.  To use the generated SDK, configure it as a dependency in Xcode.

    In the Xcode top navigation bar, select **File > Add Package Dependencies > Add Local**, and choose the folder containing the generated `Package.swift`.

Then:

1.  Develop your app schema.
2.  Set up SDK generation:
    *   With the **Add SDK to app** button in our Data Connect VS Code extension
    *   By [updating your `connector.yaml`](#generate-swift)
3.  [Initialize your client code and import libraries](#initialize-sdk).
4.  [Implement calls to queries and mutations](#queries-mutations).
5.  [Set up and use the Data Connect emulator](#prototype-and) and iterate.

Generate your Swift SDK

As with most Firebase projects, work on your Firebase Data Connect client code takes place in a local project directory. Both the Data Connect VS Code extension and the Firebase CLI are important local tools for generating and managing client code.

SDK generation options are keyed to several entries in the `dataconnect.yaml` file generated when you initialized your project.

Initialize SDK generation In your `connector.yaml`, add your `outputDir`, `package` and (for the web SDK) `packageJsonDir`.

```yaml
connectorId: "movies"
generate:
  swiftSdk:
    outputDir: "../movies-generated"
    package: "Movies"
```

`outputDir` specifies where the generated SDK should output to. If not specified, the connector folder is used as the default output directory.

`package` specifies the name of the package that will be generated. The generator will create a folder with the name of the package, containing `Package.swift` and generated code.

`observablePublisher` (optional) specifies the Observable publisher to use in query refs. Possible values are `observableMacro` (iOS 17+) and `observableObject` (pre - iOS 17). The default value, if none is specified, is `observableMacro`.

> **Note:** You can provide an absolute path to the output directory if your project is set up in a separate directory structure.

Update SDKs while prototyping

If you're prototyping interactively with the Data Connect VS Code extension and its Data Connect emulator, SDK source files are automatically generated and updated while you modify `.gql` files defining schemas, queries and mutations. This can be a useful feature in hot (re)loading workflows. In other scenarios, if you're using the Data Connect emulator from the Firebase CLI, you can set a watch on `.gql` updates and also have SDK sources automatically updated.

Alternatively, you can use the CLI to regenerate SDKs whenever .gql files are changed:

```bash
firebase dataconnect:sdk:generate --watch
```

Generate SDKs for integration and for production releases

In some scenarios, such as preparing project sources to submit for CI tests, you can call the Firebase CLI for a batch update.

In these cases, use `firebase dataconnect:sdk:generate`.

Initialize the Data Connect iOS SDK

Initialize your Data Connect instance using the information you used to set up Data Connect (all available in the Firebase console Data Connect tab).

Getting a connector instance

The code for your connector will be generated by the Data Connect emulator. If your connector name is `movies` and the package is `movies`, as specified in `connector.yaml`, then retrieve the connector object by calling:

```swift
let connector = DataConnect.moviesConnector
```

Implement queries and mutations

With the connector object, you can run queries and mutations as defined in the GraphQL source code. Suppose your connector has these operations defined:

```graphql
mutation createMovie($title: String!, $releaseYear: Int!, $genre: String!, $rating: Int!) {
  movie_insert(data: {
    title: $title
    releaseYear: $releaseYear
    genre: $genre
    rating: $rating
  })
}

query getMovieByKey($key: Movie_Key!) {
  movie(key: $key) { id title }
}

query listMoviesByGenre($genre: String!) {
  movies(where: {genre: {eq: $genre}}) {
    id
    title
  }
}
```

You can then create a movie as follows:

```swift
let mutationResult = try await connector.createMovieMutation.execute(
  title: "Empire Strikes Back",
  releaseYear: 1980,
  genre: "Sci-Fi",
  rating: 5)

print("Movie ID: \(mutationResult.data.movie_insert.id)")
```

To retrieve a movie, you will use a query reference. All query refs are Observable publishers. Depending on the configured publisher (see `connector.yaml)`, they either support the `@Observable` macro (iOS 17+) or implement the `ObservableObject` protocol. The default, if none is specified, is the `@Observable` macro supported on iOS 17+.

In a SwiftUI view, you can bind the query results using the published `data` variable of the query ref and call the query's `execute()` method to update the data. The `data` variable will match the shape of data that was defined in your GQL query definition.

All retrieved results comply with the `Decodable` protocol. If you included the object's primary key in your GQL fetch, the objects are also `Identifiable`, allowing you to use them in iterators.

> **Note:** The `@StateObject` is not updated in realtime. It is also not necessary when using an `@Observable` macro as the publisher.

```swift
struct ListMovieView: View {
    @StateObject private var queryRef = connector.listMoviesByGenreQuery.ref(genre: "Sci-Fi")
    var body: some View {
        VStack {
            Button {
                Task {
                    do {
                        try await refresh()
                    } catch {
                        print("Failed to refresh: \(error)")
                    }
                }
            } label: {
                Text("Refresh")
            }
                // use the query results in a view
            ForEach(queryRef.data?.movies ?? [], id: \.self.id) { movie in
                    Text(movie.title)
                }
            }
    }
    @MainActor
    func refresh() async throws {
        _ = try await queryRef.execute()
    }
}
```

Queries also support one-shot execution.

```swift
let resultData = try await DataConnect.moviesConnector.listMoviesByGenreQuery.execute(genre: "Sci-Fi")
```

Prototype and test your iOS application

Instrument clients to use a local emulator

You can use the Data Connect emulator, whether from the Data Connect VS Code extension or from the CLI.

Instrumenting the app to connect to the emulator is the same for both scenarios.

```swift
let connector = DataConnect.moviesConnector
// Connect to the emulator on "127.0.0.1:9399"
connector.useEmulator()

// (alternatively) if you're running your emulator on non-default port:
connector.useEmulator(port: 9999)

// Make calls from your app
```

Data types in Data Connect SDKs

The Data Connect server represents common and custom GraphQL data types. These are represented in the SDK as follows.

| Data Connect Type | Dart |
| :---------------- | :--- |

*(Table incomplete in source text)*

# Implement Data Connect mutations

Firebase Data Connect lets you create connectors for your PostgreSQL instances managed with Google Cloud SQL. These connectors are combinations of a queries and mutations for using your data from your schema.

> **Note:** Follow the complete series on building Data Connect schemas and connectors, which covers:
>
> *   [Schema development](/docs/data-connect/schemas-guide)
> *   [Query development](/docs/data-connect/queries-guide)
> *   Mutation development (this guide)

The [Get started guide](/docs/data-connect/quickstart) introduced a movie review app schema for PostgreSQL.

That guide also introduced both deployable and ad hoc administrative operations, including mutations.

*   **Deployable mutations** are those you implement to call from client apps in a connector, with API endpoints you define. Data Connect integrates authentication and authorization into these mutations, and generates client SDKs based on your API.
*   **Ad hoc administrative mutations** are run from privileged environments to populate and manage tables. You can create and execute them in the Firebase console, from privileged environments using the Firebase Admin SDK, and in local development environments using our Data Connect VS Code extension.

This guide takes a deeper look at **deployable mutations**.

Features of Data Connect mutations

Data Connect lets you to perform basic mutations in the all the ways you'd expect given a PostgreSQL database:

*   Perform CRUD operations
*   Manage multi-step operations with transactions

But with Data Connect's extensions to GraphQL, you can implement advanced mutations for faster, more efficient apps:

*   Use **key scalars** returned by many operations to simplify repeated operations on records
*   Use **server values** to populate data with operations provided by the server
*   Perform queries in the course of a multi-step mutation operations to look up data, saving lines of code and round trips to the server.

> **Note:** Before using this guide, review the movie review schema.
>
> Movie review app schema
>
> ```graphql
> # Movies
> type Movie
>   @table {
>   id: UUID! @default(expr: "uuidV4()")
>   title: String!
>   releaseYear: Int
>   genre: String
>   rating: Int
>   description: String
>   tags: [String]
> }
>
> # Movie Metadata
> # Movie - MovieMetadata is a one-to-one relationship
> type MovieMetadata
>   @table {
>   movie: Movie! @ref
>   director: String
> }
>
> // ... existing code ...
> extend type Movie {
>   movieMetadata: MovieMetadata
>   movieMetadatas_on_movie: MovieMetadata
> }
>
> # Actors
> # Suppose an actor can participate in multiple movies and movies can have multiple actors
> # Movie - Actors (or vice versa) is a many to many relationship
> type Actor @table {
>   id: UUID! @default(expr: "uuidV4()")
>   name: String!
> }
>
> # Join table for many-to-many relationship for movies and actors
> # The 'key' param signifies the primary keys of this table
> # In this case, the keys are [movieId, actorId], the foreign key fields of the reference fields [movie, actor]
> type MovieActor @table(key: ["movie", "actor"]) {
>   movie: Movie!
>   actor: Actor!
>   role: String! # "main" or "supporting"
>   # optional other fields
> }
>
> type User @table {
>   # `@default(expr: "auth.uid")` sets it to Firebase Auth UID during insert and upsert.
>   id: String! @default(expr: "auth.uid")
>   username: String!
> }
>
> # Reviews is a join table tween User and Movie.
> # It has a composite primary keys `userUid` and `movieId`.
> # A user can leave reviews for many movies. A movie can have reviews from many users.
> # User  <-> Review is a one-to-many relationship
> # Movie <-> Review is a one-to-many relationship
> # Movie <-> User is a many-to-many relationship
> type Review @table {
>   user: User!
>   movie: Movie!
>   rating: Int
>   reviewText: String
>   reviewDate: Date! @default(expr: "request.time")
>
> ```

Use generated fields to implement mutations

Your Data Connect operations will extend a set of fields automatically generated Data Connect based on the types and type relationships in your schema. These fields are generated by local tooling whenever you edit your schema.

> **Tip:** To discover the generated fields while building operations, use the query editor in the Firebase console, or our Visual Studio Code extension.

You can use generated fields to implement mutations, from creating, updating, and deleting individual records in single tables, to more complex multi-table updates.

Assume your schema contains a `Movie` type and an associated `Actor` type. Data Connect generates `movie_insert`, `movie_update`, `movie_delete` fields, and more.

> **Note:** These mutation fields return and let you pass a *key scalar* type, here a `Movie_Key`, to identify records. These are created based on your [schema](#key_scalars_and_server_values).

Mutation with the `movie_insert` field

Mutation with the `movie_update` field

Mutation with the `movie_delete` field

> **Tip:** The schema definition language also lets you explicitly control how names are generated for fields using [`singular` and `plural` arguments for the `@table` directive](/docs/reference/data-connect/gql/directive#customizations_2).

Essential elements of a mutation

Data Connect mutations are GraphQL mutations with Data Connect extensions. Just as with a regular GraphQL mutation, you can define an operation name and a list of GraphQL variables.

Data Connect extends GraphQL queries with customized **directives** like `@auth` and `@transaction`.

> **Tip:** You can use AI assistance to help you create and test GraphQL mutations in the Firebase console and in our local tooling. Learn more at [Use AI assistance for schemas, queries and mutations](/docs/data-connect/ai-assistance).

So the following mutation has:

*   A `mutation` type definition
*   A `SignUp` operation (mutation) name
*   A single variable `$username` operation argument
*   A single directive, `@auth`
*   A single field `user_insert`.

```graphql
mutation SignUp($username: String!) @auth(level: USER) {
  user_insert(data: {
    id_expr: "auth.uid"
    username: $username
  })
}
```

Every mutation argument requires a type declaration, a built-in like `String`, or a custom, schema-defined type like `Movie`.

> **Note:** The example shows how to sign up an account as yourself. Anyone that logs in can create a user account for themselves.

Write basic mutations

You can start writing mutations to create, update and delete individual records from your database.

> **Tip:** You can use Gemini in Firebase to help you create and run GraphQL mutations in the Firebase console. Learn more at [Use AI assistance for queries and mutations](/docs/data-connect/ai-assistance).

Create

Let's do basic creates.

```graphql
# Create a movie based on user input
mutation CreateMovie($title: String!, $releaseYear: Int!, $genre: String!, $rating: Int!) {
  movie_insert(data: {
    title: $title
    releaseYear: $releaseYear
    genre: $genre
    rating: $rating
  })
}

# Create a movie with default values
mutation CreateMovie2 {
  movie_insert(data: {
    title: "Sherlock Holmes"
    releaseYear: 2009
    genre: "Mystery"
    rating: 5
  })
}
```

Or an upsert.

```graphql
# Movie upsert using combination of variables and literals
mutation UpsertMovie($title: String!) {
  movie_upsert(data: {
    title: $title
    releaseYear: 2009
    genre: "Mystery"
    rating: 5
    genre: "Mystery/Thriller"
  })
}
```

Perform updates

Here are updates. Producers and directors certainly hope that those average ratings are on trend.

The `movie_update` field contains an expected `id` argument to identify a record and a `data` field you can use to set values in this update.

```graphql
mutation UpdateMovie(
  $id: UUID!,
  $genre: String!,
  $rating: Int!,
  $description: String!
) {
  movie_update(id: $id,
    data: {
      genre: $genre
      rating: $rating
      description: $description
    })
}
```

To perform multiple updates, use the `movie_updateMany` field.

```graphql
# Multiple updates (increase all ratings of a genre)
mutation IncreaseRatingForGenre($genre: String!, $rating: Int!) {
  movie_updateMany(
    where: { genre: { eq: $genre } },
    data:
      {
        rating: $rating
      })
}
```

Use increment, decrement, append, and prepend operations with `_update`

While in `_update` and `_updateMany` mutations you can explicitly set values in `data:`, it often makes more sense to apply an operator like increment to update values.

To modify the earlier update example, assume you want to increment the rating of a particular movie. You can use `rating_update` syntax with the `inc` operator.

```graphql
mutation UpdateMovie(
  $id: UUID!,
  $ratingIncrement: Int!
) {
  movie_update(id: $id, data: {
    rating_update: {
      inc: $ratingIncrement
    }
  })
}
```

Data Connect supports the following operators for field updates:

*   `inc` to increment `Int`, `Int64`, `Float`, `Date` and `Timestamp` data types
*   `dec` to decrement `Int`, `Int64`, `Float`, `Date` and `Timestamp` data types

> **Note:** For these operations, if an existing numeric is `null`, then it is treated as `0`. If an existing `Date` or `Timestamp` is `null`, then it is treated as the current date or time.

For lists, you can also update with individual values or lists of values using:

*   `add` to append item(s) if they are not already present to list types, except Vector lists
*   `remove` to remove all items, if present, from list types, except Vector lists
*   `append` to append item(s) to list types, except Vector lists
*   `prepend` to prepend item(s) to list types, except Vector lists

> **Note:** For these operations, if the existing list field is `null`, it is treated as an empty list.
> **Tip:** For details of the interface, see the [`_Update` and `_ListUpdate` reference documentation entries](/docs/reference/data-connect/gql/input_object).

Perform deletes

You can of course delete movie data. Film preservationists will certainly want the physical films to be maintained for as long as possible.

```graphql
# Delete by key
mutation DeleteMovie($id: UUID!) {
  movie_delete(id: $id)
}
```

Here you can use `_deleteMany`.

```graphql
# Multiple deletes
mutation DeleteUnpopularMovies($minRating: Int!) {
  movie_deleteMany(where: { rating: { le: $minRating } })
}
```

Write mutations on relations

Observe how to use the implicit `_upsert` mutation on a relation.

```graphql
# Create or update a one to one relation
mutation MovieMetadataUpsert($movieId: UUID!, $director: String!) {
  movieMetadata_upsert(
    data: { movie: { id: $movieId }, director: $director }
  )
}
```

> **Tip:** The complete set of GraphQL language extensions for Data Connect is [documented in the language reference guide](/docs/reference/data-connect).

Design schemas for efficient mutations

Data Connect provides two important features that allow you to write more efficient mutations and save round-trip operations.

**Key scalars** are concise object identifiers that Data Connect automatically assembles from key fields in your schemas. Key scalars are about efficiency, allowing you to find in a single call information about the identity and structure of your data. They are especially useful when you want to perform sequential actions on new records and need a unique identifier to pass to upcoming operations, and also when you want to access relational keys to perform additional more complex operations.

Using **server values**, you can effectively let the server dynamically populate fields in your tables using stored or readily-computable values according to particular server-side CEL expressions in the `expr` argument. For example, you can define a field with a timestamp applied when the field is accessed using the time stored in an operation request, `updatedAt: Timestamp! @default(expr: "request.time")`.

Write advanced mutations: let Data Connect supply values using `field_expr` syntax

As discussed in [key scalars and server values](#key_scalars_and_server_values), you can design your schema so that the server populates values for common fields like `id`s and dates in response to client requests.

In addition, you can make use of data, such as user IDs, sent in Data Connect `request` objects from client apps.

When you implement mutations, use `field_expr` syntax to trigger server-generated updates or access data from requests. For example, to pass the authorization `uid` stored in a request to an `_upsert` operation, pass `"auth.uid"` in the `userId_expr` field.

```graphql
# Add a movie to the user's favorites list
mutation AddFavoritedMovie($movieId: UUID!) @auth(level: USER) {
  favorite_movie_upsert(data: { userId_expr: "auth.uid", movieId: $movieId })
}

# Remove a movie from the user's favorites list
mutation DeleteFavoritedMovie($movieId: UUID!) @auth(level: USER) {
  favorite_movie_delete(key: { userId_expr: "auth.uid", movieId: $movieId })
}
```

Or, in a familiar to-do list app, when creating a new to-do list, you could pass `id_expr` to instruct the server to auto-generate a UUID for the list.

```graphql
mutation CreateTodoListWithFirstItem(
  $listName: String!
) @transaction {
  # Step 1
  todoList_insert(data: {
    id_expr: "uuidV4()", # <-- auto-generated. Or a column-level @default on `type TodoList` will also work
    name: $listName,
  })
}
```

For more information, see the `_Expr` scalars in the [scalars reference](/docs/reference/data-connect/gql/scalar).

Write advanced mutations: multi-step operations

There are many situations in which you might want to include multiple write fields (like inserts) in one mutation. You might also want to read your database during execution of a mutation to lookup and verify existing data before performing, for example, inserts or updates. These options save round trip operations and hence costs.

Data Connect lets you perform multi-step logic in your mutations by supporting:

*   Multiple write fields
*   Multiple read fields in your mutations (using the `query` field keyword).
*   The [`@transaction` directive](#query-mutation-directives), which provides transaction support familiar from relational databases.
*   The [`@check` directive](#query-mutation-directives), which lets you evaluate the contents of reads using CEL expressions, and based on the results of such evaluation:
    *   Proceed with creates, updates and deletes defined by a mutation
    *   Proceed to return the results of a query field
    *   Use returned messages to perform appropriate logic in your client code
*   The [`@redact` directive](#query-mutation-directives), which lets you omit query field results from wire protocol results.
*   The CEL `response` binding, which stores the accumulated results of all mutations and queries performed in a complex, multi-step operation. You can access the `response` binding:
    *   In `@check` directives, through the `expr:` argument
    *   With server values, using `field_expr` syntax

The `@transaction` directive

Support for multi-step mutations includes error handling using transactions.

The `@transaction` directive enforces that a mutation - with either a single write field (for example, `_insert` or `_update`) or with multiple write fields - always run in a database transaction.

*   Mutations without `@transaction` execute each root field one after another in sequence. The operation surfaces any errors as partial field errors, but not the impacts of the subsequent executions.
*   Mutations with `@transaction` are guaranteed to either fully succeed or fully fail. If any of the fields within the transaction fails, the entire transaction is rolled back.

The `@check` and `@redact` directives

The `@check` directive verifies that specified fields are present in query results. A Common Expression Language (CEL) expression is used to test field values. The default behavior of the directive is to check for and reject nodes whose value is `null` or `[]` (empty lists).

The `@redact` directive redacts a part of the response from the client. Redacted fields are still evaluated for side effects (including data changes and `@check`) and the results are still available to later steps in CEL expressions.

Use `@check`, `@check(message:)` and `@redact`

A major use for `@check` and `@redact` is looking up related data to decide whether certain operations should be authorized, using the lookup in logic but hiding it from clients. Your query can return useful messages for correct handling in client code.

For illustration, the following query field checks whether a requestor has an appropriate "admin" role to view users who can edit a movie.

```graphql
query GetMovieEditors($movieId: UUID!) @auth(level: USER) {
  moviePermission(key: { movieId: $movieId, userId_expr: "auth.uid" }) @redact {
    role @check(expr: "this == 'admin'", message: "You must be an admin to view all editors of a movie.")
  }
  moviePermissions(where: { movieId: { eq: $movieId }, role: { eq: "editor" } }) {
    user {
      id
      username
    }
  }
}
```

To learn more about `@check` and `@redact` directives in authorization checks, refer to the [discussion of authorization data lookup](/docs/data-connect/authorization-and-security#authz-data-lookup).

Use `@check` to validate keys

Some mutation fields, such as `_update`, may no-op if a record with a specified key does not exist. Similarly, lookups may return null or an empty list. These are not considered errors and therefore won't trigger rollbacks.

To guard against this result, test whether keys can be found using the `@check` directive.

```graphql
# Delete by key, error if not found
mutation MustDeleteMovie($id: UUID!) @transaction {
  movie_delete(id: $id) @check(expr: "this != null", message: "Movie not found, therefore nothing is deleted")
}
```

> **Tip:** See the [directives reference for the `@check` and `@redact` directives](/docs/reference/data-connect/gql/directive) and the [CEL expression reference](/docs/data-connect/cel-reference).

Use the `response` binding to chain multi-step mutations

The basic approach to creating related records, for example a new `Movie` and an associated `MovieMetadata` entry, is to:

1.  Call an `_insert` mutation for `Movie`
2.  Store the returned key of the created movie
3.  Then, call a second `_insert` mutation to create the `MovieMetadata` record.

But with Data Connect, you can handle this common case in a single multi-step operation by accessing the *results* of the first `_insert` in the second `_insert`.

Making a successful movie review app is a lot of work. Let's track our to-do list with a new example.

Use `response` to set fields with server values

In the following to-do list mutation:

*   The `response` binding represents the partial response object so far, which includes all top-level mutation fields before the current one.
*   The results of the initial `todoList_insert` operation, which returns the `id` (key) field, are accessed later in `response.todoList_insert.id` so we can immediately insert a new to-do item.

```graphql
mutation CreateTodoListWithFirstItem(
  $listName: String!,
  $itemContent: String!
) @transaction {
  # Sub-step 1:
  todoList_insert(data: {
    id_expr: "uuidV4()", # <-- auto-generated. Or a column-level @default on `type TodoList` will also work
    name: $listName,
  })
  # Sub-step 2:
  todo_insert(data: {
    listId_expr: "response.todoList_insert.id" # <-- Grab the newly generated ID from the partial response so far.
    content: $itemContent,
  })
}
```

> **Note:** Results of sub-steps are available in the same `@transaction`, so you still get the atomicity guarantees as you'd expect from a relational database.

Use `response` to validate fields using `@check`

`response` is available in `@check(expr: "...")` as well, so you can use it to build even more complicated server-side logic. Combined with `query { ... }` steps in mutations, you can achieve a lot more without any additional client-server roundtrips.

In the following example, note: that `@check` already has access to `response.query` because a `@check` always runs after the step it is attached to.

> **Tip:** You can hide results of intermediate steps from the wire and clients using `@redact`. Redacted fields are still available in `response` for use in later steps.

```graphql
mutation CreateTodoInNamedList(
  $listName: String!,
  $itemContent: String!
) @transaction {
  # Sub-step 1: Look up List.id by its name
  query
  @check(expr: "response.query.todoLists.size() > 0", message: "No such TodoList with the name!")
  @check(expr: "response.query.todoLists.size() < 2", message: "Ambiguous listName!") {
    todoLists(where: { name: $listName }) {
      id
    }
  }
  # Sub-step 2:
  todo_insert(data: {
    listId_expr: "response.todoLists[0].id" # <-- Now we have the parent list ID to insert to
    content: $itemContent,
  })
}
```

For more information about the `response` binding, see the [CEL reference](/docs/data-connect/cel-reference#the_response_binding).

Understand interrupted operations with `@transaction` and `query @check`

Multi-step mutations can encounter errors:

*   Database operations may fail.
*   query `@check` logic may terminate operations.

Data Connect recommends that you use the `@transaction` directive with your multi-step mutations. This results in a more consistent database and mutation results that are easier to handle in client code:

*   At the first error or failed `@check`, the operation will terminate, so there is no need to manage execution of any subsequent fields or evaluation of CEL.
*   Rollbacks are performed in response to database errors or `@check` logic, yielding a consistent database state.
*   A rollback error is always returned to client code.

There may be some use cases where you choose not to use `@transaction`: you might opt for eventual consistency if, for example, you need higher throughput, scalability or availability. However, you need to manage your database and your client code to allow for the results:

*   If one field fails due to database operations, subsequent fields will continue to execute. However, failed `@check`s still terminate the entire operation.
*   Rollbacks are not performed, meaning a mixed database state with some successful updates and some failed updates.
*   Your operations with `@check` may give more inconsistent results if your `@check` logic uses the results of reads and/or writes in a previous step.
*   The result returned to client code will contain a more complex mix of success and failure responses to be handled.

Directives for Data Connect mutations

In addition to the directives you use in defining types and tables, Data Connect provides the `@auth`, `@check`, `@redact` and `@transaction` directives for augmenting the behavior of operations.

> **Tip:** Complete reference documentation for these directives is available in the [directives reference guide](/docs/reference/data-connect/gql/directive).

Next steps

> **Note:** This guide is part of a complete series on building Data Connect schemas and connectors, which covers:
>
> *   [Schema development](/docs/data-connect/schemas-guide).
> *   [Query development](/docs/data-connect/queries-guide).
> *   Mutation development (this guide).

You may be interested in:

*   Generating mutations for your apps using [AI assistance tools](/docs/data-connect/ai-assistance).
*   Authorizing your mutations per the [authorization guide](/docs/data-connect/authorization-and-security).
*   Calling mutations from your client code for [web](/docs/data-connect/web-sdk), [iOS](/docs/data-connect/ios-sdk), [Android](/docs/data-connect/android-sdk) and [Flutter](/docs/data-connect/flutter-sdk).
*   Performing [bulk data operations with mutations](/docs/data-connect/data-seeding-bulk-operations).

# Implement Data Connect queries

Firebase Data Connect lets you create connectors for your PostgreSQL instances managed with Google Cloud SQL. These connectors are combinations of a queries and mutations for using your data from your schema.

> **Note:** Follow the complete series on building Data Connect schemas and connectors, which covers:
>
> *   [Schema development](/docs/data-connect/schemas-guide)
> *   Query development (this guide)
> *   [Mutation development](/docs/data-connect/mutations-guide)

The [Get started guide](/docs/data-connect/quickstart) introduced a movie review app schema for PostgreSQL.

That guide also introduced both deployable and ad hoc administrative operations, including queries.

*   **Deployable queries** are those you implement to call from client apps, with API endpoints you define. You bundle them into a **connector** deployed to the server. Data Connect tooling generates client SDKs based on your API. Deployed queries aren't protected by IAM policy, so be sure to secure them using the Data Connect `@auth` directive.
*   **Ad hoc administrative queries** are run from privileged environments to read data. You can create and execute them in the Firebase console or in local development environments using our Data Connect VS Code extension.

This guide takes a deeper look at **deployable queries**.

Features of Data Connect queries

Data Connect lets you perform basic queries in all the ways you'd expect given a PostgreSQL database.

But with Data Connect's extensions to GraphQL, you can implement advanced queries for faster, more efficient apps:

*   Use **key scalars** returned by many operations to simplify repeated operations on records
*   Perform queries in the course of a multi-step mutation operations to look up data, saving lines of code and round trips to the server.

> **Note:** Before using this guide, review the movie review schema.
>
> Movie review app schema
>
> ```graphql
>       type User @table {
>       id: String! @default(expr: "auth.uid")
>       username: String! @col(dataType: "varchar(50)")
>       }
>
>       type Review @table(name: "Reviews", key: ["movie", "user"]) {
>       user: User!
>       movie: Movie!
>       rating: Int
>       reviewText: String
>       reviewDate: Date! @default(expr: "request.time")
>       }
>
>       type Movie
>       @table(name: "Movies", singular: "movie", plural: "movies", key: ["id"]) {
>       id: UUID! @col(name: "movie_id") @default(expr: "uuidV4()")
>       title: String!
>       releaseYear: Int @col(name: "release_year")
>       genre: String
>       rating: Int @col(name: "rating")
>       description: String @col(name: "description")
>       tags: [String] @col(name: "tags")
>       }
>
>       type MovieMetadata
>       @table(
>         name: "MovieMetadata"
>       ) {
>       movie: Movie! @ref
>       director: String @col(name: "director")
>       }
>
>       extend type Movie {
>       movieMetadata: MovieMetadata
>       movieMetadatas_on_movie: MovieMetadata
>       }
>
>       type MovieActors @table(
>       key: ["movie", "actor"]
>       ) {
>       movie: Movie!
>       actor: Actor!
>       }
>
>       extend type MovieActors {
>       movieId: UUID!
>       actorId: UUID!
>       }
>
>       extend type Movie {
>       movieActors: [MovieActors!]!
>       actors: [Actor!]!
>       actors_via_MovieActors: [Actor!]!
>       }
>
>       extend type Actor {
>       movieActors: [MovieActors!]!
>       movies: [Movie!]!
>       movies_via_MovieActors: [Movie!]!
>       }
> ```

Use generated fields to build queries

Your Data Connect operations will extend a set of fields automatically generated Data Connect based on the types and type relationships in your schema. These fields are generated by local tooling whenever you edit your schema.

> **Tip:** To discover the generated fields while building operations, use the query editor in the Firebase console, or our Visual Studio Code extension.

You can use generated fields to implement increasingly complex queries, from retrieving individual records or multiple records from single tables to multiple records from related tables.

Assume your schema contains a `Movie` type and an associated `Actor` type. Data Connect generates `movie`, `movies`, `actors_on_movies` fields, and more.

> **Note:** These query fields let you pass a *key scalar* type, here a `Movie_Key`, to identify records. These are created based on your [schema](#key-scalars).

Query with the `movie` field

| Characteristic                                                                       | Example                                                                                                 |
| :----------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------ |
| The `movie` field represents a single record in the `Movie` table.              | Use this field to query a single movie by its key.                                                 |
| `graphql query GetMovie($myKey: Movie_Key!) { movie(key: $myKey) { title } }` | *(Content in second row is incomplete in source text, original markdown structure assumed)*              |

Query with the `movies` field

| Characteristic                                                                        | Example                                                                                                                                                                                           |
| :------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| The `movies` field represents a list of records in the `Movie` table.            | Use this field to query multiple movies, for example, all movies with a given year.                                                                                                  |
| `graphql query GetMovies($myYear: Int!) { movies(where: { year: { eq: $myYear } }) { title } }` | *(Content in second row is incomplete in source text, original markdown structure assumed)*                                                                                                |

Query with the `actors_on_movies` field

| Characteristic                                                                                                                                       | Example                                                                                                                                                                                                         |
| :--------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| The `actors_on_movies` field represents a list of records that connect `Actor` and `Movie` tables. Use this field to query all actors associated with a given movie. | Use this field to query all actors associated with a given movie.                                                                                                                                          |
| `graphql query GetActorsOnMovie($myKey: Movie_Key!) { actors_on_movies(where: { movie: { key: { eq: $myKey } } }) { actor { name } } }` | *(Content in second row is incomplete in source text, original markdown structure assumed)*                                                                                                                     |

> **Tip:** The schema definition language also lets you explicitly control how names are generated for fields using [`singular` and `plural` arguments for the `@table` directive](/docs/reference/data-connect/gql/directive#customizations_2).

Essential elements of a query

Data Connect queries are GraphQL queries with Data Connect extensions. Just as with a regular GraphQL query, you can define an operation name and a list of GraphQL variables.

Data Connect extends GraphQL queries with customized **directives** like `@auth`.

> **Tip:** You can use Gemini in Firebase to help you create and test GraphQL queries in the Firebase console. Learn more at [Use AI assistance for queries and mutations](/docs/data-connect/ai-assistance).

So the following query has:

*   A `query` type definition
*   A `ListMoviesByGenre` operation (query) name
*   A single query argument, here a `$genre` variable of `String` type
*   A single directive, `@auth`.
*   A single field, `movies`.

```graphql
query ListMoviesByGenre($genre: String!) @auth(level: PUBLIC) {
  movies(where: { genre: { eq: $genre } }) {
    id
    title
  }
}
```

Every query argument requires a type declaration, a built-in like `String`, or a custom, schema-defined type like `Movie`.

This guide will look at the signature of increasingly complex queries. You'll end by introducing powerful, concise relationship expressions you can use to build your deployable queries.

Key scalars in queries

But first, a note about key scalars.

Data Connect defines a special *key scalar* to represent primary keys of each table, identified by {TableType}\_Key. It is a JSON object of primary key values.

You retrieve key scalars as a response returned by most auto-generated read fields, or of course from queries where you have retrieved all the fields needed to build the scalar key.

Singular automatic queries, like `movie` in our running example, support a key argument that accepts a key scalar.

You might pass a key scalar as a literal. But, you can define variables to pass key scalars as input.

Query

```graphql
query GetMovie($myKey: Movie_Key!) {
  movie(key: $myKey) { title }
}
```

Response

```json
{
  "data": {
    "movie": {
      "title": "Example Movie Title"
    }
  }
}
```

These can be provided in request JSON like this (or other serialization formats):

```json
{
  # ...
  "variables": {
    "myKey": {"id": "xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx"}
  }
}
```

Thanks to custom scalar parsing, a `Movie_Key` can also be constructed using the object syntax, which may contain variables. This is mostly useful when you want to break individual components into different variables for some reason.

Write basic queries

You can start writing queries to get individual records from your database, or list records from a table with the option to limit and order results.

> **Tip:** You can use Gemini in Firebase to help you create and run GraphQL queries in the Firebase console. Learn more at [Use AI assistance for queries and mutations](/docs/data-connect/ai-assistance).

Retrieve individual records

The simplest query gets a single record by ID. Your query will use the auto-generated `movie` field.

Query

```graphql
query GetMovieById($id: UUID!) @auth(level: PUBLIC) {
  movie(id: $id) {
    id
    title
    imageUrl
    genre
  }
}
```

Response

```json
{
  "data": {
    "movie": {
      "id": "some-uuid",
      "title": "Example Movie Title",
      "imageUrl": "https://example.com/movie.jpg",
      "genre": "Action"
    }
  }
}```

Retrieve all records in a table

To retrieve a subset of fields for the full list of movies from the `Movies` table, your query will make use of the auto-generated `movies` field, and your implementation might look like the following.

Query

```graphql
query ListMovies @auth(level: PUBLIC) {
  movies {
    id
    title
    imageUrl
    genre
  }
}
```

Response

```json
{
  "data": {
    "movies": [
      {
        "id": "some-uuid",
        "title": "Example Movie Title",
        "imageUrl": "https://example.com/movie.jpg",
        "genre": "Action"
      },
      {
        "id": "another-uuid",
        "title": "Another Movie Title",
        "imageUrl": "https://example.com/another-movie.jpg",
        "genre": "Comedy"
      }
    ]
  }
}
```

Use `orderBy`, `limit` and `offset` operators

Naturally, listing all records from a table has limited usefulness.

You can order and perform pagination on results. These arguments are accepted but not returned in results.

Here, the query gets the titles of the top 10 movies by rating.

Query

```graphql
query MoviesTop10 {
  movies(orderBy: [{ rating: DESC }], limit: 10) {
    # graphql: list the fields from the results to return
    title
  }
}
```

Response

```json
{
  "data": {
    "movies": [
      { "title": "Top Movie 1" },
      { "title": "Top Movie 2" },
      { "title": "Top Movie 3" }
      // ... other 7 movies
    ]
  }
}
```

You might have a use case for fetching rows from an offset, like movies 11-20 ordered by rating.

Query

```graphql
query Movies11to20 {
  movies(orderBy: [{ rating: DESC }], limit: 10, offset: 10) {
    # graphql: list the fields from the results to return
    title
  }
}
```

Response

```json
{
  "data": {
    "movies": [
      { "title": "Movie 11" },
      { "title": "Movie 12" },
      { "title": "Movie 13" }
      // ... other 7 movies
    ]
  }
}
```

Use aliases in queries

Data Connect supports GraphQL aliasing in queries. With aliases, you rename the data that is returned in a query's results. A single Data Connect query can apply multiple filters or other query operations in one efficient request to the server, effectively issuing several "sub-queries" at once. To avoid name collisions in the returned dataset, you use aliases to distinguish the sub-queries.

Here is a query where an expression uses the aliases `mostPopular` and `leastPopular`.

Query

```graphql
query ReviewPopularitySpread($genre: String) {
  mostPopular: review(
    first: {
      where: {genre: {eq: $genre}},
      orderBy: {popularity: DESC}
    }
  ),
  leastPopular: review(
    last: {
      where: {genre: {eq: $genre}},
      orderBy: {popularity: DESC}
    }
  )
}
```

Response

```json
{
  "data": {
    "mostPopular": [
      { "popularity": 9 }
    ],
    "leastPopular": [
      { "popularity": 1 }
    ]
  }
}
```

Use query filters

Data Connect queries map to all common SQL filters and order operations.

Filter with `where` with `orderBy` operators

Returns all matched rows from the table (and nested associations). Returns an empty array if no records match the filter.

Query

```graphql
query MovieByTopRating($genre: String) {
  mostPopular: movies(
    where: { genre: { eq: $genre } },
    orderBy: { rating: DESC }
  ) {
    # graphql: list the fields from the results to return
    id
    title
    genre
    description
  }
}
```

Response

```json
{
  "data": {
    "mostPopular": [
      {
        "id": "some-uuid",
        "title": "Example Movie Title",
        "genre": "Action",
        "description": "A great movie"
      }
    ]
  }
}
```

Filter by testing for null values

You can test for `null` values using the `isNull` operator.

Query

```graphql
query ListMoviesWithoutDescription {
  movies(where: { description: { isNull: true }}) {
    id
    title
  }
}
```

Response

```json
{
  "data": {
    "movies": [
      {
        "id": "some-uuid",
        "title": "Example Movie Title"
      },
      {
        "id": "another-uuid",
        "title": "Another Movie Title"
      }
    ]
  }
}
```

For more operators, see the [input objects types reference guide](/docs/reference/data-connect/gql/input_object).

Filter with value comparisons

You can use operators like `lt` (less than) and `ge` (greater than or equal) to compare values in your queries.

Query

```graphql
query ListMoviesByRating($minRating: Int!, $maxRating: Int!) {
  movies(where: { rating: { ge: $minRating, lt: $maxRating }}) {
    id
    title
  }
}
```

Response

```json
{
  "data": {
    "movies": [
      {
        "id": "some-uuid",
        "title": "Example Movie Title"
      },
      {
        "id": "another-uuid",
        "title": "Another Movie Title"
      }
    ]
  }
}
```

Filter with `includes` and `excludes` operators for array fields

You can test that an array field includes a specified item.

The following example illustrates the `includes` operator.

Data Connect supports `includesAll`, `excludes`, `excludesAll` and more. Review all such operators for integers, strings, dates and other data types in the [`_ListFilter` headings of the reference documentation](/docs/reference/data-connect/gql/input_object).

Query

```graphql
query ListMoviesByTag($tag: String!) {
  movies(where: { tags: { includes: $tag }}) {
    # graphql: list the fields from the results to return
    id
    title
  }
}
```

Response

```json
{
  "data": {
    "movies": [
      {
        "id": "some-uuid",
        "title": "Example Movie Title"
      }
    ]
  }
}
```

Filter with string operations and regular expressions

Your queries can use typical string search and comparison operations, including regular expressions. Note for efficiency you are bundling several operations here and disambiguating them with aliases.

```graphql
query MoviesTitleSearch($prefix: String, $suffix: String, $contained: String, $regex: String) {
  prefixed: movies(where: {title: {startsWith: $prefix}}) {...}
  suffixed: movies(where: {title: {endsWith: $suffix}}) {...}
  contained: movies(where: {title: {contains: $contained}}) {...}
}
```

Filter with `_or`, `_and`, `_not` operator logic

Use `_or` for more complex logic. Data Connect also supports `_and` and `_not` operators.

Query

```graphql
query ListMoviesByGenreAndGenre($minRating: Int!, $genre: String) {
  movies(
    where: { _or: [{ rating: { ge: $minRating } }, { genre: { eq: $genre } }] }
  ) {
    # graphql: list the fields from the results to return
    title
  }
}
```

Response

```json
{
  "data": {
    "movies": [
      { "title": "Movie Title 1" },
      { "title": "Movie Title 2" }
    ]
  }
}
```

> **Tip:** The complete set of GraphQL language extensions for Data Connect is [documented in the language reference guide](/docs/reference/data-connect).

Write relational queries

Data Connect queries can access data based on the relationships among tables. You can use the object (one-to-one) or array (one-to-many) relationships defined in your schema to make nested queries, that is, fetch data for one type along with data from a nested or related type.

Such queries use magic Data Connect `_on_` and `_via` syntax in generated read fields.

Remember to review the [sample schema](#movie-schema-intro).

Many to one

Now look at a query to illustrate `_on_` syntax.

Query

```graphql
query MyReviews @auth(level: USER) {
  user(key: {id_expr: "auth.uid"}) {
    reviews: reviews_on_user {
      movie { name }
      rating
    }
  }
}
```

Response

```json
{
  "data": {
    "user": {
      "reviews": [
        {
          "movie": { "name": "Movie Title" },
          "rating": 5
        }
      ]
    }
  }
}
```

One to one

You can write a one-to-one query using `_on_` syntax.

Query

```graphql
query GetMovieMetadata($id: UUID!) @auth(level: PUBLIC) {
  movie(id: $id) {
    movieMetadatas_on_movie {
      director
    }
  }
}
```

Response

```json
{
  "data": {
    "movie": {
      "movieMetadatas_on_movie": {
        "director": "Some Director"
      }
    }
  }
}
```

Many to many

Many-to-many queries use `_via_` syntax. A many-to-many query might retrieve actors for a specified movie.

Query

```graphql
query MoviesActors($id: UUID!) @auth(level: USER) {
  movie(id: $id) {
     actors: actors_via_MovieActors {
        name
     }
  }
}
```

Response

```json
{
  "data": {
    "movie": {
      "actors": [
        {
          "name": "Actor Name"
        }
      ]
    }
  }
}
```

But we can write a more complex query, using aliases, to filter based on `role` to retrieve actors and associated movies in `mainActors` and `supportingActors` results. Since this is many-to-many, `_via_` syntax is used.

Query

```graphql
query GetMovieCast($movieId: UUID!, $actorId: UUID!) @auth(level: PUBLIC) {
  movie(id: $movieId) {
    mainActors: actors_via_MovieActor(where: { role: { eq: "main" } }) {
      name
    }
    supportingActors: actors_via_MovieActor(
      where: { role: { eq: "supporting" } }
    ) {
      name
    }
  }
  actor(id: $actorId) {
    mainRoles: movies_via_MovieActor(where: { role: { eq: "main" } }) {
      title
    }
    supportingRoles: movies_via_MovieActor(
      where: { role: { eq: "supporting" } }
    ) {
      title
    }
  }
}
```

Response

```json
{
  "data": {
    "movie": {
      "mainActors": [
        {
          "name": "Main Actor Name"
        }
      ],
      "supportingActors": [
        {
          "name": "Supporting Actor Name"
        }
      ]
    },
    "actor": {
      "mainRoles": [
        {
          "title": "Main Role Movie Title"
        }
      ],
      "supportingRoles": [
        {
          "title": "Supporting Role Movie Title"
        }
      ]
    }
  }
}
```

> **Tip:** The complete set of GraphQL language extensions for Data Connect is [documented in the language reference guide](/docs/reference/data-connect).

Aggregation queries

What are aggregates, and why use them?

Aggregate fields let you perform calculations on a list of results. With aggregate fields, you can do things like:

*   Find the average score of a review
*   Find the total cost of items in a shopping cart
*   Find the highest- or lowest-rated product
*   Count the number of products in your store

Aggregates are performed on the server, which offers a number of benefits over calculating them client side:

*   Faster app performance (since you avoid client side calculations)
*   Reduced data egress costs (since you send just the aggregated results instead of all of the inputs)
*   Improved security (since you can give clients access to aggregated data instead of the entire data set)

> **Note:** Refer to the Data Connect GraphQL reference documentation for the complete list of aggregation fields.

Example schema for aggregates

In this section, we'll switch to a storefront example schema, which is a good for explaining how to use aggregates:

```graphql
type Product @table {
  name: String!
  manufacturer: String!
  quantityInStock: Int!
  price: Float!
  expirationDate: Date
}
```

Simple aggregates

`_count` for all fields

The simplest aggregate field is `_count`: it returns how many rows match your query. For each field in your type, Data Connect generates corresponding aggregate fields depending on the field type.

Query

```graphql
query CountProducts {
  products {
    _count
  }
}
```

Response

```json
{
  "products": [
    {
    "_count": 5
    }
  ]
}
```

For example, if you have 5 products in your database, the result would be:

```json
{
  "products": [
    {
    "_count": 5
    }
  ]
}
```

All fields have a `<field>_count` field, which counts how many rows have a non-null value in that field.

Query

```graphql
query CountProductsWithExpirationDate {
  products {
    expirationDate_count
  }
}
```

Response

```json
{
  "products": [
    {
    "expirationDate_count": 3
    }
  ]
}
```

For example, if you have 3 products with an expiration date, the result would be:

```json
{
  "products": [
    {
    "expirationDate_count": 3
    }
  ]
}
```

`_min`, `_max`, `_sum`, and `_avg` for numeric fields

Numeric fields (int, float, int64) also have `<field>_min`, `<field>_max`, `<field>_sum`, and `<field>_avg`.

Query

```graphql
query NumericAggregates {
  products {
  quantityInStock_max
  price_min
  price_avg
  quantityInStock_sum
  }
}
```

Response

```json
{
  "products": [
    {
    "quantityInStock_max": 20,
    "price_min": 1.99,
    "price_avg": 3.6566666666666666,
    "quantityInStock_sum": 35
    }
  ]
}
```

For example, if you have the following products:

*   Product A: `quantityInStock: 10`, `price: 2.99`
*   Product B: `quantityInStock: 5`, `price: 5.99`
*   Product C: `quantityInStock: 20`, `price: 1.99`

The result would be:

```json
{
  "products": [
    {
    "quantityInStock_max": 20,
    "price_min": 1.99,
    "price_avg": 3.6566666666666666,
    "quantityInStock_sum": 35
    }
  ]
}
```

`_min` and `_max` for dates and timestamps

Date and timestamp fields have `<field>_min` and `<field>_max`.

Query

```graphql
query DateAndTimeAggregates {
  products {
  expirationDate_max
  expirationDate_min
  }
}
```

Response

```json
{
  "products": [
    {
    "expirationDate_max": "2024-03-01",
    "expirationDate_min": "2024-01-01"
    }
  ]
}
```

For example, if you have the following expiration dates:

*   Product A: `2024-01-01`
*   Product B: `2024-03-01`
*   Product C: `2024-02-01`

The result would be:

```json
{
  "products": [
    {
    "expirationDate_max": "2024-03-01",
    "expirationDate_min": "2024-01-01"
    }
  ]
}
```

Distinct

The `distinct` argument lets you get all unique values for a field (or combination of fields). For example:

Query

```graphql
query ListDistinctManufacturers {
  products(distinct: true) {
    manufacturer
  }
}
```

Response

```json
{
  "products": [
    { "manufacturer": "Acme" },
    { "manufacturer": "Beta" }
  ]
}
```

For example, if you have the following manufacturers:

*   Product A: `manufacturer: "Acme"`
*   Product B: `manufacturer: "Beta"`
*   Product C: `manufacturer: "Acme"`

The result would be:

```json
{
  "products": [
    { "manufacturer": "Acme" },
    { "manufacturer": "Beta" }
  ]
}
```

You can also use the `distinct` argument on aggregate fields to instead aggregate the distinct values. For example:

Query

```graphql
query CountDistinctManufacturers {
  products {
    manufacturer_count(distinct: true)
  }
}
```

Response

```json
{
  "products": [
    {
    "manufacturer_count": 2
    }
  ]
}
```

For example, if you have the following manufacturers:

*   Product A: `manufacturer: "Acme"`
*   Product B: `manufacturer: "Beta"`
*   Product C: `manufacturer: "Acme"`

The result would be:

```json
{
  "products": [
    {
    "manufacturer_count": 2
    }
  ]
}
```

Grouped aggregates

You perform a grouped aggregate by selecting a mix of aggregate and non-aggregate fields on a type. This groups together all matching rows that have the same value for the non-aggregate fields, and calculate the aggregate fields for that group. For example:

Query

```graphql
query MostExpensiveProductByManufacturer {
  products {
  manufacturer
  price_max
  }
}
```

Response

```json
{
  "products": [
    { "manufacturer": "Acme", "price_max": 2.99 },
    { "manufacturer": "Beta", "price_max": 5.99 }
  ]
}
```

For example, if you have the following products:

*   Product A: `manufacturer: "Acme"`, `price: 2.99`
*   Product B: `manufacturer: "Beta"`, `price: 5.99`
*   Product C: `manufacturer: "Acme"`, `price: 1.99`

The result would be:

```json
{
  "products": [
    { "manufacturer": "Acme", "price_max": 2.99 },
    { "manufacturer": "Beta", "price_max": 5.99 }
  ]
}
```

`having` and `where` with grouped aggregates

You can also use the `having` and `where` argument to only return groups that meet a provided criteria.

*   `having` lets you filter groups by their aggregate fields
*   `where` lets you filter the rows based on non-aggregate fields.

Query

```graphql
query FilteredMostExpensiveProductByManufacturer {
  products(having: {price_max: {ge: 2.99}}) {
  manufacturer
  price_max
  }
}
```

Response

```json
{
  "products": [
    { "manufacturer": "Acme", "price_max": 2.99 },
    { "manufacturer": "Beta", "price_max": 5.99 }
  ]
}
```

For example, if you have the following products:

*   Product A: `manufacturer: "Acme"`, `price: 2.99`
*   Product B: `manufacturer: "Beta"`, `price: 5.99`
*   Product C: `manufacturer: "Acme"`, `price: 1.99`

The result would be:

```json
{
  "products": [
    { "manufacturer": "Acme", "price_max": 2.99 },
    { "manufacturer": "Beta", "price_max": 5.99 }
  ]
}
```

Aggregates across tables

Aggregate fields can be used in concert with generated one-to-many relationship fields to answer complex questions about your data. Here is a modified schema, with separate table, `Manufacturer`, we can use in examples:

```graphql
type Product @table {
  name: String!
  manufacturer: Manufacturer!
  quantityInStock: Int!
  price: Float!
  expirationDate: Date
}

type Manufacturer @table {
  name: String!
  headquartersCountry: String!
}
```

Now we can use aggregate fields to do things like find how many products a manufacturer makes:

Query

```graphql
query GetProductCount($id: UUID) {
  manufacturers {
    name
    products_on_manufacturer {
      _count
    }
  }
}
```

Response

```json
{
  "manufacturers": [
    { "name": "Acme", "products_on_manufacturer": { "_count": 2 } },
    { "name": "Beta", "products_on_manufacturer": { "_count": 1 } }
  ]
}```

For example, if you have the following manufacturers:

*   Manufacturer A: `name: "Acme"`, `products_on_manufacturer: 2`
*   Manufacturer B: `name: "Beta"`, `products_on_manufacturer: 1`

The result would be:

```json
{
  "manufacturers": [
    { "name": "Acme", "products_on_manufacturer": { "_count": 2 } },
    { "name": "Beta", "products_on_manufacturer": { "_count": 1 } }
  ]
}
```

Write advanced queries: use `query` fields to read data in multi-step operations

There are many situations in which you might want to read your database during execution of a mutation to lookup and verify existing data before performing, for example, inserts or updates. These options save round trip operations and hence costs.

Data Connect supports this functionality. See [multi-step operations](/docs/data-connect/mutations-guide#multi-step-operations).

Next steps

> **Note:** Follow the complete series on building Data Connect schemas and connectors, which covers:
>
> *   [Schema development](/docs/data-connect/schemas-guide)
> *   Query development (this guide)
> *   [Mutation development](/docs/data-connect/mutations-guide)

You may be interested in:

*   Generating queries for your apps using [AI assistance tools](/docs/data-connect/ai-assistance).
*   Authorizing your queries per the [authorization guide](/docs/data-connect/authorization-and-security).
*   Calling queries from your client code for [web](/docs/data-connect/web-sdk), [iOS](/docs/data-connect/ios-sdk), [Android](/docs/data-connect/android-sdk) and [Flutter](/docs/data-connect/flutter-sdk).

# Design Data Connect schemas

With Firebase Data Connect, you design a GraphQL schema that represents the data model required for your application. Data Connect converts this schema to the Cloud SQL for PostgreSQL instance that backs your app. You then author queries and mutations to interface with the backend and bundle these operations into connectors for using your data from client code.

Data Connect offers AI tooling to help you design and implement your schemas. This guide introduces important concepts of schema design to support and complement your standard and AI-assisted workflows when you [start developing an app](/docs/data-connect/quickstart), and [beyond](/docs/data-connect/ai-assistance).

> **Note:** Follow the complete series on building Data Connect schemas and connectors, which covers:
>
> *   Schema development (this guide)
> *   [Query development](/docs/data-connect/queries-guide)
> *   [Mutation development](/docs/data-connect/mutations-guide)

The [Get started guide](/docs/data-connect/quickstart) introduced a movie review app schema for PostgreSQL.

This guide develops that schema further and provides a [SQL listing](#equivalent-sql) equivalent to the final movie review app schema.

The schema for a movie review app

Imagine you want to build a service that lets users submit and view movie reviews.

You need an initial schema for such an app to support basic queries. You will extend this schema later to create complex relational queries.

In Data Connect, you'll define *GraphQL types* to define the shape of the data your clients can query and manipulate. When you write your schema, your types are translated to Cloud SQL for PostgreSQL tables, most often in a direct relationship between GraphQL types and database tables, though other mappings are possible. This guide shows some examples from basic to more advanced.

Define a basic `Movie` type

You can start with a `Movie` type.

The schema for `Movie` contains core directives like:

*   `@table(name)` and `@col(name)` to customize the SQL table and column names. Data Connect generates snake_case names if not specified.
*   `@col(dataType)` to customize SQL column types.
*   `@default` to configure SQL column default values during insert.

For more details, check out the reference docs for [`@table`](/docs/reference/data-connect/gql/directive?#table), [`@col`](/docs/reference/data-connect/gql/directive?#col), [`@default`](/docs/reference/data-connect/gql/directive?#default).

> **Note:** The underscore character, `_`, cannot be used in field names. Data Connect uses that character when it generates supplemental fields, and implicit queries and mutations.

```graphql
# Movies
type Movie @table(name: "movie", key: "id") {
  id: UUID! @col(name: "movie_id") @default(expr: "uuidV4()")
  title: String!
  releaseYear: Int
  genre: String @col(dataType: "varchar(20)")
  rating: Int
  description: String
}
```

Store important user data automatically in a `User` type

Your app will keep track of users, so you need a `User` type.

The `@default` directive is especially useful in this case. The `id` field here can automatically grab the user's ID from authentication: note the use of `@default(expr: "auth.uid")` in the following sample.

```graphql
# Users
# Suppose a user can leave reviews for movies
type User @table {
  id: String! @default(expr: "auth.uid")
  username: String! @col(dataType: "varchar(50)")
}
```

> **Tip:** The complete set of GraphQL language extensions for Data Connect is [documented in the language reference guide](/docs/reference/data-connect).

Key scalars and server values

Before looking more at the movie review app, it's important to introduce Data Connect *key scalars* and *server values*.

**Key scalars** are concise object identifiers that Data Connect automatically assembles from key fields in your schemas. Key scalars are about efficiency, allowing you to find in a single call information about the identity and structure of your data. They are especially useful when you want to perform sequential actions on new records and need a unique identifier to pass to upcoming operations, and also when you want to access relational keys to perform additional more complex operations.

Using **server values**, you can effectively let the server dynamically populate fields in your tables using stored or readily-computable values according to particular server-side CEL expressions in the `expr` argument. For example, you can define a field with a timestamp applied when the field is accessed using the time stored in an operation request, `updatedAt: Timestamp! @default(expr: "request.time")`.

Handle many-to-many relationships in `Actor` and `MovieActor` types

With users handled, you can get back to modeling movie data.

Next, you want actors to star in your movies.

The `Actor` table is pretty straightforward.

```graphql
# Actors
# Suppose an actor can participate in multiple movies and movies can have multiple actors
# Movie - Actors (or vice versa) is a many to many relationship
type Actor @table {
  id: UUID! @default(expr: "uuidV4()")
  name: String! @col(dataType: "varchar(30)")
}
```

If you want actors to be in multiple movies and movies to have multiple actors, you'll need a "join table."

The `MovieActor` table handles the **many-to-many** relationship, and its primary key is a combination of `[movie, actor]` (the foreign key fields from `movie` and `actor`).

```graphql
# Join table for many-to-many relationship for movies and actors
# The 'key' param signifies the primary keys of this table
# In this case, the keys are [movieId, actorId], the foreign key fields of the reference fields [movie, actor]
type MovieActor @table(key: ["movie", "actor"]) {
  movie: Movie!
  # movieId: UUID! <- implicitly added foreign key field
  actor: Actor!
  # actorId: UUID! <- implicitly added foreign key field
  role: String! # "main" or "supporting"
  # optional other fields
}
```

When you define a SQL relationship on the table with a foreign key constraint, Data Connect automatically generates the corresponding field on the other side. You don't need to define the reverse mapping field (e.g., from `Actor` back to `MovieActor`).

> **Note:** Relations are defined on one side, not both! Data Connect generates names with underscores (like `actors_on_movies` and `actors_via_actormovie`) to avoid clashes with your own field names.

Handle one-to-one relationships in a `MovieMetadata` type

Now, keep track of movie directors, as well as set up a **one-to-one** relationship with `Movie`.

You can use the `@ref` directive to customize foreign key constraints:

*   `@ref(fields)` specifies which foreign key fields to use.
*   `@ref(references)` specifies the fields referenced in the target table (defaults to the primary key, but `@unique` fields work too). This is a more advanced option; Data Connect can often infer this for you.

For more details, check out the reference docs for [`@ref`](/docs/reference/data-connect/gql/directive?#ref).

```graphql
# Movie Metadata
# Movie - MovieMetadata is a one-to-one relationship
type MovieMetadata @table {
  # @unique ensures that each Movie only has one MovieMetadata.
  movie: Movie! @unique
  # Since it references to another table type, it adds a foreign key constraint.
  #  movie: Movie! @unique @ref(fields: "movieId", references: "id")
  #  movieId: UUID! <- implicitly added foreign key field
  director: String
}
```

Use fields generated from your schema to build operations

Your Data Connect operations will extend a set of fields automatically generated Data Connect based on the types and type relationships in your schema. These fields are generated by local tooling whenever you edit your schema.

> **Tip:** To discover the generated fields while building operations, use the query editor in the Firebase console, or our Visual Studio Code extension.

Assume your schema contains a `Movie` type and an associated `Actor` type. Data Connect generates `movie`, `movies`, `actors_on_movies` fields, and more.

> **Note:** These query fields let you pass a *key scalar* type, here a `Movie_Key`, to identify records. These are created based on your schema.

Query with the `movie` field

| Characteristic                                                                       | Example                                                                                                 |
| :----------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------ |
| The `movie` field represents a single record in the `Movie` table.              | Use this field to query a single movie by its key.                                                 |
| `graphql query GetMovie($myKey: Movie_Key!) { movie(key: $myKey) { title } }` | *(Content in second row is incomplete in source text, original markdown structure assumed)*              |

Query with the `movies` field

| Characteristic                                                                        | Example                                                                                                                                                                                           |
| :------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| The `movies` field represents a list of records in the `Movie` table.            | Use this field to query multiple movies, for example, all movies with a given year.                                                                                                  |
| `graphql query GetMovies($myYear: Int!) { movies(where: { year: { eq: $myYear } }) { title } }` | *(Content in second row is incomplete in source text, original markdown structure assumed)*                                                                                                |

Query with the `actors_on_movies` field

| Characteristic                                                                                                                                       | Example                                                                                                                                                                                                         |
| :--------------------------------------------------------------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| The `actors_on_movies` field represents a list of records that connect `Actor` and `Movie` tables. Use this field to query all actors associated with a given movie. | Use this field to query all actors associated with a given movie.                                                                                                                                          |
| `graphql query GetActorsOnMovie($myKey: Movie_Key!) { actors_on_movies(where: { movie: { key: { eq: $myKey } } }) { actor { name } } }` | *(Content in second row is incomplete in source text, original markdown structure assumed)*                                                                                                                     |

> **Tip:** The schema definition language also lets you explicitly control how names are generated for fields using [`singular` and `plural` arguments for the `@table` directive](/docs/reference/data-connect/gql/directive#customizations_2).

With this in mind, you can read how to implement operations using these fields in the [guide to implementing queries](/docs/data-connect/queries-guide) and [guide to implementing mutations](/docs/data-connect/mutations-guide).

> **Note:** See the [quickstart guide](/docs/data-connect/quickstart) or [local quickstart guide](/docs/data-connect/quickstart-local) for more on how to discover auto-generated fields.

More advanced schema concepts

To move beyond basic but useful types and relationships, refer to examples in the [reference documentation](/docs/reference/data-connect/gql/object).

Supported data types

Data Connect supports the following scalar data types, with assignments to PostgreSQL types using `@col(dataType:)`.

> **Note:** If you assign a PostgreSQL serial `dataType` in your schema (for example, `myField: Int @col(dataType: "serial")`). the corresponding database column is a PostgreSQL serial (autoincrementing) type.

| Data Connect type | GraphQL built-in type or Data Connect custom type | Default PostgreSQL type                                    | Supported PostgreSQL types **(alias in parentheses)**                                                                                                                                         |
| :---------------- | :------------------------------------------------ | :--------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| String            | GraphQL                                           | text                                                       | text bit(n), varbit(n) char(n), varchar(n)                                                                                                                                            |
| Int               | GraphQL                                           | int                                                        | Int2 (smallint, smallserial), int4 (integer, int, serial)                                                                                                                             |
| Float             | GraphQL                                           | float8                                                     | float4 (real) float8 (double precision) [numeric](https://www.postgresql.org/docs/current/datatype-numeric.html) (decimal)                                                              |
| Boolean           | GraphQL                                           | boolean                                                    | boolean                                                                                                                                                                               |
| UUID              | Custom                                            | [uuid](https://www.postgresql.org/docs/current/datatype-uuid.html) | uuid                                                                                                                                                                                  |
| Int64             | Custom                                            | bigint                                                     | int8 (bigint, bigserial) [numeric](https://www.postgresql.org/docs/current/datatype-numeric.html) (decimal)                                                                           |
| Date              | Custom                                            | [date](https://www.postgresql.org/docs/current/datatype-datetime.html) | date                                                                                                                                                                                  |
| Timestamp         | Custom                                            | [timestamptz](https://www.postgresql.org/docs/current/datatype-datetime.html) | timestamptz **Note:** Local timezone information is not stored. PostgreSQL converts and stores such timestamps as UTC.                                                                |
| Vector            | Custom                                            | [vector](https://github.com/pgvector/pgvector)             | vector See [Perform vector similarity search with Vertex AI](//firebase.google.com/docs/data-connect/solutions-vector-similarity-search). |

*   GraphQL `List` maps to a one-dimensional array.
    *   For example, `[Int]` maps to `int5[]`, `[Any]` maps to `jsonb[]`.
    *   Data Connect does not support nested arrays.

Equivalent SQL schema

> **Note:** This schema does not represent the DDL or transformation of the Data Connect schema. It's provided for illustration only.

```sql
-- Movies Table
CREATE TABLE Movies (
    movie_id UUID DEFAULT uuid_generate_v4() PRIMARY KEY,
    title VARCHAR(255) NOT NULL,
    release_year INT,
    genre VARCHAR(30),
    rating INT,
    description TEXT,
    tags TEXT[]
);
-- Movie Metadata Table
CREATE TABLE MovieMetadata (
    movie_id UUID REFERENCES Movies(movie_id) UNIQUE,
    director VARCHAR(255) NOT NULL,
    PRIMARY KEY (movie_id)
);
-- Actors Table
CREATE TABLE Actors (
    actor_id UUID DEFAULT uuid_generate_v4() PRIMARY KEY,
    name VARCHAR(30) NOT NULL
);
-- MovieActor Join Table for Many-to-Many Relationship
CREATE TABLE MovieActor (
    movie_id UUID REFERENCES Movies(movie_id),
    actor_id UUID REFERENCES Actors(actor_id),
    role VARCHAR(50) NOT NULL, # "main" or "supporting"
    PRIMARY KEY (movie_id, actor_id),
    FOREIGN KEY (movie_id) REFERENCES Movies(movie_id),
    FOREIGN KEY (actor_id) REFERENCES Actors(actor_id)
);
-- Users Table
CREATE TABLE Users (
    user_id UUID DEFAULT uuid_generate_v4() PRIMARY KEY,
    user_auth VARCHAR(255) NOT NULL
    username VARCHAR(30) NOT NULL
);
-- Reviews Table
CREATE TABLE Reviews (
    review_id UUID DEFAULT uuid_generate_v4() PRIMARY KEY,
    user_id UUID REFERENCES Users(user_id),
    movie_id UUID REFERENCES Movies(movie_id),
    rating INT,
    review_text TEXT,
    review_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE (movie_id, user_id)
    FOREIGN KEY (user_id) REFERENCES Users(user_id),
    FOREIGN KEY (movie_id) REFERENCES Movies(movie_id)
);
-- Self Join Example for Movie Sequel Relationship
ALTER TABLE Movies
ADD COLUMN sequel_to UUID REFERENCES Movies(movie_id);
```

Next steps

> **Note:** Follow the complete series on building Data Connect connectors, which covers:
>
> *   Schema development (this guide)
> *   [Query development](/docs/data-connect/queries-guide)
> *   [Mutation development](/docs/data-connect/mutations-guide)

You may be interested in:

*   Generating schemas for your apps using [AI assistance tools](/docs/data-connect/ai-assistance).
*   Reviewing the [syntax reference documentation](/docs/reference/data-connect).

# Perform vector similarity search with Vertex AI

Welcome to Firebase Data Connect's vector similarity search --- Firebase's implementation of semantic search that integrates with [Google Vertex AI](//cloud.google.com/vertex-ai/docs/vector-search/overview).

At the core of this feature are vector embeddings, which are arrays of floating point numbers representing the semantic meaning of text or media. By running a nearest neighbor search using an input vector embedding, you can find all semantically similar content. Data Connect uses PostgreSQL's `pgvector` extension for this capability.

This powerful semantic search can drive use cases like recommendation engines and search engines. It's also a key component in [retrieval-augmented generation](//developers.google.com/machine-learning/glossary#retrieval-augmented-generation-rag) in generative AI flows. The Vertex AI documentation is a great place to [learn more](//cloud.google.com/vertex-ai/docs/vector-search/overview).

You can rely on Data Connect's built-in support for generating vector embeddings automatically using [Vertex AI's Embeddings API](//cloud.google.com/vertex-ai/generative-ai/docs/embeddings/get-text-embeddings), or use that API to generate them manually.

Prerequisites

*   [Set up Data Connect](/docs/data-connect/quickstart) for your project.

    > **Note:** As you work through the setup flow, be aware that Data Connect's Vertex AI integration is supported only for certain Cloud SQL for PostgreSQL locations. See the [location list](/docs/data-connect/manage-services-and-databases#vertex-ai-limitations).
*   Enable [Vertex AI APIs](//cloud.google.com/vertex-ai/docs/start/cloud-environment#enable_vertexai_apis).

    > **Note:** You don't need to create a separate Google Cloud project or install the Google Cloud CLI.

Setup

You can choose between a local development flow (if you're a web, Kotlin Android, or iOS developer) or an IDX flow (for web developers). You can use a local database or your production Data Connect project and its Cloud SQL for PostgreSQL instance for development.

> **Note:** Whether you work locally or with your production project, you are using Vertex AI, and you will incur [Vertex AI usage costs](//cloud.google.com/vertex-ai/pricing#vectorsearch).

These instructions assume you have created your Data Connect project [following the quickstart guide](/docs/data-connect/quickstart).

Integrate with local PostgreSQL

1.  Set up a local PostgreSQL instance.
2.  [Grant](//cloud.google.com/iam/docs/grant-role-console) yourself the [Vertex AI user IAM role](https://cloud.google.com/vertex-ai/docs/general/access-control#aiplatform.user).
3.  Set up [Google Cloud Application Default Credentials](//cloud.google.com/docs/authentication/provide-credentials-adc) in your environment.
4.  Install the [`pgvector` extension](https://github.com/pgvector/pgvector) in your local PostgreSQL instance.
5.  Enable the extension using `CREATE EXTENSION vector` per the `pgvector` repository instructions.

Integrate with IDX

1.  Set up your IDX workspace using the Data Connect template.
2.  [Grant](//cloud.google.com/iam/docs/grant-role-console) yourself the [Vertex AI user IAM role](//cloud.google.com/vertex-ai/docs/general/access-control#aiplatform.user).
3.  Enable the extension using `CREATE EXTENSION vector` per the `pgvector` repository instructions.

Design your schema

To perform vector search, add a new field of `Vector` type in your schema. For example, if you want to do a semantic search using movie descriptions, add a field to hold the vector embeddings associated with the movie description. In this schema, `descriptionEmbedding` is added to store vector embeddings for the `description` field.

```graphql
type Movie @table {
 id: ID! @col(name: "movie_id") @default(id: ID! @col(name: "movie_id") @default(expr: "uuidV4()")
 title: String!
 description: String
 descriptionEmbedding: Vector! @col(size:768)
 // ...
}
```

> **Note:** Ensure that the vector embedding dimension is provided using the `@col(size: X)` schema directive, since vector embedding search can only compare vectors of the same dimensions. The vector embeddings generated using Vertex AI are of size 768.

Generate and retrieve embeddings

Data Connect brings integrated support for vector embeddings with the `_embed` server value. This directs Data Connect to generate vector embeddings by internally calling Vertex AI's Embedding APIs. The `_embed` server value can be used in both mutations and queries.

> **Note:** Vector embeddings generated from different model versions are generally considered to be incompatible. Thus, for all operations on a field (queries or mutations), it is the best practice to use vector embeddings generated using the same model. The list of supported Vertex AI models is available in [the documentation](//cloud.google.com/vertex-ai/generative-ai/docs/model-reference/text-embeddings#model_versions).

Mutations

Generate and store an embedding through Data Connect

In your vector search app, you'll likely want to request that embeddings be generated as soon as you add records to your database. Here's a `createMovie` mutation adds a movie record to the `Movie` table and also passes a movie description with a specified embedding `model`.

```graphql
mutation createMovie($title: String!, $description: String!) {
  movie_insert(data: {
    title: $title,
    description: $description,
    descriptionEmbedding_embed: {model: "textembedding-gecko@003", text: $description}
  })
}
```

In some cases, you may want to update the movie description and embedding.

```graphql
mutation updateDescription($id: String!, $description: String!) {
  movie_update(id: $id, data: {
    description: $description,
    descriptionEmbedding_embed: {model: "textembedding-gecko@003", text: $description}
  })
}
```

To call the latter mutation from a client:

```javascript
import { updateMovieDescription } from 'lib/dataconnect-sdk/';

await updateMovieDescription({ id: movieId, description: description});

// Use the response
```

Queries

Fetch vector embeddings using a query like the following. Note that the `descriptionEmbedding` returned by the query is an array of floats, which is typically not human-readable. Thus, Data Connect generated SDKs don't support returning it directly.

You can use returned vector embeddings to do similarity search, as described in the next section.

```graphql
query getMovieDescription($id: String!) @auth(level: PUBLIC) {
 movie(id: $id)
   id
   description
   descriptionEmbedding
}
```

Perform similarity search

Now we can perform similarity search.

For each `Vector` field, Data Connect generates a GraphQL function that implements the similarity search. The name of this generated function is `${pluralType}_${vectorFieldName}_similarity`. It supports a few parameters as shown in the following examples and in the [reference list](#parameters-similarity).

You can define a GraphQL function that invokes the similarity search. As mentioned above, the `_embed` server value directs Data Connect to generate the vector embeddings using Vertex AI's Embedding APIs, in this case to create embeddings for the search string used for comparison with movie description embeddings.

In this example, the similarity search will return up to 5 movies whose description is semantically closest to the input query. The result set is sorted in the ascending order of the distance - closest to furthest.

```graphql
query searchMovieDescriptionUsingL2Similarity ($query: String!) @auth(level: PUBLIC) {
    movies_descriptionEmbedding_similarity(
      compare_embed: {model: "textembedding-gecko@003", text: $query},
      where: {content: {ne: "No info available for this movie."}}, limit: 5)
      {
        id
        title
        description
      }
  }
```

Tune the similarity query

Default values for search parameters like `method` and `within` perform well for most use cases. However, if you notice that your query returns results that are too dissimilar, or is missing results that you want included, try tuning these parameters.

To find an appropriate value for `within`, we can add `_metadata.distance` to the selected fields to see how far from the query vector each result is. Based on the returned `distance` values, we can set the `within` parameter; only results with distance less than the value of `within` will be included:

```graphql
query searchMovieDescriptionUsingL2Similarity ($query: String!) @auth(level: PUBLIC) {
    movies_descriptionEmbedding_similarity(
      compare_embed: {model: "textembedding-gecko@003", text: $query},
      within: 2,
      where: {content: {ne: "No info available for this movie."}}, limit: 5)
      {
        id
        title
        description
        _metadata {
          distance
        }
      }
  }
```

You can also experiment with different distance functions by setting the `method` parameter.

```graphql
query searchMovieDescriptionUsingL2Similarity ($query: String!) @auth(level: PUBLIC) {
    movies_descriptionEmbedding_similarity(
      compare_embed: {model: "textembedding-gecko@003", text: $query},
      within: .5,
      method: COSINE,
      where: {content: {ne: "No info available for this movie."}}, limit: 5)
      {
        id
        title
        description
      }
  }
```

Note that different methods return very different values for distance: if you've set `within`, you will need to tune that value again after changing `method`.

Call the similarity query

To call a similarity search from client code:

```javascript
import { searchMovieDescriptionUsingL2similarity} from 'lib/dataconnect-sdk';

const response = await searchMovieDescriptionUsingL2similarity({ query });

// Use the response
```

Use custom embeddings

Data Connect also lets you work with embeddings directly as `Vector`s rather than using the `_embed` server value to generate them.

Store a custom embedding

Using the Vertex Embeddings API, specify a matching model and request embedding results of the correct dimension.

Then, cast the returned array of floats to a `Vector` to pass to the update operation for storage.

```graphql
mutation updateDescription($id: String!, $description: String!, $descriptionEmbedding: Vector!) {
  movie_update(id: $id, data: {
    // title, genre...
    description: $description,
    descriptionEmbedding: $descriptionEmbedding
  })
}
```

Perform similarity search using custom embeddings

Carry out the same operation to retrieve embeddings for search terms and cast them to `Vectors`.

Then, call the `_similarity` query to perform each search.

```graphql
query searchMovieDescriptionUsingL2Similarity($compare: Vector!, $within: Float, $excludesContent: String, $limit: Int) @auth(level: PUBLIC) {
    movies_descriptionEmbedding_similarity(
      compare: $compare,
      method: L2,
      within: $within,
      where: {content: {ne: $excludesContent}}, limit: $limit)
      {
        id
        title
        description
      }
  }
```

Deploy to production

Deploy your schema and connector

The last step in a typical Data Connect iteration is to deploy your assets to production.

When deploying your schema containing `Vector` types to CloudSQL using the `firebase deploy` command, the Firebase CLI takes the necessary steps to enable Vertex AI-based embedding generation on your CloudSQL instance.

```bash
firebase deploy --only dataconnect
```

if you wish to enable embedding support in your CloudSQL instance manually, or encounter a CLI error, follow [these instructions](//cloud.google.com/sql/docs/postgres/integrate-cloud-sql-with-vertex-ai).

Vector search syntax

Schema extensions

Data Connect's `Vector` data type maps to PostgreSQL's `vector` type as defined by the [`pgvector` extension](https://github.com/pgvector/pgvector). pgvector's `vector` type is stored as an array of single precision floating point numbers in PostgreSQL.

In Data Connect, the `Vector` type is represented as an array of JSON numbers. Inputs are coerced into an array of `float32` values. If coercion fails, an error is raised.

> **Note:** JavaScript numerics are compatible with float coercion.

Use the size parameter of the `@col` directive to set the dimensions of the vector.

```graphql
type Question @table {
    text: String!
    category: String!
    textEmbedding: Vector! @col(size: 768)
}
```

`size` is only supported for `Vector` types. `Vector` operations, such as similarity-search, necessitate that all the `Vector`s have the same number of dimensions.

```graphql
directive @col(
  # ... existing args
  """
  Defines a fixed column size for certain scalar types.

  - For Vector, size is required.
  - For all other types, size is currently unsupported and hence supplying it will result in a schema error.
  """
  size: Int
) on FIELD_DEFINITION
```

`_embed` server value for queries and mutations

`_embed`

This server value directs the Data Connect service to generate and store embeddings using [Vertex AI's Embedding APIs](//cloud.google.com/vertex-ai/generative-ai/docs/embeddings/get-text-embeddings). This server value can be used on both queries and mutations.

Parameters For similarity search

`method: COSINE|INNER_PRODUCT|L2`

The distance function used to search for nearby neighbors. Currently-supported algorithms are a subset of [pgvector search algorithms](https://github.com/pgvector/pgvector?tab=readme-ov-file#vector-functions).

`within: float`

A constraint on the distance within which the nearest neighbor search is performed.

`where: FDC filter condition`

See the [schemas, queries and mutations guide](/docs/data-connect/schemas-queries-mutations).

`limit: int`

The number of results to return.

# Use generated web SDKs

Firebase Data Connect client SDKs let you call your server-side queries and mutations directly from a Firebase app. You generate a custom client SDK in parallel as you design the schemas, queries and mutations you deploy to your Data Connect service. Then, you integrate methods from this SDK into your client logic.

As we've mentioned elsewhere, it's important to note that Data Connect queries and mutations are not submitted by client code and executed on the server. Instead, when deployed, Data Connect operations are stored on the server like Cloud Functions. This means you need to deploy corresponding client-side changes to avoid breaking existing users (for example, on older app versions).

That's why Data Connect provides you with a developer environment and tooling that lets you prototype your server-deployed schemas, queries and mutations. It also generates client-side SDKs automatically, while you prototype.

When you've iterated updates to your service and client apps, both server- and client-side updates are ready to deploy.

What is the client development workflow?

If you followed the [Get started](/docs/data-connect/quickstart), you were introduced to the overall development flow for Data Connect. In this guide, you'll find more detailed information about generating Web SDKs from your schema and working with client queries and mutations.

> You can learn client development with a quickstart app repository and build a fully-featured Data Connect app by following our [codelab for web](/codelabs/firebase-dataconnect-web).

To summarize, to use generated Web SDKs in your client apps, you'll follow these prerequisite steps:

1.  Add Firebase to your [web](/docs/web/setup) app.

Then:

1.  Develop your app schema.
2.  Initialize your client code with the [JavaScript SDK](#use-core), or [React](#use-core-with-react-angular) or [Angular](#use-core-with-react-angular) libraries.
3.  For React and Angular, [install Tanstack Query packages](#tanstack-install).
4.  Set up SDK generation:
    *   With the **Add SDK to app** button in our Data Connect VS Code extension
    *   By updating your `connector.yaml` for the [JavaScript SDK](#generate-web), or [React](#generate-react-angular) or [Angular](#generate-react-angular).
5.  Import libraries and generated code with [JavaScript SDK](#import-web), or [React](#import-react-angular) or [Angular](#import-react-angular).
6.  Implement calls to queries and mutations with the [JavaScript SDK](#using-queries), or [React](#operations-react-angular) or [Angular](#operations-react-angular).
7.  Test, by setting up the Data Connect emulator with the [JavaScript SDK](#emulator), or [React](#emulator-react-angular) or [Angular](#emulator-react-angular).

Implement client code with the Firebase JavaScript SDK

This section covers how you can implement clients using the Firebase JavaScript SDK.

If you're using React or Angular, see alternate setup instructions and links to additional documentation about [generating Data Connect SDKs for frameworks](#react-angular).

Initialize your app

First, initialize your app using the [standard Firebase sequence](//firebase.google.com/docs/web/setup).

```javascript
initializeApp({...});
```

Generate your JavaScript SDK

As with most Firebase projects, work on your Firebase Data Connect client code takes place in a local project directory. Both the Data Connect VS Code extension and the Firebase CLI are important local tools for generating and managing client code.

SDK generation options are keyed to several entries in the `dataconnect.yaml` file generated when you initialized your project.

Initialize SDK generation In your `connector.yaml`, add your `outputDir`, `package` and (for the web SDK) `packageJsonDir`.

```yaml
generate:
  javascriptSdk:
    outputDir: "../movies-generated"
    package: "@movie-app/movies"
    packageJsonDir: "../../"
```

`outputDir` specifies where the generated SDK should output to.

`package` specifies the package name.

`packageJsonDir` specifies where to install the package.

> **Note:** for generation, we add `"firebase": "^10.14.0"` as a `peerDependency`. Depending on your dependency manager (i.e. `pnpm`), these dependencies may not be installed automatically.

In this case, install `firebase@latest` to ensure this peer dependency is fulfilled.

Initialize the JavaScript SDK

Initialize your Data Connect instance using the information you used to set up Data Connect (all available in the Firebase console Data Connect tab).

The ConnectorConfig object

The SDK requires a connector configuration object.

This object is automatically generated from `serviceId` and `location` in `dataconnect.yaml`, and `connectorId` in `connector.yaml`.

Import libraries

There are two sets of imports needed to initialize your client code: general Data Connect imports and specific, generated SDK imports.

Note the `ConnectorConfig` object included in the general imports.

```javascript
// general imports
import { ConnectorConfig, DataConnect, getDataConnect, QueryRef, MutationRef, QueryPromise, MutationPromise } from 'firebase/data-connect';

// generated queries and mutations from SDK
import { listMovies, ListMoviesResponse, createMovie, connectorConfig } from '@myorg/myconnector';
```

Use queries from the JavaScript SDK

The generated code will already come with predefined Query Refs. All you need to do is import and call execute on them.

```javascript
import { executeQuery } from 'firebase/data-connect';
import { listMoviesRef } from '@movie-app/movies';

const ref = listMoviesRef();
const { data } = await executeQuery(ref);
console.log(data.movies);
```

Call SDK query methods

Here's an example using these action shortcut functions:

```javascript
import { listMovies } from '@movie-app/movies';
function onBtnClick() {
// This will call the generated JS from the CLI and then make an HTTP request out
// to the server.
  listMovies().then(data => showInUI(data)); // == executeQuery(listMoviesRef);
}
```

Subscribe to changes

You can subscribe to changes (which will update any time you execute a query).

```javascript
const listRef = listAllMoviesRef();

// subscribe will immediately invoke the query if no execute was called on it previously.
subscribe(listRef, ({ data }) => {
 updateUIWithMovies(data.movies);
});

await createMovie({ title: 'Empire Strikes Back', releaseYear: 1980, genre: "Sci-Fi", rating: 5 });
await listMovies(); // will update the subscription above
```

Use mutations from the JavaScript SDK

Mutations are accessible the same way as queries.

```javascript
import { executeMutation } from 'firebase/data-connect';
import { createMovieRef } from '@movie-app/movies';

const { data } = await executeMutation(createMovieRef({ movie: 'Empire Strikes Back' }));
```

Connect to the Data Connect emulator

Optionally, you can connect to the emulator by calling `connectDataConnectEmulator` and then passing in the Data Connect instance, like so:

```javascript
import { connectDataConnectEmulator } from 'firebase/data-connect';
import { connectorConfig } from '@myorg/myconnector'; // Replace with your package name

const dataConnect = getDataConnect(connectorConfig);
connectDataConnectEmulator(dataConnect, 'localhost', 9399);

// Make calls from your app
```

To switch to production resources, comment out lines for connecting to the emulator.

> **Note:** Calling `getDataConnect` is only required if you'd like to connect to the Data Connect emulator. Otherwise the generated SDK will automatically create an instance of the `DataConnect` object for you.

Implement client code for React and Angular

Firebase Data Connect provides a generated SDK with hooks for React and Angular using libraries available from our partners at Invertase, [TanStack Query Firebase](https://react-query-firebase.invertase.dev/).

This library provides a set of hooks that greatly ease handling of asynchronous tasks with Firebase in your applications.

Initialize your app

First, as with any Firebase web app, initialize your app using the [standard Firebase sequence](//firebase.google.com/docs/web/setup).

```javascript
initializeApp({...});
```

Install TanStack Query Firebase packages

install packages for TanStack Query in your project.

React

```bash
npm i --save @tanstack/react-query @tanstack-query-firebase/react
npm i --save firebase@latest # Note: React has a peer dependency on ^11.3.0
```

Angular

```bash
ng add @angular/fire
```

Generate your React or Angular SDK

As with the standard web SDK, as described [earlier](#generate-web), Firebase tooling handles automatic generation of SDKs based on your schema and operations.

To generate a React SDK for your project, add a `react` key to your `connector.yaml` configuration file.

React

```yaml
generate:
  javascriptSdk:
    react: true
    outputDir: "../movies-generated"
    package: "@movie-app/movies"
    packageJsonDir: "../../"
```

Angular

```yaml
generate:
  javascriptSdk:
    angular: true
    outputDir: "../movies-generated"
    package: "@movie-app/movies"
    packageJsonDir: "../../"
```

Import libraries

There are four sets of imports needed to initialize your React or Angular client code: general Data Connect imports, general TanStack imports, and specific imports for your JS and React generated SDKs.

Note the `ConnectorConfig` type included in the general imports.

React

```typescript
// general imports
import { ConnectorConfig, DataConnect, getDataConnect, QueryRef, MutationRef, QueryPromise, MutationPromise } from 'firebase/data-connect';

// TanStack Query-related functions
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";

// generated queries and mutations from SDK
import { ListMoviesResponse, connectorConfig } from '@myorg/myconnector';

// generated React hooks from SDK
import { useListAllMovies, useCreateMovie } from "@myorg/connector/react";
```

Angular

```typescript
// general imports
import { ConnectorConfig, DataConnect, getDataConnect, QueryRef, MutationRef, QueryPromise, MutationPromise } from 'firebase/data-connect';

// TanStack Query-related functions
import { provideTanStackQuery, QueryClient } from "@tanstack/angular-query-experimental";

// generated queries and mutations from SDK
import { ListMoviesResponse, connectorConfig } from '@myorg/myconnector';

// generated React hooks from SDK
import { injectListAllMovies, injectCreateMovie } from "@myorg/connector/angular";
```

Use queries and mutations in your React or Angular client

With setup complete, you can incorporate methods from the generated SDK.

In the following snippet, notice the `use`-prefixed method `useListAllMovies` for React and the `inject`-prefixed method `injectListAllMovies` for Angular, both from the generated SDK.

React

All such operations in the generated SDK, both queries and mutations, call TanStackQuery bindings:

*   Queries call and return the [TanStack `useDataConnectQuery` hook](https://react-query-firebase.invertase.dev/react/data-connect/querying)
*   Mutations call and return the [TanStack `useDataConnectMutation` hook](https://react-query-firebase.invertase.dev/react/data-connect/mutations)

```typescript jsx
import { useListAllMovies } from '@movies-app/movies/react';

function MyComponent() {
  const { isLoading, data, error } = useListAllMovies();
  if(isLoading) {
    return <div>Loading...</div>
  }
  if(error) {
    return <div> An Error Occurred: {error} </div>
  }
}

// App.tsx
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';
import MyComponent from './my-component';

function App() {
  const queryClient = new QueryClient();
  return <QueryClientProvider client={queryClient}>
    <MyComponent />
  </QueryClientProvider>
}
```

Angular

> **Note:** `ng add @angular/fire` will automatically do this for you, but if you choose to manually set it up, you can do so with the following code:

```typescript
import { injectAllMovies, connectorConfig } from '@movies-app/movies/angular';
import { provideDataConnect, getDataConnect } from '@angular/fire/data-connect';
import { provideTanStackQuery, QueryClient } from "@tanstack/angular-query-experimental";
const queryClient = new QueryClient();
...
providers: [
  ...
  provideTanStackQuery(queryClient),
  provideDataConnect(() => {
    const dc = getDataConnect(connectorConfig);
    return dc;
  })
]
```

Use auto reload queries with React and Angular

You can configure queries to automatically reload when data changes.

React

```typescript
export class MovieListComponent {
  movies = useListAllMovies();
}

export class AddPostComponent {
  const mutation = useCreateMovie({ invalidate: [listAllMoviesRef()] });
  addMovie() {
    // The following will automatically cause Tanstack to reload its listAllMovies query
    mutation.mutate({ title: 'The Matrix });
  }
}
```

Angular

```typescript
// class
export class MovieListComponent {
  movies = injectListAllMovies();
}

// template
// @if (movies.isPending()) {
//     Loading...
// }
// @if (movies.error()) {
//     An error has occurred: {{  movies.error() }}
// }
// @if (movies.data(); as data) {
//     @for (movie of data.movies; track movie.id) {
//     <mat-card appearance="outlined">
//         <mat-card-content>{{movie.description}}</mat-card-content>
//     </mat-card>
//     } @empty {
//         <h2>No items!</h2>
//     }
// }
```

Connect to the Data Connect emulator

Optionally, you can connect to the emulator by calling `connectDataConnectEmulator` and then passing in the Data Connect instance to your generated hook, like so:

React

```typescript
import { getDataConnect, connectDataConnectEmulator } from 'firebase/data-connect';
import { connectorConfig } from '@movies-app/movies';
import { useListAllMovies } from '@movies-app/movies/react';

const dc = getDataConnect(connectorConfig);
connectDataConnectEmulator(dc, 'localhost', 9399);

class AppComponent() {
  // ...
  const { isLoading, data, error } = useListAllMovies(dc);
  // ...
}
```

Angular

```typescript
// app.config.ts
import { provideDataConnect } from '@angular/fire/data-connect';
import { getDataConnect, connectDataConnectEmulator } from 'firebase/data-connect';
provideDataConnect(() => {
  const dc = getDataConnect(connectorConfig);
  connectDataConnectEmulator(dc, 'localhost', 9399);
  return dc;
}),
```

To switch to production resources, comment out lines for connecting to the emulator.

> **Note:** Calling `getDataConnect` is only required if you'd like to connect to the Data Connect emulator. Otherwise the generated SDK will automatically create an instance of the `DataConnect` object for you.

Data types in the SDK

The Data Connect server represents common GraphQL data types. These are represented in the SDK as follows.

*(Table incomplete in source text)*

Special considerations for SDK generation

Configure paths relative to `node_modules`

For the JavaScript SDK, because Data Connect uses `npm link` to install your SDK, your generated SDK needs to be output to a directory at the same level as your `node_modules` path or in a child directory that can access `node_modules`.

In other words, your generated SDK needs to have access to the `firebase` node module to work correctly.

For example, if you have your `node_modules` in `my-app/`, then your output directory should be `my-app/js-email-generated` so that `js-email-generated` can import from its parent `node_modules` folder.

```
my-app/
  dataconnect/
    connector/
        connector.yaml
  node_modules/
    firebase/
  js-email-generated/
```

```yaml
# connector.yaml
connectorId: "my-connector"
generate:
  javascriptSdk:
    outputDir: "../../js-email-generated"
    package: "@myapp/my-connector"
```

Or, if you have a monorepo where your modules are hosted at the root, you can place your output directory in any folder in your monorepo.

```
my-monorepo/
  dataconnect/
    connector/
        connector.yaml
  node_modules/
    firebase/
  my-app/
    js-email-generated/
  package.json
```

```yaml
# connector.yaml
connectorId: "my-connector"
generate:
  javascriptSdk:
    outputDir: "../../my-app/js-email-generated" # You can also output to ../../js-email-generated
```

> **Note:** You can provide an absolute path to directories if your project is set up in a separate directory structure.

Update SDKs while prototyping

If you're prototyping interactively with the Data Connect VS Code extension and its Data Connect emulator, SDK source files are automatically generated and updated while you modify `.gql` files defining schemas, queries and mutations. This can be a useful feature in hot (re)loading workflows. In other scenarios, if you're using the Data Connect emulator from the Firebase CLI, you can set a watch on `.gql` updates and also have SDK sources automatically updated.

Alternatively, you can use the CLI to regenerate SDKs whenever .gql files are changed:

```bash
firebase dataconnect:sdk:generate --watch
```

Generate SDKs for integration and for production releases

In some scenarios, such as preparing project sources to submit for CI tests, you can call the Firebase CLI for a batch update.

In these cases, use `firebase dataconnect:sdk:generate`.

# Use AI assistance for Firebase Data Connect schemas, queries and mutations

You can use Gemini in Firebase to help you craft schemas, queries and mutations to include in your client-side code.

Describe an app and summarize its data model, or describe a query or mutation you want to generate in natural language, and Gemini in Firebase will provide you with its GraphQL equivalent.

This AI assistance is available in many development contexts:

*   In the Firebase console, run and test the output, deploy your schema and operations to production, and sync them to your local development environment.
*   Locally, in our Data Connect VS Code extension, design, run and test using Gemini Code Assist with a local PostgreSQL database and emulator.

Learn more about queries and mutations at [Data Connect schemas, queries, and mutations](/docs/data-connect/schemas-queries-mutations).

How AI assistance for Data Connect uses your data

See [How Gemini in Firebase uses your data](/docs/gemini-in-firebase#how-gemini-in-firebase-uses-your-data) for more information about how Gemini in Firebase uses your data.

Set up AI assistance for Data Connect

To set up AI assistance in Data Connect, enable Gemini in Firebase as described in [Set up Gemini in Firebase](/docs/gemini-in-firebase/set-up-gemini), then proceed to [Generate GraphQL queries and mutations with Gemini in Firebase](/docs/data-connect/ai-assistance#generate-insights).

> **Important:** Project members must have the Firebase Data Connect API Admin role (`roles/firebasedataconnect.admin`), which is included in the [owner or editor IAM role](/docs/projects/iam/roles-basic) to generate Data Connect GraphQL queries and mutations with Gemini in Firebase.

Generate GraphQL schemas, queries and mutations with Gemini in Firebase

AI assistance for Data Connect is available in many contexts and in many of your workflows.

> **Important:** AI assistance for Data Connect is an early-stage technology that can generate output that seems plausible but is, in fact, incorrect. It may respond with inaccurate information that doesn't represent Google's views. Validate all output from Gemini before you use it and do not use untested generated code in production. Do not enter personally-identifiable information (PII) or user data into a **Help me write GraphQL** prompt. For more information, see [How AI assistance for Data Connect uses your data](/docs/data-connect/ai-assistance#governance) and [Gemini in Google Cloud and responsible AI](https://cloud.google.com/duet-ai/docs/discover/responsible-ai).

Create a new app and its initial schema and operations in the Firebase console

When you create a new Firebase project and set up to develop a new app, the Firebase console automatically offers AI assistance for schema and operations generation.

This setup flow lets you describe an app and then AI assistance:

*   Generates a complete Data Connect schema
*   Generates a useful, core set of queries and mutations you can then integrate with client code.

You sync these resources created in the console to your local development environment to continue integration with your clients.

This workflow is described in our [Get started guide](/docs/data-connect/quickstart).

Add new queries and mutations to run in the Firebase console

To use AI assistance for Data Connect to generate GraphQL based on natural language:

1.  Open [Data Connect](//console.firebase.google.com/project/_/dataconnect) in your project and, under **Services**, select your data source.
2.  Click **Data**.
3.  Click the **Help me write GraphQL** pen_spark icon.
4.  Inside the text field that appears, describe in natural language the [query or mutation](/docs/data-connect/schemas-queries-mutations) you want to generate, and click **Generate**.

    For example, if you're using the Movies data source referenced in the ["Build with Data Connect (web)" codelab](/codelabs/firebase-dataconnect-web), you could ask, "**Return the top five movies of 2022, in descending order by rating**," which might return a result like the following:

    ```graphql
    query TopMovies2022 {
      movies(where: {releaseYear: {eq: 2022}}, orderBy: [{rating: DESC}], limit: 5) {
        id
        title
        rating
        releaseYear
      }
    }
    ```

5.  Review the response:
    *   If the response looks correct, click **Insert** to insert the response into the code editor.
    *   If the response could be refined, click **Edit**, update the prompt, and click **Regenerate**.
6.  After you've accepted the response, set the following in the **Parameters** section, if applicable:
    *   **Variables**: If your query or mutation contains variables, define them here. Use JSON to define them, for example, `{"title":"The Matrix", "releaseYear":"1999"}`.
    *   **Authorization**: Choose the [Authorization context](/docs/data-connect/authorization-and-security) (Administrator, Authenticated, or Unauthenticated) with which to run the query or mutation.

    > **Warning:** If you're running a [mutation](/docs/data-connect/schemas-queries-mutations#mutations-movie), review it carefully before running it. Running a mutation in the data editor will execute the request.
7.  Click **Run** in the code editor and review results.

To test multiple queries or mutations in the code editor, ensure they are named. For example, the following query is named `GetMovie`. Move your cursor into the first line of the query or mutation to activate the **Run** button.

```graphql
query GetMovie($myKey: Movie_Key!) {
  movie(key: $myKey) { title }
}
```

Create an initial schema and operations during local prototyping

AI assistance is available from Gemini Code Assist for your local prototyping work when you use Visual Studio Code and our Data Connect VS Code extension.

The extension lets you describe an app and then Gemini Code Assist:

*   Generates a complete Data Connect schema
*   Generates a useful, core set of queries and mutations you can then integrate with client code.

This workflow is described in our [Get started guide for local prototyping](/docs/data-connect/quickstart-local).

Use the Firebase MCP server in local prototyping

The Firebase MCP server, provided in the Firebase CLI, gives your AI-powered development tools the ability to work with your Firebase projects. The Firebase MCP server works with any AI assistant IDE that can act as an MCP client, including Cursor, Visual Studio Code Copilot, and Windsurf Editor.

You can use the MCP server to generate schemas, queries and mutations, and gather inputs to perform common operations with the Firebase CLI.

To use the MCP server:

1.  Install the server [following this guide](/docs/cli/mcp-server).
2.  Invoke the `dataconnect_generate_schema` tool, describe an app, and review the resulting recommended schema.
3.  Invoke the `dataconnect_generate_operation` tool, describe an operation you want to perform against your schema, and review the resulting recommended query or mutation.

For more Data Connect tools, see the [MCP server guide](/docs/cli/mcp-server).

More AI assistance for Data Connect use cases

The following sections describe sample use cases, including one where you can ask Gemini to help you create a mutation to populate Data Connect and then query it to verify the results.

*   [Create a mutation that adds a movie to the database based on user input](#create-a-mutation)
*   [Create a query that lists reviews based on user-provided genre and ratings](#create-a-query)

Create a mutation that adds a movie to the database based on user input

In this section, you'll walk through an example of using natural language to generate GraphQL for a mutation that you can use to populate your database. This example assumes that you're using the movie database schema used in the [Firebase Data Connect documentation](/docs/data-connect) and ["Build with Data Connect (web)" codelab](/codelabs/firebase-dataconnect-web).

> **Warning:** Running a mutation in the data editor will execute the mutation and may change your data.

1.  From the [Firebase console](//console.firebase.google.com/project/_/dataconnect), open **Data Connect**.
2.  Select your service and data source, then open the **Data** tab.
3.  Click the **Help me write GraphQL** pen_spark icon and, in the box that appears, type your query:

    `Create a movie based on user input.`

4.  Click **Generate**. The mutation is returned. For example, Gemini might return a mutation like:

    ```graphql
    mutation CreateMovie($title: String!, $releaseYear: Int!, $genre: String!, $rating: Float!, $description: String!, $imageUrl: String!, $tags: [String!] = []) @auth(level: USER) {
      movie_insert(data: {
        title: $title,
        releaseYear: $releaseYear,
        genre: $genre,
        rating: $rating,
        description: $description,
        imageUrl: $imageUrl,
        tags: $tags
      })
    }
    ```

5.  Review the output. If needed, click **Edit** to refine the prompt and click **Regenerate**.
6.  Next, click **Insert** to insert the mutation into the data editor.
7.  To execute the mutation, you'll need to add variables. From the **Parameters** section, open **Variables** and include some test variables:

    `{"title":"My amazing movie", "releaseYear":2024, "genre": "Comedy", "rating": 8, "description": "A new movie to test mutations", "imageUrl": "", "tags": ["comedy","space travel"]}`

8.  Click **Run**.

    > **Tip:** You can also ask Gemini to expand the output in more useful ways. For example, to include comments and your source prompt in the output, you might use "Create a movie based on user input. Be sure to document the mutation and include this prompt in your response" to include comments and the source prompt in Gemini in Firebase's output.
9.  Next, create a query that verifies that your movie was added. Click the **Help me write GraphQL** pen_spark and, in the box that appears, type your prompt:

    `List all movies from 2024 that include all of these tags: 'space travel', 'comedy'.`

    Gemini might return a response like the following:

    ```graphql
    query ComedySpaceTravelMovies2024 @auth(level: PUBLIC) {
      movies(
        where: {
        releaseYear: { eq: 2024 },
        tags: { includesAll: ["space travel", "comedy"] }
        }
      ) {
          id
          title
          imageUrl
          releaseYear
          genre
          rating
          description
          tags
        }
    }
    ```

10. Insert and run the query. The movie you added should appear in the **History** field.

Create a query that lists reviews based on user-provided genre and ratings

In this section, you'll walk through an example of using natural language to generate GraphQL for a query. This example assumes that you're using the movie database used in the [Firebase Data Connect documentation](/docs/data-connect) and ["Build with Data Connect (web)" codelab](/codelabs/firebase-dataconnect-web).

1.  From the [Firebase console](//console.firebase.google.com/project/_/dataconnect), open **Data Connect**.
2.  Select your service and data source, then open the **Data** tab.
3.  Click the **Help me write GraphQL** pen_spark icon and, in the box that appears, type your query:

    `List all movie reviews, based on user-configurable genre and ratings.`

4.  Click **Generate**. The query is returned. For example, Gemini might return a query like:

    ```graphql
    query ListReviewsByGenreAndRating($genre: String, $minRating: Int, $maxRating: Int) @auth(level: PUBLIC) {
      reviews(where: {
        movie: {
          genre: {eq: $genre}
        },
        rating: {ge: $minRating, le: $maxRating}
      }) {
        id
        user {
          username
        }
        movie {
          title
          genre
        }
        rating
        reviewText
        reviewDate
      }
    }
    ```

5.  Review the output. If needed, click **Edit** to refine the prompt and click **Regenerate**.
6.  Next, click **Insert** to insert the mutation into the data editor.
7.  To test this query, you'll need to add variables. From the **Parameters** section, open **Variables** and include variables to use for testing:

    `{"genre":"sci-fi", "minRating":4, "maxRating":9}`

8.  Click **Run**.

> **Tip:** You can also ask Gemini to expand the output in more useful ways. For example, to include comments and your source prompt in the output, you might use "List all movie reviews, based on user-configurable genre and ratings. Be sure to document the query and include this prompt in your response." to include comments and the source prompt in the output from Gemini.

Design prompts to use with third-party AI assistance tools

As with all AI assistance tools and agents, the better your prompts, the more useful your outputs.

When you provide natural language prompts to Gemini in Firebase, behind the scenes, the assistant translates your inputs to a more fully-developed prompt.

If you're not using Gemini in Firebase or other Firebase AI assistance, and are working with third-party AI tooling like Cursor or Windsurf, you can get better recommendations about Data Connect by using similar fleshed-out prompts.

We've published prompt templates for you to download, adapt, and copy into your IDE:

*   A template prompt for [schema generation](https://raw.githubusercontent.com/firebase/firebase-tools/refs/heads/master/templates/dataconnect-prompts/operation-generation-cursor-windsurf-rule.txt)
*   A template prompt for [operation generation](https://raw.githubusercontent.com/firebase/firebase-tools/refs/heads/master/templates/dataconnect-prompts/operation-generation-cursor-windsurf-rule.txt)

After downloading and modifying, create a prompt in familiar tooling (for example Cursor or Windsurf) as follows:

*   In Cursor (be sure to review the latest [instructions from Cursor](https://docs.cursor.com/context/rules#creating-a-rule)):
    1.  Click the settings icon on top right.
    2.  Select the **Rules** tab.
    3.  Under the **Project Rules**, click **Add a new rule** button.
    4.  Copy and paste the rule.
*   In Windsurf (be sure to review the latest [instructions from Windsurf](https://docs.windsurf.com/windsurf/cascade/memories#rules)):
    1.  Open the Cascade window by clicking the **Cascade** button in the top right corner.
    2.  Click the **Customizations** icon in the top right slider menu in Cascade, then navigate to the **Rules** panel.
    3.  Click the **+ Global** or **+ Workspace** button to create new rules at either the global or workspace level, respectively.
    4.  Copy and paste the rule.

Troubleshoot AI assistance for Data Connect

Refer to [Troubleshoot Gemini in Firebase](/docs/gemini-in-firebase/set-up-gemini#troubleshoot-gemini-in-firebase).

Pricing

AI assistance for Data Connect is available as part of Gemini in Firebase, which is included for individual users.

See [Gemini in Firebase pricing](/docs/gemini-in-firebase#pricing) for more information.

Next steps

*   Learn more about queries and mutations at [Data Connect schemas, queries, and mutations](/docs/data-connect/schemas-queries-mutations).
*   Learn more about [Gemini in Firebase](/docs/gemini-in-firebase).

# Secure Data Connect with authorization and attestation

Firebase Data Connect provides robust client-side security with:

*   Mobile and web client authorization
*   Individual query- and mutation-level authorization controls
*   App attestation with Firebase App Check.

Data Connect extends this security with:

*   Server-side authorization
*   Firebase project and Cloud SQL user security with IAM.

Authorize client queries and mutations

Data Connect is fully integrated with Firebase Authentication, so you can use rich data about users who are accessing your data (authentication) in your design for what data those users can access (authorization).

Data Connect provides an `@auth` directive for queries and mutations that lets you set the level of authentication required to authorize the operation. This guide [introduces the `@auth` directive, with examples](#auth-directive).

In addition, Data Connect supports execution of queries embedded in mutations, so you can retrieve additional authorization criteria you've stored in your database, and use those criteria in `@check` directives to decide if enclosing mutations are authorized. For this authorization case, the `@redact` directive allows you control whether query results are returned to clients in the wire protocol and the embedded query omitted in generated SDKs. Find the [introduction to these directives, with examples](#check-redact-directives).

Understand the `@auth` directive

You can parameterize the `@auth` directive to follow one of several preset access levels that cover many common access scenarios. These levels range from `PUBLIC` (which allows queries and mutations from all clients without authentication of any kind) to `NO_ACCESS` (which disallows queries and mutations outside of [privileged server environments using the Firebase Admin SDK](/docs/data-connect/admin-sdk)). Each of these levels is correlated with authentication flows provided by Firebase Authentication.

Using these preset access levels as a starting point, you can define complex and robust authorization checks in the `@auth` directive using `where` filters and Common Expression Language (CEL) expressions evaluated on the server.

> **Note:** All queries and mutations in your connector must have an `@auth` directive to be accessible by client applications. Queries and mutations default to `NO_ACCESS` if the `@auth` directive is not specified.
> **Tip:** See the [directives reference for the `@auth` directive](/docs/reference/data-connect/gql/directive#auth) and the [complete reference for access levels](#preset-authz-levels).

Use the `@auth` directive to implement common authorization scenarios

The preset access levels are the *starting point* for authorization.

The `USER` access level is the most widely useful basic level to start with.

Fully secure access will build on the `USER` level plus filters and expressions that check user attributes, resource attributes, roles and other checks. The `USER_ANON` and `USER_EMAIL_VERIFIED` levels are variations on the `USER` case.

Expression syntax lets you evaluate data using an `auth` object representing authentication data passed with operations, both standard data in auth tokens and custom data in tokens. For the list of fields available in the `auth` object, see the [reference section](#auth-cel-reference).

> **Note:** You can augment authorization with `@auth` by looking up authorization roles and other data stored in your database, as described in the [section on adding `@check` and `@redact` for lookups](#check-redact-directives).

There are of course use cases where `PUBLIC` is the correct access level to start with. Again, an access level is always a starting point, and additional filters and expressions are needed for robust security.

This guide now gives examples of how to build on `USER` and `PUBLIC`.

A motivating example

The following best practice examples refer to the following schema for a blogging platform with certain content locked behind a payment plan.

Such a platform would likely model `Users` and `Posts`.

```graphql
type User @table(key: "uid") {
  uid: String!
  name: String
  birthday: Date
  createdAt: Timestamp! @default(expr: "request.time")
}

type Post @table {
  author: User!
  text: String!
  # "one of 'draft', 'public', or 'pro'"
  visibility: String! @default(value: "draft")
  # "the time at which the post should be considered published. defaults to
  # immediately"
  publishedAt: Timestamp! @default(expr: "request.time")
  createdAt: Timestamp! @default(expr: "request.time")
  updatedAt: Timestamp! @default(expr: "request.time")
}
```

User-owned resources

Firebase recommends that you write filters and expressions that test user ownership of a resource, in the following cases, ownership of `Posts`.

In the following examples, data from auth tokens is read and compared using expressions. The typical pattern is to use expressions like `where: {authorUid: {eq_expr: "auth.uid"}}` to compare a stored `authorUid` to the `auth.uid` (user ID) passed in the authentication token.

Create

This authorization practice starts by adding the `auth.uid` from the auth token to each new `Post` as an `authorUid` field to allow comparison in subsequence authorization tests.

```graphql
# Create a new post as the current user
mutation CreatePost($text: String!, $visibility: String) @auth(level: USER) {
  post_insert(data: {
    # set the author's uid to the current user uid
    authorUid_expr: "auth.uid"
    text: $text
    visibility: $visibility
  })
}
```

Update

When a client attempts to update a `Post`, you can test the passed `auth.uid` against the stored `authorUid`.

```graphql
# Update one of the current user's posts
mutation UpdatePost($id: UUID!, $text: String, $visibility: String) @auth(level:USER) {
  post_update(
    # only update posts whose author is the current user
    first: { where: {
      id: {eq: $id}
      authorUid: {eq_expr: "auth.uid"}
    }}
    data: {
      text: $text
      visibility: $visibility
      # insert the current server time for updatedAt
      updatedAt_expr: "request.time"
    }
  )
}
```

Delete

The same technique is used to authorize delete operations.

```graphql
# Delete one of the current user's posts
mutation DeletePost($id: UUID!) @auth(level: USER) {
  post_delete(
    # only delete posts whose author is the current user
    first: { where: {
      id: {eq: $id}
      authorUid: {eq_expr: "auth.uid"}
    }}
  )
}
```

> **Note:** For these query examples, the following fragment is used to select common fields on `Post`.

```graphql
# Common display information for a post
fragment DisplayPost on Post {
  id, text, createdAt, updatedAt
  author { uid, name }
}
```

List

```graphql
# List all posts belonging to the current user
query ListMyPosts @auth(level: USER) {
  posts(where: {
    userUid: {eq_expr: "auth.uid"}
  }) {
    # See the fragment above
    ...DisplayPost
    # also show visibility since it is user-controlled
    visibility
  }
}
```

Get

```graphql
# Get a post only if it belongs to the current user
query GetMyPost($id: UUID!) @auth(level: USER) {
  post(key: {id: $id},
    first: {where: {
      id: {eq: $id}
      authorUid: {eq_expr: "auth.uid"}}
      }}, {
      # See the fragment above
      ...DisplayPost
      # also show visibility since it is user-controlled
      visibility
  }
}
```

Filter Data

Data Connect's authorization system lets you write sophisticated filters combined with preset access levels like `PUBLIC` as well as by using data from auth tokens.

The authorization system also lets you use expressions only, without a base access level, as shown in some of the following examples.

Filter by resource attributes

Here, authorization is not based on auth tokens since the base security level is set to `PUBLIC`. But, we can explicitly set records in our database as suitable for public access; assume we have `Post` records in our database with `visibility` set to "public".

```graphql
# List all posts marked as 'public' visibility
query ListPublicPosts @auth(level: PUBLIC) {
  posts(where: {
    # Test that visibility is "public"
    visibility: {eq: "public"}
    # Only display articles that are already published
    publishedAt: {lt_expr: "request.time"}
  }) {
    # see the fragment above
    ...DisplayPost
  }
}
```

Filter by user claims

Here, assume you've set up custom user claims that pass in auth tokens to identify users in a "pro" plan for your app, flagged with an `auth.token.plan` field in the auth token. Your expressions can test against this field.

```graphql
# List all public or pro posts, only permitted if user has "pro" plan claim
query ProListPosts @auth(expr: "auth.token.plan == 'pro'") {
  posts(where: {
    # display both public posts and "pro" posts
    visibility: {in: ['public', 'pro']},
    # only display articles that are already published
    publishedAt: {lt_expr: "request.time"},
  }) {
    # see the fragment above
    ...DisplayPost
    # show visibility so pro users can see which posts are pro\
    visibility
  }
}
```

Filter by order + limit

Or again, you may have set `visibility` in `Post` records to identify they are content available for "pro" users, but for a preview or teaser listing of data, further limit the number of records returned.

```graphql
# Show 2 oldest Pro post as a preview
query ProTeaser @auth(level: USER) {
  posts(
    where: {
      # show only pro posts
      visibility: {eq: "pro"}
      # that have already been published more than 30 days ago
      publishedAt: {lt_time: {now: true, sub: {days: 30}}}
    },
    # order by publish time
    orderBy: [{publishedAt: DESC}],
    # only return two posts
    limit: 2
  ) {
    # See the fragment above
    ...DisplayPost
  }
}
```

Filter by role

If your custom claim defines an `admin` role, you can test and authorize operations accordingly.

```graphql
# List all posts unconditionally iff the current user has an admin claim
query AdminListPosts @auth(expr: "auth.token.admin == true") {
  posts { ...DisplayPost }
}
```

Add the `@check` and `@redact` directives to look up authorization data

A common authorization use case involves storing custom authorization roles in your database, for example in a special permissions table, and using those roles to authorize mutations to create, update, or delete data.

Using authorization data lookups, you can query for roles based on a userID and use CEL expressions to decide if the mutation is authorized. For example, you might want to write an `UpdateMovieTitle` mutation that lets an authorized client update movie titles.

For the rest of this discussion, assume the movie review app database stores an authorization role in a `MoviePermission` table.

```graphql
# MoviePermission
# Suppose a user has an authorization role with respect to records in the Movie table
type MoviePermission @table(key: ["movie", "user"]) {
  movie: Movie! # implies another field: movieId: UUID!
  user: User!
  role: String!
}
```

Use in mutations

In the following example implementation, the `UpdateMovieTitle` mutation includes a `query` field to retrieve data from `MoviePermission`, and the following directives to ensure the operation is secure and robust:

*   A `@transaction` directive to ensure all authorization queries and checks are completed or fail atomically.
*   The `@redact` directive to omit query results from the response, meaning our authorization check is performed on the Data Connect server but sensitive data is not exposed to the client.
*   A pair of `@check` directives to evaluate authorization logic on query results, such as testing that a given userID has an appropriate role to make modifications.

    > **Note:** The `message` argument for `@check` is optional, but it's useful in combination with the `@redact` directive, so you can define messages to return to client code even though specific fields are redacted from the response.

```graphql
mutation UpdateMovieTitle($movieId: UUID!, $newTitle: String!) @auth(level: USER) @transaction {
  # Step 1: Query and check
  query @redact {
    moviePermission( # Look up a join table called MoviePermission with a compound key.
      key: {movieId: $movieId, userId_expr: "auth.uid"}
    # Step 1a: Use @check to test if the user has any role associated with the movie
    # Here the `this` binding refers the lookup result, i.e. a MoviePermission object or null
    # The `this != null` expression could be omitted since rejecting on null is default behavior
    ) @check(expr: "this != null", message: "You do not have access to this movie") {
      # Step 1b: Check if the user has the editor role for the movie
      # Next we execute another @check; now `this` refers to the contents of the `role` field
      role @check(expr: "this == 'editor'", message: "You must be an editor of this movie to update title")
    }
  }
  # Step 2: Act
  movie_update(id: $movieId, data: {
    title: $newTitle
  })
}
```

> **Tip:** Refer to the [directives reference guide](/docs/reference/data-connect/gql/directive) and [CEL reference for the `this` binding](#cel-this-binding).

Use in queries

Authorization data lookups are also useful to restrict queries based on roles or other restrictions.

In the following example, which also uses the `MoviePermission` schema, the query checks whether a requestor has an appropriate "admin" role to view users who can edit a movie.

```graphql
query GetMovieEditors($movieId: UUID!) @auth(level: PUBLIC) {
  moviePermission(key: { movieId: $movieId, userId_expr: "auth.uid" }) @redact {
    role @check(expr: "this == 'admin'", message: "You must be an admin to view all editors of a movie.")
  }
  moviePermissions(where: { movieId: { eq: $movieId }, role: { eq: "editor" } }) {
    user {
      id
      username
    }
  }
}
```

> **Tip:** Refer to the [directives reference guide](/docs/reference/data-connect/gql/directive) and [CEL reference for the `this` binding](#cel-this-binding).

Antipatterns to avoid in authorization

The previous section covers patterns to follow when using the `@auth` directive.

You should also be aware of important antipatterns to avoid.

Avoid passing user attributes IDs and auth token parameters in query and mutation arguments

Firebase Authentication is a powerful tool for presenting authentication flows and securely capturing authentication data such as registered user IDs and numerous fields stored in auth tokens.

It's not a recommended practice to pass user IDs and auth token data in query and mutation arguments.

> **Tip:** Instead, in the filters and expressions you use to augment basic access levels, test against `auth.uid` and the fields in `auth.token` to enhance security. For more information about `auth` data, see the [expression reference](#auth-cel-reference).

```graphql
# Antipattern!
# This incorrectly allows any user to view any other user's posts
query AllMyPosts($userId: String!) @auth(level: USER) {
  posts(where: {authorUid: {eq: $userId}}) {
    id, text, createdAt
  }
}
```

Avoid using the `USER` access level without any filters

As discussed several times in the guide, the core access levels like `USER`, `USER_ANON`, `USER_EMAIL_VERIFIED` are baselines and starting points for authorization checks, to be enhanced with filters and expressions. Using these levels without a corresponding filter or expression that checks *which* user is performing the request is essentially equivalent to using the `PUBLIC` level.

> **Tip:** Firebase recommends that you *always* augment basic access levels with expressions.

```graphql
# Antipattern!
# This incorrectly allows any user to view all documents
query ListDocuments @auth(level: USER) {
  documents {
    id
    title
    text
  }
}
```

Avoid using `PUBLIC` or `USER` access level for prototyping

To speed up development, it can be tempting to set all operations to the `PUBLIC` access level or to `USER` access level without further enhancements to authorize all operations and let you quickly test your code.

> **Tip:** Before you deploy your operations to production, when you prototype in the console and with the tooling in the Data Connect VS Code extension, set your queries and mutations to the `NO_ACCESS` access level. You'll be able to execute these operations in the safe console and VS Code prototyping environments before they are deployed. Following this practice means that even if you deploy such operations to production, they cannot be executed.

When you've done very initial prototyping this way, begin to switch from `NO_ACCESS` to production-ready authorization with `PUBLIC` and `USER` levels. However, don't deploy them as `PUBLIC` or `USER` without adding additional logic as shown in this guide.

```graphql
# Antipattern!
# This incorrectly allows anyone to delete any post
mutation DeletePost($id: UUID!) @auth(level: PUBLIC) {
  post: post_delete(
    id: $id,
  )
}
```

Avoid basing authorization on unverified email addresses

Granting access to users on a particular domain is a great way to limit access. However, anyone can claim to own an email during sign-in. Ensure you only grant access to email addresses that have been verified through Firebase Authentication.

```graphql
# Antipattern!
# Anyone can claim an email address during sign-in
mutation CreatePost($text: String!, $visibility: String) @auth(expr: "auth.token.email.endsWith('@example.com')") {
  post_insert(data: {
    # set the author's uid to the current user uid
    authorUid_expr: "auth.uid"
    text: $text
    visibility: $visibility
  })
}
```

Also check `auth.token.email_verified`

```graphql
mutation CreatePost($text: String!, $visibility: String) @auth(expr: "auth.token.email_verified && auth.token.email.endsWith('@example.com')") {
  post_insert(data: {
    # set the author's uid to the current user uid
    authorUid_expr: "auth.uid"
    text: $text
    visibility: $visibility
  })
}```

Audit authorization with the Firebase CLI

As indicated earlier, preset access levels such as `PUBLIC` and `USER` are the starting point for robust authorization, and should be used with additional filter and expression-based authorization checks. They shouldn't be used on their own without careful consideration of the use case.

Data Connect helps you audit your authorization strategy by analyzing your connector code when you deploy to the server using `firebase deploy` from the Firebase CLI. You can use this audit to help you review your codebase.

When you deploy your connectors, the CLI will output assessments for existing, modified and new operation code in your connector.

For modified and new operations, the CLI issues warnings and prompts you for confirmation when you use certain access levels in your new operations, or when you modify existing operations to use those access levels.

> **Note:** Insecure operation warnings are suppressed if you annotate the `@auth` directive in the operation with the [`insecureReason` argument](/docs/data-connect/authorization-and-security#insecureReasons).

Warnings and prompts always occur for:

*   `PUBLIC`

And, warnings and prompts occur on the following access levels when you *don't augment them* with filters using `auth.uid`:

*   `USER`
*   `USER_ANON`
*   `USER_EMAIL_VERIFIED`

Suppress insecure operation warnings with the `@auth(insecureReason:)` argument

In many cases, you will conclude that using the `PUBLIC` and `USER*` access levels is perfectly appropriate.

When your connector contains many operations, you may want clearer, more relevant security audit output that omits operations that would normally trigger a warning, but you know have the correct access level.

You can suppress warnings for such operations with `@auth(insecureReason:)`. For example:

```graphql
query listItem @auth(level: PUBLIC, insecureReason: "This operation is safe to expose to the public.")
  {
    items {
      id name
    }
  }
```

Use Firebase App Check for app attestation

Authentication and authorization are critical components of Data Connect security. Authentication and authorization combined with app attestation makes for a very robust security solution.

With attestation through Firebase App Check, devices running your app will use an app or device attestation provider that attests that Data Connect operations originate from your authentic app and requests originate from an authentic, untampered device. This attestation is attached to every request your app makes to Data Connect.

To learn how to enable App Check for Data Connect and include its client SDK in your app, have a [look at the App Check overview](/docs/app-check).

Authentication levels for the `@auth(level)` directive

The following table lists all standard access levels and their CEL equivalents. Authentication levels are listed from broad to narrow -- each level encompasses all users who match following levels.

> **Warning:** These access levels are only the starting point for security, upon which you implement additional filter and expression-based authorization checks like those [discussed above](#auth-best-practices).

*(Table incomplete in source text, missing actual levels and CEL equivalents)*

CEL Reference for `@auth(expr)`

As shown in examples elsewhere in this guide, you can and should use expressions defined in Common Expression Language (CEL) to control authorization for Data Connect using `@auth(expr:)` and `@check` directives.

This section covers CEL syntax relevant to creating expressions for these directives.

Complete reference information for CEL is provided in the [CEL specification](https://github.com/google/cel-spec).

Test variables passed in queries and mutations

`@auth(expr)` syntax allows you access and test variables from queries and mutations.

For example, you can include an operation variable, such as `$status`, using `vars.status`.

```graphql
mutation Update($id: UUID!, $status: Any) @auth(expr: "has(vars.status)")
```

Data available to expressions: request, response, this

You use data for:

*   Evaluation with CEL expressions in `@auth(expr:)` and `@check(expr:)` directives
*   Assignment using server expressions, `<field>_expr`.

Both `@auth(expr:)` and `@check(expr:)` CEL expressions can evaluate the following:

*   `request.operationName`
*   `vars` (alias for `request.variables`)
*   `auth` (alias for `request.auth`)

In mutations, you can access and assign the contents of:

*   `response` (to check partial results in multi-step logic)

Additionally, `@check(expr:)` expressions can evaluate:

*   `this` (the value of the current field)
*   `response` (to check partial results in multi-step logic)

The `request.operationName` binding

The `request.operarationName` binding stores the type of operation, either query or mutation.

The `vars` binding (`request.vars`)

The `vars` binding allows your expressions to access all variables passed in your query or mutation.

You can use `vars.<variablename>` in an expression as an alias for the fully-qualified `request.variables.<variablename>`:

```graphql
# The following are equivalent
mutation StringType($v: String!) @auth(expr: "vars.v == 'hello'")
mutation StringType($v: String!) @auth(expr: "request.variables.v == 'hello'")
```

The `auth` binding (`request.auth`)

Authentication identifies users requesting access to your data and provides that information as a binding you can build on in your expressions.

In your filters and expressions, you can use `auth` as an alias for `request.auth`.

The auth binding contains the following information:

*   `uid`: A unique user ID, assigned to the requesting user.
*   `token`: A map of values collected by Authentication.

For more details on the contents of `auth.token` see [Data in auth tokens](#auth-token-contents).

The `response` binding

The `response` binding contains the data being assembled by the server in response to a query or mutation *as that data is being assembled*.

As the operation proceeds, as each step is completed successfully, `response` contains response data from successfully-completed steps.

The `response` binding is structured according the shape of its associated operation, including (multiple) nested fields and (if applicable) embedded queries.

Note that when you access **embedded query response data**, fields can contain any data type, depending on the data requested in the embedded query; when you access data returned by mutation fields like `_insert`s and `_delete`s, they may contain UUID keys, number of deletes, nulls (see the [mutations reference](/docs/reference/data-connect/gql/mutation)).

For example:

*   In a mutation that contains an embedded query, the `response` binding contains lookup data at `response.query.<fieldName>.<fieldName>....`, in this case, `response.query.todoList` and `response.query.todoList.priority`.

    ```graphql
    mutation CheckTodoPriority(
      $uniqueListName: String!
    ) {
      # This query is identified as `response.query`
      query @check(expr: "response.query.todoList.priority == 'high'", message: "This list is not for high priority items!") {
        # This field is identified as `response.query.todoList`
        todoList(where: { name: $uniqueListName }) {
          # This field is identified as `response.query.todoList.priority`
          priority
        }
      }
    }
    ```

*   In a multi-step mutation, for example with multiple `_insert` fields, the `response` binding contains partial data at `response.<fieldName>.<fieldName>....`, in this case, `response.todoList_insert.id`.

    ```graphql
    mutation CreateTodoListWithFirstItem(
      $listName: String!,
      $itemContent: String!
    ) @transaction {
      # Step 1
      todoList_insert(data: {
        id_expr: "uuidV4()",
        name: $listName,
      })
      # Step 2:
      todo_insert(data: {
        listId_expr: "response.todoList_insert.id" # <-- Grab the newly generated ID from the partial response so far.
        content: $itemContent,
      })
    }
    ```

The `this` binding

> **Note:** The `this` binding is valid for `@check` expressions, not `@auth` expressions.

The binding `this` evaluates to the field that the `@check` directive is attached to. In a basic case, you might evaluate single-valued query results.

```graphql
mutation UpdateMovieTitle (
  $movieId: UUID!,
  $newTitle: String!)
  @auth(level: USER)
  @transaction {
  # Step 1: Query and check
  query @redact {
    moviePermission( # Look up a join table called MoviePermission with a compound key.
      key: {movieId: $movieId, userId_expr: "auth.uid"}
    ) {
      # Check if the user has the editor role for the movie. `this` is the string value of `role`.
      # If the parent moviePermission is null, the @check will also fail automatically.
      role @check(expr: "this == 'editor'", message: "You must be an editor of this movie to update title")
    }
  }
  # Step 2: Act
  movie_update(id: $movieId, data: {
    title: $newTitle
  })
}
```

If the returned field occurs multiple times because any ancestor is a list, each occurrence is tested with `this` bound to each value.

For any given path, if an ancestor is `null` or `[]`, the field won't be reached and the CEL evaluation will be skipped for that path. In other words, evaluation only takes place when `this` is `null` or non-`null`, but never `undefined`.

When the field itself is a list or object, `this` follows the same structure (including all descendants selected in case of objects), as illustrated in the following example.

```graphql
mutation UpdateMovieTitle2($movieId: UUID!, $newTitle: String!) @auth(level: USER) @transaction {
  # Step 1: Query and check
  query {
    moviePermissions( # Now we query for a list of all matching MoviePermissions.
      where: {movieId: {eq: $movieId}, userId: {eq_expr: "auth.uid"}}
    # This time we execute the @check on the list, so `this` is the list of objects.
    # We can use the `.exists` macro to check if there is at least one matching entry.
    ) @check(expr: "this.exists(p, p.role == 'editor')", message: "You must be an editor of this movie to update title") {
      role
    }
  }
  # Step 2: Act
  movie_update(id: $movieId, data: {
    title: $newTitle
  })
}
```

Complex expression syntax

You can write more complex expressions by combining with the `&&` and `||` operators.

```graphql
mutation UpsertUser($username: String!) @auth(expr: "(auth != null) && (vars.username == 'joe')")
```

The following section describes all available operators.

Operators and operator precedence

Use the following table as a reference for operators and their corresponding precedence.

Given arbitrary expressions `a` and `b`, a field `f`, and an index `i`.

*(Table incomplete in source text, missing actual operators and precedence)*

Data in auth tokens

The `auth.token` object may contain the following values:

*(Table incomplete in source text)*

Additional fields in JWT ID tokens

You can also access the following `auth.token` fields:

*(Table incomplete in source text)*

What's next?

*   Firebase Data Connect provides an Admin SDK to let you perform [queries and mutations from privileged environments](/docs/data-connect/admin-sdk).
*   Learn about IAM security in the [guide for managing services and databases](/docs/data-connect/manage-services-and-databases).

# Common Expression Language syntax reference for Data Connect

This reference guides covers Common Expression Language (CEL) syntax relevant to creating expressions for the `@auth(expr:)` and `@check(expr:)` directives.

Complete reference information for CEL is provided in the [CEL specification](https://github.com/google/cel-spec).

Test variables passed in queries and mutations

`@auth(expr)` syntax allows you access and test variables from queries and mutations.

For example, you can include an operation variable, such as `$status`, using `vars.status`.

```graphql
mutation Update($id: UUID!, $status: Any) @auth(expr: "has(vars.status)")
```

Data available to expressions: request, response, this

You use data for:

*   Evaluation with CEL expressions in `@auth(expr:)` and `@check(expr:)` directives
*   Assignment using server expressions, `<field>_expr`.

Both `@auth(expr:)` and `@check(expr:)` CEL expressions can evaluate the following:

*   `request.operationName`
*   `vars` (alias for `request.variables`)
*   `auth` (alias for `request.auth`)

In mutations, you can access and assign the contents of:

*   `response` (to check partial results in multi-step logic)

Additionally, `@check(expr:)` expressions can evaluate:

*   `this` (the value of the current field)
*   `response` (to check partial results in multi-step logic)

The `request.operationName` binding

The `request.operarationName` binding stores the type of operation, either query or mutation.

The `vars` binding (`request.vars`)

The `vars` binding allows your expressions to access all variables passed in your query or mutation.

You can use `vars.<variablename>` in an expression as an alias for the fully-qualified `request.variables.<variablename>`:

```graphql
# The following are equivalent
mutation StringType($v: String!) @auth(expr: "vars.v == 'hello'")
mutation StringType($v: String!) @auth(expr: "request.variables.v == 'hello'")
```

The `auth` binding (`request.auth`)

Authentication identifies users requesting access to your data and provides that information as a binding you can build on in your expressions.

In your filters and expressions, you can use `auth` as an alias for `request.auth`.

The auth binding contains the following information:

*   `uid`: A unique user ID, assigned to the requesting user.
*   `token`: A map of values collected by Authentication.

For more details on the contents of `auth.token` see [Data in auth tokens](#auth-token-contents).

The `response` binding

The `response` binding contains the data being assembled by the server in response to a query or mutation *as that data is being assembled*.

As the operation proceeds, as each step is completed successfully, `response` contains response data from successfully-completed steps.

The `response` binding is structured according the shape of its associated operation, including (multiple) nested fields and (if applicable) embedded queries.

Note that when you access **embedded query response data**, fields can contain any data type, depending on the data requested in the embedded query; when you access data returned by mutation fields like `_insert`s and `_delete`s, they may contain UUID keys, number of deletes, nulls (see the [mutations reference](/docs/reference/data-connect/gql/mutation)).

For example:

*   In a mutation that contains an embedded query, the `response` binding contains lookup data at `response.query.<fieldName>.<fieldName>....`, in this case, `response.query.todoList` and `response.query.todoList.priority`.

    ```graphql
    mutation CheckTodoPriority(
      $uniqueListName: String!
    ) {
      # This query is identified as `response.query`
      query @check(expr: "response.query.todoList.priority == 'high'", message: "This list is not for high priority items!") {
        # This field is identified as `response.query.todoList`
        todoList(where: { name: $uniqueListName }) {
          # This field is identified as `response.query.todoList.priority`
          priority
        }
      }
    }
    ```

*   In a multi-step mutation, for example with multiple `_insert` fields, the `response` binding contains partial data at `response.<fieldName>.<fieldName>....`, in this case, `response.todoList_insert.id`.

    ```graphql
    mutation CreateTodoListWithFirstItem(
      $listName: String!,
      $itemContent: String!
    ) @transaction {
      # Step 1
      todoList_insert(data: {
        id_expr: "uuidV4()",
        name: $listName,
      })
      # Step 2:
      todo_insert(data: {
        listId_expr: "response.todoList_insert.id" # <-- Grab the newly generated ID from the partial response so far.
        content: $itemContent,
      })
    }
    ```

The `this` binding

> **Note:** The `this` binding is valid for `@check` expressions, not `@auth` expressions.

The binding `this` evaluates to the field that the `@check` directive is attached to. In a basic case, you might evaluate single-valued query results.

```graphql
mutation UpdateMovieTitle (
  $movieId: UUID!,
  $newTitle: String!)
  @auth(level: USER)
  @transaction {
  # Step 1: Query and check
  query @redact {
    moviePermission( # Look up a join table called MoviePermission with a compound key.
      key: {movieId: $movieId, userId_expr: "auth.uid"}
    ) {
      # Check if the user has the editor role for the movie. `this` is the string value of `role`.
      # If the parent moviePermission is null, the @check will also fail automatically.
      role @check(expr: "this == 'editor'", message: "You must be an editor of this movie to update title")
    }
  }
  # Step 2: Act
  movie_update(id: $movieId, data: {
    title: $newTitle
  })
}
```

If the returned field occurs multiple times because any ancestor is a list, each occurrence is tested with `this` bound to each value.

For any given path, if an ancestor is `null` or `[]`, the field won't be reached and the CEL evaluation will be skipped for that path. In other words, evaluation only takes place when `this` is `null` or non-`null`, but never `undefined`.

When the field itself is a list or object, `this` follows the same structure (including all descendants selected in case of objects), as illustrated in the following example.

```graphql
mutation UpdateMovieTitle2($movieId: UUID!, $newTitle: String!) @auth(level: USER) @transaction {
  # Step 1: Query and check
  query {
    moviePermissions( # Now we query for a list of all matching MoviePermissions.
      where: {movieId: {eq: $movieId}, userId: {eq_expr: "auth.uid"}}
    # This time we execute the @check on the list, so `this` is the list of objects.
    # We can use the `.exists` macro to check if there is at least one matching entry.
    ) @check(expr: "this.exists(p, p.role == 'editor')", message: "You must be an editor of this movie to update title") {
      role
    }
  }
  # Step 2: Act
  movie_update(id: $movieId, data: {
    title: $newTitle
  })
}
```

Complex expression syntax

You can write more complex expressions by combining with the `&&` and `||` operators.

```graphql
mutation UpsertUser($username: String!) @auth(expr: "(auth != null) && (vars.username == 'joe')")
```

The following section describes all available operators.

Operators and operator precedence

Use the following table as a reference for operators and their corresponding precedence.

Given arbitrary expressions `a` and `b`, a field `f`, and an index `i`.

*(Table incomplete in source text, missing actual operators and precedence)*

Data in auth tokens

The `auth.token` object may contain the following values:

*(Table incomplete in source text)*

Additional fields in JWT ID tokens

You can also access the following `auth.token` fields:

*(Table incomplete in source text)*

# Audit logging for Firebase Data Connect

This page describes the audit logs created by Firebase as part of [Cloud Audit Logs](https://cloud.google.com/logging/docs/audit/).

Overview

Firebase services write audit logs to help you answer the questions, "Who did what, where, and when?". These are Cloud Audit Logs, provided as part of the [Google Cloud project connected to your Firebase project](//firebase.google.com/docs/projects/learn-more#firebase-cloud-relationship).

Your Firebase projects each contain only the audit logs for resources that are directly within the project.

For a general overview of Cloud Audit Logs, see [Cloud Audit Logs overview](https://cloud.google.com/logging/docs/audit/). For a deeper understanding of the audit log format, see [Understand audit logs](https://cloud.google.com/logging/docs/audit/understanding-audit-logs).

Available audit logs

The following types of audit logs are available for Firebase Data Connect:

*   Admin Activity audit logs

    Includes "admin write" operations that write metadata or configuration information.

    You can't disable Admin Activity audit logs.
*   Data Access audit logs

    Includes "admin read" operations that read metadata or configuration information. Also includes "data read" and "data write" operations that read or write user-provided data.

    To receive Data Access audit logs, you must explicitly enable them.

For fuller descriptions of the audit log types, see [Types of audit logs](https://cloud.google.com/logging/docs/audit#types).

Audited operations

The following summarizes which API operations correspond to each audit log type in Firebase Data Connect:

*(Table incomplete in source text, missing API operations and corresponding log types)*

Audit log format

Audit log entries include the following objects:

*   The log entry itself, which is an object of type [`LogEntry`](https://cloud.google.com/logging/docs/reference/v2/rest/v2/LogEntry). Useful fields include the following:
    *   The `logName` contains the resource ID and audit log type.
    *   The `resource` contains the target of the audited operation.
    *   The `timestamp` contains the time of the audited operation.
    *   The `protoPayload` contains the audited information.
*   The audit logging data, which is an [`AuditLog`](https://cloud.google.com/logging/docs/reference/audit/auditlog/rest/Shared.Types/AuditLog) object held in the `protoPayload` field of the log entry.
*   Optional service-specific audit information, which is a service-specific object. For older integrations, this object is held in the `serviceData` field of the `AuditLog` object; newer integrations use the `metadata` field.

For other fields in these objects, and how to interpret them, review [Understand audit logs](https://cloud.google.com/logging/docs/audit/understanding-audit-logs).

Log name

Cloud Audit Logs resource names indicate the Firebase project or other Google Cloud entity that owns the audit logs, and whether the log contains Admin Activity, Data Access, Policy Denied, or System Event audit logging data. For example, the following shows log names for project-level Admin Activity audit logs and an organization's Data Access audit logs. The variables denote Firebase project and organization identifiers.

```
projects/PROJECT_ID/logs/cloudaudit.googleapis.com%2Factivity
```

```
organizations/ORGANIZATION_ID/logs/cloudaudit.googleapis.com%2Fdata_access
```

> **Note:** The part of the log name following `/logs/` must be URL-encoded. The forward-slash character, `/`, must be written as `%2F`.

Service name

Firebase Data Connect audit logs use the service name `firebasedataconnect.googleapis.com`.

For a full list of all the Cloud Logging API service names and their corresponding monitored resource type, see [Map services to resources](https://cloud.google.com/logging/docs/api/v2/resource-list#service-names).

Resource types

Firebase Data Connect audit logs use the resource type `audited_resource` for all audit logs.

For a list of all the Cloud Logging monitored resource types and descriptive information, see [Monitored resource types](https://cloud.google.com/logging/docs/api/v2/resource-list#resource-types).

Enable audit logging

Admin Activity audit logs are always enabled; you can't disable them.

Data Access audit logs are disabled by default and aren't written unless explicitly enabled (the exception is Data Access audit logs for BigQuery, which can't be disabled).

For instructions on enabling some or all of your Data Access audit logs, see [Configure Data Access logs](https://cloud.google.com/logging/docs/audit/configure-data-access).

Permissions and roles

[Cloud IAM](https://cloud.google.com/iam/docs) permissions and roles determine your ability to access audit logs data in Google Cloud resources.

When deciding which [Logging-specific permissions and roles](https://cloud.google.com/logging/docs/access-control#permissions_and_roles) apply to your use case, consider the following:

*   The Logs Viewer role (`roles/logging.viewer`) gives you read-only access to Admin Activity, Policy Denied, and System Event audit logs. If you have just this role, you cannot view Data Access audit logs that are in the `_Default` bucket.
*   The Private Logs Viewer role(`roles/logging.privateLogViewer`) includes the permissions contained in `roles/logging.viewer`, plus the ability to read Data Access audit logs in the `_Default` bucket.

    Note that if these private logs are stored in user-defined buckets, then any user who has permissions to read logs in those buckets can read the private logs. For more information on log buckets, see [Routing and storage overview](https://cloud.google.com/logging/docs/routing/overview).

For more information on the Cloud IAM permissions and roles that apply to audit logs data, see [Access control](https://cloud.google.com/logging/docs/access-control).

View logs

To find and view audit logs, you need to know the identifier of the Firebase project, folder, or organization for which you want to view audit logging information. You can further specify other indexed [`LogEntry`](https://cloud.google.com/logging/docs/reference/v2/rest/v2/LogEntry) fields, like `resource.type`; for details, review [Find log entries quickly](https://cloud.google.com/logging/docs/view/advanced-queries#finding-quickly).

The following are the audit log names; they include variables for the identifiers of the Firebase project, folder, or organization:

```sql
   projects/PROJECT_ID/logs/cloudaudit.googleapis.com%2Factivity
   projects/PROJECT_ID/logs/cloudaudit.googleapis.com%2Fdata_access
   projects/PROJECT_ID/logs/cloudaudit.googleapis.com%2Fsystem_event
   projects/PROJECT_ID/logs/cloudaudit.googleapis.com%2Fpolicy

   folders/FOLDER_ID/logs/cloudaudit.googleapis.com%2Factivity
   folders/FOLDER_ID/logs/cloudaudit.googleapis.com%2Fdata_access
   folders/FOLDER_ID/logs/cloudaudit.googleapis.com%2Fsystem_event
   folders/FOLDER_ID/logs/cloudaudit.googleapis.com%2Fpolicy

   organizations/ORGANIZATION_ID/logs/cloudaudit.googleapis.com%2Factivity
   organizations/ORGANIZATION_ID/logs/cloudaudit.googleapis.com%2Fdata_access
   organizations/ORGANIZATION_ID/logs/cloudaudit.googleapis.com%2Fsystem_event
   organizations/ORGANIZATION_ID/logs/cloudaudit.googleapis.com%2Fpolicy
```

You can view audit logs in Cloud Logging using the Google Cloud console, the `gcloud` command-line tool, or the Logging API.

Console

You can use the Logs Explorer in the Google Cloud console to retrieve your audit log entries for your Firebase project, folder, or organization:

1.  In the Google Cloud console, go to the **Logging > Logs Explorer** page.

    [Go to the Logs Explorer page](https://console.cloud.google.com/logs/viewer)

    > **Note:** If you're using the **Legacy Logs Viewer** page, switch to the **Logs Explorer** page.
2.  On the **Logs Explorer** page, select an existing Firebase project, folder or organization.
3.  In the **Query builder** pane, do the following:
    *   In **Resource type**, select the Google Cloud resource whose audit logs you want to see.
    *   In **Log name**, select the audit log type that you want to see:
        *   For Admin Activity audit logs, select **activity**.
        *   For Data Access audit logs, select **data_access**.
        *   For System Event audit logs, select **system_event**.
        *   For Policy Denied audit logs, select **policy**.

    If you don't see these options, then there aren't any audit logs of that type available in the Firebase project, folder, or organization.

    For more details about querying using the Logs Explorer, see [Build log queries](https://cloud.google.com/logging/docs/view/building-queries).

`gcloud`

The `gcloud` command-line tool provides a command-line interface to the Cloud Logging API. Supply a valid `PROJECT_ID`, `FOLDER_ID`, or `ORGANIZATION_ID` in each of the log names.

To read your Firebase project-level audit log entries, run the following command:

```bash
gcloud logging read "logName : projects/PROJECT_ID/logs/cloudaudit.googleapis.com" --project=PROJECT_ID
```

To read your folder-level audit log entries, run the following command:

```bash
gcloud logging read "logName : folders/FOLDER_ID/logs/cloudaudit.googleapis.com" --folder=FOLDER_ID
```

To read your organization-level audit log entries, run the following command:

```bash
gcloud logging read "logName : organizations/ORGANIZATION_ID/logs/cloudaudit.googleapis.com" --organization=ORGANIZATION_ID
```

For more information about using the `gcloud` tool, see [Read log entries](https://cloud.google.com/sdk/gcloud/reference/logging/read).

API

When building your queries, replace the variables with valid values, substitute the appropriate project-level, folder-level, or organization-level audit log name or identifiers as listed in the audit log names. For example, if your query includes a `PROJECT_ID`, then the project identifier you supply must refer to the currently selected Firebase project.

To use the Logging API to look at your audit log entries, do the following:

1.  Go to the **Try this API** section in the documentation for the [`entries.list`](https://cloud.google.com/logging/docs/reference/v2/rest/v2/entries/list) method.
2.  Put the following into the **Request body** part of the **Try this API** form. Clicking on this [prepopulated form](https://cloud.google.com/logging/docs/reference/v2/rest/v2/entries/list?apix_params=%7B%22resource%22%3A%7B%22resourceNames%22%3A%5B%22projects%2F%5BPROJECT_ID%5D%22%5D%2C%22pageSize%22%3A5%2C%22filter%22%3A%22logName%3D(projects%2F%5BPROJECT_ID%5D%2Flogs%2Fcloudaudit.googleapis.com%252Factivity%20OR%20projects%2F%5BPROJECT_ID%5D%2Flogs%2Fcloudaudit.googleapis.com%252Fsystem_events%20OR%20projects%2F%5BPROJECT_ID%5D%2Flogs%2Fcloudaudit.googleapis.com%252Fdata_access)%22%7D%7D) automatically fills the request body, but you need to supply a valid `PROJECT_ID` in each of the log names.

    ```json
    {
      "resourceNames": [
        "projects/PROJECT_ID"
      ],
      "pageSize": 5,
      "filter": "logName : projects/PROJECT_ID/logs/cloudaudit.googleapis.com"
    }
    ```
3.  Click **Execute**.

For more details about querying, see [Logging query language](https://cloud.google.com/logging/docs/view/logging-query-language).

For an example of an audit log entry and how to find the most important information in it, see [Sample audit log entry](https://cloud.google.com/logging/docs/audit/understanding-audit-logs#sample).

Route audit logs

You can [route audit logs](https://cloud.google.com/logging/docs/routing/overview) to supported destinations in the same way that you can route other kinds of logs. Here are some reasons you might want to route your audit logs:

*   To keep audit logs for a longer period of time or to use more powerful search capabilities, you can route copies of your audit logs to Google Cloud Storage, BigQuery, or Google Cloud Pub/Sub. Using Cloud Pub/Sub, you can route to other applications, other repositories, and to third parties.
*   To manage your audit logs across an entire organization, you can create [aggregated sinks](https://cloud.google.com/logging/docs/export/aggregated_sinks) that can route logs from any or all Firebase projects in the organization.
*   If your enabled Data Access audit logs are pushing your Firebase projects over your log allotments, you can create sinks that exclude the Data Access audit logs from Logging.

For instructions on routing logs, see [Configure sinks](https://cloud.google.com/logging/docs/export/configure_export_v2).

Pricing

[Admin Activity audit logs](https://cloud.google.com/logging/docs/audit#admin-activity) and [System Event audit logs](https://cloud.google.com/logging/docs/audit#system-event) are no-cost.

[Data Access audit logs](https://cloud.google.com/logging/docs/audit#data-access) and [Policy Denied audit logs](https://cloud.google.com/logging/docs/audit#policy_denied) are chargeable.

For more information about Cloud Logging pricing, see [Google Cloud's operations suite pricing: Cloud Logging](https://cloud.google.com/stackdriver/pricing#logging-costs).

# Use the Data Connect emulator for CI/CD

Firebase Data Connect provides you with a local emulator for end-to-end prototyping as well as continuous integration and continuous deployment (CI/CD) flows:

*   The Data Connect emulator interacts with a local integrated PGLite database instance to let you prototype queries and mutations and test client code in a fully local environment.
*   The Data Connect emulator can also be used for non-interactive work. It lets you run automated tests and is suitable for use with CI/CD workflows. This is useful when your schemas are stable and you want to prototype and test client-side code.

This guide covers installation and usage of the emulator in more detail than the quickstart.

Install the Data Connect emulator

Before installing the Local Emulator Suite to use the Data Connect emulator, you will need:

*   Node.js version 18.0 or higher.

Install the Firebase CLI and set up project directory

> **Note:** If you've followed the [Get started with Firebase Data Connect](/docs/data-connect/quickstart) guide, you can skip this section.

1.  Install the Firebase CLI, [following the installation guide](/docs/cli). Be sure to [update regularly](/docs/cli#update-cli), since the Data Connect emulator is under active development with bug fixes and new features.
2.  If you haven't already done so, initialize the current working directory as a Firebase project, following prompts to specify which products to use:

    ```bash
    firebase init
    ```

Set or modify the Local Emulator Suite configuration

If you started the Data Connect emulator from the Firebase VS Code extension, the emulator was installed for you, if needed.

You can use the Firebase CLI to manually install the emulator along with other selected components of the Local Emulator Suite. This command starts a configuration wizard that lets you select emulators of interest, download the corresponding emulator binary files, and set emulator ports if the defaults are not appropriate.

```bash
firebase init emulators
```

Once an emulator is installed, no update checks are performed and no additional automatic downloads will occur until you update your Firebase CLI version.

Choose a Firebase project

In the setup flow, the Firebase CLI prompts you to choose or create a Firebase project. If you choose an existing project you've set up with Data Connect in the Firebase console, the configuration you chose there will be suggested.

Set up the emulator

> **Note:** Usage of the emulator in the Firebase Data Connect VS Code extension is covered in [Get started with Firebase Data Connect](/docs/data-connect/quickstart).

Configure the emulator

Running the `firebase init` flow will guide you through emulator setup options. Like other emulators in the Local Emulator Suite, configuration parameters are stored in local project files.

*   Your `firebase.json` file contains emulator port assignments.
*   The `emulators:ui` key does not apply to the Data Connect emulator.

Work with local and production Data Connect resources

If you want to be sure not to impact production resources, set a `demo-` projectID or make sure your client code is instrumented to connect to the emulator, as discussed in a later section.

Start the emulator

If you're running the emulator non-interactively, for example for CI/CD workflows, start it with the `exec` option.

```bash
firebase emulators:exec ./path/to/test-script.sh
```

If you're integrating predefined queries and mutations in client code and are using the emulator specifically for testing clients, you can use the `start` option for interactive work. You can also start the emulator from the VS Code extension.

```bash
firebase emulators:start
```

> **Note:** When you start the emulator with `firebase emulators:start`, SDK code will be automatically generated just as if you had run `firebase sdk:generate`.

Instrument your client code to talk to the emulator

Set up your in-app configuration or test classes to interact with the Data Connect emulator as follows.

JavaScript

```javascript
import { initializeApp } from "firebase/app";
import { connectorConfig } from "@name-of-package";
import { connectDataConnectEmulator, getDataConnect } from 'firebase/data-connect';

// TODO: Replace the following with your app's Firebase project configuration
const firebaseConfig = {
  //...
};

const app = initializeApp(firebaseConfig);

const dataConnect = getDataConnect(app, connectorConfig);
connectDataConnectEmulator(dataConnect, "localhost", 9399);

// Make calls from your app
```

Kotlin Android

```kotlin
val connector = MoviesConnector.instance

// Connect to the emulator on "10.0.2.2:9399"
connector.dataConnect.useEmulator()

// (Alternatively) if you're running your emulator on non-default port:
connector.dataConnect.useEmulator(port = 9999)

// Make calls from your app
```

iOS

```swift
let connector = DataConnect.dataConnect(DefaultConnectorClient.connectorConfig)

// Connect to the emulator on "127.0.0.1:9399"
connector.useEmulator()

// (alternatively) if you're running your emulator on non-default port:
connector.useEmulator(port: 9999)

// Make calls from your app
```

Use the emulator for testing and continuous integration

Run containerized Local Emulator Suite images

Installation and configuration of the Local Emulator Suite with containers in a typical CI setup is straightforward.

There are a few issues to note:

*   Emulator binaries are installed and cached at `~/.cache/firebase/emulators/`. You may want to add this path to your CI cache configuration to avoid repeated downloads.
*   If you don't have a `firebase.json` file in your repository, you must add a command line argument to the `emulators:start` or `emulators:exec` command to specify which emulators should be started. For example, `--only dataconnect`.

Clear your database between tests

To reset your test environments between runs, Firebase recommends:

*   Writing dedicated mutations to handle the following:
    *   In setup, populate a local database instance with starting data.
    *   In teardown, delete modified data from post-test database instance.

How the Data Connect emulator differs from production

The Data Connect emulator simulates many features of the server-side product. However, there are some exceptions to be aware of:

*   The version and detailed configuration of PGLite may differ from the version of your production Cloud SQL instance.
*   If you're using the emulator to develop with Data Connect's pgvector and Vertex API integration, calls to the Cloud Vertex API are made directly, rather than through Cloud SQL's Vertex integration. However, calls to the production API are still made, meaning you must use a real Firebase project, cannot use a `demo-` project, and costs of the Vertex API will be incurred.

# Use generated Flutter SDKs

Firebase Data Connect client SDKs let you call your server-side queries and mutations directly from a Firebase app. You generate a custom client SDK in parallel as you design the schemas, queries and mutations you deploy to your Data Connect service. Then, you integrate methods from this SDK into your client logic.

As we've mentioned elsewhere, it's important to note that Data Connect queries and mutations are not submitted by client code and executed on the server. Instead, when deployed, Data Connect operations are stored on the server like Cloud Functions. This means you need to deploy corresponding client-side changes to avoid breaking existing users (for example, on older app versions).

That's why Data Connect provides you with a developer environment and tooling that lets you prototype your server-deployed schemas, queries and mutations. It also generates client-side SDKs automatically, while you prototype.

When you've iterated updates to your service and client apps, both server- and client-side updates are ready to deploy.

What is the client development workflow?

If you followed the [Get started](/docs/data-connect/quickstart), you were introduced to the overall development flow for Data Connect. In this guide, you'll find more detailed information about generating Flutter SDKs from your schema and working with client queries and mutations.

To summarize, to use generated Flutter SDKs in your client apps, you'll follow these prerequisite steps:

1.  Add Firebase to your [Flutter](/docs/flutter/setup) app.
2.  Install the flutterfire CLI `dart pub global activate flutterfire_cli`.
3.  Run `flutterfire configure`.

Then:

1.  Develop your app schema.
2.  Set up SDK generation:
    *   With the **Add SDK to app** button in our Data Connect VS Code extension
    *   By [updating your `connector.yaml`](#generate-flutter).
3.  [Initialize your client code and import libraries](#set-client).
4.  [Implement calls to queries](#using-queries) and [mutations](#using-mutations).
5.  [Set up and use the Data Connect emulator](#prototype-and) and iterate.

Generate your Flutter SDK

As with most Firebase projects, work on your Firebase Data Connect client code takes place in a local project directory. Both the Data Connect VS Code extension and the Firebase CLI are important local tools for generating and managing client code.

SDK generation options are keyed to several entries in the `dataconnect.yaml` file generated when you initialized your project.

Initialize SDK generation In your `connector.yaml`, add your `outputDir`, `package` and (for the web SDK) `packageJsonDir`.

```yaml
connectorId: movies
generate:
  dartSdk:
    outputDir: ../../lib/generated # Feel free to change this to a different path
    package: movies
```

`outputDir` specifies where the generated SDK should output to. This path is relative to the directory that contains the `connector.yaml` file itself. Optionally, you can provide an absolute path to your `outputDir`.

`package` specifies the package name.

Update SDKs while prototyping

If you're prototyping interactively with the Data Connect VS Code extension and its Data Connect emulator, SDK source files are automatically generated and updated while you modify `.gql` files defining schemas, queries and mutations. This can be a useful feature in hot (re)loading workflows. In other scenarios, if you're using the Data Connect emulator from the Firebase CLI, you can set a watch on `.gql` updates and also have SDK sources automatically updated.

Alternatively, you can use the CLI to regenerate SDKs whenever .gql files are changed:

```bash
firebase dataconnect:sdk:generate --watch
```

Generate SDKs for integration and for production releases

In some scenarios, such as preparing project sources to submit for CI tests, you can call the Firebase CLI for a batch update.

In these cases, use `firebase dataconnect:sdk:generate`.

Set up client code

Initialize your Data Connect app

First, initialize your app using the [standard Firebase setup instructions](//firebase.google.com/docs/flutter/setup).

Then, install the Data Connect plugin:

```bash
flutter pub add firebase_data_connect
```

Initialize the Data Connect Flutter SDK

Initialize your Data Connect instance using the information you used to set up Data Connect (all available in the Firebase console Data Connect tab).

Import libraries

There are two sets of imports needed to initialize your client code, general Data Connect imports and specific, generated SDK imports.

```dart
// general imports
import 'package:firebase_data_connect/firebase_data_connect.dart';

// generated queries and mutations from SDK
import 'generated/movies.dart';
```

Use queries on the client side

The generated code will already come with predefined Query Refs. All you need to do is import and call `execute` on them.

```dart
import 'generated/movies.dart';

await MoviesConnector.instance.listMovies().execute();
```

Call SDK query methods

Here's an example using these action shortcut functions:

```dart
import 'generated/movies.dart';

// This will call the generated Dart from the CLI and then make an HTTP request to the server.
MoviesConnector.instance.listMovies().execute().then((data) => showInUI(data)); // == MoviesConnector.instance.listMovies().ref().execute();
```

Optional Fields

Some queries may have optional fields. In these cases, the Flutter SDK exposes a builder method, and will have to be set separately.

For example, the field `rating` is optional when calling `createMovie`, so you need to provide it in the builder function.

```dart
await MoviesConnector.instance.createMovie(
  title: 'Empire Strikes Back',
  releaseYear: 1980,
  genre: "Sci-Fi",
).rating(5).execute();
```

Subscribe to changes

You can subscribe to changes (which will update any time you execute a query).

```dart
QueryRef<ListMoviesData, void> listRef = MoviesConnector.instance.listMovies().ref();

// subscribe will immediately invoke the query if no execute was called on it previously.
listRef.subscribe().listen((data) {
  updateUIWithMovies(data.movies);
});

await MoviesConnector.instance.createMovie(
  title: 'Empire Strikes Back',
  releaseYear: 1980,
  genre: "Sci-Fi",
).rating(5).execute();
await listRef.execute(); // will update the subscription above
```

Use mutations on the client side

Mutations are accessible in the same way as queries.

```dart
await MoviesConnector.instance.createMovie(
  title: 'Empire Strikes Back',
  releaseYear: 1980,
  genre: "Sci-Fi",
).rating(5).execute();
```

Prototype and test your Flutter apps

Instrument clients to use a local emulator

You can use the Data Connect emulator, whether from the Data Connect VS Code extension or from the CLI.

Instrumenting the app to connect to the emulator is the same for both scenarios.

```dart
import 'package:firebase_data_connect/firebase_data_connect.dart';
import 'generated/movies.dart';

MoviesConnector.instance.dataConnect
          .useDataConnectEmulator('127.0.0.1', 9399);

// Make calls from your app
QueryRef<ListMoviesData, void> ref = MoviesConnector.instance.listMovies.ref();
```

To switch to production resources, comment out lines for connecting to the emulator.

Data types in the Dart SDK

The Data Connect server represents common GraphQL data types. These are represented in the SDK as follows.

| Data Connect Type | Dart                               |
| :---------------- | :--------------------------------- |
| Timestamp         | `firebase_data_connect.Timestamp`  |
| Int (32-bit)      | `int`                              |
| Date              | `DateTime`                         |
| UUID              | `string`                           |
| Int64             | `int`                              |
| Float             | `double`                           |
| Boolean           | `bool`                             |
| Any               | `firebase_data_connect.AnyValue`   |

# Deploy and manage Data Connect schemas and connectors

A Firebase Data Connect service has three main components:

*   An underlying PostgreSQL **database** with its own **SQL schema**
*   a Data Connect **application schema** (declared in your `.gql` files)
*   a number of **connectors** (declared in your `.gql` files, configured in `connector.yaml` files).

The SQL schema is the source of truth for your data, the Data Connect schema is how your connectors can see that data, and the connectors declare the APIs that your clients can use to access that data.

When you deploy your Data Connect service with the CLI, you will migrate your SQL schema, then update your Data Connect schema, then update each of your connectors.

> **Note:** Deploying and managing client code you develop with generated SDKs is covered in the SDK guides ([Android](/docs/data-connect/android-sdk), [web](/docs/data-connect/web-sdk), [iOS](/docs/data-connect/ios-sdk), and [Flutter](/docs/data-connect/flutter-sdk)).

Important deployment concepts

To fully understand deployment, it's important to note key concepts about schemas and connectors.

Schema deployments

Deployment of a Data Connect schema affects the SQL schema for your Cloud SQL database. Data Connect helps you *migrate* your schemas during deployment, whether you're working with a new database or need to non-destructively adapt an existing database.

Data Connect schema migrations have two different schema validation modes: *strict* and *compatible*.

*   Strict mode validation requires that the database schema *exactly* match the application schema before the application schema can be updated. Any tables or columns that are not used in your Data Connect schema will be deleted from the database.
*   Compatible mode validation requires that the database schema be *compatible* with the application schema before the application schema can be updated; any additional changes that drop schemas, tables or columns are optional.

    Compatible means that schema migrations only affect tables and columns referenced in your application schema. Elements in your database that are not used by your application schema are left unmodified. Therefore, after deployment, your database may contain unused:
    *   Schemas
    *   Tables
    *   Columns

> **Note:** By default, tooling that handles migration will apply compatible mode changes automatically and then prompt you for optional strict mode changes. You can adjust this behavior as discussed in [migrate database schemas](#migrate-schemas-manually).

Connector deployments

Data Connect queries and mutations are not submitted by client code and executed on the server. Instead, when deployed, these Data Connect operations are stored on the server, like Cloud Functions. This means deployment may break existing users.

Data Connect integrates analysis of breaking changes in your connector updates into the Firebase CLI.

The CLI analyzes changes to each connector with respect to your schema, and issues a set of assessment messages with respect to connector changes that might *alter client behavior* (messages are warning-level) or **might or will break** (messages are breaking-level) previous versions of client code.

For example:

*   Connector changes that might alter client behavior include removing a nullable field from a query without a `@retired` schema annotation.
*   Connector changes that might or will break clients include changing a nullable operation variable to non-null without a default value, or changing the data type of a field to something incompatible (e.g. `String` to `Int`).

A more extensive list of warning-level and breaking-level scenarios is given in the [CLI reference guide](/docs/data-connect/cli-reference#update-connectors).

Follow the deployment workflow

You can work on a Data Connect project both in a local project directory and in the Firebase console.

A recommended deployment flow involves:

1.  Listing currently-deployed **schemas and connectors** with `firebase dataconnect:services:list`.
2.  Managing any **schema updates**.
    1.  Check for SQL schema differences between your Cloud SQL database and local Data Connect schema with `firebase dataconnect:sql:diff`.
    2.  If needed, perform SQL schema migration with `dataconnect:sql:migrate`.
3.  Performing **schema and connect deployments** by running `firebase deploy`, for either just your schema, just your connectors, or combinations of resources.

Deploy and manage Data Connect resources

It's a good idea to verify production resources before performing deployments.

```bash
firebase dataconnect:services:list
```

When working in a local project directory, you'll generally use the `firebase deploy` command to deploy your schema and connectors into production, with interactive feedback.

Using any `deploy` command, the `--only dataconnect` flag lets you to separate Data Connect deployments from other products in your project.

Normal deployment

```bash
firebase deploy --only dataconnect
```

In this normal deployment, the Firebase CLI attempts to deploy your schema and connectors.

> **Note:** Data Connect imposes a 100kB limit on schema source files and connector source files. Avoid including extraneous or unused files in your schema or connector deployments to prevent hitting this limit.

It validates that the new schema does not breaking any existing connectors. Follow [best practices](#best-practices) when making breaking changes.

It also verifies that the SQL schema is already migrated before updating the Data Connect schema. If not, it automatically prompts you through any necessary steps to [migrate schemas](#migrate-schemas-manually).

`--force` flag deployment

```bash
firebase deploy --only dataconnect --force
```

If neither the connector or SQL schema validations are of concern, you can re-run the command with `--force` to ignore them.

The `--force` deploy still checks if the SQL schema matches the Data Connect schema, warns of incompatibility, and prompts.

Deploy selected resources

To deploy with more granular control, use the `--only` flag with the `serviceId` argument. To deploy only schema changes for a particular service:

```bash
firebase deploy --only dataconnect:serviceId:schema
```

You can also deploy all resources for a specified connector and service.

```bash
firebase deploy --only dataconnect:serviceId:connectorId
```

Finally, you can deploy the schema and all connectors for a single service.

```bash
firebase deploy --only dataconnect:serviceId
```

Roll back a deployment

To perform a manual rollback, check out a previous version of your code and deploy it. If the original deployment included destructive breaking changes, you may not be able to fully recover any data deleted.

Migrate database schemas

If you're prototyping rapidly, experimenting with schemas, and know your schema changes are destructive, you can plan on using Data Connect tools to verify the changes and supervise how the updates are carried out.

> **Tip:** Follow our recommended best practices for working with [new databases](#new-databases-recommendations) and [existing databases](#existing-databases-recommendations).

Diff SQL schema changes

You can verify changes:

```bash
firebase dataconnect:sql:diff
```

You can pass a comma-separated list of services.

The command compares local schema for a service with the current schema of the corresponding Cloud SQL database. If there is a difference, it prints out the SQL commands that would be run to fix that difference

Apply changes

When you're satisfied and ready to deploy changes to the schema Cloud SQL instance, issue the `firebase dataconnect:sql:migrate` command. You'll be prompted to approve changes.

```bash
firebase dataconnect:sql:migrate [serviceId]```

In interactive environments, SQL migration statements and action prompts are displayed.

Migrate in strict or compatible mode

In a brand new project, the default [schema validation mode](#schema-deployments) applies. The behavior of the `migrate` command is to apply all database schema changes that are required by your application schema, then prompt you to approve optional operations that drop schemas, tables or columns to force your database schema to exactly match your application schema.

You can adjust this behavior by modifying your `dataconnect.yaml` file. Uncomment the `schemaValidation` key, and declare `COMPATIBLE` so that only required changes are applied in migrations.

```yaml
schemaValidation: "COMPATIBLE"
```

Or set the behavior to `STRICT` so that all schema changes are applied and your database schema is forced to match your application schema.

```yaml
schemaValidation: "STRICT"
```

See the [Data Connect CLI reference for more information](/docs/data-connect/cli-reference#manage-cloudsql-schemas).

Update connectors

When you run `firebase deploy`, the CLI initiates an update of the applicable connectors and issues applicable warning-level (may impact client behavior) and breaking-level (possibly or certainly breaking) assessment messages.

Manage connector updates with the CLI

The CLI has slightly different behavior in interactive mode and non-interactive mode.

As you might expect, in interactive mode, the CLI prompts you to accept all messages. You can override and force connector deployment with the `--force` flag.

```bash
# Prompts for acceptance for any warning-level or breaking-level changes prior
# to deploying connectors.
firebase deploy --only dataconnect
# Will deploy connectors without prompting.
firebase deploy --only dataconnect --force
```

In non-interactive mode, the CLI will deploy your connector as long as there are no breaking-level assessments. Otherwise, your script will exit with a log of breaking changes. You can override and deploy by setting the `--force` flag.

```bash
# Will deploy connectors with warning-level changes. If any breaking changes
# are present, the deploy will fail and output any breaking changes
firebase deploy --only dataconnect --non-interactive
# Will deploy the connectors from the previous step, if the same issues are present.
firebase deploy --only dataconnect --non-interactive --force
```

For more information, see the [CLI reference guide](/docs/data-connect/cli-reference#update-connectors).

Best practices for managing schemas and connectors

Firebase recommends some practices to follow in your Data Connect projects.

Minimize breaking changes

*   Firebase recommends keeping your Data Connect schema and connector files in source control.
*   Avoid breaking changes when possible. Some common examples of breaking changes include:
    *   Removing a field from your schema
    *   Making a nullable field in your schema nonnullable (ie `Int` -> `Int!`)
    *   Renaming a field in your schema.
*   If you do need to remove a field from your schema, consider splitting it into a few deployments to minimize impact:
    *   First, remove any references to the field in your connectors, and deploy the change.
    *   Next, update your apps to use newly generated SDKs.
    *   Finally, remove the field in your schema `.gql` file, migrate your SQL schema, and deploy once more.

Use strict mode when working with new databases

If you are using Data Connect with a new database and actively developing your application schema, and you want to ensure your database schema stays exactly in line with your application schema, you can specify `schemaValidation: "STRICT"` in your `dataconnect.yaml`.

This will ensure optional changes are applied as well.

Use compatible mode when you have production data in your database

If you are making changes to a database that contains production data, we recommend you execute your schema migrations in compatible mode, to ensure existing data is not dropped. You can specify `schemaValidation: "COMPATIBLE"` in your `dataconnect.yaml`.

In compatible mode, only required schema migration changes are applied to your database.

*   `DROP SCHEMA`, `DROP TABLE`, and `DROP COLUMN` are considered optional statements and will not be generated for your plan, even if your database schema contains schemas, tables, or columns not defined in your application schema.
*   If your database table contains a non-null column that is not included in your application schema, the `NOT NULL` constraint will be removed, so that data can still be added to the table with your defined connectors.

What's next?

*   Deploying and managing client code you develop with generated SDKs are covered in the guides for [Android](/docs/data-connect/android-sdk), [iOS](/docs/data-connect/ios-sdk), [web](/docs/data-connect/web-sdk), and [Flutter](/docs/data-connect/flutter-sdk).
*   For more information about deployment tooling, review the [Data Connect CLI reference](/docs/data-connect/cli-reference) and [Data Connect configuration file reference](/docs/data-connect/configuration-reference).

# Manage Data Connect services and databases

Your Data Connect projects consist of two major infrastructure elements:

*   One or more Data Connect service instances
*   One or more Cloud SQL for PostgreSQL instances

This guide discusses how to set up and manage your Data Connect service instances, and introduces how to manage your associated Cloud SQL instances.

Configure regions for Firebase Data Connect

Projects that use Data Connect require a location setting.

When you create a new Data Connect service instance, you're prompted to select the location of the service.

> **Note:** The locations of your Data Connect services don't affect the options for locations needed for other Firebase products you might have in your project, like your default Cloud Firestore location.

Available locations

Data Connect services can be created in the following [regions](https://cloud.google.com/docs/geography-and-regions).

> **Note:** Cloud SQL for PostgreSQL instances must be provisioned in the same location as their associated Data Connect instance.

*   asia-east1
*   asia-east2
*   asia-northeast1
*   asia-northeast2
*   asia-northeast3
*   asia-south1
*   asia-southeast1
*   asia-southeast2
*   australia-southeast1
*   australia-southeast2
*   europe-central2
*   europe-north1
*   europe-southwest1
*   europe-west1
*   europe-west2
*   europe-west3
*   europe-west4
*   europe-west6
*   europe-west8
*   europe-west9
*   me-west1
*   northamerica-northeast1
*   northamerica-northeast2
*   southamerica-east1
*   southamerica-west1
*   us-central1
*   us-east1
*   us-east4
*   us-south1
*   us-west1
*   us-west2
*   us-west3
*   us-west4

> Data Connect's Vertex AI integration is not supported for CloudSQL for PostgreSQL instances deployed in:
>
> *   asia-northeast2
> *   asia-southeast2
> *   australia-southeast2
> *   northamerica-northeast2
> *   southamerica-west1
> *   us-west2
> *   us-west3

Manage Data Connect service instances

Create services

To create a new service, use the Firebase console or run the local project initialization using the Firebase CLI. These workflows create a new Data Connect service.

These flows also guide you through:

*   Provisioning a new Cloud SQL instance (no-cost tier)
*   Linking an existing Cloud SQL instance to Data Connect (Blaze plan)

> **Note:** Cloud SQL for PostgreSQL instances must be provisioned in the same location as their associated Data Connect instance. If your application needs Cloud SQL instances in multiple regions, the Firebase CLI can help deploy the same schema, queries and mutations to the many data connect services in each region.

Manage users

Data Connect provides tools to manage user access that follow the the *principle of least privilege* (grant each user or service account the minimum necessary permissions to support needed functionality) and the notion of *role-based access control (RBAC)* (with predefined roles to manage database permissions, simplifying security management).

To add project members as users who can modify Data Connect instances in your project, use the Firebase console to select appropriate predefined user roles.

> **Note:** Data Connect services and Cloud SQL for PostgreSQL are separate components of your Data Connect project. You administer each component separately. For example, you might add Data Connect users with permissions to delete schemas, but this would not grant them the ability to [perform backups of a PostgreSQL database](#administer-cloud).

These roles grant permissions using Identity and Access Management (IAM). A role is a collection of permissions. When you assign a role to a project member, you grant that project member all the permissions that the role contains. See more information in:

*   The [overview of Firebase IAM roles](/docs/projects/iam/overview)
*   The detailed list of [Data Connect roles](/docs/data-connect/configuration-reference#iam-configuration)

Choose roles to enable specific workflows

IAM roles enable Firebase CLI workflows to let you manage your Data Connect projects.

| CLI command, other workflow         | Role(s) required                                                                                              |
| :---------------------------------- | :------------------------------------------------------------------------------------------------------------ |
| `firebase init dataconnect`         | - No permissions (when not linking a Cloud SQL instance) - `roles/cloudsql.admin` (when creating a Cloud SQL instance) |
| `firebase deploy ---only dataconnect` | - `firebasedataconnect.connectors.*` - `firebasedataconnect.services.*` - `firebasedataconnect.schemas.*` - `roles/cloudsql.admin` |
| `firebase dataconnect:sql:diff`     | - `firebasedataconnect.services.*` - `firebasedataconnect.schemas.*`                                         |
| `firebase dataconnect:sql:migrate`  | - `roles/cloudsql.admin` on the target Cloud SQL instance                                                   |
| `firebase dataconnect:sql:grant`    | - `roles/cloudsql.admin` on the target Cloud SQL instance                                                   |

Monitor Data Connect service performance

Understand service performance

The performance of both the Data Connect service and the Cloud SQL for PostgreSQL service can affect your experience.

*   For the Cloud SQL for PostgreSQL service, refer to general guidance in the [Quotas and limits documentation](//cloud.google.com/sql/docs/postgres/quotas).
*   For the Data Connect service, there is quota for GraphQL requests, affecting the rate at which you can call and execute queries:
    *   An overall per-project quota of 6000 requests per minute from client app connectors.
    *   An overall per-project quota of 6000 requests per minute from the Firebase Admin SDK and from the REST API.
    *   A per-user quota of 1200 requests per minute. Here, per-user means the limit applies to requests initiated by one IP address, whether from a client app, from the Firebase Admin SDK or from the REST API.

    If you run into those quota limits, please reach out to [Firebase support](https://firebase.google.com/support/troubleshooter/contact) to adjust the relevant quota.

Monitor service performance, usage and billing

You can monitor requests, errors and operation rates, both globally and per operation in the Firebase console.

Manage Cloud SQL instances

Free trial limitations

The following Cloud SQL for PostgreSQL features are not supported in the [3 month free trial](/docs/data-connect/pricing):

*   PostgreSQL versions other than 15.x
*   Use of existing Cloud SQL for PostgreSQL instances
*   Different machine tier than **db-f1-micro**
*   Changing resources of your instance, such as storage, memory, CPU
*   Read replicas
*   Private instance IP address
*   High-availability (multi-zone); only single-zone instances are supported
*   Enterprise Plus edition
*   Automatic backups
*   Automatic storage increase.

Administer Cloud SQL instances

In general, you can manage your Cloud SQL instances using the [Google Cloud console](https://console.cloud.google.com/sql/instances) to perform the following workflows.

> **Note:** Data Connect services and Cloud SQL for PostgreSQL are separate components of your Data Connect project. You administer each component separately. For example, you might add Cloud SQL users with permissions to handle PostgreSQL administrative tasks, like performance monitoring and backups, but this would not grant them the ability to [modify Data Connect instances](#manage-data-connect-users).

*   Stop and restart Cloud SQL instances
*   Create and delete Cloud SQL databases (within instances)
*   Start PostgreSQL database instances with flags and use a [variety of extensions](https://cloud.google.com/sql/docs/postgres/extensions)
*   Monitor performance with [Cloud SQL observability features](https://cloud.google.com/sql/docs/postgres/observability) in the [Google Cloud console](https://console.cloud.google.com/monitoring?project=_)
*   Manage Cloud SQL access and security with features like IAM, secret manager, data encryption and auth proxy
*   Add, delete and administer Cloud SQL users.

For these and other workflows, refer to the [Cloud SQL for PostgreSQL documentation](//cloud.google.com/sql/docs/postgres).

Grant PostgreSQL user roles

Data Connect provides tools to manage user access that follow the the *principle of least privilege* (grant each user or service account the minimum necessary permissions to support needed functionality) and the notion of *role-based access control (RBAC)* (with predefined roles to manage database permissions, simplifying security management).

In some cases, you might want to connect to the Data Connect-managed Cloud SQL database directly via a SQL client of your choice using, for example, Cloud Run, Cloud Functions or GKE.

To enable such connections, you need to grant SQL permissions by:

*   Assigning the `roles/cloudsql.client` IAM role to the user or service account that needs to connect to the instance, either from the Google Cloud console or using the gcloud CLI
*   Granting the necessary PostgreSQL role using the Firebase CLI

Assign the Cloud SQL IAM role

For information on working with Cloud SQL for PostgreSQL to assign IAM role `roles/cloudsql.client`, see [Roles and permissions](//cloud.google.com/sql/docs/postgres/roles-and-permissions).

Grant PostgreSQL roles

Using the Firebase CLI, you can grant predefined PostgreSQL roles to users or service accounts associated with your project with the `firebase dataconnect:sql:grant` command.

For example, to grant the writer role, run this command at the CLI:

```bash
firebase dataconnect:sql:grant --role writer
```

For details, refer to the [CLI reference guide](/docs/data-connect/cli-reference#grant-cloudsql-roles).

Integrate existing Cloud SQL for PostgreSQL databases

The default database provisioning and management flow assumes your project uses a new (greenfield) databases, and when you invoke `firebase deploy`, Data Connect will display database schema changes to be made and performs any migrations after you approve.

For existing (brownfield) databases, you may have your own workflow for managing schemas and cannot use Data Connect tooling for migrations, yet would like to use your database in a Data Connect project to take advantage of its SDK generation for mobile and web, query-based authorization, client connection management, and more.

This section offers guidance about the latter case: integrating existing databases with Data Connect.

> **Note:** This discussion assumes you have a CloudSQL for PostgreSQL database and have set up user roles for database administration. If you have a PostgreSQL database you want to migrate to Cloud SQL, you can use the Database Migration Service following [this Cloud SQL for PostgreSQL guide](//cloud.google.com/database-migration/docs/postgres/quickstart).

Integrate an existing database into a Data Connect project

The workflow for integrating an existing database generally involves these steps:

1.  During Data Connect project setup in the Firebase console, select the instance and database.
2.  Using the Firebase CLI, run the `firebase dataconnect:sql:setup` command and decline the option to allow Data Connect to handle SQL migrations.

    To prevent changes to your database schema not driven by your custom tooling, the `setup` command will assign appropriate reader and writer roles, but not the `owner` role. More information about the `setup` command and PostgreSQL roles is available in the [CLI reference guide](/docs/data-connect/cli-reference#cloudsql-management-commands).
3.  Write a Data Connect GraphQL schema that matches your database schema.

    You can only deploy your GraphQL schema, queries and mutations when your GraphQL schema is compatible with your PostgreSQL schema.

    To simplify aligning both schemas, we provide the `firebase dataconnect:sql:diff` command, which will provide you with the required SQL statements to migrate your database. You can use this to iteratively refine your GraphQL schema to match your existing database schema.
4.  Moving forward, you can iterate quickly on your GraphQL schema, queries, and mutation in your local development environment. Then, when satisfied, you can use `firebase dataconnect:sql:diff` to obtain the SQL migration statements that you can apply to PostgreSQL using your custom tooling and flows.
5.  Alternatively, you might make changes directly to your PostgreSQL database first, then try to port them back into your GraphQL schema. We recommend the GraphQL-first approach, since there might be cases where the schema changes aren't supported. In addition, if you deploy changes that make your PostgreSQL schema incompatible with deployed connector queries or mutation, then those connectors might stop working or misbehave.

# Firebase Data Connect pricing

This document explains Firebase Data Connect pricing details.

If you pay in a currency other than USD, the prices listed in your currency on [Cloud Platform SKUs](https://cloud.google.com/skus) apply.

Understand Data Connect billing

Firebase Data Connect consists of two billable components:

*   The Data Connect service itself
*   The Cloud SQL for PostgreSQL instance that contains your project data.

If you integrate with Vertex AI, you are billed for vector embeddings.

Data Connect service pricing

*   Network egress has no cost up to 10 Gib/month; more than 10 Gib/month, egress is charged at [Google Cloud Internet Data Transfer Rate Premium Tier pricing](https://cloud.google.com/vpc/pricing#internet_egress).
*   Operations (queries or mutations) executed from clients incur no cost up to 250,000 operations per month; more than 250,000, operations are charged at $4.00 per million.

    > **Note:** The price is per operation and is not related to the amount of data read from the database; there is no "per row read" fee. Each Data Connect operation can perform efficient, complex, multi-table queries or multi-row updates.

Cloud SQL no cost trial

If you accept the default configuration when you provision a Cloud SQL for PostgreSQL instance, you will be qualified for a no cost trial for 3 months.

*   5 free trials are available per billing account.
*   1 free trial Cloud SQL for PostgreSQL instance per project, although you can have multiple non-free instances within that project.
*   The default configuration of your Cloud SQL for PostgreSQL instance is equivalent to a [db-f1-micro instance](https://cloud.google.com/products/calculator) that has 1 vCPU, 10 GB of storage, 628.74 MB of memory.

During the no cost trial, you can add computing resources to your Cloud SQL instance, set up a private IP for your instance, and create a read replica for your instance, at which point you will be billed according to [Cloud SQL pricing](https://cloud.google.com/sql/docs/postgres/pricing).

After 3 months, pricing starts as low as $9.37 / month. Pricing varies based on regions and configurations. See [Cloud SQL pricing](https://cloud.google.com/sql/docs/postgres/pricing).

> **Note:** Existing customers who participated in the Public Preview trials will automatically roll into the 3 month no cost trials when General Availability starts.
> **Note:** If you delete your no cost trial instance, your no cost trial for the associated Firebase project will terminate immediately.

Vertex AI embedding generation

Using Data Connect with [Vertex AI](https://cloud.google.com/vertex-ai) will incur standard usage charges from Vertex AI for embedding generation.

Manage spending

To monitor your Data Connect usage, to access an overall view of all service activity, and links to analyze individual service activity, open the [Data Connect product page](//console.firebase.google.com/project/_/dataconnect). Use the dashboards to gauge your usage over different time periods.

To track your Data Connect costs, create a monthly budget in the Cloud console. Budgets won't limit your usage, but you can set alerts to notify you when you're approaching or exceeding your planned costs for the month.

To set a budget, in the Cloud console, go to the [Billing](https://console.cloud.google.com/billing/) section and create a budget for your Cloud Billing account. You can use the default alert settings or modify the alerts to send notifications at different percentages of your monthly budget.

Learn more about [setting up budgets and budget alerts](//firebase.google.com/docs/projects/billing/avoid-surprise-bills#set-up-budget-alert-emails).

# Get started with Firebase Data Connect

> **Note:** Follow this quickstart guide if you want to add Data Connect to one of your Firebase projects **on the Blaze plan**, create a Data Connect service, and provision a Cloud SQL database for your prototyping. If you'd rather **use the Spark plan** and prototype locally with an emulator and local database, try the [local development get started](/docs/data-connect/quickstart-local).

In this quickstart, you will learn how to build Firebase Data Connect in your application with a production SQL instance.

In the Firebase console you will:

*   Add Firebase Data Connect to your Firebase project.
*   Create a **schema** for an app with AI-assisted schema generation in the Firebase console, and deploy it.
*   Provision a Cloud SQL instance for your app.
*   With Gemini in Firebase, populate your database with **sample data**.
*   Create **queries and mutations**, with AI-assisted operation generation, which you can deploy and use to develop client code locally.

Then, in your local development environment, you will:

*   Set up a development tooling including a Visual Studio Code extension to work with your production instance.
*   Sync your local environment with the assets you created in the console.
*   Generate **strongly typed SDKs** and use them in your app.

> Explore a quickstart app repository and build a fully-featured Data Connect app by following our [codelab for web](/codelabs/firebase-dataconnect-web), [codelab for iOS](/codelabs/firebase-dataconnect-ios), or [codelab for Android](/codelabs/firebase-dataconnect-android).

Console flow: Use AI assistance to design your schema, then deploy it to your database

1.  If you haven't already, create a Firebase project.
    1.  In the [Firebase console](https://console.firebase.google.com), click **Add project**, then follow the on-screen instructions.
2.  Navigate to the Data Connect section of the Firebase console.
3.  Click the **Get started with Gemini** button.
4.  In the **Schema Generator** workflow panel that appears, describe an app so Gemini can help create a GraphQL schema with you.
5.  Review the GraphQL schema, then click **Upgrade and deploy**.
6.  Upgrade your project to the Blaze plan. This lets you create a Cloud SQL for PostgreSQL instance.

    > **Note:** Though you set up billing in your Blaze upgrade, you won't be charged for usage of Data Connect or the [default Cloud SQL for PostgreSQL configuration](/docs/data-connect#pricing) during the trial.
7.  Select **Create a new Cloud SQL** instance. In the dialog that appears, select a location and naming for your Cloud SQL for PostgreSQL database.

    Your app schema is deployed, along with a PostgreSQL database corresponding to that schema.

    > **Note:** If you would like to use customer-managed encryption keys (CMEK) make sure you choose **Use existing Cloud SQL instance** and select an existing Cloud SQL database with CMEK.
    > **Note:** It may take up to 15 minutes to finish provisioning your Cloud SQL for PostgreSQL instance. You can confirm the Data Connect setup flow, including database provisioning, is complete using the [Google Cloud console](//console.cloud.google.com/sql/instances?project=_).

Console flow: Use AI assistance to create operations for your clients

Once your schema is deployed, you can take the first steps to make this data available accessible from your client apps by creating a **connector** of queries and mutations to deploy to the backend, and later call from clients.

Our AI assistance tools are here to help.

> **Note:** You cannot create operations until you've created and deployed a schema.

1.  When prompted, click the **Generate operations with Gemini** button.
2.  After a few moments, in the **Generate your operations** workflow panel that appears, review the list of queries and mutations provided by Gemini based on your schema.
3.  Click each operation row to review the GraphQL code that defines that operation. If necessary, use the trashcan control to delete operations you don't need.
4.  To add operations, click the **+ Add** button. Then:
    1.  Describe your operation in natural language.

        For example:

        `List all products`

    2.  Review the generated GraphQL.
    3.  If the operation is acceptable, click **Insert** to add it to your operations list.
5.  Continue removing and adding operations until your operation set is acceptable.
6.  To deploy this list of operations as a client-callable **connector** set, choose the connector's name, then click **Deploy**.

Console flow: Use Gemini in Firebase to create a mutation and populate your database

By completing previous steps, you created a Data Connect **schema** consisting of relevant entity types, and deployed it to production, meaning a PostgreSQL database with corresponding **tables** was also created and deployed.

To populate your database, you can use Gemini in Firebase to help you take your natural language inputs to define a GraphQL **mutation** to update one of your tables and a **query** to confirm your updates.

> **Note:** You cannot create operations until you've created and deployed a schema.
> **Tip:** Since your schema can describe any kind of app, what entity can we refer to for sake of learning Data Connect in this guide? Well, your schema is likely to contains basic entity types like `Movie` (for a movie review app), `Product` (for an ecommerce app) or `Account` (for a payments app). Pick a single type in your schema for the next few steps.
> **Warning:** Running a mutation in the data editor will execute the mutation and may change your data.

1.  Open the **Data** tab.
2.  Click the **Help me write GraphQL** pen_spark icon and, in the box that appears, type your input.

    > **Note:** Pick a simple, basic entity like `Product` or `Account` to populate with data.

    For example:

    `Add data for three sample products to my app.`

3.  Click **Generate**. The mutation is returned.
4.  Review the output. If needed, click **Edit** to refine the prompt and click **Regenerate**.
5.  Next, click **Insert** to insert the mutation into the data editor.
6.  Click **Run**.

When you run the mutation, data is written to the applicable table in your PostgreSQL database. You can create a query in the console to view the stored data:

1.  Repeat the previous steps, using **Help me write GraphQL** pen_spark to create a query.
2.  In the box that appears, type your input.

    For example:

    `Query data for all sample products in my app.`

3.  Click **Generate**, then **Run**.

Local flow: Choose development tooling

Now that your have data in your deployed database, and have deployed a connector, you can continue development of your schema and connectors in your local development environment.

First, you need to set up a local environment. Data Connect offers you two ways to install development tools.

Auto installation (macOS or Linux)

Manual installation (Windows)

Local flow: Set up the development environment

1.  Create a new directory for your local project.
2.  To set up a Data Connect development environment and browser-based IDE and generate client SDKs, run the following command in the new directory you created.

    ```bash
    curl -sL https://firebase.tools/init/dataconnect | editor=true bash
    ```

    This script attempts the installation. The installed IDE provides toolings, including pre-bundled VS Code extensions, to help you manage your schema and define queries and mutations to be used in your application, and generate strongly-typed SDKs.

    The script also syncs assets you created in the Firebase console to your local directory, and generates client SDKs for any apps you registered for your project.

    > **Note:** If you already have the desktop version of VS Code installed, the script will open it automatically.
    > **Note:** If the script fails, use the [manual installation](/docs/data-connect/quickstart?userflow=manual#code-examples) steps.

Local flow: Set up your local project

To set up your local project, initialize your project directory. In the IDE window, in the left-hand panel, click the Firebase icon to open the Data Connect VS Code extension UI:

1.  Click the **Start emulators** button.

    > **Note:** In the integrated Terminal, verify that your configured emulators start up. Once they are running, you should see your extension UI update with emulator details.

Local flow: Find your schema and connector in the local environment The auto installation option for macOS or Linux you used to sync assets to an existing project has the following effects:

*   It syncs the **schema** you deployed
    *   Find your schema: it is located in your Firebase project directory, in the `/dataconnect/schema/schema.gql` file.
*   It syncs the queries and mutations in the **connector** you deployed
    *   Find your connector: the operations are located in your Firebase project directory, in the `/dataconnect/connector/` directory.

> **Note:** Your schema is unique to the app you described for Gemini and deployed earlier, and contains entity types appropriate for that app.
>
> For the rest of this guide, examples will focus on a `Movie` type that might appear if you had prompted Gemini for a movie review app. This guide will use `Movie` to introduce GraphQL and workflow concepts that apply to any kind of app schema.

Local flow: Understand your schema

Schema example: Movie

In Data Connect, GraphQL fields are mapped to columns. A `Movie` type would likely have `id`, `title`, `imageUrl` and `genre`. Data Connect recognizes the primitive data types `String` and `UUID`.

```graphql
# File `/dataconnect/schema/schema.gql`

# By default, a UUID id key will be created by default as primary key.
# If you want to specify a primary key, say title, which you can do through
# the @table(key: "title") directive
type Movie @table {
  id: UUID! @default(expr: "uuidV4()")
  title: String!
  imageUrl: String!
  genre: String
}
```

Schema example 1:1 table: MovieMetadata

With movies, you can model movie metadata.

For example, in `schema.gql`, you might add the following snippet or review code generated by Gemini.

```graphql
# Movie - MovieMetadata is a one-to-one relationship
type MovieMetadata @table {
  # This time, we omit adding a primary key because
  # you can rely on Data Connect to manage it.

  # @unique indicates a 1-1 relationship
  movie: Movie! @unique
  # movieId: UUID <- this is created by the above reference
  rating: Float
  releaseYear: Int
  description: String
}
```

Notice that the `movie` field is mapped to a type of `Movie`. Data Connect understands that this is a relationship between `Movie` and `MovieMetadata` and will manage this relationship for you.

[Learn more about Data Connect schemas in the documentation](/docs/data-connect/schemas-queries-mutations)

Local flow: Add more data to your tables

In the IDE editor panel, you can see CodeLens buttons appear over the GraphQL types in `/dataconnect/schema/schema.gql`. Just as you did in the console, you can create a mutation to add data to your production database.

> **Note:** Your schema is unique to the app you described to Schema Assist. Pick a basic type in your schema to add data to, like `Movie` (for a movie review app), or `Product` or `Account` (for an ecommerce app).

Working locally, to add data to a table:

1.  In `schema.gql`, click the **Add data** button above the declaration for one of your types (like `Movie`, `Product`, `Account`, depending on the nature of your app).
2.  A new file, `<type>_insert.qgl`, is added to your working directory, such as `Movie_insert.gql` or `Product_insert.gql`. Hard code data in the fields for that type.
3.  Click the **Run (Production)** button.
4.  Repeat the previous steps to add a record to other tables.

To quickly verify data was added:

1.  Back in `schema.gql`, click the **Read data** button above the type declaration.
2.  In the resulting `<type>_read.gql` file, like `Product_read.gql`, click the **Run (Production)** button to execute the query.

[Learn more about Data Connect mutations in the documentation](/docs/data-connect/schemas-queries-mutations)

Define a query

Now for more fun: define the queries you will need in your application. As a developer, you're accustomed to writing SQL queries rather than GraphQL queries, so this can feel a bit different at first.

> **Note:** This section covers creating a query, but the flow applies to mutations as well.

However, GraphQL is far more terse and type-safe than raw SQL. And, our VS Code extension eases the development experience, both for queries and mutations.

To create a query using Gemini Code Assist:

1.  Click the Data Connect VS Code extension icon to open its sidebar.
2.  Click **Try Gemini with @FirebaseDataConnect**. The Gemini Code Assist chat window opens.
3.  Click the chat interface, and begin typing `@FirebaseDataConnect` to filter relevant commands.
4.  Select the `/generate_operation` command and at the prompt, complete the command, asking Gemini to build a query.

    For example:

    `@FirebaseDataConnect /generate_operation List all movies with titles start with "A".`

5.  After a few moments, a recommended query appears. Review the query.

    > **Note:** If you want to modify the initial query, you can execute a new `@FirebaseDataConnect /generate_operation` command and ask Gemini to, for example, filter titles starting with numeric digits. Or, ask it create multiple mutations with an instruction like "Generate a mutation for all my schema types".
6.  To add the code to `queries.gql`:
    1.  Click the **Insert to bottom of file** button
    2.  Or, to insert the code at your cursor position, click the **+** button at the top of the chat response.

Execute the query using the nearby CodeLens button.

[Learn more about Data Connect queries in the documentation](/docs/data-connect/schemas-queries-mutations)

Generate SDKs and use them in your app

In the IDE left-hand panel, click the Firebase icon to open the Data Connect VS Code extension UI:

1.  Click the **Add SDK to app** button.
2.  In the dialog that appears, select a directory containing code for your app. Data Connect SDK code will be generated and saved there.

    > **Note:** If you don't have an app directory yet, you can create and select a new directory for SDK code for now and link it to your app later.
3.  Select your app platform, then note that SDK code is immediately generated in your selected directory.

Use the SDKs to call your query from an app

You can use the SDK that Data Connect generated to implement a call to your `ListMovies` query. You can then execute this query locally using the Data Connect emulator.

Web

1.  Add Firebase to your [web](/docs/web/setup) app.
2.  In your React app's main file:
    *   import your generated SDK
    *   instrument your app to connect to the Data Connect emulator
    *   call Data Connect methods.

    > **Note:** In this sample, the React app calls your query using the Firebase JavaScript SDK. Data Connect also provides special bindings to work with Data Connect asynchronously in [React](/docs/data-connect/web-sdk#react).

    ```javascript
    import React from 'react';
    import ReactDOM from 'react-dom/client';

    import { connectDataConnectEmulator, getDataConnect } from 'firebase/data-connect';

    // Generated queries.
    // Update as needed with the path to your generated SDK.
    import { listMovies, ListMoviesData } from '@movie-app/movies';

    const dataConnect = getDataConnect(connectorConfig);
    connectDataConnectEmulator(dataConnect, 'localhost', 9399);

    function App() {
      const [movies, setMovies] = useState<ListMoviesData['movies']>([]);
      useEffect(() => {
        listMovies.then(res => setMovies(res.data));
      }, []);
      return (
        movies.map(movie => <h1>{movie.title}</h1>)
      );
    }

    const root = ReactDOM.createRoot(document.getElementById('root'));
    root.render(<App />);
    ```

Swift

1.  Add Firebase to your [iOS](/docs/ios/setup) app.
2.  To use the generated SDK, configure it as a dependency in Xcode.

    In the Xcode top navigation bar, select **File > Add Package Dependencies > Add Local**, and choose the folder containing the generated `Package.swift`.
3.  In your app's main delegate:
    *   import your generated SDK
    *   instrument your app to connect to the Data Connect emulator
    *   call Data Connect methods.

    ```swift
    import SwiftUI

    import FirebaseDataConnect
    // Generated queries.
    // Update as needed with the package name of your generated SDK.
    import <CONNECTOR-PACKAGE-NAME>
    let connector = DataConnect.moviesConnector
    // Connect to the emulator on "127.0.0.1:9399"
    connector.useEmulator()
    // (alternatively) if you're running your emulator on non-default port:
    // connector.useEmulator(port: 9999)
    struct ListMovieView: View {
      @StateObject private var queryRef = connector.listMovies.ref()

      var body: some View {
        VStack {
          Button {
            Task {
              do {
                try await refresh()
              } catch {
                print("Failed to refresh: \(error)")
              }
            }
          } label: {
            Text("Refresh")
          }

          // use the query results in a view
          ForEach(queryRef.data?.movies ?? []) { movie in
            Text(movie.title)
          }
        }
      }
      @MainActor
      func refresh() async throws {
        _ = try await queryRef.execute()
      }

      struct ContentView_Previews: PreviewProvider {
        static var previews: some View {
          ListMovieView()
        }
      }
    ```

Kotlin Android

1.  Add Firebase to your [Android](/docs/android/setup) app.
2.  To use the generated SDK, configure Data Connect as a dependency in Gradle.

    Update `plugins` and `dependencies` in your `app/build.gradle.kts`.

    ```kotlin
    plugins {
      // Use whichever versions of these dependencies suit your application.
      // The versions shown here were the latest as of March 14, 2025.
      // Note, however, that the version of kotlin("plugin.serialization") must,
      // in general, match the version of kotlin("android").
      id("com.android.application") version "8.9.0"
      id("com.google.gms.google-services") version "4.4.2"
      val kotlinVersion = "2.1.10"
      kotlin("android") version kotlinVersion
      kotlin("plugin.serialization") version kotlinVersion
    }

    dependencies {
      // Use whichever versions of these dependencies suit your application.
      // The versions shown here were the latest versions as of March 14, 2025.
      implementation("com.google.firebase:firebase-dataconnect:16.0.0-beta04")
      implementation("org.jetbrains.kotlinx:kotlinx-coroutines-core:1.10.1")
      implementation("org.jetbrains.kotlinx:kotlinx-serialization-core:1.7.3")

      // These dependencies are not strictly required, but will very likely be used
      // when writing modern Android applications.
      implementation("org.jetbrains.kotlinx:kotlinx-coroutines-android:1.9.0")
      implementation("androidx.appcompat:appcompat:1.7.0")
      implementation("androidx.activity:activity-ktx:1.10.1")
      implementation("androidx.lifecycle:lifecycle-viewmodel-ktx:2.8.7")
      implementation("com.google.android.material:material:1.12.0")
    }
    ```

3.  In your app's main activity:
    *   import your generated SDK
    *   instrument your app to connect to the Data Connect emulator
    *   call Data Connect methods.

    ```kotlin
    import android.os.Bundle
    import android.widget.TextView
    import androidx.appcompat.app.AppCompatActivity
    import androidx.lifecycle.Lifecycle
    import androidx.lifecycle.lifecycleScope
    import androidx.lifecycle.repeatOnLifecycle
    import kotlinx.coroutines.launch

    private val connector = com.myapplication.MoviesConnector.instance
    .apply {
    // Connect to the emulator on "10.0.2.2:9399" (default port)
    dataConnect.useEmulator()
    // (alternatively) if you're running your emulator on non-default port:
    // dataConnect.useEmulator(port = 9999)
    }
    class MainActivity : AppCompatActivity() {

      override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        val textView: TextView = findViewById(R.id.text_view)

        lifecycleScope.launch {
          lifecycle.repeatOnLifecycle(Lifecycle.State.STARTED) {
            val result = connector.listMovies.runCatching { execute { } }
            val newTextViewText = result.fold(
              onSuccess = {
    val titles = it.data.movies.map { it.title }
    "${titles.size} movies: " + titles.joinToString(", ")
    },
    onFailure = { "ERROR: ${it.message}" }
            )
            textView.text = newTextViewText
          }
        }
      }
    }
    ```

Flutter

1.  Add Firebase to your [Flutter](/docs/flutter/setup) app.
2.  Install the flutterfire CLI `dart pub global activate flutterfire_cli`.
3.  Run `flutterfire configure`.
4.  In your app's main function:
    *   import your generated SDK
    *   instrument your app to connect to the Data Connect emulator
    *   call Data Connect methods.

    ```dart
    import 'package:firebase_core/firebase_core.dart';
    import 'package:flutter/material.dart';
    import 'firebase_options.dart';

    // Generated queries.
    // Update as needed with the path to your generated SDK

    import 'movies_connector/movies.dart';

    void main() async {
      WidgetsFlutterBinding.ensureInitialized();
      await Firebase.initializeApp(
        options: DefaultFirebaseOptions.currentPlatform,
      );
      MoviesConnector.instance.dataConnect
        .useDataConnectEmulator(Uri.base.host, 443, isSecure: true);
      runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
      const MyApp({super.key});
      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          home: Scaffold(
            body: Column(
              children: [
                ConstrainedBox(
                  constraints: const BoxConstraints(maxHeight: 200),
                  child: FutureBuilder(
                    future: MoviesConnector.instance.listMovies().execute(),
                    builder: (context, snapshot) {
                      if (snapshot.connectionState == ConnectionState.done) {
                        return ListView.builder(
                          scrollDirection: Axis.vertical,
                          itemBuilder: (context, index) => Card(
                            child: Text(snapshot.data!.data.movies[index].title),
                          ),
                          itemCount: snapshot.data!.data.movies.length,
                        );
                      }
                      return const CircularProgressIndicator();
                    },
                  ),
                )
              ],
            ),
          ),
        );
      }
    }
    ```

Deploy your schema and query to production

Once you have your local setup on your app, now you can deploy your **schema and connector** to the cloud. You need a Blaze plan project to set up a Cloud SQL instance.

1.  Navigate to Data Connect section of the Firebase console and create a free trial Cloud SQL instance.

    > **Note:** Provisioning of your Cloud SQL for PostgreSQL instance can take up to 15 minutes. You won't be able to deploy until your instance is ready.
    > **Note:** If you would like to use customer-managed encryption keys (CMEK) make sure you choose **Use existing Cloud SQL instance** and select an existing Cloud SQL database with CMEK.
2.  In the IDE integrated **Terminal**, run `firebase init dataconnect` and select the **Region/Service ID** you just created on the console.
3.  Select **"Y"** when prompted with **"File dataconnect/dataconnect.yaml already exists, Overwrite?"**.
4.  In the IDE window, in the VS Code Extension UI, click the **Deploy to production** button.
5.  Once deployed, go to the [Firebase console](https://console.firebase.google.com) to verify the schema, operations and data has been uploaded to the cloud. You should be able to view the schema, and run your operations on the console as well. The Cloud SQL for PostgreSQL instance will be updated with its final deployed generated schema and data.

Next steps

Review your deployed project and discover more tools:

*   Add data to your database, inspect and modify your schemas, and monitor your Data Connect service in the [Firebase console](https://console.firebase.google.com).

Access more information in the documentation. For example, since you've completed the quickstart:

*   Discover more AI assistance tools and guidance to help you generate schemas, queries and mutations. The AI assistance guide covers how to [set up and use our MCP server with your IDEs](/docs/data-connect/ai-assistance#mcp-server) and [best practices for writing prompts](/docs/data-connect/ai-assistance#prompt-design).
*   Learn more about [schema, query and mutation development](/docs/data-connect/schemas-queries-mutations).
*   Learn about generating client SDKs and calling queries and mutations from client code for [web](/docs/data-connect/web-sdk), [Android](/docs/data-connect/android-sdk), and [iOS](/docs/data-connect/ios-sdk), and [Flutter](/docs/data-connect/flutter-sdk).