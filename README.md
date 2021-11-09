# Question 1

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

---

# Question 2

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

---

# Question 3

> A Developer is creating an Auto Scaling group whose instances need to publish a custom metric to Amazon CloudWatch. Which method would be the MOST secure way to authenticate a CloudWatch PUT request?

- A. Create an IAM user with PutMetricData permission and put the user credentials in a private repository; have applications pull the credentials as needed.
- B. Create an IAM user with PutMetricData permission, and modify the Auto Scaling launch configuration to inject the user credentials into the instance user data.
- C. Modify the CloudWatch metric policies to allow the PutMetricData permission to instances from the Auto Scaling group.
- D. Create an IAM role with PutMetricData permission and modify the Auto Scaling launching configuration to launch instances using that role.

<details>
<summary>Show Answer:</summary>

---

## D

Create an IAM role with PutMetricData permission and modify the Auto Scaling configuration to launch instances using that role.

</details>

# Question 4

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

---

# Question 5

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

---

# Question 6

> What are the steps to using the AWS CLI to launch a templatized serverless application?

- A. Use AWS CloudFormation get-template then CloudFormation execute-change-set.
- B. Use AWS CloudFormation validate-template then CloudFormation create-change-set.
- C. Use AWS CloudFormation package then CloudFormation deploy.
- D. Use AWS CloudFormation create-stack then CloudFormation update-stack.

<details>
<summary>Show Answer:</summary>

## C

https://docs.aws.amazon.com/serverless-application-model/latest/
https://docs.aws.amazon.com/serverless-application-model/latest/
Use this command to quickly upload artifacts that might be required by your template. After you package your templates's artifacts, run the deploy command to deploy the returned template.
https://docs.aws.amazon.com/cli/latest/reference/cloudformation/

</details>

# Question 7

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

---

# Question 8

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

---

# Question 9

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

---

# Question 10

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

Use AWS Step Functions to define and manage your workflows in the Amazon States Language. Also, the Step Functions Console provides a graphical representation of the state machine to help visualize your application logic.

Step functions can specify whether it should be re-tried on failure. You can specify the interval between retries, the maximum number of attempts and the back-off rate. This means that you can prevent your process from failing due a temporary outage in one of your dependencies.

</details>

---

# Question 11

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

---

# Question 12

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

---

# Question 13

> A company is building a stock trading application that requires sub-millisecond latency in processing trading requests. Amazon DynamoDB is used to store all the trading data that is used to process each request. After load testing the application, the development team found that due to data retrieval times, the latency requirement is not satisfied. Because of sudden high spikes in the number of requests, DynamoDB read capacity has to be significant over-provisioned to avoid throttling.
>
> What steps should be taken to meet latency requirements and reduce the cost of running the application?

- A. Add Global Secondary Indexes for trading data.
- B. Store trading data in Amazon S3 and use Transfer Acceleration.
- C. Add retries with exponential back-off for DynamoDB queries.
- D. Use DynamoDB Accelerator to cache trading data.

<details>
<summary>Show Answer:</summary>

## D

Use DynamoDB Accelerator to cache trading data:

- https://aws.amazon.com/blogs/database/how-to-use-dynamodb-global-secondary-indexes-to-improve-query-performance-and-reduce-costs/
- https://docs.amazonaws.cn/en_us/amazondynamodb/latest/
- https://aws.amazon.com/blogs/database/a-walkthrough-of-the-amazon-dynamodb-accelerator-console-part-2/

"DAX is a managed cache that is API compatible with DynamoDB providing fast in-memory performance for demanding applications like real-time gaming, bidding, weather analysis and trading. With DAX, users save cost by efficiently provisioning read capacity units and experience increased throughput as response times of eventually-consistent read workloads is reduced to microseconds."

</details>

---

# Question 14

> A Developer needs temporary access to resources in a secound account.
>
> What is the MOST secure way to achieve this?

- A. Use the Amazon Cognito user pools to get short-lived credentials for the second account.
- B. Create a dedicated IAM access key for the second account, and send it by mail.
- C. Create a cross-acount access role, and use sts:AssumeRole API to get short-lived credentials.
- D. Establish trust, and add an SSH key for the second account to the IAM user.

<details>
<summary>Show Answer:</summary>

## C

Create a cross-account access role, and use sts: AssumeRole API to get short-lived credentials.

</details>

---

# Question 15

