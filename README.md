# 1

> A developer created a dashboard for an application using Amazon API Gateway, Amazon S3, AWS Lambda, and Amazon RDS. The Developer needs an authentication mechanism allowing a user to sign in and view the dashboard. It must be accesible from mobile application, desktops, and tablets, and must remember user preferences across platforms. Which AWS service should the Developer use to support this authentication scenario?

- A. AWS KMS
- B. Amazon Cognito
- C. AWS Directory Service
- D. Amazon IAM

<details>
  <summary>Show Answer:</summary>

## B

- A: KMS is for encryption not IAM
- C: Directory Service is for connecting On-Prem AD
- D: IAM is not suitable for mobile platform

Amazon Cognito lets you add user sign-up, sign-in, and access control to your web and mobile apps quickly and easily. Amazon Cognito scales to millions of users and supports sign-in with social identity provider, such as Facebook, Google, and Amazon, and enterprise identity providers via SAML 2.0.

</details>

# 2

> A Developer has created an S3 bucket s3://mycoolapp and has enabled server across logging that points to the folder s3://mycoolapp/logs. The Developer moved 100 KB of Casacading Style Sheets (CSS) documents to the folder s3://mycoolapp/css, and then stopped work. When the developer came back a few days later, the bucket was 50 GB. What is the MOST likely cause of this situation?

- A. The CSS files were not compressed and S3 versioning was enabled.
- B. S3 replication was enabled on the bucket.
- C. Logging into the same bucket caused exponential log growth.
- C. An S3 lifecycle policy has moved the entire CSS file to S3 Infrequent Access/

<details>
<summary>Show Answer:</summary>

## C

Logging into the same bucket caused exponential log growth.
https://aws.amazon.com/premiumsupport/knowledge-center/s3-server-access-logs-same-bucket/
https://docs.aws.amazon.com/AmazonS3/latest/dev/replication-and-other-bucket-configs-html

</details>

# 3

> A Developer is creating an Auto Scaling group whose instances need to publish a custom metric to Amazon CloudWatch. Which method would be the MOST secure way to authenticate a CloudWatch PUT request?

- A. Create an IAM user with PutMetricData permission and put the user credentials in a private repository; have applications pull the credentials as needed.
- B. Create an IAM user with PutMetricData permission, and modify the Auto Scaling launch configuration to inject the user credentials into the instance user data.
- C. Modify the CloudWatch metric policies to allow the PutMetricData permission to instances from the Auto Scaling group.
- D. Create an IAM role with PutMetricData permission and modify the Auto Scaling launching configuration to launch instances using that role.

<details>
<summary>Show Answer:</summary>

## D

Create an IAM role with PutMetricData permission and modify the Auto Scaling configuration to launch instances using that role.

</details>

# 4

> A Developer is working on an application that tracks hundreds of millions of product reviews in an Amazon DynamoDB table. The records include the data elements shown in the table:
>
> | Name       | Type   | Description                |
> | ---------- | ------ | -------------------------- |
> | reviewID   | Number | 16 digit UUID              |
> | starRating | Number | Integer 1-5 of user rating |
> | comment    | String | User comment string        |
> | productID  | Number | Product ID being reviewed  |
>
> Which field, when uised as the partition key, would result in the MOST consistent performance using DynamoDB?

- A. starRating
- B. reviewID
- C. comment
- D. productID

<details>
<summary>Show Answer:</summary>

## B

16 Digit UUID has highest cardinality.

https://aws.amazon.com/blogs/database/choosing-the-right-dynamodb-partition-key/

</details>

# 5

> A Developer has written a serverless application using multiple AWS services. The business logic is written as a Lambda function which has dependencies on third-party libraries. The Lambda function endpoints will be exposed using Amazon API Gateway. The Lambda function will write the information to Amazon DynamoDB. The Developer is ready to deploy the application but must have the ability to rollback. How can this deployment be automated, based on these requirements?

- A. Deploy using Amazon Lambda API operations to create the Lmabda function by providing a deployment package.
- B. Use an AWS CloudFormation template and use CloudFormation syntax to define the Lambda function resource in the template.
- C. Use syntax conforming to the Serverless Application Model in the AWS CloudFormation template to define the Lambda function resource.
- D. Create a bash script which uses AWS CLI to package and deploy the application/

<details>
  <summary>Show Answer:</summary>

## C

SAM extends the CloudFormation template to provide lambda dialect features, such as Blue/Green deployment.

