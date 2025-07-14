# 9. Serverless Operations Cost Management

## The Serverless Pay-Per-Use Model Benefits and Risks

- **Core Innovation:** Serverless introduces a "pay-as-you-go" or "pay-per-use" pricing model, where users only pay for the resources their application actually consumes, rather than for idle servers. This is a "key innovation that serverless has brought to software operations in the cloud."

![image (61).png](static/chapter9/image_(61).png)

- **Cost-Efficiency Potential:** This model allows applications to "scale usage... from zero, paying very little or nothing at all, to peak demand, with rising costs." This offers "huge potential for serverless to allow you to focus on building software to meet your business and user needs without breaking the bank."
- **The "Double-Edged Sword":** While beneficial, the pay-per-use model "should be approached with caution as well as optimism." Running serverless "at scale can mean inefficient usage is penalized with huge bills." As industry expert Ben Ellerby states, "the pay-per-use model can lead to less predictability."
- **Matching Cost with Demand:** Serverless "allows us to match cost with demand, all while enabling high levels of scalability." (Ben Ellerby)

## Total Cost of Ownership (TCO) in Serverless

- **Beyond the Monthly Bill:** TCO is an "established concept that helps organizations understand the cost of software over time, not just at the point of acquisition or creation." It goes beyond the "obvious, regular cost of running your serverless application in the cloud."
- **Diminished TCO Potential:** Serverless technology, by leveraging managed services and pay-per-use, "can be significantly diminished."
- **Components of Serverless TCO:Engineering Cost:** "The cost of the humans who design, build, and operate the application." This is "in all likelihood be your most significant cost."
- **Delivery Cost:** "The cost of delivering code iterations to your users."
- **Operations Cost:** The "cost you’ll see on your monthly bill," covering "storage, compute, data transfer, and so on." This cost scales with traffic, but also includes constant costs like monitoring and security.
- **Maintenance Cost:** "The cost of maintaining the application over time," influenced by codebase complexity, team knowledge, and application stability.
- **Code as a Liability:** "Running software in production for a long period of time has proven the opposite [of more code is better] to be true: code is a liability." Reducing TCO is "all about reducing the amount of code you own and simplifying what is left."
- **Types of Code:Production code:** Value-generating code that runs in production.
- **Non-production code:** Code not executed by user actions, should be minimized and dedicated to stability.
- **Third-party code:** Code run in production but written externally; should be minimized due to integration challenges and debugging difficulties.
- **TCO as a Core Driver:** For enterprises, TCO is "typically the core driver for enterprises in their adoption of serverless, be that from a cost perspective or as an enabler for reduced time to value." (Ben Ellerby)

## Core Contributing Factors to AWS Serverless Costs

- **Compute:**Pay-per-use model; only pay for what you use.
- **AWS Lambda:** Billed by "requests and duration." Free Tier includes "1 million requests per month for free." Duration cost varies by memory allocation. "The cheapest Lambda function is one that is never invoked!"
- **AWS Step Functions:** Billed by "state transitions" for standard workflows and "number of requests... and its duration" for express workflows. Retries count as additional state transitions.
- **Compute costs often less than expected:** "Lambda is rarely the most expensive line in your monthly bill." Business logic and compute are spread across many services (Lambda, Step Functions, EventBridge, SQS), not just concentrated in Lambda.
- **Storage:**Cost based on "amount of data written to and read from your chosen data store" and "storing the data over time."
- **Amazon S3:** Primary costs are "storage and requests." Storage costs vary by "storage class" (e.g., Standard, Standard-IA, Glacier Deep Archive). Data compression can "save on storage costs." Lifecycle policies can automate object movement to cheaper storage classes or expiration.

![image (62).png](static/chapter9/image_(62).png)

- **Amazon DynamoDB:** Billed by "read and write requests" and "amount of data stored." Two billing modes: "provisioned or on-demand." On-demand for unpredictable traffic, provisioned for consistent traffic. Standard-IA class can reduce storage costs. DynamoDB Accelerator (DAX) can reduce read/write request costs.
- **Storage costs often similar to non-serverless:** "The cost of storing operational data and application state will most likely be similar to the non-serverless applications you have operated in the past."
- **Outbound Data Transfer:**"Mostly associated with sending data outside of containers or managed services... to the public internet."
- Examples include "sending CloudWatch metrics to a third-party application monitoring platform, leveraging S3 object replication, or using DynamoDB global tables."
- For serverless, costs "will mostly concentrate around compute and storage."

## Common Serverless Cost "Gotchas"

