# 1. Introduction To Serverless on AWS

![image.png](static/chapter1/image.png)

## Serverless Characteristics

A critical distinction for serverless:

- **Managed Services:** Service provider manages implementation and operation, but "certain managed services require you to create and maintain the necessary infrastructure before consuming them" (e.g., Amazon RDS requires VPC setup).
- **Fully Managed Services:** Can be set up and consumed "almost instantly" (e.g., DynamoDB). These are "sometimes referred to as serverless services."

Serverless is defined as a "technological concept that utilizes fully managed cloud services to carry out undifferentiated heavy lifting by abstracting away the infrastructure intricacies and server maintenance tasks." It gained popularity after AWS Lambda's launch in 2014 and Amazon API Gateway in 2015. While initially equated with FaaS, "FaaS is regarded as one of the many service types that form part of the serverless ecosystem."

## Core Characteristics

1. **Pay-per-Use:** The "main characteristic that everyone associates with serverless." Costs are based on actual usage (e.g., Lambda invocations and memory, DynamoDB API invocations and data volume), not fixed resource allocation. "You are not charged for an entire disk drive or storage array."
2. **Autoscaling and Scale to Zero:** Fully managed services "scale up and down based on demand, without manual intervention." "Scale to zero" is unique to serverless, meaning resources are reclaimed during inactivity, stopping charges. Conversely, services like Lambda can automatically "scale up by provisioning the infrastructure to run as many concurrent instances...as needed to meet the demand."
3. **High Availability (HA):** Serverless, by employing fully managed services, provides "high availability out of the box as standard." AWS handles redundancy and data replication across multiple Availability Zones (AZs) to prevent single points of failure.
4. **Cold Start:** Primarily associated with FaaS, it's the "latency in this initial setup" when an idle function's execution environment needs to be provisioned. Factors like deployment package size, runtime, and memory allocation contribute to cold start time.

**NOTE:** There is a limit to total capacity is dependent on accounts concurrency limit.

**NOTE:** Lambdas have a 15 min runtime timeout. 

**High Availability:** AWS takes care of the redundancy and data replication by distributing the compute and storage resources across multiple AZs, thus avoiding a single point of failure.

**Cold Start:** When an AWS Lambda function is idle for a period of time its execution environment is shut down. If the function gets invoked again after being idle for a while, AWS provisions a new execution environment to run it. The latency in this initial setup is usually called the cold start time. Once the function execution is completed, the Lambda service retains the execution environment for a nondeterministic period. If the function is invoked again during this period, it does not incur the cold start latency. However, if there are additional simultaneous invocations, the Lambda service provisions a new execution environment for each concurrent invocation, resulting in a cold start.

Many factors contribute to this initial latency: the size of the function’s deployment package, the runtime environment of the programming language, the memory (RAM) allocated to the function, the number of pre-configurations (such as static data initializations), etc.

**TIP:** You can opt to keep a certain number of functions "warm" in ready state by setting a functions provisioned concurrency value. 

![image.png](static/chapter1/image%201.png)

## Individuality and Granularity of Resources

*The ability to configure and operate serverless services at an individual level allows you to look at your serverless application not just as a whole but at the level of each resource, working with its specific characteristics.

![image.png](static/chapter1/image%202.png)

## Optimize for Service Cost and Performance

When you optimize to reduce cost, you target reducing the processing power, memory consumption, and storage allocation. With a traditional application, you exercise these changes at a high level, impacting all parts of the application. You cannot select a particular function or database table to apply the changes to.

## Storage Optimization

Managed data services provide built-in features to remove or transition unneeded data. For example, Amazon S3 supports per-bucket data retention policies to either delete data or transition it to a different storage class, and DynamoDB allows you to configure the Time to Live (TTL) value on every item in a table. The storage optimization options are not confined to the mainstream data stores; you can specify the message retention period for each SQS queue, Kinesis stream, API cache, etc.

Warning: DynamDB manages the TTL configuration of the table items efficiently but may take up to 48 hours to delete from the table. 

## Granular Security Permissions

With Identity and Access Management you can apply least privilege to a simple function or lambda level. 

