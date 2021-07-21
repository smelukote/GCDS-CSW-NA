# GCDS-CSW-NA
Deployment architecture
In this guide, you use the following Google Cloud products:

Cloud Build to create a CI/CD pipeline for building, deploying, and testing a data-processing workflow, and the data processing itself. Cloud Build is a managed service that runs your build on Google Cloud. A build is a series of build steps where each step is run in a Docker container.
Cloud Composer to define and run the steps of the workflow, such as starting the data processing, testing and verifying results. Cloud Composer is a managed Apache Airflow service, which offers an environment where you can create, schedule, monitor, and manage complex workflows, such as the data-processing workflow in this tutorial.
Dataflow to run the Apache Beam WordCount example as a sample data process.
The CI/CD pipeline
At a high level, the CI/CD pipeline consists of the following steps:

Cloud Build packages the WordCount sample into a self-running Java Archive (JAR) file using the Maven builder. The Maven builder is a container with Maven installed in it. When a build step is configured to use the Maven builder, Maven runs the tasks.
Cloud Build uploads the JAR file to Cloud Storage.
Cloud Build runs unit tests on the data-processing workflow code and deploys the workflow code to Cloud Composer.
Cloud Composer picks up the JAR file and runs the data-processing job on Dataflow.
The following diagram shows a detailed view of the CI/CD pipeline steps.

