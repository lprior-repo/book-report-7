# 2. Enterprise Readiness For Serverless

Changing mindsets around app development is hard especially if you are used to containers and monolotics apps. 

One of the primary differentiators (and mindset changes that you need to make) when building serverless microservices is that you’re not *programming* everything using a particular language to create your microservice. Instead, you are *composing* it using managed services. Programming is part of the process, but not all of it.

Here are some essential areas to focus on to equip your mind to think about the new ways of working with serverless:

- Developing knowledge of the serverless technology ecosystem and its parts
- Gaining a practical understanding of the characteristics of serverless
- Determining how to map the benefits of serverless to your business requirements
- Recognizing that observability principles are as important as business logic
- Creating cost awareness while architecting and building your serverless application
- Trusting AWS as your cloud provider and using managed services

Alongside the serverless-specific areas, your experience with Agile 
development practices, microservices, and DevOps principles will be 
highly beneficial. You will see all these points discussed throughout 
this book.

Habits to offboard from a legacy mindset

- Move away from the legacy siloed development rituals followed in
waterfall models. For example, lengthy testing phases by dedicated QA
teams or infrequent production deployment by designated teams won’t suit an agile team iteratively building serverless solutions.
- Disperse “superstar” teams and encourage equal participation and
delegation. The idea is to equip and develop all engineers to share the
responsibility.
- As there are no servers to manage, accept that you don’t need to SSH into virtual machines to troubleshoot.
- The roles and responsibilities of team members need not be fixed and permanent. As serverless favors multiskilled engineers (see [“Multiskilled, Diverse Engineering Teams”](https://learning.oreilly.com/library/view/serverless-development-on/9781098141929/ch01.html#multiskilledcomma_diverse_engineering_t)), you may not find a dedicated database administrator, infrastructure, or network engineer in every serverless team.
- The flow of architecture and design proposals is not one-way between architects and engineering teams. With the cloud and serverless, it’s a collaboration between architects, tech leads, and engineers.

## Serverless is not a silver bullet

In an organization riddled with years of technical neglect, team misalignment, Stone Age thinking, and stubborn engineering minds that resist change, serverless adoption is a tough act to pull off. There is considerable preparation work required to bring such an organization into a state conducive to serverless adoption and growth. Else you will create the Serverless Big Ball of Mud

![image (70).png](static/chapter2/image_(70).png)

Embrace first principles thinking 

First principles thinking is a thought process that can help you get to the fundamentals of a problem. Rather than focusing on the problem as a whole, you break it into parts to identify the basic elements and causes. Understanding the basics often makes it simpler to find innovative solutions to the business problems your enterprise is trying to solve. In this space, serverless is just a technology enabler.

## Domain

*Domain-Driven Design: Tackling Complexity in the Heart of Software*

Core concepts: 

Bounded Contexts: 

A bounded context is a boundary within a domain where a particular domain model applies. It reveals distinct characteristics and interacts with other bounded contexts via well-defined communication mechanisms such as APIs.

![image (71).png](static/chapter2/image_(71).png)

Answering the following questions becomes easier when you get to this level:

- Who is responsible for protecting the domain boundary and implementing the domain logic?
- How will you safeguard the domain boundary to control the information flow into and out of that domain?
- Within a guarded boundary, which technology is apt to implement the business logic?

Once you’ve mapped out your subdomains and their boundaries, you need people who are well versed in each subdomain and speak the common business (ubiquitous) language used by the domain experts and business stakeholders. These people/teams must be aligned to focus on one thing and work together with a single purpose.

## Team-First

NOTE: The *two-pizza team* rule at Amazon stipulates that a team should
 be small enough to be fed by two pizzas. According to founder Jeff 
Bezos, smaller teams collaborate better because there are fewer 
communication links between the members. This in turn allows them to 
move faster with development and releases. This approach requires 
removing silos and giving teams end-to-end visibility of their 
products—that is, an ownership culture.

Amazon’s two-pizza team concept is often brought up in discussions about modern software development teams. But while it’s become common to measure the size of a team based on their appetite for pizza, people often forget that these teams are intentionally kept small because the business domains they are part of are also broken down to a granular level to give each team a singular purpose, focus, and identity. 

![image (72).png](static/chapter2/image_(72).png)

Team Topologies introduces new thinking around effective team structures for enterprise software delivery. It discusses four team types: stream-aligned, 
enabling, platform, and complicated subsystem teams.

A common misconception in the industry is that serverless technology does not require some of the roles and responsibilities an enabling team fulfills. This is not entirely true, even though serverless eliminates most platform and infrastructure heavy lifting. Your organization requires engineers with the expertise to set up guardrails and processes, such as security principles, well-architected service audit processes, etc. Unlike the siloed team structure, the key difference here is that enabling teams don’t carry out the work on behalf of the stream-aligned teams; instead, they empower others to perform better with a reduced cognitive load and work efficiently to increase velocity and flow.

## API First

When such a team owns and operates its single-purpose product, it becomes the guardian responsible for protecting its contextual boundary by employing adequate technical and communication measures. 

Once you have identified and marked the boundaries of each subdomain, it becomes easier to answer the following questions:

- How can you protect the boundary?
- Who can get access to interact with the system?
- How can you grant access to external systems?
- What information can be transacted across the border?

An *API-first* approach is about identifying, implementing, and 
publishing the interfaces to the system you are building. The API 
becomes a first-class citizen and plays a significant role in the 
tactical design and evolution of the application.

![image (74).png](static/chapter2/image_(74).png)

TIP: 

API governance and discoverability are the two most common issues enterprises face when several teams own  and operate APIs. API portals often help discover and consume APIs in a *self-service* model. However, if you are just starting out with your API-first strategy and initial APIs, don’t get overburdened with these different processes, as they can be worked on in parallel as you create more APIs 
and gain experience.

## Microservice First

With a marked boundary (bounded context) and well-defined (micro) interfaces (API), it becomes easier to own and manage the implementation of the business logic. In this context, microservices offer a suitable development pattern to realize the domain logic. Each microservice has a purpose and identity. In most designs, you will find a microservice related to a bounded context as a one-to-one mapping, but that isn’t the only option.

![image (75).png](static/chapter2/image_(75).png)

A microservice should be owned and operated by one team. Never have two teams share ownership of one microservice. This clear responsibility and business alignment reduces the cognitive load on engineers, thereby increasing development velocity and flow.

## Event Driven First

Asynchronous communication (Async) and event-driven architecture (EDA) are terms sometimes trouble traditional engineering minds that are accustomed to developing monolithic applications using legacy practices and on-premises technologies.

Asynchronicity, eventual consistency, and event-driven communication are the driving forces behind the managed services that power serverless. 

## Note

An *event*, in general, is something that has already happened. A *domain event* is about something that has happened within your business domain. Event-driven architecture (EDA) is an architectural concept that uses events to  communicate between decoupled microservices asynchronously. In EDA,  there are systems that produce events (producers), systems that consume events (consumers), applications that transport events (event buses, messaging systems, etc.), and systems that react to events. Among several other benefits, EDA is key to the scaling and resiliency of applications.

![image (76).png](static/chapter2/image_(76).png)

**Serverless First:** 

*Serverless-first* is a way of thinking that views serverless as 
the best-fit technology choice to build and operate business 
applications to deliver value faster.

*The Value Flywheel Effect: Power the Future and Accelerate Your Organization to the Modern Cloud* (IT Revolution Press), David Anderson sums it up nicely:

*It’s about doing the simplest thing to deliver value by removing the unnecessary baggage. Today serverless-first is the perfect strategy to achieve this; it’s a quiet revolution happening right in front of us. A serverless-first mindset enables teams to focus on business outcomes and business impact, not keeping the lights on.*

It’s about driving value for your business in this modern, fast-paced, 
and highly competitive world. Organizations are constantly iterating and
 finding ways to reach customers and bring value to the business quicker
 than before. As an engineer, architect, or CTO, you are part of the 
fast-spinning value flywheel. Hence, you must learn to leave the heavy 
engineering to the managed cloud service providers, such as AWS, and 
evolve your business solutions on top with a pragmatic and practical 
mindset. *Serverless-first* as a principle and strategy becomes part of that value-generation process.

## Assessing Workloads for Serverless Suitability

Many demo’s are available but in reality enterprise solutions have to evaluate many fundamental questions. Serverless is a solution to many problems but isn’t for all domains. 

Tip

When you assess the suitability of serverless technology with serverless-first thinking, you consider serverless as your first technology choice. This does not mean you overrule other technologies with a serverless-must mindset.

## Understanding the Performance Measures of Distributed Serverless Architecture

Unlike in legacy systems, where performance is mostly measured by the speed of an operation as one big unit, in modern serverless applications, there isn’t a simple yardstick to measure performance. Due to having the work being split amoung many different pieces it’s harder to evaluate each piece. Here are some ways to do that: 

- **End‑to‑End Efficiency**
    - Measures latency across the entire chain of services—crucial when customer satisfaction hinges on rapid responses (e.g., fetching product prices for a storefront).
    - Encourages thinking in terms of the complete user journey rather than isolated calls.
- **Part Efficiency**
    - Focuses on individual services (for instance, the order‑submission API).
    - Recognizes that behind‑the‑scenes tasks (like order processing) may tolerate higher latency without compromising the customer experience.
- **Deliberate Efficiency and Inefficiency**
    - Introduces strategic throttling, where premium users’ requests (such as image uploads) are processed faster than those of anonymous visitors.
    - Aligns performance with business priorities.
- **Expected Efficiency**
    - Accounts for asynchronous or deferred tasks, where timely delivery of an event matters more than immediate processing.
    - Supports event‑driven designs that balance speed and resource utilization.
- **Contractual Efficiency**
    - Ties performance to SLAs or session validity (e.g., ticket‑booking windows).
    - Stresses the importance of meeting legally or commercially mandated time constraints.

## **Non‑ideal Serverless Use Cases**

- **Compute‑heavy, complex apps:** High‑performance computing (HPC) tasks (e.g., structural analysis) need specialized EC2 instances—Lambda can’t match their raw power. Think needing 500$ an hour EC2’s for instance.
- **Long‑running jobs:** Batch processes exceeding Lambda’s timeout require rearchitecting into smaller ETL chunks or another platform.
    - TIP: Use ECS or Fargate for some of these!
- **Low‑level computing:** Code needing direct OS, processor, or network access won’t fit in a managed function.
- **Ultrafast, consistent sub‑10 ms responses:** Cold starts and scaling limits make serverless a gamble for guaranteed <10 ms at 100% traffic.
- **Durable, proprietary‑protocol connections:** Maintaining port‑level sessions favors containers or hybrid models over ephemeral functions. I need to use port 32189 (made up instance)

---

**Cost‑Effectiveness Considerations and Alternatives**

- **Resource configurations vary costs:** Memory, execution time, logs/metrics (CloudWatch), and auxiliary services (Secrets Manager) all add up.
- **Compute‑intensive data processing:** Breaking 10‑minute, 7 GB jobs into smaller Lambda batches lowers memory/time per invocation and cost.
- **IoT ingestion at scale:** Serverless (Kinesis, Lambda, S3) slashes infrastructure upkeep and scales with device‑generated data.
- **High CloudWatch usage:** Optimize log retention, stream metrics to third‑party tools, and reduce API calls to cut monitoring expenses.

> Tip: Use managed-service data lifecycle features (automatic cleanup, tiered storage) for seamless, cost‑effective hygiene—no risky, manual purges needed.
> 

Most of the rest of the chapter goes into Serverless Adoption for the Enterprise, growing serverless teams and lock Well it’s a good read, I’m not focused on bringing this across the enterprise and will lightly touch 

## Discussion About Lock In

1. Consider the Cloud Provider (AWS) as Your Partner, Not a vendor. 

Consequently, you form a working relationship with your cloud provider to identify the most efficient and cost-effective services for your business and the optimal operational configurations. Furthermore, when your team prepares for special events such as new product launches, movie trailer releases, or festive sale events such as Black Friday, you seek your cloud provider’s expertise and work with their infrastructure event management (IEM) team to get your organization through the occasion smoothly.

1. Gregor Hoppe has a ton of good material on this and I recommend you read more into that. 
    1. https://www.youtube.com/watch?v=DVxNbNXcEeM
2. Follow standards (Use OpenAPI standards, Use Open Source Software)

Warning

To operate open source software for the needs of a globally distributed modern consumer base, you require scalability, availability, security, and resiliency. You will likely run it on a cloud platform to achieve all these goals. Even if you use containers and bare metal, switching from one platform to another does involve effort and disruption.

## Migration to Serverless

Another section I will lightly cover: 

LIfting and shift: Probably not the best idea

All at once; Usually a massive failure but companies have done it. 

Use a phased Migration: 

Pick a few and apply the strangler pattern to them., Take the learnings and keep going. 

![image (77) (1).png](static/chapter2/image_(77)_(1).png)

![image (78).png](static/chapter2/image_(78).png)

## Growing Serverless Teams

- Need a conducive Team environment
    - Freedom to take risks to build self-belief among the engineers
    - Encouragement to experiment with ideas to foster product inventions
    - Teams’ involvement in technical and operational decision making to build trust and promote motivation
    - Autonomy to self-govern, removing bureaucracy and allowing increased team velocity
    - Nurturing an ownership culture to create a sense of belonging that encourages responsibility
    - Sufficient learning opportunities to keep engineers in the know about advances in technology
- Finding a Garder:
    - Someone who has some background and able to help the team as they move forward and grow
    - Similarly, the engineers who are part of an organization’s serverless ecosystem need a constant supply of knowledge to upskill and keep up with the evolving technology landscape. New services, features, tools, frameworks, patterns, and capabilities are announced almost daily, and keeping pace with the speed of change can be challenging for a new team of serverless engineers. Hence, the necessary measures must be identified and implemented to swiftly assess and address these needs from the early days of serverless adoption.
- Be willing to upskill in Mass
    
    ![image (79).png](static/chapter2/image_(79).png)
    
    - 
- Find the Passionate Pilot Engineers
    - Let them be the torch bearers and act as catalysts to spearhead serverless movement
    - They MUST possess a positive attitude and willingness to take on challenges.
- Celebrate the Growth of Your Team
    - Cultivating a growth-promoting enterprise environment for serverless is not a solo effort. It involves several teams—engineering, products, people partners, recruitment, etc.—working toward a unified goal.
    - Show to stakeholders how serverless has helped delivery value and promote better ways of working.
- Build teams to have the following characteristerics
    - Form a small group that can be fed with two pizzas
    - Understand their business domain and interact with stakeholders
    - Are responsible for their software products
    - Are quality-conscious and automate their tests
    - Can define and implement their deployment pipelines
    - Understand security and employ threat prevention measures
    - Implement good observability and engage in proactive monitoring
    - Take part in architectural discussions and implement solution designs
    - Are not afraid to deploy to production on a Friday afternoon

![image (80).png](static/chapter2/image_(80).png)

A serverless engineer is a software engineer who is innovative and capable of building efficient, secure, cost-effective, functional, and event-driven solutions iteratively using managed services and operating them on the cloud.

**Frequently asked questions about serverless teams**

Here are some common questions people ask about serverless teams, and some analysis about the accuracy of the underlying conceptions and misconceptions:

Is a serverless team a backend team?

```
This is not always true. In a commercial product development organization, you’ll see teams that focus on domain logic implementation as microservices, teams that own the end-to-end flow of user-facing features, teams that focus mainly on the user experience and aesthetics, and teams that handle data processing and utility services. All these teams could use serverless technology in part or in full.

```

Is a full-stack team ideal for serverless development?

```
A stream-aligned engineering team that owns a feature or a product is responsible for its end-to-end flow, including both frontend and backend functionality. Such a team functions with engineers capable of working on any part of the application stack and avoids the frontend and backend silos. Serverless thrives in environments where knowledge is shared and there is a greater collaboration.

```

Is serverless technology only for developing microservices?

```
Modern applications have several parts, and many of these parts can benefit from serverless. The backend microservices that implement business logic, the Backend for Frontend (BFF) layers that use GraphQL federation, and the frontend user experience implementations that require server-side rendering, data processing pipelines, etc., can all use serverless technologies.

```

Interview with David Anderson: 

David Anderson, Architect, G-P Globalization Partners

David is a technical leader who enjoys writing and speaking about the leading edge of technology. After starting out as a software engineer in leading telecom companies (including Three, Nokia, and Ericsson), David moved to Liberty Mutual in 2007, where he continued to drive technology change and cloud adoption. As a practicing architect with G-P, he continues to empower and enable peers with a focus on serverless-first, well-architected principles, and engineering excellence, all to enable digital transformation, AI, improved time to value, and high-performing teams. His book The Value Flywheel Effect, published by IT Revolution in fall 2022, continues to inspire modernization journeys. David is based in Belfast, writes on The Serverless Edge, is the lead organizer for ServerlessDays Belfast, and is a member of the Wardley Mapping community. 

**Q: What is a serverless mindset, and why is it essential to serverless adoption?**

For me, the serverless mindset is a set of tenets or principles that must be true for the technical and executive leadership and the engineers. I see many companies building on legacy cloud (i.e., treating the cloud like a data center), but they have yet to experience the transformational change the cloud should bring. It’s important they ask the question of why a company would spend 25–50% of their technology budget building an infrastructure platform that (in most cases) is not needed and will, in the long term, slow delivery.

- “The technology strategy is the business strategy.” We speak the same language and can relate technology efforts to the top line.
- “Offload as much as possible to external cloud providers.” You think differently about architecture, but that’s okay.
- “Embrace the fallback.” Start with serverless and fall back when you need to. Don’t be dogmatic—containers are not evil, but make sure engineers don’t fall back because “we don’t know serverless.”
- “Code is a liability; the system is the asset you are creating.” You don’t need to build everything. Spend time on the big picture of what you are building, and don’t code your way out of trouble. Step back and look at the overall design. Create logical components over actual classes.
- Finally, “be brave about your approach.” What seems like a complicated feature could be a solved problem by a managed service; don’t be afraid to use it. No one will think less of an engineer who can deliver a six-month project in two weeks.

The serverless mindset embraces evolutionary architecture and uses cloud providers to create business value quickly. Get features in the hands of users and adapt based on feedback. Don’t be pressured into using a vendor recommendation—think for yourself and use vendor services as building blocks. Don’t get locked into a framework.

By the way, you will notice I didn’t mention functions. If you think serverless is functions, you need to broaden your thinking. **Serverless is “access to capability when needed”—but we still don’t have a good name for it.**

Q: You played a pivotal role in Liberty Mutual’s adoption of serverless. The term serverless-first became a mantra from those days. What does it mean to an organization thinking of adopting serverless?

Following the principle of “building blocks, not frameworks,” it’s essential that technology leaders understand that their outcomes drive the company forward. Technology is not a cost center; it’s an engine for business growth. There was a phase when companies would say, “We are not an X company; we are a technology company that sells X.” Liberty Mutual is an insurance company with a deep understanding of technology—this happens when you make a long-term bet on “technology as a differentiator.” Policyholders don’t care how cool the event logger for the web app is or that the backend is Lambda; they just need help quickly. The journey at Liberty Mutual was awesome, and there are a lot of nice articles if you google “Liberty Mutual serverless.”

Specifically, for an organization-wide adoption of serverless, there are several key areas:

Infrastructure

```
There is a significant evolution required for the infrastructure teams. We are not building a wrapper around the cloud, and the infrastructure team is not the conduit for everything external—this is not sustainable. Don’t wrap application engineers in cotton wool; clear guardrails will enable them to move quickly. Serverless allows application teams to do some infrastructure as code, and the infrastructure teams focus on management and governance of the cloud. The cloud provider is now one of your platform teams (you have several).

```

Security

```
Security [experts] must think in a very purist way about the cloud. The traditional approach of building a wall around the data center does not work for the cloud. The principle of least privilege is critical, and the application engineers now become the front line of security. We need to train our engineers in security (teach them the threat model) and partner with them. Serverless may be a challenge for some of the existing security tools, so we need to think differently.

```

IT and product leadership

```
Courage is required, as serverless is a paradigm shift. The technology and techniques that IT leaders used when they were engineers (or executing projects) have often changed dramatically. Some leaders will say, “When I was an engineer, we did this.” That is correct sometimes; other times, it is the opposite of what needs to happen in a serverless environment. IT leaders must learn about the serverless mindset and trust their technology leaders. It’s difficult for busy executives and managers to carve out time to learn about new technology, but it is critical for success.

```

Engineering capability

```
We must ensure the engineers and architects are comfortable with the new technology and techniques, maybe through cloud certification, workshops and labs, or even external speakers and internal conferences. Regardless, bring your engineers on the journey and invest in them. You won’t hire a new cohort of serverless engineers; bring your engineers today through the journey, and they won’t let you down.

```

One of the critical blockers against serverless is “we can’t get buy-in.” Pitching a “let’s rebuild everything in this new tech” effort is challenging. It’s better to focus on key problem areas and show the value of serverless through results: “We built this solution in 50% of the time,” “We’ve reduced running costs by 80%,” or “We can now scale to meet our demand, and our costs are lower.” Start with showing the results and demonstrate that a serverless mindset was the technique that made it possible—show, don’t tell.

Finally, it’s critical to value tech leadership. The cloud is changing quickly, so you need technical leaders who are switched on and will spot new developments early. Technical leaders will drive engineering excellence (EE). For me, EE is the cornerstone of a serverless organization. I define it as three things: autonomy for teams (build it, own it, run it), mastery (the engineers apply good practices consistently across the organization), and purpose (business KPIs drive tech efforts, and the teams know exactly why they are building). Yes, this is borrowed from Dan Pink’s Drive, but don’t be afraid to reuse!

**Q: Could you share some of the measures you have employed to promote the growth of serverless skills in an organization?**

When teams take more responsibility, we must ensure they are executing well. Looking through the lens of the three engineering excellence areas, we can measure high performance through:

Mastery

```
The critical measure here uses the Well-Architected Framework (from AWS, but it equally applies to the version from Google or Azure). I like to use a process called SCORP (Security, Cost, Operational Excellence, Reliability, Performance—it’s detailed in my book) that enables teams to gather metrics for these five pillars and publish them in a single dashboard (a wiki page or whiteboard). This is updated and reviewed every sprint. Well-architected becomes front of mind, not just an audit-type activity.

Speed of delivery is also essential, so we look at the four key DORA metrics. I dislike being too formal about these, but deployment frequency is a great leading indicator.

```

Autonomy

```
I’m a huge fan of Team Topologies, and there are many measures for fast flow around team metrics. What is the team type, team size, work prioritization, and effectiveness of process? There is a sociotechnical element to the serverless organization. You have to get the technology environment and system design right. You also have to get the team dynamics right to ensure the people can interact with the technology effectively.

```

Purpose

```
This is the easiest one, but the one that is often most ignored. Does the team own a business KPI? (It could also be two teams contributing to the same KPI.) The best measure is to ask an engineer about the business KPI—is the team aware of what it is and how they are changing it?

```

There are some antipatterns or smells that I often look out for:

```
The team’s purpose is “looking after technology X”—“We are the Kafka team.”

The stack is not ephemeral. If we deleted that stack now, could you recover it quickly?

You’re locked into a process, and a QA/infrastructure/security team is slowing down delivery.

What is the Time to Try?

```

Time to Try is a great metric. Let’s imagine a new cloud service announcement at noon on a Monday. How long will it take for an engineer in a regular team to access the service (in a compliant manner) with a view to using it in production? Many traditional organizations will give estimates from weeks to months (we need to make security updates, add to our internal portal, write some Terraform, train our platform team, etc.). My expectation would be 24 hours, for a security review and an update to the cloud policies to add the service to the allow list.

**Q: Your book The Value Flywheel Effect has a chapter dedicated to discussing the “environment for success.” In your opinion, what should the environment be for an enterprise adopting serverless?**

There are four phases in the book The Value Flywheel Effect: Clarity of Purpose (ensures the goal is clear), Challenge (creating an environment for success), Next Best Action (applying a serverless-first approach for rapid execution), and Long-Term Value (using the Well-Architected Framework for sustainable change). My coauthors (Mark McCann and Michael O’Reilly) and I have observed this pattern in many companies. When it’s in effect, change happens rapidly and repeatedly.

The second phase addresses “the environment for success.” The primary method is the ability to challenge. I have found that Wardley Mapping is an excellent technique to open up Challenge (and by Challenge, I mean the environment to ask questions and respectfully critique strategy).

What we describe here is the opposite of the HIPPO (Highest Paid Person’s Opinion) effect. Technical leaders should always have the environment to dig into how and what we are doing to solve a problem. The Amazon leadership principle “Have backbone; disagree and commit” captures this well.

In short, we are talking about psychological safety in the organization. Do engineers (at all levels of the organization) have the confidence and are comfortable in their ability to perform? You don’t want “beaten down engineers.” If your engineers do not exceed your expectations, you need to look at their environment.