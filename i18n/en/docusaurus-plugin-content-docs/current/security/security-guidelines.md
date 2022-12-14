---
id: security-guidelines
title: Security Guidelines
---

*Version: March 2021*


*Document history*

| Date  | Description | Author | Approvers |
| -  | - | - | - |
| March 2021 | Fixed DB notes, Improve Infosec notes | ANB | SIBS |
| January 2021 | First Version | JCB | RAT, SIBS |


## Security Guidelines

**WE BELIEVE THAT SECURITY IS NON NEGOTIABLE AND MUST BE PRESENT, TESTED AND ENFORCED IN ALL ASPECTS AND STAGES OF THE PRODUCT.** 

**SECURITY MUST BE PRESENT IN DOCUMENTS, CODE, SOURCE CODE, TESTS, MESSAGING, ANALYTICS, IMAGES OR ANY OTHER DIGITAL OR PHYSICAL INFRASTRUCTURE USED TO PROVIDE SERVICES TO OUR CUSTOMERS.**


## Development Strategy & Guidelines

We're a digital platform as such our security will be heavily related to how we: Design, Code, build, Release code to production. 

Good code stands for lesser risks and higher security.

### Code ownership

Developers must act as owners and guardians of the code they build.

The development teams must operate in squads. Allowing developers to be owners and accountable for what they code.

Development only begins after the user interface and experience (UI/UX) baseline are completed. 

We code only when clear requirements and deliverables are defined. Developers are encouraged, allowed and expected to challenge and even refuse unclear designs or misleading guidelines.

### Continuous building

We'll rely heavily on continuous building and continuous integration. 

Once the development of a new release starts, it will be made available for testing. Only after approval will it be moved to the production environment. 

When coding for mobile App both IOS and Android platforms are created simultaneously reeling in the React Native framework. The features and scope of each sprint will be defined in conjunction with the Product team.

This approach allows fast and continuous learning about the features of the App, as well as adjustments and corrections of possible errors in an agile way. 

A sprint only finishes after code reaches production.

## Front End Security

### Mobile apps security
 
Our Apps are important features for our customers. However we don't control all the distribution chain of mobile apps. Devices can be compromised, downloads can be altered as such our Apps can be targeted as potential security attack vectors. In order to ensure App security will cover multiple security requirements regarding App life cycle: Development, test, release and use. Each step will have a separate scope and set of requirements as part of our security routines.

OpenPix Mobile Apps are entirely developed with our own, dedicated, development team and will also be subject to coding guidelines.

### App security assumptions

**TRUST NO ONE**

Devices can be compromised, tampered, altered, infected with viruses. The device OS, hardware neither and its security framework can't be trusted. For example root certificates can be injected, forged or removed. User Keys can be compromised

**NETWORK LAYER CAN BE COMPROMISED**

The communication between our App and our own backend can be compromised. We won't trust the network layer that our platform users. Examples: Man in the middle attacks

**MINIMUM FOOTPRINT**

Front-end will consume only what it needs, only when needed, leaving minimum footprint behind. Data will be lazily requested and used solely when needed.



## App security requirements

| Item | Description |
| - | - |
| **Code streamlining** | Code streamlining reduces the footprint of code that needs to be tested, certified. This reduces risks of code-mismatch.<br/><br/> Within the Mobile App scope both IOS and Android apps share the same repository re-using most of the code. This is possible through React Native the main programming language for Apps.<br/><br/> This strategy reduces code complexity while maintaining great customer experience. |
| **Code quality guidelines** | App development must use the code best-practices.<br/><br/><ul><li>ES7</li> <li>Automatic Lint</li> <li>Unit Testing</li><li>Asynchronous functions (async/await)</li><li>Modern component rendering</li><li>Relay Modern.</li></ul>|
| **Build process** | The final build (production build) must be always generated by the CI/CD system.<br/><br/> No human intervention is performed when creating the build |


## Web security

Most of our customers will connect to the platform using browsers on a regular basis. Web is a key component to the platform and is widely exposed on the internet. 

Web is a potential security attack vector. 

In order to ensure web security will cover multiple security requirements regarding App life cycle: Development, test, release and use. Each step will have a separate scope and set of requirements as part of our security routines.

### Web security requirements


| Item | Description |
| - | - |
| **Code streamlining** | Web uses a single code base on React. React allows components to be built as lego bricks. Each component can individually tested<br/><br/>Streamlining reduces risks of code-mismatch. |
| **Code guidelines** | App must use development code best-practices<br/><br/> <ul><li>ES7</li><li>Automatic Lint</li><li>Unit Testing</li><li>Modern component rendering</li></ul> |
| Build process | The final build (production build) must be always generated by the CI/CD system.<br/><br/> Build is generated on an automated platform. After the code is compiled, it is moved to a private container registry. The registry is consumed by Kubernetes Agent that will reload the container directly from the registry. |




## Test policy

Tests are a key element for code quality and code security.

