# Cyberwar of Convienence

## Rational / Goals

Based on concepts discussed in [secops.md](secops.md), we feel the best way to improve security and resilience in the face of cyber war threats is to shift security capabilities and responsibilities to developers, in the same way that DevOps blended in Operations.  By making it 'their problem', rather than an external security team, it is expected that security issues with both be addressed more readily, as well as balanced against cost and effort appropriately.  Who knows better than the team that owns responsibility for a service and it's data?

Today, the simplest step towards this goal is the use of tooling during the development and deployment cycle to ensure:

1. Code is written better, safer, faster - and comes with ponies.
2. Code is attributable to a developer - insider threat is a real problem, attribution is a key component of minimizing this risk.
3. Code is the primary output and artifact of the team - Infrastrucre as Code, Application Code, Security Policy Code, etc.  No 'opaque' artifacts.
4. Cloud can be utilized to dramatically increase saftey, speed to deploy, and consistency, while simultaneously dramatically reducing attack surface, resource consumption, and operations risk.
5. Risk, as a core operations component, can be understood, categorized and managed against.
6. Developers should be able to work from anywhere, from any device in a secure fashion.
7. Opinionated baselines should be provided to guide teams and developers down the 'happy path'.  

## Assumptions

1. Infrastructure
    1. Dev Access is via web browser to IDE or development workstation in the cloud, ephemerally. (e.g. cloud9 or jupyter)
    2. Access is gated via SSO and MFA
    3. Entirely serverless infrastructure - FaaS or Fargate style containers, cloud only.
    4. Bake in a presumed deploy model by default (e.g. blue/green lambda phase in)
    5. Bake in log collection and monitoring and observability by default (e.g. in templates)
2. Security
    1. Make the default / convienent choice the RIGHT choice security-wise
    2. Map compliance controls to each component of the solution (and to reference guides where possible)
    3. Provide easy-to-use and easier-to-understand documentation for security critical components (authn/authz, encryption, keymgmt, certificates, etc.)
    4. Bake in security-relevant data collection in every template and model -> Make users turn it off by choice
3. Management
    1. Metrics should be surfaced that are relevant to quality: velocity (deploy frequency), defect rates and types, state of integration, etc.  [Nb. derive these directly from Accelerate/DORA reporting on what's important]
    2. Training new teams on the system is the NUMBER ONE adoption blocker.  This process must be both self-paced and well done.
    3. Interfaces to the rest of the organization will need to be managed (both data/network and reporting/organizational type things)

## The Mess

Github and Ruby on Rails and then React/Angular became *dominant* in their fields not due to any form of technical mastery or complexity, but for *making it easy to pickup*.  Git prior to github was extremely hard to grok, not well known, and restricted to serious, hardcore devs only.  Github radically changed that by making a web-ui to source, and adding TONS of 'how tos' that explained not just the command or switch, but what to use and why, all the way through to developing and proseltyzing the 'github flow' that many developers use today without even realizing it. (PRs merged into Main branch).

Ruby on Rails won because it turned setting up a webserver with php or python or C or whatever from a nightmare to a simple task.  In seconds you could be up and running with a 'Hello World' app - 'Todo list' development as a tutorial is probably the most common github repo to this day (although I'm guessing react is pushing up on it hard).
Rails took an opinionated approach to the 600000 choices you had to make for a fully functional web application (cookies, databases, authentication, authorization, caching, APIs, etc.) and just..made them for you.  The 'Rails Way' eliminated analysis paralysis and got folks just making web apps.  Their choices tended to be 'mostly the right ones', and infinitely better than the choices many would make on their own (writing your own cookie encryptor to store auth tokens, for example).

CI/CD space is like this today.  As evidenced by Gitlab, Spinnaker, the CD.Foundation, GitHub, AWS and thousands of other component choices.  Teams spend months evaluating, testing and struggling to configure basic pipelines out of the gate.  Nearly all of that struggle is 'sysadmin' _muda_.  It doesn't get business value delivered, it doesn't help code get deployed, etc.
In the DoD, this is almost pathological, tail-wagging-the-dog waste, with sysadmin teams building pipelines that no developer has used or wants, because they're not developers and don't understand that mindset.

Additionally, there is minimal insight into security from a CI/CD perspective, and virtual no available research or published content on security OR CI/CD for FaaS and serverless applications.  Many of the CI/CD applications require servers of their own (e.g. SonarQube, Jenkins, etc.).

## The Way

We will develop an opinionated, serverless, secure-ops focused CI/CD capability, with a heavy emphasis on Developer Experience (DX), in an assumed DevSecOps blended team operational mode.  Both the capability itself, as well as the 'deploy' target space will be serverless.  We will NOT intend to address anything requiring a virtual machine, anything that runs 'on prem', etc.  The security models, operational models, and conceptual models are so radically different that the two approaches (serverless vs serverful) cannot be addressed by a single system in a way that doesn't hobble either one.

### Components to be addressed

1. CI pipeline
2. CD tooling
3. Dashboarding for management
4. Dashboarding, o11y and monitoring for devsecops team
5. Templates and suggested architectures
6. Security in CI and in CD components
7. Deployment templates (e.g. blue/green lambda app)
8. Documentation with extensive how-to (assume copy/paste)
9. IDE
10. Developer end-to-end experience (from login, to code edit, to deployment, to troubleshooting)