> An application reads data from an Amazon DynamoDB table. Several times a day, for a period of 15 seconds, the application receives multiple ProvisionedThroughputExceeded errors.
>
> How should this exception be handled?

- A. Create a new global secondary index for the table to help with the additional request.
- B. Retry the failed read request with exponential backoff.
- C. Immediately retry the failed read request.
- D. Use the DynamoDB UpdateItem API to increase the provisioned throughput capacity of the table.

<details>
<summary>Show Answer:</summary>

## B

</details>

---

# Question 16

> A Developer has created a large Lambda function, and deployment is failing with the following error:
> ClientError: An error occurred (InvalidParameterValueException) when calling the createFunction operation: Unzipped size must be smaller than XXXXXXXXX bytes, where XXXXXXXXX is current Lambda limit
>
> What can the Developer do to fix this problem?

- A. Submit a limit increase request to AWS Support to increase the function to the size needed.
- B. Use a compression algorithm that is more efficient than ZIP.
- C. Break the function into multiple smaller Lambda functions.
- D. ZIP the ZIP file twice to compress it further.

<details>
<summary>Show Answer:</summary>

## C

Break the function into multiple smaller Lambda functions.

</details>

---

# Question 17

> Given the source code for an AWS Lambda function in the local store.py containing a handler function called get_store and the following AWS CloudFormation template:

```bash
Transform: AWS::Serverless-2016-10-31

Resources:
      StoreFunc: AWS::Serverless::Function
      Properties:
        Handler: store.get_store
        Runtime: python3.6

```

> What should be done to prepare the template so that it can be deployed using the AWS CLI command aws cloudformation deploy?

- A. Use AWS CloudFormation compile to base64 encode and embed the source file into a modified CloudForamtion template.
- B. Use AWS CloudFormation package to upload the source code to an Amazon S3 bucket and produice a modified CloudFormation template.
- C. Use AWS Lambda zip to package the source file togheter with the CloudFormation template and deploy the resulting zip archive.
- D. Use AWS Serverless create-package to embed the source file directly into the existing CloudFormation template.

<details>
<summary>Show Answer:</summary>

## B

D can also be used if AWS CLI is not specified in the question (SAM useas serverless CLI)

- Step 1: Run the CloudFormation package command. The following command creates a .zip file containing the function's source code folder, and then uploads the .zip file to the root folder of the my-bucket bucket.

```
aws cloudformation package --template / path_to_template/
template.json --s3-bucket mybucket --output json > packagedtemplate.jso
```

In addition to uploafing the .zip file to the S3 bucket, the above command also saves the template that it generates to the path specified by the --output option as below

```
Output:
AWSTemplateFormatVersion:'2010-09-09'
Transform:'AWS::Serverless-2016-10-31'
Resources:
MyFunction:
Type:'AWS::Serverless::Function'
Properties:
Handler:index.handler
Runtime: nodejs8.10
CodeUri: s3://mybucket/lambdafunction.zip
```

- Step 2: Run the CloudFormation deploy command by passing the above template as parameter

```
ws cloudformation deploy --template /path_to_template/mytemplate.json --stack-name my-new-stack --parameter-overrides
Key1=Value1 Key2=Value2
```

https://aws.nz/best-practice/cloudformation-package-deploy/

Use aws cloudformation package to upload the source code to an
Amazon S3 bucket and produce a modified CloudFormation template.

https://docs.aws.amazon.com/cli/latest/reference/cloudformation/
package.html

Examples:
Following command exports a template named template.json by
uploading local artifacts to S3 bucket bucket-name and writes the
exported template to packaged-template.json:

```
aws cloudformation package --template-file /path_to_template/
template.json --s3-bucket bucket-name --output-template-file
packaged-template.json
```

</details>

# Question 18

> An application stores images in an S3 bucket. Amazon S3 event notifications are used to trigger a Lambda functions that resizes the images. Processing each image takes less than a second.
>
> How will AWS Lambda handle the additional traffic?

- A. Lambda will scale out to execute the request concurrently.
- B. Lambda will handle the request sequentially in the order received.
- C. Lambda will process multiple images in a single execution.
- D. Lambda will add more compute to each execution to reduce processing time.

<details>
<summary>Show Answer:</summary>

## A

Lambda will scale out to execute the request concurrently.

https://docs.aws.amazon.com/lambda/latest/dg/gettingstarted-limits.html