Our testing policy mandates that the code used in production must be accompanied by its respective tests. In addition to following good development practices we always write the tests first before we create lines of code.

### Automated tests

Code is always accepted if provided with applicable, relevant unit tests. Best practice expects; Write tests first, then code.

For each commit, tests will run again. We always use continuous and automated testing. Automated tests use the Jest framework and run in our CI/CD platform.

Tests will run automatically, even if the new code is not applicable to the master repository. 

In addition, the development team receives, in real time, the result of all the tests.

### Human tests

All releases will have a final, manual review, executed by a human using the staging environment.


### TypeScript testing. Code validation during development
 
JavaScript code will use the TypeScript validation framework. This tool helps validate the quality of the code at editing time and warns the developer if consistency errors are found. The use of TypeScript is extremely important to meet a basic premise of this project: code reuse. 

Code components can only be reused with quality if at their source they state clearly and concisely what data they expect to receive and or produce.

### Code review

Each developer of the team has its peer reviewer, that is, another developer who did not participate in the development of the code will act as bar raiser performing the review of the code in a critical and constructive way.

Repositories must be private, branches are protected. Every commit must be performed using a pull-request. Pull requests will only be merged if two or more developers approve the commit.

### Unified API and backend component

When communicating with the backend the App or Browser App will use a single component in the code that handles all outside world communication

All requests originating from the client must pass through the API component, and must connect to a well known backend service.
 
 
### Reduce memory usage and exposure

Code or libraries must make little use of memory in the devices. This is fundamental to the correct operation of the App in low cost devices. This also reduces the risk of 

The use of functions such as should Component Update on components drastically improves the user experience as it significantly reduces the use of computing resources on mobile devices. For Android devices with low RAM and / or low CPU resources the correct use of this feature can significantly increase the number of supported devices, especially in the case of low cost devices.

### Mature and stable libraries
 
Code Libraries must always be mature or LTS. Preference will be given to implementations using open source.

As a strategy for continuous development we always practice keeping the production code in tandem with each new release (stable) of React Native (for Android devices and IOS) and with React for web platforms.


### EcmaScript use latest LTS version 

All produced JavaScript muse use ES6 and newer version functions. Async / await (ES7 functions) must be used whenever asynchronous operations are required.

 
### Crash Reporting tools

Crash reporting tools (Firebase Crashlytics) must not log any personally identifiable information (PII), or sensitive personal information (SPI). 

This is the information that can be used on its own or with other information to identify, contact, or locate a single person, or to identify an individual in context. 




## Back End Security

### Cloud security
 
OpenPix platform runs on the Cloud. Cloud reduces our go-to-market time allowing fast prototyping and controlled costs. However the cloud is not secure by default. 

Regardless of the cloud provided used the platform security remains or responsibility

### Cloud security assumptions


**TRUST NO ONE**

Cloud is just someone else's server, managed by a third party. We must factor into our code that the cloud provider can and will eventually be hacked. 
	
**EVERYTHING EVENTUALLY FAILS**

Even the best cloud provider will crash. Even the best replication schema will fail.

**ENCRYPT**

Data must be encrypted at all times. Data must be encrypted while in flight or when stored



### Cloud security requirements

| Item | Description |
| - | - |
| **Encryption at rest** | Database data must be encrypted using unique encryption keys. Keys must be stored in a secure enclave HSM keys. This ensures that data is not readable by an unauthorized person in the event that the files are compromised.<br/><br/>With encryption at rest databases encrypt the data before storing it into disk.<br/><br/>HSM keys access must be protected by IAM keys.
| Containers | All backend services must run on its own designated container |
| Code Guidelines |  App must use development code best-practices<br/><br/><ul><li>ES, using latest LTS</li><li>Automatic Lint</li><li>Unit Testing</li><li>Asynchronous functions (async/await)</li></ul> |
| Separation of duties | Separation of duties and role-based access control is inherent in the design of the Cloud.<br/><br/>Systems that run code or monitors the health and network availability of your HSMs should not be involved in the creation and management of the key material stored within your HSMs. |
| Build process | The final build (production build) must be always generated by the CI/CD system.<br/><br/>Build is generated on an automated platform. After the code is compiled, it is moved to a private container registry. The registry is consumed by Kubernetes Agent that will reload containers directly from the registry. |
| Limited access to cloud infrastructure | Access to the cloud provider is restricted to a reduced number of senior developers in the company, all members of the company.<br/><br/>Developers only have access to the source code. The development environment is separate from the productive environment (staging environment).<br/><br/>Code changes whether in development, staging or production are only performed through the continuous deployment platform so it is possible to track and control each change in the code. |
| MFA | Humans must use Multi Factor Authentication when connecting to cloud infrastructure. |
| IAM key management | Each environment will use its own set of keys. Keys will be loaded directly into Kubernetes. |
| IAM keys must be rotated every 6 months. | Key rotation is performed directly in Kubernetes config environment |


## Backup Policy & Security

### Backup Policy
 
Backup policy & security requirements [Backup Policy](backup-policy)


