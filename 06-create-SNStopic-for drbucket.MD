### create-SNStopic-for drbucket ###

1. Steps-to-create-sns-topic-and-attach-to-dr

  * go to sns console click on (create topic)

      * Create topic:
        
         Details: [select] Standard

         Name: drbucket

         Display name - optional: drbucket
      
      * Encryption - optional

         [select] Encryption

         AWS KMS key: default

         Description: Default key that protects my SNS data when no other key is defined

         Account: 052492120851

         KMS key ARN: arn:aws:kms:ap-south-1:052492120851:key/8615c730-96b7-4959-960c-c196adc12048

      * Access policy - optional

         [select] Advanced

        JSON editor: {
             "Version": "2008-10-17",
             "Id": "MySNSPolicy",
               "Statement": [
               {
                 "Sid": "MySNSStatement",
                 "Effect": "Allow",
                 "Principal": {
                   "AWS": "*"
               },
              "Action": [
                 "SNS:Publish",
                 "SNS:RemovePermission",
                 "SNS:SetTopicAttributes",
                 "SNS:DeleteTopic",
                 "SNS:ListSubscriptionsByTopic",
                 "SNS:GetTopicAttributes",
                 "SNS:AddPermission",
                 "SNS:Subscribe"
               ],
              "Resource": "arn:aws:sns:ap-south-1:052492120851:secondarybucket",
              "Condition": {
                 "ArnEquals": {
                    "aws:SourceArn": "arn:aws:s3:::secondarybuckets3"
                },
              "StringEquals": {
                 "AWS:SourceOwner": "052492120851"
                }
              }
            }
          ]
        }

      * Data protection policy - optional 

          default

      * Delivery policy (HTTP/S) - optional 

          default

      * Delivery status logging - optional 

          default

      * Tags - optional

          default

      * Active tracing - optional 

        default

        click on create topic button

2. go to sns topic console

     click on drbucket

       copy sns topic arn
         
     click on drbucket and click on edit option

       go to access policy option 

          "Resource" : arn:aws:sns:ap-south-1:052492120851:drbucket (paste)

      click on save

3.   click on drbucket

       go to subcribers
         
         click on (create subscriber)

           Create subscription:
             
             Details:

             Topic ARN: arn:aws:sns:ap-south-1:052492120851:drbucket

             Protocol: Email

             Endpoint: koppada.parasu@gmail.com

           Subscription filter policy - optional 

             default

           Redrive policy (dead-letter queue) - optional

             default

           click on create subscription

4. go to s3 bucket console and 
     
     click on production bucket(appolo-dhl-prods3)

       note: we have multiple options 

         [select] properties

        click on Event notification

          * General configuration

             Event name: appolo-dhl-prods3notify //Event name can contain up to 255 characters.

             Prefix - optional: //Limit the notifications to objects with key starting with specified characters.

             Suffix - optional: //imit the notifications to objects with key ending with specified characters.

          * Event types

             Object creation

               [select] All object create events

             Object removal

               [select] All object removal events

             Object restore

               [select] All restore object events

             Reduced Redundancy Storage

               [select] Reduced Redundancy Storage (RRS) object lost events

             Replication

               [select] All replication events

          * Destination

             Destination:

               [select] SNS topic

             Specify SNS topic:

               
               [select] Choose from your SNS topics
               
               [select] Enter SNS topic ARN  

            click on save
        



    
             
                  
