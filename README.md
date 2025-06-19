# Specmatic Studio Demo

[Specmatic Studio](https://specmatic.io/specmatic-studio/) is a #NOCODE GUI interface that simplifies API Contract Testing, API Mocking, API Resiliency Testing, Backward Compatibility Testing, API Spec Generation and more.

This demo project showcases how we can contract test a [Backend For Frontent (BFF) Service / API](https://github.com/specmatic/specmatic-order-bff-java). We will also look at how we can isolate this BFF service from it's dependencies, a HTTP [Domain Service / API](https://github.com/specmatic/specmatic-order-api-java) and Kafka using API mocking. In the process we will look at ability record API specifications using Specmatic Proxy and also Backward Compatibility Testing as we make changes to API specifcations.

The video on our [website](https://specmatic.io/specmatic-studio/) uses this very same repo to demonstrate the above. You can also use this repo as a way to follow along with the video to learn above the various capabilities.

## Application Architecture and Test Setup

![HTML client talks to client API which talks to backend API](specmatic-order-bff-architecture.gif)

## Prerequisites

* [Docker Desktop](https://www.docker.com/products/docker-desktop/)

# Usage

## Setup

1. Clone the repository:
   ```shell
   git clone https://github.com/specmatic/studio-demo
   ```

2. Navigate to the project directory
   ```shell
   cd studio-demo
   ```

3. Start Studio along with the required App services
   ```shell
   docker compose up
   ```

The steps you have run so far will bring up below services in addition to Specmatic Studio itself.
1. Order BFF Service / API
2. Order Domain Service / API

## Getting familiar with the studio interface

Open [Specmatic Studio](http://localhost:9000/_specmatic/studio) in your browser:
   ```shell
   open http://localhost:9000/_specmatic/studio
   ```

## Exploring API Specifications

Click on the the hamburger icon on the left hand side of the screen to reveal the API Spec browser. This demo setup is already preloaded with two API specifcations.
1. An OpenAPI spec that describes the API exposed by the Order BFF service
2. An AsyncAPI spec that describes the API interface of the Kafka that the BFF service depends on

## Getting started with the API Contract Testing and API Mocking

Since we need a Kafka broker to be running for the BFF let us start a Specmatic KafkaMock using the AsyncAPI specification mentioned above. When you click on the file `kafka.yaml` you will see a screen appear which allows you to start the Mock.

And now we can jump right into running Contract Test on the BFF service using the OpenAPI specification.
1. When you click on the OpenAPI spec you will see an API overview appear
2. On the top you will see a `TEST` button
3. Please fill the BFF service URL as `http://order-bff:8080` (because the Order BFF service is running within Docker we are using the container name instead of localhost) and run the test

Now you will see the test report appear and you can click on the details to drill down into the test results.
1. Review the request and response
2. Observe how the test name is based on the operations

Contgrats! you have successfully run API Contract Test completely based on OpenAPI spec without running a single line of code.