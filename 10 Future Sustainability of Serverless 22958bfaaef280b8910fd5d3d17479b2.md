# Future/Sustainability of Serverless

## The Transformative Journey of Serverless Adoption

The adoption of serverless technology is like the challenging yet empowering journey of a newborn calf. Initially, the vast, complex, crowded, and confusing world of serverless can make one feel like you are drowning. However, with the right guidance, this transforms into an understanding that allows engineers to compose serverless microservices using managed services and build modular and extendable serverless applications that live longer.

## Key Takeaways from the Adoption Journey

- **Mindset Shift**: Moving from legacy software development to serverless requires a fundamental shift to a serverless mindset, enabling engineers to see technology differently.
- **Structured Approach**: Initial enthusiasm to immediately start building everything serverless can lead to mistakes. Emphasizing vital principles of how to structure your teams and draw service boundaries is crucial.
- **Autonomy and Value Delivery**: Once foundational ideas like microservices and event-driven architectures are grasped, teams become autonomous and can utilize the serverless technology ecosystem to bring value to your business faster than before.
- **Long-Term Sustainability**: The critical question becomes for how long and how far? Serverless is not a set-it-and-forget-it technology; it requires sustained effort and adaptation due to its continuous evolution.

---

## Emerging Trends in Serverless

The serverless ecosystem is constantly evolving, driven by the ethos of less is more and the goal of simplifying the development of sophisticated applications by offloading undifferentiated heavy lifting of server management to the cloud provider.

## The Low-Code and Functionless Promise

- **Core Principle**: This trend is a realization of the claim that All the code you will ever write is business logic.
- **Native Integrations**: The need for custom Lambda functions to act as glue code between various services is diminishing as native integrations between these services fill the gap.
- **Impact**: This trend, particularly through functionless integration patterns, will influence the way you architect and build distributed serverless applications, allowing for greater focus on core business logic.

## The Renaissance of Event-Driven Architecture (EDA)

- **Resurgence, Not Novelty**: EDA is not new, but its full potential was somewhat masked by how we built legacy monolithic applications.
- **Central to Serverless**: The promise of event-driven architecture is central to serverless development. Its presence will be stronger in the future.
- **Key Drivers of EDA's Renaissance**:
  - **Data Economy**: EDA facilitates federated data ownership with self-service data publishing and consumption by using domain events to share data and set checkpoints to audit your data and governance roles and responsibilities.
  - **Acceptance of Eventual Consistency**: The shift to smaller, distributed, loosely coupled microservices makes it acceptable to maintain eventual consistency, a paradigm shift from legacy systems.
  - **Fueling Functionless and Low-Code**: Many event-driven service integrations now follow a functionless or low-code pattern, reducing the need for integration code.
  - **Connecting Diverse Systems**: EDA provides a common thread for modern applications operating on multiple technology stacks, supported by emerging standards like CloudEvents and AsyncAPI.

## Multicloud Orchestration

- **Reality of Diverse Environments**: Enterprises often operate in multicloud environments due to legacy systems, specific service requirements, or public/private/gov cloud needs.
- **Primary Provider Orchestration**: The best approach is to have one primary provider orchestrate services from others as necessary.
- **Caution against Cloud Agnosticism**: While appealing, the complexities and high developmental and operational costs can be detrimental to an enterprise. Similarly, running the same workloads on different cloud providers is not recommended without a strong business case.

## Infrastructure from Code (IfC)

- **Abstraction of Cloud Development**: IfC frameworks select, create, configure, deploy, and manage the cloud resources for your application by abstracting explicit cloud resource references from business logic.
- **Motivation**: Advantages include speed of development, cloud-agnostic deployment, code colocation, and a low cognitive load on engineers. It can be beneficial for experimenting or prototyping a complex system or quickly deploying utility services.
- **Drawbacks and Industry Division**: IfC has not gained wide adoption, with criticisms including:
  - **Debugging Complexity**: High abstraction can make investigating problems in a production environment much more complex.
  - **Loss of Control**: It removes critical infrastructure choices, which are typically driven by the business requirements and logic, making it unsuitable for core business domains.
  - **Lack of Transferable Skills**: Limited exposure to underlying infrastructure can lead to a steep learning curve when engineers change roles.
- **Related Concept**: **Observability as Code (OaC)** is a new initiative to incorporate tracing and monitoring capabilities... as part of the implementation, defining alerts... and log queries as code.

## The Evolution and Influence of Generative AI (GenAI)

- **Revolutionary Potential**: GenAI, fueled by transformer architecture, represents a tremendous amount of transformation in AI.
- **Definition**: GenAI models create entirely new content (text, images, code, music, etc.), learning in a self-supervised way. They leverage advanced foundation models (FMs) that can be adapted and trained with specific data, making model building much more efficient.
- **Synergy with Serverless**: The combination of serverless and generative API can achieve unprecedented results. Organizations with a modern serverless/tech stack moving even faster, extending their lead as they combine these resources with GenAI to conceptualize, build, and monetize new ideas.
- **Engineer Empowerment**: GenAI promises to relieve serverless engineers of mundane and repetitive work and freeing you up to focus on innovating for the next iteration of features and functionality.

