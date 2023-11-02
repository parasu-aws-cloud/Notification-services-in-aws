##### Notification-services-in-aws

***  What is Amazon SNS? ***

   * Amazon Simple Notification Service (Amazon SNS) is a managed service that provides message delivery from publishers to subscribers (also known as producers and consumers). Publishers communicate asynchronously with subscribers by sending messages to a topic, which is a logical access point and communication channel. Clients can subscribe to the SNS topic and receive published messages using a supported endpoint type, such as Amazon Kinesis Data Firehose, Amazon SQS, AWS Lambda, HTTP, email, mobile push notifications, and mobile text messages (SMS).

![Alt text](sns-delivery-protocols.png)

   ### Amazon SNS provides the following features and capabilities:

   1. Application-to-application messaging:

     * Application-to-application messaging supports subscribers such as Amazon Kinesis Data Firehose delivery streams, Lambda functions, Amazon SQS queues, HTTP/S endpoints, and AWS Event Fork Pipelines. For more information, see Using Amazon SNS for application-to-application (A2A) messaging.  
   
   2. Application-to-person notifications:
      
     * Application-to-person notifications provide user notifications to subscribers such as mobile applications, mobile phone numbers, and email addresses. For more information, see Using Amazon SNS for application-to-person (A2P) messaging.([*] - https://docs.aws.amazon.com/sns/latest/dg/sns-user-notifications.html ) 

   3. Standard and FIFO topics:

      * Use a FIFO topic to ensure strict message ordering, to define message groups, and to prevent message duplication. You can use both FIFO and standard queues to subscribe to a FIFO topic. For more information, see Message ordering and deduplication (FIFO topics)([*] - https://docs.aws.amazon.com/sns/latest/dg/sns-fifo-topics.html ).
      
      Use a standard topic when message delivery order and possible message duplication are not critical. All of the supported delivery protocols can subscribe to a standard topic.

   4. Message durability:

      * Amazon SNS uses a number of strategies that work together to provide message durability:

      * Published messages are stored across multiple, geographically separated servers and data centers.

      * If a subscribed endpoint isn't available, Amazon SNS runs a delivery retry policy ([*] - https://docs.aws.amazon.com/sns/latest/dg/sns-message-delivery-retries.html ).
       
      * To preserve any messages that aren't delivered before the delivery retry policy ends, you can create a dead-letter queue([*] - https://docs.aws.amazon.com/sns/latest/dg/sns-dead-letter-queues.html ).

   5. Message archiving, replay, and analytics:

      * You can archive messages with Amazon SNS in multiple ways including subscribing ( [*] - https://docs.aws.amazon.com/sns/latest/dg/sns-firehose-as-subscriber.html ) (Kinesis Data Firehose delivery streams to SNS topics), which allows you to send notifications to analytics endpoints such as Amazon Simple Storage Service (Amazon S3) buckets, Amazon Redshift tables, and more. Additionally, Amazon SNS FIFO topics support message archiving and replay as a no-code, in-place message archive that lets topic owners store (or archive) messages within their topic. Topic subscribers can then retrieve (or replay) the archived messages back to a subscribed endpoint. For more, see Message archiving and replay for FIFO topics.([*] - https://docs.aws.amazon.com/sns/latest/dg/fifo-message-archiving-replay.html )  
    
   6. Message attributes:
     
      * Message attributes let you provide any arbitrary metadata about the message([*] - https://docs.aws.amazon.com/sns/latest/dg/sns-message-attributes.html ). Amazon SNS message attributes.

   7. Message filtering
      
      * By default, each subscriber receives every message published to the topic. To receive a subset of the messages, a subscriber must assign a filter policy to the topic subscription. A subscriber can also define the filter policy scope to enable payload-based or attribute-based filtering. The default value for the filter policy scope is MessageAttributes. When the incoming message attributes match the filter policy attributes, the message is delivered to the subscribed endpoint. Otherwise, the message is filtered out. When the filter policy scope is MessageBody, filter policy attributes are matched against the payload. For more information, see Amazon SNS message filtering([*] - https://docs.aws.amazon.com/sns/latest/dg/sns-message-filtering.html ).

   8. Message security:
      
      * Server-side encryption protects the contents of messages that are stored in Amazon SNS topics, using encryption keys provided by AWS KMS. For more information, see Encryption at rest([*] - https://docs.aws.amazon.com/sns/latest/dg/sns-server-side-encryption.html ).

      You can also establish a private connection between Amazon SNS and your virtual private cloud (VPC). for more information, see Internetwork traffic privacy([*] - https://docs.aws.amazon.com/sns/latest/dg/sns-internetwork-traffic-privacy.html ).

      * Pricing for Amazon SNS:
        
        Amazon SNS has no upfront costs. You pay based on the number of messages that you publish, the number of notifications that you deliver, and any additional API calls for managing topics and subscriptions. Delivery pricing varies by endpoint type. You can get started for free with the Amazon SNS free tier.
   
    follow this link for more steps about SNS service:  [*] - https://docs.aws.amazon.com/sns/latest/dg/welcome.html  .

    note: SNS in the secnce if you have 3dr party email server(domain) yahoo.com ,gmail.com,outlook.com ,SNS can support http and https protocol.

    example: app1 data center at singapure and you purchased domain from gmail this data center at us.singapore region to us region publically you need to send the notification by using those protocals. then the email nothing but respective subscriber recieve the notification.

    note : you are using out region email server we can go with sns service.