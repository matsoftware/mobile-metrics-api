# mobile-metrics-api

Bootstrap for a CRUD backend system targeted at persisting [mobile apps metrics](https://github.com/matsoftware/mobile-metrics).

The REST API backend has been developed using **Node JS 12 LTS** using **MS SQL** as default database (to comply with most of the corporates requirements). 

You can change the SQL configuration in [api/app/config/db.config.js](api/app/config/db.config.js).

## Pre-requisites

1. Make sure you have [Node](https://nodejs.org/en/download/) installed

2. Install DB engines:
    - **MS SQL**: install SQL Server using Docker on Unix: https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-linux-2017&pivots=cs1-bash and [Azure Data Studio](https://github.com/microsoft/azuredatastudio/releases/tag/1.21.0) to connect directly to the database
    - **SQLite**: no actions needed (Mac OS)

3. Create a `.env` file in the `api` folder with the local database settings:
    - **MS SQL**:
    ```bash
    DB_HOST=localhost
    DB_USER=sa
    DB_PASS=YourStrong@Passw0rd1
    DB_PORT=1401
    DB_DIALECT=mssql
    SERVER_PORT=3000
    ```
    - **SQLite**:
    ```bash
    DB_HOST=localhost
    DB_USER=root
    DB_PASS=root
    DB_PORT=1401
    DB_STORAGE=mobile_metrics.sqlite
    DB_DIALECT=sqlite
    SERVER_PORT=3000
    ```

4. Install the dependencies by running `./yarn install`; for true offline installations, please update the `.gitignore` file to persist the downloaded binaries

5. Run the server locally with `npm run debug`

     To kill existing open instances of the server do:
    ```bash
    sudo lsof -i :3000
    kill -9 <PID>
    ```

    The project is structured to be easily debugged using VS Code with a preconfigured launch command

6. Add a new `User` entry to the `users` table in the database with the `token` that will be matched against the `X-API-Token` value of the API requests

7. Test the APIs using this Postman collection:

    [![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/d0dbb85e24c41bbcfa42)

## Development

In order to update dependencies, please make sure check your [Yarn offline](https://classic.yarnpkg.com/blog/2016/11/24/offline-mirror/) configuration.