- **CloudWatch Costs:** Often "at or near the top of any serverless bill." Charged per GB of data ingested and stored in CloudWatch Logs. Recommendations: "Keep logging to a minimum," "always set a retention period," "only retain log data for as long as it is useful," consider moving logs to S3 Glacier, remove alarms without clear purpose.
- **Transfer-out Costs:** Incurred when transferring logs/metrics from CloudWatch "out from AWS to the internet." Prefer "metric streams" over polling for metrics.
- **Expensive Caching:** While often a cost-saving technique, "this may not always be true with serverless compute on Lambda." API Gateway caching, for instance, "can get very expensive" as it's billed per GB of cache size per hour. Costs should always be estimated with and without caching.

![image (63) (1).png](static/chapter9/image_(63)_(1).png)

- **Services Calling Other Services:** "Hidden" costs from underlying operations of integrated services (e.g., Athena calling S3, Glue, KMS). Pricing pages should be consulted, and "always monitor costs in production when releasing new pieces of infrastructure."
- **Infinite Lambda Loops:** Functions recursively invoking themselves (e.g., Lambda outputs to SQS queue that triggered it). Lambda's "recursive loop detection feature" can prevent this.
- **Non-Production Costs:** Pay-per-use applies to non-production environments. Costs can add up from "scheduled jobs, continuous integration pipelines, or third-party webhooks." Keep pre-production environments to a minimum, and reduce log data in non-prod.
- **Service Limits/Quotas:** While protective, they "should not be raised blindly." (Ben Ellerby)

## Serverless Cost Estimation and Optimization

![image (67).png](static/chapter9/image_(67).png)

- **Importance of Estimation:** "Cost estimation can be a very useful exercise, especially when designing new serverless applications or microservices and evaluating architectural options."
- **Difficulty of Prediction:** "Difficult to accurately predict operational costs for an application that is distributed across myriad managed services, all with pay-per-use pricing models." Precise estimates rely on "fairly accurate knowledge of expected traffic."

![image (64).png](static/chapter9/image_(64).png)

**Estimation Steps:**

1. Gather data on expected request volume.
2. Identify cost-generating areas in the architecture.
3. Extract relevant costs from AWS service pricing pages.
4. Use tools like spreadsheets, FinOps platforms, or AWS Pricing Calculator.
- Consult AWS solution architects for insights.
- **Tiered Pricing:** As consumption increases, the "cost per resource will decrease" for certain services (e.g., CloudWatch metrics, S3 Standard storage). This should be considered in estimates.
- **AWS Free Tier:** "Indispensable tool" for new applications and experimentation. Offers include "Free trials," "12 months free," and "Always free" allocations (e.g., 1 million free Lambda requests/month, 25 GB free DynamoDB storage).
- **Continuous Optimization:** "Cost optimization must be a continuous process that is part of the fabric of your team." It is "not a one-time, pre-production activity."
- **Cost-Driven Design:** Engineers should be "aware of the pricing models of the services they use and the cost implications of their architectural decisions." Solution designs should include cost estimates and relevant pricing/quotas.
- **FinOps:** The "emergent practice of FinOps is crucial to continued operational and cost efficiency." It advocates for engineers to "own" the financial operations ("You build it, you pay for it"). Requires "FinOps maturity" and a shift in "budget ownership and in the interaction mode between finance and technology." (Ben Ellerby)
- **Billing Analysis:** Essential to provide AWS bill access to all engineers. Use "AWS Billing console and Cost Explorer" for monthly analysis to "identify consistently high costs" and drill down into line items. Set up "critical billing alert[s]" for unexpected spikes.
- **Budget Alerts:** Use AWS Budgets to "proactively monitor your monthly expenditure" and receive alerts when budgets are exceeded. Set alerts based on a baseline with buffer (e.g., 80%, 90%, 100% of budget). AWS Cost Management console offers "cost anomaly detection."

![image (68).png](static/chapter9/image_(68).png)

- **Strategies for Cost Reduction:**
    - Continuously monitor application costs for anomalies.
    - Architect for cost (e.g., S3 object lifecycle, DynamoDB on-demand, express Step Functions).
    - Minimize Lambda functions where alternatives (direct integrations) exist. Do not monolithize functions for this purpose.
    - Batch events and requests to reduce API call costs.
    - Use caching where "viable and cost-efficient."
    - Deploy operational resources (CloudTrail, CloudWatch alarms) "only where needed," primarily in production.
    - Architect sustainably (correlates with cost efficiency).
    - Consider savings plans for predictable compute usage.

Ben Ellerby, Founder, aleios, AWS Serverless Hero

