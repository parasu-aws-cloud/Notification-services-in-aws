#### What is Amazon Simple Queue Service?

*  Amazon Simple Queue Service (Amazon SQS) offers a secure, durable, and available hosted queue that lets you integrate and decouple distributed software systems and components. Amazon SQS offers common constructs such as dead-letter queues and cost allocation tags. It provides a generic web services API that you can access using any programming language that the AWS SDK supports.

* Benefits of using Amazon SQS:
  
  1. Security – You control who can send messages to and receive messages from an Amazon SQS queue. You can choose to transmit sensitive data by protecting the contents of messages in queues by using default Amazon SQS managed server-side encryption (SSE), or by using custom SSE keys managed in AWS Key Management Service (AWS KMS).

  2. Durability – For the safety of your messages, Amazon SQS stores them on multiple servers. Standard queues support at-least-once message delivery, and FIFO queues support exactly-once message processing and high-throughput mode.

  3. Availability – Amazon SQS uses redundant infrastructure to provide highly-concurrent access to messages and high availability for producing and consuming messages.

  4. Availability – Amazon SQS uses redundant infrastructure to provide highly-concurrent access to messages and high availability for producing and consuming messages.

  5. Reliability – Amazon SQS locks your messages during processing, so that multiple producers can send and multiple consumers can receive messages at the same time.

  6. Customization – Your queues don't have to be exactly alike—for example, you can set a default delay on a queue. You can store the contents of messages larger than 256 KB using Amazon Simple Storage Service (Amazon S3) or Amazon DynamoDB, with Amazon SQS holding a pointer to the Amazon S3 object, or you can split a large message into smaller messages. 

  follow this link for more steps about SNS service ([*] - https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html )


  note: bunch of notification you want to send for external user at a time 50 notification or 100 or 1000 or lac or milions we should go with SQS,SWf. i dont have knowledge on these services and follow the aficial docs from aws 
  
  
  youtube Ex1: d:/aws_with_terraform_project/diagrams/photo-processinga-app.drawio follow this diagram.
   
   [*] - https://www.youtube.com/watch?v=MH01PNZLR98&list=PLwyXYwu8kL0wg9R_VMeXy0JiK5_c70IrV&index=30
   
                                    ####### TYPE OF QUEUES #######

   1. Standered Queue:
      
      * nearly unlimited number of transactions per second 
      * at aleast once delivery; accosanally more then one copy is delivered.
      * best-effort ordering; may be delivered in an order differet form which they were sent.
   
   2. FIFO (FIRST-IN-FIRST-OUT):

      * up to 300 messeges per second or 3000 messeges if batch them into 10.
      * Exactly once processing; duplicates are not introduced into the queue.
      * first in first out delivery; preserves the order in which they were recieved  
    ![Alt text](<Screenshot 2023-11-02 152311.png>)

    ![Alt text](<Screenshot 2023-11-02 152403.png>)
     Other notes about SQS:
     
      * unlimited messases and queues

        - to prioritize queues and create multiple

      * messase payloads of 256KB in any text formart, retained for 14 days.

      * Batching (1 batch = 10 messages)

        - send ,recieve and delete in batches
        - A batch costs the same as a single message so helps with cost saving  
   
   3. SQS functionality(Count.):
      
      * long polling:
        
        - when the que is empty,wait 20 seconds to poll again.
        - reduces extraneous polling and minimizes cost

      * Dead letter queues

        - Messages that failed to process in the "regular" queue can be moved to a dead letter queue to be handled   
        separately

   4. step to create sqs
      
      * go to aws console and click on create SQS

        Create queue:
          Details:
            
            Type: [select] Standard

            Name: my-app

          Configuration:
            
            Visibility timeout: 30 seconds

            Delivery delay: 0 default value

            Receive message wait time: 0 default value

            Message retention period: 4 days

            Maximum message size: 256KB
          
          Encryption:
            
            Server-side encryption: [select] Enabled

            Encryption key type: Amazon SQS key (SSE-SQS)

          Access policy:

            Choose method: [select] Basic

            Define who can send messages to the queue: [select] only the queue owner

            Define who can receive messages from the queue: [select] Only the queue owner

          remaining all default:
            
            click on create Queue

        * go to Queue console [select] my-app

            clickon send and recieve messages

              Send message : 

                Message body: here is photo processing

              click on send message

               Send message : 

                Message body: here is another photo processing

              click on send message

            again click on  recieve messages

              recieve messages:

                click on poll for messages

                [select] recieve messages id click on that recieved message.

            select all 

              click on delete button 

              4 messages deleted successfully.
             
            finally delete the queue      
              
             
                