</details>

---

# Question 19

> A company wants to implement a continuous integration for its workloads on AWS. The company wants to trigger unit test in its pipeline for commits-on its code repository, and wants to be notified of failure events in the pipeline.
>
> How can these requirements be met?

- A. Store the source code in AWS CodeCommit. Create a CodePipeline to automate unit testing. Use Amazon SNS to trigger notifications of failure events.
- B. Store the source code in Github. Create a CodePipeline to automate unit testing. Use Amazon SES to trigger notifications of failure events.
- C. Store the source code on Github. Create a CodePipeline to automate unit testing. Use Amazon CloudWatch to trigger notifications of failure events.
- D. Store the source code in AWS CodeCommit. Create a CodePipeline to automate unit testing. Use Amazon CloudWatch to trigger notification of failure events.

<details>
<summary>Show Answer:</summary>

## Answer seems D but there are some reasons to support A.

Store the source code in AWS CodeCommit. Create a CodePipeline to automate unit testing. Use Amazon CloudWatch to trigger notification of failure events.

- https://docs.aws.amazon.com/codepipeline/latest/userguide/tutorials-cloudwatch-sns-notifications.html
- https://docs.aws.amazon.com/codepipeline/latest/userguide/detect-state-changes-cloudwatch-events.html

CodePipeline can talk with SNS directly:

- https://docs.aws.amazon.com/codepipeline/latest/userguide/notification-rule-create.html
- https://docs.aws.amazon.com/codepipeline/latest/userguide/monitoring.html

Use Amazon CloudWatch Events to detect and React tom PipeLine execution state changes (for example, send an Amazon SNS notification or invoke a Lambda function):

- https://docs.aws.amazon.com/codepipeline/latest/userguide/detect-state-changes-cloudwatch-events.html

- The Build & Test Phase happens in COdeBuild.
- SNS does not trigger any failure in CodePipeline.
- CloudWatch is able to trigger events i.e. when a test has failed in CodeBuild, and it will use SNS to notify the developer:
  - https://docs.aws.amazon.com/codepipeline/latest/userguide/detect-state-changes-cloudwatch-events.html

</details>

---

# Question 20

> A serverless application uses an API Gateway and AWS Lambda.
>
> Where should the Lambda function store its session information across function calls?

- A. In an Amazon DynamoDB table.
- B. In an Amazon SQS queue.
- C. n the local filesystem.
- D. In an SQLite session table using `DSQLITE_ENABLE_SESSION`

<details>
<summary>Show Answer:</summary>

## A

In an Amazon DynamoDB table.

It ask about "store" session data.

- C: file system - **INCORRECT** because all lambda executions are serverless, no local file systems attached.
- B: SQS - **INCORRECT** because SQS is not used to "store" data but just to exchange data.
- A: DynamoDB - **CORRECT** because this is only "persistent" medium which "stores" data.

Although Lambda's local file system can be leveraged for certain use cases, for storing session state DynamoDB is more reliable. After a Lambda function is executed, AWS Lambda maintains the execution context for some time in anticipation of another Lambda function invocations.
However, when writing Lambda function code, do not assume that AWS Lambda automatically reuses the execution context for subsequent functions invocations. Other factors may dictate a need for AWS Lambda to create a new execution context, which can lead to unexpected results:

- https://aws.amazon.com/fr/lambda/faqs

</details>

---

# Question 21

> A Developer has created a software package to be deployed on multiple EC2 instances using IAM roles.
>
> What actions could be performed to verify IAM access to get records from Amazon Kinesis Streams? (Choose two)

- A. Use the AWS CLI to retrieve the IAM group.
- B. Query Amazon EC2 metadata for in-line IAM policies.
- C. Request a token from AWS STS, and perform a describe action.
- D. Perform a ghet action using the `-dry-run` argument.
- E. Validate the IAM role policy with the IAM policy simulator.

<details>
<summary>Show Answer:</summary>

## D and E

https://docs.aws.amazon.com/cli/latest/userguide/cli-usage-help.html

```
--dry-run | --no-dry-run (boolean)
```

Checks whether you have the required permissions for the action,
without actually making the request, and provides an error response.
If you have the required permissions, the error response is DryRun-Operation. Otherwise, it is UnauthorizedOperation

</details>

---

# Question 22

> When writing a Lambda function, what is the benefit of instantiating AWS client outside the scope of the handler?

