# Backend

![Cover](cover.jpg)

## Kotlin

Kotlin can seamlessly leverage the largest ecosystem out there (the JVM), has excellent language features (e.g., custom DSLs, functional programming, scripting), and has excellent tooling (e.g., JetBrains IDE support, multiple compilation targets with relevant libraries, mulitplatform frameworks).

## OpenAPI

Using OpenAPI, you'll no longer face the following problems.
- [Generating documentation](https://github.com/Redocly/redoc)
- Verifying that the docs [match the implementation](http://dredd.io/en/latest/)
- Creating [SDKs](https://github.com/OpenAPITools/openapi-generator) again and again and again for every language ever, and then some more for when the data models update
- Having your frontend buddy in the hackathon [use hardcoded dummy data](https://github.com/stoplightio/prism) which is out-of-sync with what you're [actually working on](https://getsandbox.com/)

## Docker

Runs any program anywhere. It doesn't matter if you use PostgreSQL v11.7 with seeding and migration scripts, Python 2.7 for one server, Java for another server, a reverse proxy server such as nginx, and a bunch of other things. Instead of having complex platform-specific installation instructions, and worries about the device's specific (security) setup (e.g., exposing a particular port), a single command (e.g., `docker-compose up`) will run the entire application with nothing but Docker installed. Since you're developing in the same environment, you can easily migrate between different hosting solutions (e.g., serverless, hybrid cloud), pull in software packages regardless of the OS you're using locally, and can run your program flawlessly with tools such as CI/CD pipelines (i.e., you no longer have to find a CI/CD provider which supports the specific version of your specific language).

## PostgreSQL

It is better to use an RDBMS such as PostgreSQL, than it is to use a NoSQL DBMS such as MongoDB. NoSQL systems are meant for data dumps, such as storing sizeable logs which do not adhere to strict formats. NoSQL databases are meant to be used as a data store so that consumers such as data scientists may query relevant data in an ad-hoc manner. NoSQL systems are easily corrupted (only recently did MongoDB, the most popular NoSQL DBMS, become ACID compliant). There is no schema which causes for duplicate verification code to be created. The lack of a schema makes DB migrations next to impossible, and allows bugs to screw up the entire DB's integrity.

It may seem easier to use NoSQL in the very beginning because it uses objects to store data without any data type specification. But this is the way languages such as Python seem easier to absolute beginners simply because you can type `x = 3` instead of `val x = 3`. As soon as the codebase crosses a noticeable amount (e.g., 100 lines), it not only becomes unmaintainable, but also causes for excessive boilerplate to be written. In essence, it is actually easier and more concise to use what was previously thought to be difficult and verbose.

There is no easy or concise query syntax, and NoSQL systems lack features such as functions, views, joins, etc. Many people think that SQL is difficult simply because they can't wrap their heads around somewhat advanced concepts such as joining tables. The reality is that you don't need to join tables in order to use SQL. In fact, the ability to use features such as joins makes SQL easier. NoSQL simply lacks such features, which gives it a false impression of being simpler.