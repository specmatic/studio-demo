# Specmatic Studio Demo 🚀

[Specmatic Studio](https://specmatic.io/specmatic-studio/) is a **#NOCODE** GUI interface that simplifies:
- API Contract Testing 🤝
- API Mocking 🧪
- API Resiliency Testing 🛡️
- Backward Compatibility Testing 🔄
- API Spec Generation 📄
- ...and more!

---

This demo project showcases how to contract test a [Backend For Frontend (BFF) Service / API](https://github.com/specmatic/specmatic-order-bff-java). We will also demonstrate how to isolate this BFF service from its dependencies—a HTTP [Domain Service / API](https://github.com/specmatic/specmatic-order-api-java) and another asynchronous service listening on Kafka—using API mocking. In the process, we will explore the ability to record API specifications using Specmatic Proxy and perform Backward Compatibility Testing as we make changes to API specifications.

The video on our [website](https://specmatic.io/specmatic-studio/) uses this very same repo to demonstrate the above. You can also use this repo to follow along with the video and learn about the various capabilities.

---

## 🏗️ Application Architecture and Test Setup

![HTML client talks to client API which talks to backend API](specmatic-order-bff-architecture.gif)

---

## 🛠️ Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

---

## 🚦 Usage

### 1️⃣ Setup

1. **Clone the repository:**
   ```shell
   git clone https://github.com/specmatic/studio-demo
   ```

2. **Navigate to the project directory:**
   ```shell
   cd studio-demo
   ```

3. **Start Studio along with the required App services:**
   ```shell
   docker compose up
   ```

These steps will bring up the following services in addition to Specmatic Studio itself:
- Order BFF Service / API
- Order Domain Service / API

---

### 2️⃣ Getting Familiar with the Studio Interface

Open [Specmatic Studio](http://localhost:9000/_specmatic/studio) in your browser:
   ```shell
   open http://localhost:9000/_specmatic/studio
   ```

---

### 3️⃣ Exploring API Specifications

Click on the hamburger icon on the left-hand side of the screen to reveal the API Spec browser. This demo setup is already preloaded with two API specifications:
1. An OpenAPI spec ([product_search_bff_v3.yaml](specs/product_search_bff_v3.yaml)) that describes the API exposed by the Order BFF service
2. An AsyncAPI spec ([kafka.yaml](specs/kafka.yaml)) that describes the API interface of the Kafka that the BFF service depends on

---

### 4️⃣ Getting Started with API Contract Testing and API Mocking

Since we need a Kafka broker running for the BFF, let's start a Specmatic KafkaMock using the AsyncAPI specification mentioned above. When you click on the file `kafka.yaml`, a screen will appear allowing you to start the Mock.

Now, you can jump right into running Contract Tests on the BFF service using the OpenAPI specification:
1. Click on the OpenAPI spec `product_search_bff_v3` to see an API overview.
2. At the top, you will see a `TEST` button.
3. Enter the BFF service URL as `http://order-bff:8080` (since the Order BFF service is running within Docker, we use the container name instead of localhost) and run the test.

You will now see the test report appear, and you can click on the details to drill down into the test results:
- Review the request and response
- Observe how the test name is based on the operations

---

🎉 **Congratulations!** You have successfully run an API Contract Test completely based on the OpenAPI spec without writing a single line of code.