---

## Sustaining Serverless Adoption in the Enterprise

Successfully adopting serverless is only the first step; maintaining its momentum requires addressing both organizational/cultural and technology challenges. Serverless is not a technology that can be left unattended once successfully adopted.

## Challenges Facing Enterprise Teams

- **Siloed Teams**: As organizations grow, teams can become busy chasing their individual goals and become siloed within their service boundaries.
- **Skill Disparity**: Rapid recruitment can lead to a lack of uniformity, resulting in teams with different levels of serverless skills.
- **Inconsistent Practices**: Fast growth can dilute established principles and practices, with Each team develops its own rulebook, causing further divisions and silos.
- **Autonomy without Guardrails**: Unchecked team autonomy can lead to irresponsible behavior, friction, and product quality suffers.
- **Solution**: A shared awareness and understanding of the recommended best practices is vital, and serverless enablers can connect the teams and guide them.

## Sustaining a Serverless Knowledge Pool

- **Talent Challenge**: Finding and retaining skillful engineers is one of an organization’s biggest challenges.
- **Support and Guidance**: As serverless is relatively new, most engineers require adequate support and guidance to advance their learning and keep their enthusiasm high.
- **Strategies**: Providing sufficient training and learning opportunities, involving engineers in community activities, and forming a serverless guild or center of excellence are crucial.

## Embracing Continuous Refactoring

- **Beyond Legacy**: Refactoring in serverless is a process of continuous improvement or continuous renewal of your applications.
- **Serverless-Specific Refactoring**: This includes rewiring services and refactoring at granular levels, such as:
  - Lambda function code
  - Infrastructure code
  - Performance improvement
  - Cost reduction
  - Sustainability enhancement
  - Consuming new features/managed services
  - Introducing well-architected principles
- **Justifying Refactoring to Business**:
  - **Translate Technical to Business Goals**: Convert technical needs into business goals that are understandable to everyone and share improvement metrics.
  - **Make it Recurring**: Integrate refactoring as a regular part of the development process, allocating dedicated time every quarter for your team’s refactoring needs.
- **Importance**: Continuous refactoring is essential to your serverless development cycle to keep up with the evolving ecosystem.

---

## Playing the Long Game Community and Collaboration

Sustaining serverless momentum requires a strong emphasis on community, collaboration, and human values.

## Establishing a Serverless Guild and Center of Excellence (SCoE)

- **Purpose**: An SCoE is a group of people dedicated to establishing best practices, guidelines, and policies and providing the required support and advice.
- **Role**: An SCoE aims to steer the organization as a whole and the individual teams in the right direction.
- **Key Skills**: An SCoE team should possess skills in serverless technology, the Well-Architected Framework, observability, IaC, microservices principles, and data legislation.
- **Balancing Act**: The SCoE establishes the guardrails, principles, standards but shouldn’t become an impediment. Its primary objective is empowering engineers and teams by providing direction.

## Becoming a Serverless Evangelist

- **Sharing is Caring**: Individuals with expertise in serverless are encouraged to share their knowledge. If you possess one or more of the following skills, someone will always benefit from your experience.

## Joining a Serverless Community

- **Value of Communities**:
  - **Knowledge Hubs**: Communities are vibrant hubs of knowledge where individuals collaborate to exchange knowledge, push boundaries, and learn from their collective experiences.
  - **Sense of Belonging**: They foster a sense of belonging and collective identity, providing social and professional support networks.
  - **Creativity and Collaboration**: Communities encourage the sharing of ideas that may not emerge in solitude.
  - **Advocacy and Shaping Services**: Community input often drives organizations... to make necessary adjustments or develop innovative services.
  - **Democratization of Knowledge**: Online communities remove barriers of distance and income, offering cutting-edge information and resources to anyone with internet access.
- **Challenges in Leading a Diverse Community**:
  - **Time Zone Coordination**: Can make members feel overlooked and discouraged.
  - **Reluctance to Express**: Diverse backgrounds can lead to a reluctance to express oneself openly.
  - **Cultural Differences**: Varying perspectives require recognition that what may be considered normal in one place might be unfamiliar or even offensive in another.
  - **Competition vs. Collaboration**: Competition can divert attention from collective objectives toward their personal interests.
- **Strategies for Inclusive Communities**: Prioritizing schedules, building a warm and inclusive atmosphere, valuing every voice, fostering teamwork, and offering many opportunities for engagement.
- **Making Human Values Central**:
  - **Widen Viewpoint**: Ingrain the why and for whom into technological discourse.
  - **Inclusive Discussions**: Invite diverse leaders and speakers from around the world.
  - **Human-Centric Content**: Focus tech content on the human element.
  - **Context and Delivery**: Use inclusive and easy for nontechnical individuals to understand language and storytelling.
  - **Highlight Individuals**: Foster a conversational style that recognizes, appreciates, and honors the unique qualities and values of each individual.
- **Avenues for Community Involvement**:
  - Community Builder programs
  - AWS Hero invitations
  - Publishing serverless newsletters
  - Sharing insights via podcasts
  - Organizing local serverless meetups and conferences
  - Contributing to open-source projects
