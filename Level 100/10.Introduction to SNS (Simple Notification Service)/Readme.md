# Introduction to SNS (Simple Notification Service)

## Cloud Service Provider

* Amazon Web Services

## Difficulty

* Level 100 (Introductory)

---

## Objectives

### You need to complete the following:

* ✅ Create an SNS topic
* ✅ Subscribe to that SNS topic using your email address
* ✅ Confirm the subscription by clicking the link in the email you receive
* ✅ Publish a test message to the SNS topic
* ✅ Verify that the test message is received in your email inbox

---

## Step-by-Step Instructions

### 1. **Create an SNS Topic**

* Go to the **[Amazon SNS Console](https://console.aws.amazon.com/sns/)**.
* Click **"Topics"** from the left sidebar.
* Click **“Create topic.”**
* Select **“Standard”** as the type.
* Give your topic a **name** (e.g., `my-first-sns-topic`).
* Leave all other settings as default and click **"Create topic."**

> ✅ *SNS topics act as communication channels for publishing messages.*

---

### 2. **Subscribe to the SNS Topic Using Email**

* After the topic is created, click on it to open its details page.
* Click **“Create subscription.”**
* In **Protocol**, choose **Email**.
* In the **Endpoint** field, enter your email address.
* Click **“Create subscription.”**

> 📧 *SNS will send a confirmation email to your address. The subscription is inactive until you confirm it.*

---

### 3. **Confirm the Email Subscription**

* Check your email inbox for a message from **AWS Notifications**.
* Click the **“Confirm subscription”** link in the email.

> 🚀 *Once confirmed, your email address becomes an active subscriber to the topic.*

---

### 4. **Publish a Test Message**

* Go back to the topic's detail page.
* Click **"Publish message."**
* Enter a **Subject** (e.g., `Test Notification`).
* Enter a **Message body** (e.g., `This is a test SNS message.`).
* Scroll down and click **"Publish message."**

> ✉️ *This message will be sent to all confirmed subscribers of the topic.*

---

### 5. **Verify Message Delivery**

* Open your email inbox.
* You should receive the test message from AWS SNS.

> ✅ *You’ve now successfully used SNS to send notifications via email!*

---

## You need to answer the following:

### ***What is Simple Notification Service (SNS)?***

**Amazon Simple Notification Service (SNS)** is a fully managed messaging service that enables message delivery from publishers to subscribers using a **publish/subscribe (pub/sub)** model. It allows you to send messages to distributed systems, services, or users through various protocols such as **email, SMS, HTTP/HTTPS, Lambda, or SQS**.

---

### ***How do Pub/Sub notifications work?***

The **publish/subscribe** model works like this:

1. A **publisher** creates a topic and sends messages to it.
2. **Subscribers** register to receive messages from that topic.
3. Whenever a message is published to the topic, **SNS automatically pushes the message** to all subscribed endpoints.

> 🔄 *This decouples message producers from consumers, allowing for scalable and flexible architectures.*

---

### ***What are the different endpoints that SNS can send notifications to?***

SNS supports the following endpoint types:

* **Amazon SQS**
* **AWS Lambda**
* **HTTP/HTTPS**
* **Email/Email-JSON**
* **SMS**
* **Mobile Push Notifications** (via APNS, FCM, etc.)

---

### ***What happens if a message or notification in SNS cannot be delivered?***

* SNS retries message delivery for supported protocols like **SQS, Lambda, HTTP/HTTPS**.
* If delivery repeatedly fails, messages can be redirected to a **Dead Letter Queue (DLQ)**.
* For **email or SMS**, failed deliveries are not retried extensively, but you can **monitor delivery status via CloudWatch**.

---

### ***What's the difference between SNS and SQS?***

| Feature                  | SNS (Push Model)                    | SQS (Pull Model)                       |
| ------------------------ | ----------------------------------- | -------------------------------------- |
| **Delivery Method**      | Pushes messages to subscribers      | Consumers pull messages from the queue |
| **Use Case**             | Real-time alerts, fan-out messaging | Task queuing, asynchronous processing  |
| **Message Retention**    | No retention                        | Stores messages for up to 14 days      |
| **Multiple Subscribers** | Yes                                 | Typically one consumer                 |

> 💡 *SNS and SQS can also be used together for fan-out architectures: SNS pushes messages to multiple SQS queues for downstream processing.*

---

## Reference

* [AWS SNS Official Documentation](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)
* [Setting Up Amazon SNS Notifications](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/US_SetupSNS.html)
* [Amazon SNS – The Ultimate Guide](https://www.serverless.com/amazon-sns)
* [What is Amazon SES and SNS in AWS?](https://intellipaat.com/blog/what-is-amazon-ses-sns-in-aws/)

---

## Costs

* Amazon SNS offers generous limits within the **AWS Free Tier**:

  * 1 million publishes
  * 100,000 HTTP(S) deliveries
  * 1,000 email deliveries per month

> 📌 *Always review AWS pricing if working outside the Free Tier.*

---

## Estimated time to complete

* ⏱️ Approximately **10 minutes**

---
=