Ben Ellerby is the founder of aleios and a dedicated member of the serverless community. In 2020 AWS named him a Serverless Hero, recognizing his outstanding work and innovation in cloud and serverless. He is the editor of Serverless Transformation: a blog, newsletter, and podcast that share tools, techniques, and use cases for all things serverless. He co-organizes the Serverless User Group in London, is part of the ServerlessDays London organizing team, and regularly speaks about serverless around the world. At aleios, Ben helps start-ups disrupt and large organizations remain competitive by building with serverless.

**Q: As an AWS Serverless Hero and the head of aleios, you have been involved with several serverless implementations. How has serverless changed the way teams pay to deliver and operate their software?**

Serverless provides an optimal total cost of ownership by removing complexity and providing a unique pay-per-use billing model that allows us to match cost with demand, all while enabling high levels of scalability. Done correctly, this lowers the cost of delivering and operating software, reducing the cost of building, running, and maintaining it. However, there is a shift from CapEx (fixed assets) to OpEx (ongoing) and the potential for surprises in costs.

Teams need to work to develop their FinOps maturity to ensure they maintain low costs while creating predictability. This is not just a change for the technology team, but a change in budget ownership and in the interaction mode between finance and technology.

**Q: You’ve been a great thought leader in the serverless community, delivering talks, publishing the Serverless Transformation newsletter, and sharing innovative ideas through your blog posts. Are we getting the most out of serverless, or could teams still generate more business value and reduce costs even further?**

Serverless is a good step, but it’s always part of a larger vision. Whether that vision is reducing time to value or creating an optimal TCO, teams need to be driven by their North Star and leverage serverless to reach it. Serverless can remove complexity, yet when done in a naive way it can create additional cost and get in the way of business value. Serverless is a technology that works well when combined with event-driven and domain-driven design patterns, and when an organization moves to think in a “serverless-first” way.

**Q: You have worked on diverse projects with many enterprises over the last few years. How have you estimated the total cost of ownership with serverless, and how effective has that process been?**

TCO is typically the core driver for enterprises in their adoption of serverless, be that from a cost perspective or as an enabler for reduced time to value. TCO covers the infrastructure cost (the charge for resources consumed), development cost (the up-front cost to build), and of course the maintenance cost (operational running of the application).

Several organizations have publicly referenceable figures on their achieved TCO results with variation based on the use case, industry, and method of measuring.

When working with enterprises on their adoption of serverless we use our Serverless Staircase framework to structure the modernization program. The first stage, Vision, works to set a North Star Metric as well as lagging and leading indicators. The IDC 2018 study is a useful reference in baselining targets during this phase.

It’s difficult to compare TCO results between different organizations and even different divisions of a large enterprise, but it is possible to demonstrate reduction and tie this down to an ROI figure. In practice this means finding a way to baseline your current TCO and finding relevant data points to reality-check your target.

**Q: The combination of a pay-per-use billing model and highly scalable serverless operation can result in surprises and unpleasant bills. From your experience, which are the potential billing mistakes teams should watch out for?**

Indeed, serverless can scale to large levels, and the pay-per-use model can lead to less predictability. Firstly, service limits/quotas should be raised to levels that enable your application to function well, but they should not be raised blindly—they are a protection. Secondly, analysis should be made of your application architecture, and coupled with load testing, this allows you to model expected costs. Costs should be monitored, and alarms and alerts configured to spot issues early. Some cost spikes will come from natural traffic, others from application errors or from malicious actors. Security should be at the core of your application design to prevent denial of wallet attacks, and protections against common antipatterns like recursive Lambda functions should be in place.

Finally, the ability for serverless to scale, especially in reaction to downstream errors, makes the design of integrations with third parties a key element to get correct. For instance, leveraging a circuit breaker pattern (see “Resilient Architecture: The Circuit Breaker Pattern”) between your application and a third party not only protects both applications, but also protects against generating large amounts of expensive calls to a paid API.

**Q: Through your consultancy work with aleios and Theodo, you have firsthand experience witnessing organizations benefit from migrating their workloads to serverless. What advice would you give to enterprise teams on cost awareness as they design, implement, and operate their first serverless applications?**

The key is to recognize that the model of IT procurement has changed. It’s no longer provisioning large resources with a predictable and forecasted approach, but instead is a completely dynamic cost, embodied in the move from CapEx to OpEx. This is not just a change in accounting but a change in how costs are managed and evolve.

While the engineering team needs to design and manage costs, it should work closely with finance as a joint team, sharing responsibility. The FinOps movement is a good example of this and can be put into practice with shared cost dashboards, FinOps retros (involving both the engineering and finance teams), and a holistic cost strategy that is able to measure TCO, enabling the right short-term and long-term cost trade-offs to be made.