https://docs.aws.amazon.com/serverless-application-model/latest/
https://docs.aws.amazon.com/lambda/latest/dg/lambda-rolling-deployments.html

Always use SAM to build your serverless application.

</details>

# 6

> What are the steps to using the AWS CLI to launch a templatized serverless application?

- A. Use AWS CloudFormation get-template then CloudFormation execute-change-set.
- B. Use AWS CloudFormation validate-template then CloudFormation create-change-set.
- C. Use AWS CloudFormation package then CloudFormation deploy.
- D. Use AWS CloudFormation create-stack then CloudFormation update-stack.

<details>
<summary>Show Answer:</summary>
</details>

## C

https://docs.aws.amazon.com/serverless-application-model/latest/
https://docs.aws.amazon.com/serverless-application-model/latest/
Use this command to quickly upload artifacts that might be required by your template. After you package your templates's artifacts, run the deploy command to deploy the returned template.
https://docs.aws.amazon.com/cli/latest/reference/cloudformation/

# 7

> A Developer is creating a web application thet requires authentication, but also needs to support guest access to provide users limited access without having to authenticate. What service can provide support for the application to allow guest access?

- A. IAM temporary credentials using AWS STS.
- B. Amazon Directory Service.
- C. Amazon Congnito with unauthenticated access enabled.
- D. IAM with SAML integration.

<details>
<summary>Show Answer:</summary>

## C

https://docs.aws.amazon.com/cognito/latest/developerguide/identity-pools.html

To enable unauthenticated identities select Enable access to unauthenticated identitites from the Unauthenticated identitites collapsible section.
Choose Allow to create the two default roles associated with your identity pool - one for unauthenticated users and one for authenticated users.
Amazon Cognito Identity Pools can support unauthenticated identities by providing a unique identifier and AWS credentials for users who do not authenticate with an identity provider. In the Cognito identity management dashboard, select and edit your identity pool,

1. Scroll down and click Unauthenticated identities to expand it and
2. Select the checkbox to enable or disable access to unauthticated identities.
</details>

# 8

> An application takes 40 seconds to process instructions received in an Amazon SQS message.
>
> Assuming the SQS queue is configured with the default VisibilityTimeout value, what is the BEST way, upon receiving the message, to ensure that no other instances can retrieve a message that has already been processed or is currently being processed?

- A. Use the ChangeMessageVisibility API to increase the VisibilityTimeout, then use the DeleteMessage API to delete the message.
- B. Use the DeleteMessage API call to delete the message from the queue, then call DeleteQueue API to remove the queue.
- C. Use the ChangeMessageVisibility API to decrease the timeout value, then use the DeleteMessage API to delete the message.
- D. Use the DeleteMessageVisibility API to cancel the VisibilityTimeout, then use the DeleteMessage API to delete the message.

<details>
<summary>Show Answer:</summary>

## A

Use the ChangeMessageVisibility API to increases the VisibilityTimeout, then use the DeleteMessage API to delete the message.
**NOTE:** The default visibility timeout for a message is 30 seconds. Its how long SQS will make a message invisible to other components once its been polled by the intended recipient. After 30 secs it will reappear int the queue unless you delete it or it expires.

</details>

# 9

> A Developer has implemented a Lambda function that needs to add new customers to an RDS database that is expected to run hundreds of times per hour. The Lambda function is configured to use 512MB of RAM and is based on the following pseudo code:

```python
def lambda_handler(event, context):


db = database.connect()
db.statement(`INSERT INTO Customers (CustomerName) VALUES (context.name)`)
db.close()
```

> After testing the Lambda function, the Developer notices that the Lambda execution time is much longer than expected. What should the Developer do to improve performance?

- A. Increase the amount of RAM allocated to the Lambda function, which will increase the number of threads the Lambda can use.
- B. Increase the size of the RDS database to allow for an increased number of database connections per hour.
- C. Move the database connection and close statement out of the handler. Place ther connection in the global space.
- D. Replace RDS with Amazon DynamoDB to implement control over the number of writes per second.

<details>
<summary>Show Answer:</summary>

## C

Move the database connection and close statement out of the handler. Place the connection in the global space.
You are suppose to initialize db connection in the initialization phase of the lambda function. Even better, create a connection pool instead of just 1 connection.

https://docs.aws.amazon.com/lambda/latest/dg/runtimes-context.html

