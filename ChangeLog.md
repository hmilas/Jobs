# Rhetos.Jobs Release notes

## 5.2.0 (2022-07-06)

* Better error reporting for missing connection string.

## 5.1.0 (2022-04-08)

* Bugfix: Hangfire Dashboard startup error "Unable to find the required services", missing AddHangfire (issue #1).
* Support for anonymous user with executeInUserContext option.
* The application name in database connection string is extended with " Hangfire" suffix, to help with database debugging (configurable).

## 5.0.0 (2022-03-25)

### Breaking changes

1. Migrated from .NET Framework to .NET 5 and Rhetos 5.
2. Removed method `RhetosJobServer.ConfigureHangfireJobServers`.
   See [Readme.md](Readme.md) for new setup instructions.
3. Renamed class `RhetosJobServer` to `RhetosJobServerFactory`.

## 1.1.0 (2022-02-14)

* Recurring jobs supported, specified by a [CRON expression](https://en.wikipedia.org/wiki/Cron#CRON_expression).
* The recurring jobs that execute a DSL Action can be specified in the application's configuration setting.

## 1.0.0 (2021-04-23)

* Asynchronous execution of background jobs:
  * *IBackgroundJobs* - Creates a new background job that will be executed after the current transaction is completed.
  * *IJobExecuter* - A custom background job executer.
* Helper methods for executing DSL Action in background.
* Integration with Hangfire (optional).
* If the unit of work (web request) that created the job does not complete successfully, the job will not be executed.
* Duplicate jobs, created within a single unit of work, can be aggregated or removed.
* Support for multiple jobs queues.
* Background jobs execution can be distributed over multiple applications, and execute on multiple types of application, such as the main web application, a console app or a windows service.