The same principles apply to DynamoDB to access only specific parts of records. 

## Incremental and Iterative Development

You can start very simple with serverless and also scale up incredibly fast as well. 

At the heart of serverless development is Event Driven Architecture. you compose your applications with loosely coupled services that interact via events, messages, and APIs. EDA principles enable you to build modular and extensible serverless applications. You avoid hard dependencies between services, it becomes easier to extend applications by adding new services without breaking functionality of existing when done right.

## Building Multiskilled, Diverse Engineering Teams

Adding new tech brings challengs and opporounities to learn new languages, databases, SaaS platforms, or cloud providers often requirng changes from others. By moving to the cloud you develop new skillsets and skills. 

You will have to learn many different technologies and various design patterns adopting to serverless: 

- AWS Lambda
- AWS Fargate
- AWS EventBridge
- AWS Step Functions
- AWS SQS
- AWS SNS
- AWS API Gateway
- AWS AppSync
- AWS S3
- AWS DynamoDB
- AWS EFS
- AWS Aurora Serverless
- AWS Redshift Serverless
- AWS Neptune Serverless
- AWS Opensearch Serverless
- AWS ElasticCache Sererless

Serverless is more than an architecture; it's a comprehensive "technology ecosystem" with interconnected technical and non-technical elements:

- **The cloud platform:** The enabler (e.g., AWS) providing compute, storage, and network.
- **Managed cloud services:** The "basic building blocks" for computation, messaging, data storage, etc.
- **Architecture:** The "blueprint" defining application purpose and behavior.
- **Infrastructure definition (IaC):** Descriptive scripts (like AWS CloudFormation, CDK, SAM) that "weaves everything together with the appropriate characteristics, dependencies, permissions, and access controls."
- **Development and test tools:** Programming languages, libraries, testing frameworks specific to the FaaS runtime environment.
- **Repository and pipelines:** Versioned storage for artifacts and CI/CD pipelines to deploy applications.
- **Observability tools:** (e.g., Amazon CloudWatch, AWS X-Ray, AWS CloudTrail) to monitor the application's operational state. "A non-observable system cannot be sustained."
- **Best practices:** "Well-architected principles" and guidelines (like the AWS Well-Architected Framework) for security, scaling, resilience, and observability.
- **Builders and stakeholders:** The human element – those who define requirements, design, build, and operate applications.

## Influence of DevOps Culture

Adopting a DevOps model takes a software engineer who otherwise focuses on developing applications into performing operational tasks. You no longer work in a siloed software development cycle but are involved in its many phases, such as continuous integration and delivery (CI/CD), monitoring and observability, commissioning the cloud infrastructure, and securing applications, among other things.

Adopting a serverless model takes you many steps further. Though it frees you from managing servers, you are now programming the business logic, composing your application using managed services, knitting them together with infrastructure as code (IaC), and operating them in the cloud. Just knowing how to write software is not enough. You have to protect your application from malicious users, make it available 24/7 to customers worldwide, and observe its operational characteristics to improve it continually. Becoming a successful serverless engineer thus requires developing a whole new set of skills, and cultivating a DevOps mindset 

![image.png](static/chapter1/image%203.png)

## What’s in a Name?

When you look at the AWS service names, you’ll notice a mix of “Amazon” and “AWS” prefixes—for example, Amazon DynamoDB and AWS Step Functions. This confuses everyone, including employees at Amazon. Apparently, it’s not a random selection but a way to differentiate services based on their fundamental characteristics.

The most popular and relevant theory suggests that services with the Amazon prefix work on their own (standalone services), whereas the ones with the AWS prefix support other services (utility services) and are not intended to be used on their own. AWS Lambda, for example, is triggered by other services. However, as services evolve over time with new capabilities, you may find exceptions where this distinction no longer holds true.

Various AWS Resources:

![image.png](static/chapter1/image%204.png)

## The AWS Well-Architected Framework

This framework provides "architectural best practices for designing, building, and operating secure, scalable, highly available, resilient, and cost-effective applications in the cloud." It consists of six pillars:

1. **Operational Excellence:** Focuses on identifying, preparing, operating, observing, and improving cloud workloads.
2. **Security:** Covers identity and access management, data protection, auditing, and incident response, emphasizing "security thinking at all stages."
3. **Reliability:** Ensures applications scale and function consistently, preventing and recovering from failures.
4. **Performance Efficiency:** Selecting and using the right technology and resources efficiently.
5. **Cost Optimization:** Operating applications to deliver value while keeping costs low, using cost-effective resources like serverless.
6. **Sustainability:** The latest addition, focusing on "reducing energy consumption" and optimizing resource use (compute, storage, network) to the required level, not ove

Chapter 1 Interview: 

Danilo Poccia, Chief Evangelist (EMEA), Amazon Web Services

**Why does the software Industry Need serverless?** 

When you build an application, it can become complex to deploy, test, or add a new feature sooner or later without breaking the existing functionalities. In the last 20 years, complexity has become a science that has found similarities across many different fields, such as mathematics, physics, and social sciences. Complexity theory finds that when there are strong dependencies between components, even simple components, you might experience the emergence of “complex” and difficult-to-predict behaviors. For example, the behavior of an ant is simple, but together, ants can discover food hidden in remote locations and bring it back to their nest. The emergence of unexpected behaviors applies very well to software development.

When you have a large codebase, it requires a lot of effort to reduce side effects so that you don’t break something else when you add a new feature. In my experience, monolithic applications with a large codebase only work when there is a small core team of developers that have worked for years on the same application and have accumulated a large amount of experience in the business domain. Microservices help, but you still need business domain knowledge to find where to split the application. That’s what domain-driven design (DDD) calls the “bounded context.” And that’s why microservices are more successful if they are implemented as a migration from an existing application than when you’re starting from scratch. If the boundaries are well chosen and defined, you limit the internal dependencies to reduce the overall code complexity and the emergence of unexpected issues.

But still, each microservice brings its nonfunctional requirements in terms of security, reliability, scalability, observability, performance, and so on. Serverless architecture helps implement these nonfunctional requirements in a much easier way. It can reduce the overall code size by using services to implement functionalities that are not unique to your implementation. It lets you focus on the features you want to build and not managing the infrastructure required to run the application. In this way, moving from idea to production is much faster, and the advantage of serverless technologies is not only for the technical teams but also for the business teams that are able to deliver more and faster to their customers.

**How does serverless as a technology enable teams of different sizes to innovate and build solutions faster?**

Small teams work better. Serverless empowers small teams to do more 
because it lets them remove the parts that can be implemented off the 
shelf by an existing service. It naturally leads them to adopt a 
microservice architecture and use distributed systems. It can be hard at
 first if they don’t have any experience in these fields, but it’s 
rewarding when they learn and see the results.

If you need to make a big change in the way you build applications, 
for example, adopting serverless or microservices, put yourself in a 
place where you can make mistakes. It’s by making mistakes that we 
learn. As you move to production, collecting metrics on code complexity 
in your deployment pipeline helps keep the codebase under control. To 
move that a step further, I find the idea of a “fitness function” (as 
described in the book [*Building Evolutionary Architectures*](https://oreil.ly/ZZOko)
 by Rebecca Parsons, Neal Ford, and Patrick Kua [O’Reilly]) extremely 
interesting, especially if you define “guardrails” about what the 
fitness of your application should be.

Automation helps at any scale but is incredibly effective for small teams.

**What advice would you give to the readers starting their personal or organizational serverless adoption journey?**

Learn the mental model. Don’t focus on the implementation details. 
Understand the pros and cons of using microservices and distributed 
architectures. Time becomes important because there is latency and 
concurrency to be considered. Design your systems for asynchronous 
communication and eventual consistency.

Faults are a natural part of any architecture. Think of your strategy
 to recover and manage faults. Can you record and repeat what your 
application is doing? Can events help you do that? Also, two core 
requirements that are more important now than before are observability 
and sustainability. They are more related than one might think at first.

Offload the parts that are not unique to your application to services
 and SaaS offerings that can implement those functionalities for you. 
Focus on what you want to build. It’s there where you can make a difference.