You can add all of database connection and statement management functionality into a separate module.

Store the state of database connections and then use promises to manage async calls.

This is a great way to cennect to the database only when you need to, instead of making sure it is enabled for every invocation.

The database had to connect every time since database.connect() is not made global in the code. Therefore, make it global and it reduces the size automatically.

If you create database connection inside the handler, it will call for every request you receive. We could optimize performance by keeping that outside of function handler. Actually Lambda try to reuse the existing database connection.

Lambda keep the environment open for some time so that future request can be processed faster. Here if we move the DB connect string out of handler then it will be initialized once for most further executions.

## C

Because you need to always do resource-heavy operations outside of your function body, and DB connection is one of them.

https://docs.aws.amazon.com/lambda/latest/dg/services-rds-tutorial.html

Define the client connection to the database server outside the AWS Lambda handler fucntion. This makes the database connection available between invocations of the AWS Lambda function for the duration of the lifecycle of the function.

**Bonus:** Also read about AWS RDS Proxy, it's fully managed, highly available database proxy for RDS. RDS Proxy sits between your appplication and its database to pool and share established database connections, improving database efficiency and application scalability. In case of a failure, RDS Proxy automatically connects to a standby database instance while preserving connections from your application and reduces failover times for RDS and Aurora multi-AZ databases by up to 66%.

</details>

# 10

> A current architecture uses many Lambda functions invoking one another as a large state machine, The coordination of this state machine is legacy custom code that breaks easily.
>
> Which AWS Service can help refactor and manage the state machine?

- A. AWS Data Pipeline
- B. AWS SNS with AWS SQS
- C. Amazon Elastic MapReduce
- D. AWS Step Functions

<details>
<summary>Show Answer:</summary>

## D

https://aws.amazon.com/step-functions/

Use AWS Step Functioons to define and manage your workflows in the Amazon States Language. Also, the Step Functions Console provides a graphical representation of the state machine to help visualize your application logic.

Step functions can specify whether it should be re-tried on failure. You can specify the interval between retries, the maximum number of attempts and the back-off rate. This means that you can prevent your process from failing due a temporary outage in one of your dependencies.

</details>

# 11

> A Developer is asked to implement a caching layer in front of Amazon RDS. Cached content is expensive to regenerate in case of service failure. Which implementation below would work while maintaining maximum uptime?

- A. Implement Amazon ElastiCache Redis in Cluster Mode
- B. Install Redis on an Amazon EC2 instance
- C. Implement Amazon ElastiCache Memcached
- D. Migrate the database to Amazon Redshift

<details>
<summary>Show Answer:</summary>

## A

Implement Amazon ElastiCache Redis in Cluster Mode.

Definitely A, Redis support multi-AZ which is used for failovers. EC2 is just 1 instance with no failover. Memcached does not allow failover, and also when capacity is reached, default behavior is to eject data. Redshift is a data warehouse, not a cache solution. Response time is slow.

https://aws.amazon.com/elasticache/redis-vs-memcached/

Redis survives reboots and is more persistent, while MemCached doesn't survive reboots.
Redis "cluster mode disabled" cluster has one shard and 0 to 5 replica nodes.
Redis "cluster mode enabled" cluster which REQUIRES multi-AZ, has aup to 90 shards with 1 to 5 read replica nodes in each where the cluster's data partitioned across the shards. This cluster configuration can range from "90 shards and 0 replicas" to "15 shards and 5 replicas", which is the maximum number of replicas allowed.

Expanding a little more on MemCached: https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/

</details>

# 12

> A large e-commerce site is being designed to deliver static objects from Amazon S3. The Amazon S3 bucket will serve more than 300 GET request per second.
>
> What should be done to optimize performance? (Choose two)

- A. Integrate Amazon CloudFront with Amazon S3.
- B. Enablwe Amazon S3 corss-region replication.
- C. Delete expired Amazon S3 server log files.
- D. Configure Amazon S3 lifecycle rules.
- E. Randomize Amazon S3 key name prefixes.

<details>
<summary>Show Answer:</summary>

## A and E, but after a recent update A and B.

There are no limits to the number of prefixes in a bucket. You can increase your read or write performance by parallelizing reads. Amazon S3 performance guidelines recommended randomizing prefix naming with hashed characters to optimize performance for frequent data retrievals.

https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html

Prefix randomization has no more effects on performance unlike old times: https://aws.amazon.com/s3/features/replication/

</details>