- A. Legibility and stylistic convention
- B. Taking advantage of connection re-use
- C. Better error handling
- D. Creating a new instance per invocation

<details>
<summary>Show Answer:</summary>

## B

taking advantage of connection re-use.

</details>

---

# Question 23

> An application on AWS is using third-party APIs. The Developer needs to monitor API errors in the code, and wants to receive notifications if failures go above a set threshold value.
>
> How can the Developer achieve these requirements?

- A. Publish a custom metric on Amazon CloudWatch and use Amazon SES for notification.
- B. Use an Amazon CloudWatch API-error metric and use Amazon SNS for notification.
- C. Use an Amazon CloudWatch API-error metric and use Amazon SES for notification.
- D. Publish a custom metric on Amazon CloudWatch and use Amazon SNS for notification.

<details>
<summary>Show Answer:</summary>

## D

Publish a custom metric on Amazon CloudWatch and use Amazon SNS for notification.
there is no CloudWatch API-error metric.

</details>

---

# Question 24

> A Developer has an application that can upload tens of thousands of objects per second to Amazon S3 in parallel within a single AWS account. As part of new requirements, data stored in S3 must use server side encryption with AWS KMS (SSE-KMS). After creating this change, performance of the application is slower.
>
> Which of the following is MOST likely the cause of the application latency?

- A. Amazon S3 throttles the rate at which uploaded objects can be encrypted using Customer Master Keys.
- B. The AWS KMS API calls limit is less than needed to achieve the desired performance.
- C. The client encryption of the objects is using a poor algorithm.
- D. KMS requires that an alias be used to create an independent display name that can be mapped to a CMK.

<details>
<summary>Show Answer:</summary>

## B

The AWS KMS API calls limit is less than needed to achieve the desired performance:
https://aws.amazon.com/about-aws/whats-new/2018/08/aws-key-management-service-increases-api-requests-per-second-limits/

KMS API access limit is 10k/sec in us-east and some others and 5.5k/sec for the rest of the regions.

Client can request this limit to be changed: https://docs.aws.amazon.com/kms/latest/developerguide/requests-per-second.html

</details>

---

# Question 25

> A company wants to migrate its web application to AWS and leverage Auto Scaling to handle pear workloads. The Solution Architect determined that the best metric for an Auto Scaling events is the number of concurrent users.
>
> Based on this information, what should the Developer use to autoscale based on concurrent users?

- A. An Amazon SNS topic to be triggered when a concurrent user threshold is met.
- B. An Amazon CloudWatch Networking metric.
- C. Amazon CloudFront to leverage AWS Edge Locations.
- D. A Custom Amazon CloudWatch metric for concurrent users.

<details>
<summary>Show Answer:</summary>

## D

A custom Amazon CloudWatch metric for concurrent users.
There is no ‘concurrent user threshold’ metric for Auto Scaling. You should create custom metric, if you want to scale depending on this value.

- https://docs.aws.amazon.com/connect/latest/adminguide/monitoring-cloudwatch.html

</details>

---

# Question 26

> A company is migrating its on-premises database to Amazon RDS for MySQL. The company has read-heavy workloads, and wants to make sure it re-factors its code to achieve optimum read performance for its queries.
>
> How can this objective be met?

- A. Add database retries to effectively use RDS with vertical scaling.
- B. Use RDS with multi-AZ deployment.
- C. Add a connection string to use an RDS read replica for read queries.
- D. Add a connection string to use a read replica on an EC2 instance.

<details>
<summary>Show Answer:</summary>

## C

Add a connection string to use an RDS read replica for read queries.

</details>

---

# Question 27

> A Developer is receiving HTTP 400: ThrottlingException errors intermittently when calling the Amazon CloudWatch API. When a call fails, no data is retrieved.
>
> What best practice should first be applied to address this issue?

- A. Contact AWS Support for a limit increase.
- B. Use the AWS CLI to get the metric.
- C. Analyze the application and remove the API call.
- D. Retry the call with exponential backoff.

<details>
<summary>Show Answer:</summary>

## D

- https://aws.amazon.com/premiumsupport/knowledge-center/

It's a best practice to use the following methods to reduce your call
rate and avoid API throttling:

