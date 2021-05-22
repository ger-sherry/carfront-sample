# Car Database

A simple Spring Boot application that uses the H2 in memory database to store cars.

To start the application:  
`./mvnw spring-boot:run`

This Service is dependent on https://github.com/bvader/car-value-estimator and should be started first.

This is the backend for:

The front end React application is at: https://github.com/bvader/carfront which should be started last

If you enter a new Car with the brand of Ferrari it will cause a long running estimate in the car-value-estmator service.

To run on a host other than local you will need to update the `estimator.uri` property
`application.properties` file.

## To start the application with Elastic Java APM Agent and log correlation

Run the build and run script you can change the agent verion if you whish, or add other options. This will start the service expecting all other services and the ELK stack runing on `localhost`

`./run-with-agent.sh`

## To Deploy to Cloud foundry and Leverage Elastic APM agent and log correlation

See the Cloud Foundry Elastic APM Document

https://github.com/cloudfoundry/java-buildpack/blob/master/docs/framework-elastic_apm_agent.md

Create the user provided service with log correlation

`cf cups elastic-apm-service -p '{"server_urls":"https://my-apm-server:8200","secret_token":"my-secret-token", "enable_log_correlation":"'true'"}'`

`cf push -f cardatabase-manifest.yml`