1. Distribute your API calls evely over time rather than making several API calls in a short time span. If you require data to be available with a one-minute resolution, you have an entire minute to emit that metric. Use jitter (randomized delay) to send data points at various times.
2. Combine as many metrics as possible into a single APÏ call. For example, a single PutMetricData call can include 20 metrics and 150 data points. You can also use pre-aggregated data sets, such as StatisticSet, to publish aggregated data points, thus reducing the number of PutMetricData calls per second.
3. Retry your call with exponential backoff and jitter.

</details>

---

# Question 28

> A Developer is testing a Docker-based application that uses the AWS SDK to interact with Amazon DynamoDB. In the local development environment, the application has used IAM access keys. The application is now ready for deployment onto an ECS cluster.
>
> How should the application authenticate with AWS services in production?

- A. Configure an ECAS task IAM role for the application to use.
- B. Refactor the application to call AWS STS AssumedRole based on an instance role.
- C. Configure AWS access key/secret access key environment variables with new credentials.
- D. Configure the credentials file with a new access key/secret access key.

<details>
<summary>Show Answer:</summary>

## A

Configure an ECS task IAM role for the application to use: https://docs.aws.amazon.com/AmazonECS/latest/developerguide/

With IAM roles for Amazon ECS tasks, you can specify an IAM role that can be used by the containers in a task.

</details>

---

# Question 29

> A Developer created a Lambda function for a web application backend. When testing the Lambda fucntion from the AWS Lambda console, the Developer can see that the function is being executed, but there is no log data being generated in Amazaon CloudWatch Logs, even afeter several minutes.
>
> What could cause this situation?

- A. The Lambda function does not have any explicity log statement for the log data to send it to CloudWatch Logs.
- B. The Lambda function is missing CloudWatch Logs as a source trigger to send log data.
- C. The execution role for the Lambda function is missing permissions to write log data to the CloudWatch Logs.
- D. The Lambda fucntion is missing a target CloudWatch Log group.

<details>
<summary>Show Answer:</summary>

## C

The execution role for the Lambda function is missing permissions to write log data to the CloudWatch Logs: https://docs.aws.amazon.com/lambda/latest/dg/monitoring-cloudwatchlogs.html

- A. The Lambda function does not have any explicit log statements
  for the log data to send it to CloudWatch Logs. -- If Lambda was
  executed, it will always have some logs to send. For example
  execution time and memory usage will be always send after
  execution is done [Incorrect]
- B. The Lambda function is missing CloudWatch Logs as a source
  trigger to send log data. -- Lambda is connected to CloudWatch by
  default and you cannot disable it. [Incorrect]
- C. The execution role for the Lambda function is missing permissions
  to write log data to the CloudWatch Logs. -- You have to explicitly
  define a IAM role with IAM policy which allows Lambda to send logs
  to CloudWatch. [Correct]
- D. The Lambda function is missing a target CloudWatch Log group. --
  See explanation in answer B. [Incorrect]

</details>

---

# Question 30

> An application has hundreds of users. Each user may use multiple devices to access the application. The Developer wants to assign unique identifiers to these users regardless of the device they use.
>
> Which of the following methods should be used to obtain unique identifiers?

- A. Create a user table in Amazon DynamoDB as key-value pairs of users and their devices. Use these keys as unique identifiers.
- B. Use IAM-generated access key IDs for the users as the unique identifier, but do not store secret keys.
- C. Implement developer-authenticated identities by using Amazon Cognito, and get credentials for these identities.
- D. Assign IAM users and roles to the users. Use the unique IAM resource ID as the unique identifier.

<details>
<summary>Show Answer:</summary>

## C

Implement developer-authenticated identities by using Amazon Cognito, and get credentials for these identities.
With developer authenticated identities, you can register and uthenticate users via your own existing authentication process, while still using Amazon Cognito to synchronize user data and
access AWS resources.

- https://docs.aws.amazon.com/cognito/latest/developerguide/developer-autheticated-identites.html
- https://aws.amazon.com/blogs/mobile/amazon-cognito-announcingdeveloper-authenticate-identities/

With the addition of “Developer Authenticated Identities” to Amazon Cognito, developers can use their own authentication system with Cognito. What this means is that your app can benefit from all of the features of Amazon Cognito while utilizing your own authentication system. This works by your app requesting a unique identity ID for your end users based on the identifier you use in your own authentication system. You can use the Cognito identity ID to save and synchronize user data across devices with the Cognito sync service or retrieve temporary, limited-privilege AWS credentials to securely access your AWS resources

</details>

---
