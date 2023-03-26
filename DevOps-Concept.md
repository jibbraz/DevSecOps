<!-- # DevOps Methodology, Principles & Stages Explained
* `DevOps` is a term that refers to the collaboration of software developers (dev) and operations personnel (ops).
  
# History of DevOps
* Before DevOps, We had two approaches for software development namely the `Waterfall` and the `Agile`.
  
## Waterfall Model
* `Requirements gathering and analysis`
* `Design`
* `Implementation`
* `Verification`
* `Maintenance`

### Advantages of the Waterfall Model:
* Simple to understand and use
* Allows for easy testing and analysis
* Saves a significant amount of time and money
* Good for small projects if all requirements are clearly defined
* Allows for departmentalization & managerial control
### Disadvantages of Waterfall Model:
* Risky and uncertain
* Lack of visibility of the current progress
* Not suitable when the requirements keep changing
* Difficult to make changes to the product when it is in the testing phase
* The end product is available only at the end of the cycle
* Not suitable for large and complex projects -->

# Build Automation
* Automation of the process of preparing code for deployment to a live environment
* Depending on what languages are used
* Do in a consistent, automated way using a script or tool 
* The tools of build automation often differ depending on what programming language are used 

### Why do build automation?
* `fast`
* `consistent`
* `repeatable`
* `portable`
* `reliable`

### Tools
* Depend on programming language and framwork
* `Java - ant, maven, gradle`
* `Javascript - npm, grunt, gulp`
* `Make - wildly used in Unix-base system`
* `Packer - build machine images and containers`

# Continuous Integration (CI) >> Build, Test, Merge
* the practice of frequenty merging code change done by developer
* ปกติ dev ใช้ทำงานแยกกัน ใช้เวลาหลายวันกว่าจะรวมโคด
* Merging all the time could be a lot of work, so to avoid that it should be `automated`
```bash
CI เข้ามามีบทบาทในการช่วย Developer ให้ Merge code ที่แก้ไขส่งกลับไปที่ Pool กลาง เช่น Git Repository ซึ่งอาจจะตั้งค่าให้ทำวันละครั้งก็ได้ ทีนี้เวลาที่ Developer มีการเปลี่ยนแปลงอะไรเกี่ยวกับ App ก็จะมี CI ช่วย Merge code รวมไปถึงการทำ Automate test, Unit test และ Integration test เพื่อให้มั่นใจว่าสิ่งที่ Developer เปลี่ยนแปลงไปจะไม่กระทบกับการทำงานของ Application จะให้ได้ว่ามีการทดสอบหลาย ๆ อย่าง ทดสอบทุกอย่างตั้งแต่ Class ไปจนถึง Function ใน Module ที่แตกต่างกันแล้วนำมาประกอบเป็น Application ถ้าการทำ Automate test แล้วเจอปัญหาเรื่อง Conflict ระหว่าง Code เดิมกับของใหม่ CI จะช่วยให้ง่ายต่อการหา และแก้ไข Bug ครับ
```
### Why do Continuous Integration?
* `Early Detection`
* `Eliminate the scramble`
* `Frequent release`
* `Continuous testing` > QA 
* `Good coding practice`
  
### Tools
* `Jenkins` - open source, widely used, java servlet-based
* `Travis CI` - open source, built aroud github integration, executes builds in clean VMs
* `Bamboo` - enterprise product

# Continuous Deliverly and Continuous Deployment (CD)
* `Continuous Deliverly` the practice of continuously maintaining code in a deployable stat,  keep the code in deployable state
```bash
หลังจากที่มีการทำ Automation ในเรื่องของการ Build test, Unit test และ Integration test ในฝั่ง CI กันไปแล้ว CD ที่เป็น Continuous Delivery จะทำหน้าที่ส่ง Code ที่มีการตรวจสอบแล้วไปยัง Repository ดังนั้นถ้าต้องการให้ระบบ Continuous Delivery มีประสิทธิภาพมากที่สุด จะต้องทำระบบ CI ให้อยู่ใน Pipeline เดียวกันกับ CDเป้าหมายของการทำ CD คือการที่พร้อมที่จะนำ Code ไป Deploy ที่ Production ได้ตลอดเวลานั่นเองครับ แต่ Continuous Delivery จะยังเป็น Step Manual อยู่ ไม่ได้เป็น Automation ทั้งหมด
```
* `Continuous Deployment` the practice of frequently deploying small code chage to production (routine)
```bash
CD อีกตัวนึงที่ต่างจาก Continuous Delivery นั่นก็คือ Continuous Deployment ขั้นตอนนี้เป็นขั้นตอนสุดท้ายของ CI/CD Pipeline ซึ่งเป็นส่วนที่ขยายมากจาก Continuous Delivery ซึ่งจะทำหน้าที่จัดการโดยอัตโนมัติในส่วนของการนำ Code จาก Repository ไป Deploy บน Production Continuous Deployment จะเหมาะกับการใช้งานที่มีการ Deploy เป็นจำนวนมาก และมีขั้นตอน Test automation ที่ออกแบบมาเป็นอย่างดีโดยในทางปฏิบัติแล้ว Continuous Deployment หมายถึงการที่ Developer สามารถ Dev app ขึ้นมาแล้วไป Go Live บน Cloud ได้โดยใช้เวลาเพียงไม่กี่นาที (อันนี้สมมุติว่าทดสอบด้วยระบบ Automate ผ่านด้วยนะ ) การที่สามารถทำแบบนี้ได้จะช่วยให้ได้รับ Feedback ต่าง ๆ กลับมาไว ไม่ว่าจะเป็นจากฝั่ง User หรือว่า QA ทีนี้เวลาเราเอา CI กับ CD มารวมกัน เป็น CI/CD ก็จะช่วยให้สามารถ Deploy app โดยลดความเสี่ยงและปัญหาที่จะเกิดขึ้นได้ อย่างไรก็ตาม CI/CD จะเหมาะกับการแก้ไขหรือเปลี่ยน Feature เล็ก ๆ น้อย ๆ มากกว่าแก้ไขทั้งหมด แต่การที่จะทำ CI/CD Pipeline ขึ้นมาจะต้องลงแรง และใช้เวลาเนื่องจากต้องวางแผนเรื่อง Automated test ซึ่งมีการเขียนที่หลากหลายรูปแบบตามสถานการณ์ในการทดสอบ
```
* Each version of the code go through a series of stat such as `automated build`, `automated testing`, `manual acceptance testing`. The result of this process is an `artifact` or `package` that is able to deploy
* If deployment cause a problem, it is quickly and reliably `rolled back` using an automated process

### Why do Continuous Deliverly and Continuous Deployment?
* `Faster time-to-market`
* `Fewer problem cause by the deployment process`
* `Lower risk`
* `Reliable rollbacks`
* `Fearless Deployments`
* ลดปัญหาเรื่องการแก้ไข Code –  เนื่องจากมีระบบที่คอยนำ Code มารวมกันแล้วทดสอบให้
* ลดปัญหาจากการทำงานแยกส่วนกัน – จากเหตุผลเดียวกับด้านบน
* ลดระยะเวลาในการส่งมอบงาน – ระบบเป็นผู้ทดสอบให้ ทำให้ไม่ต้องเสียเวลาให้คนมาตรวจสอบแบบ Manual
* เพิ่มความน่าเชื่อถือในการทดสอบ – เนื่องเวลาแก้ไข Feature จะแก้ไขแบบเล็ก ๆ ทำให้เวลาเปลี่ยนแปลงระบบ จะทดสอบด้วยเวลาไม่นาน และมีความแม่นยำมากกว่าการเริ่มทำใหม่ตั้งแต่ต้น
* ลดค่าใช้จ่าย – เนื่องจากเป็นระบบอัตโนมัติทำให้ Flow การทำงานบางส่วนไม่ต้องใช้จำนวนคนในการ Monitor
* ดูแลง่าย Update ง่าย – การทำ CI/CD ช่วยทำให้สามารถตรวจสอบหาปัญหาได้ในทุก ๆ ขั้นตอน ไม่ว่าจะเป็นในช่วงแรกของการ Build หรือการ Update จาก App เดิมที่มีอยู่ โดย Bug ที่เกิดขึ้นจะถูกตรวจสอบได้ง่ายและตรงจุด ทำให้สามารถ Maintenance และ Update ได้ง่ายครับ

### ความแตกต่างของ CI และ CD มีอะไรบ้าง?
```bash
# CI จะเป็นระบบ Automate test สำหรับ Developer ถ้าแก้ Code แล้วผ่านระบบ CI ไปได้หมายถึง Code จะ Merge ไปยัง Repository สำเร็จ CI เข้ามาตอบโจทย์ในกรณีที่ Developer มีการ Dev แยกส่วนกันแล้วต้องทำ Code มารวมกัน ทำให้อาจเกิดปัญหาเรื่อง Conflict กันได้
# CD ตัวแรก Continuous Delivery ส่วนใหญ่จะหมายถึงการที่ Developer สามารถ Upload Code เพื่อไปทดสอบหา Bug ที่ Repository เช่น GitHub ได้โดยอัตโนมัติ ซึ่งทำให้ทีม Operation สามารถนำไป Deploy ได้เลย ช่วยให้ลดปัญหาเรื่องของการสื่อสารระหว่าง Developer และทีม Business สุดท้ายแล้วจุดประสงค์ของการทำ Continuous Delivery คือการทำให้มั่นใจว่าเราจะใช้แรง หรือความพยายามที่น้อยที่สุดในการ Deploy Code ใหม่ ๆ นั่นเองครับ
# CD ตัวถัดมา Continuous Deployment หมายถึง การปล่อย Code จาก Repository ไปยัง Production โดยอัตโนมัติ ซึ่งจะถูกใช้งานโดยลูกค้า การทำแบบนี้ช่วยลดการทำงานของทีม Operation ในการทำระบบแบบ Manual ซึ่งอาจทำให้การ Deploy ล่าช้าได้
```

# Infrastucture as Code (IaC)
* Manage and provision infrastructure through code and automation
* Automatation and code create and change : `servers`, `instaces`, `environments`, `Containers`, `Other infrastructure`
* Change some code or configuration file with an `automated tool` 
* Provisioning new resource and changing existing resources through automation

### Why do Infrastructure as Code?
* `Consistency`
* `Reusability `
* `Scalabilty`
* `Self-Documenting`
* `Simplify the complexity`

# Configuration Management
* Maintaining and changing the state of pieces of infrastructure in consistent, maitainable, and stable way
* Configuration management allow you to minimize `configuration drift`
* Infrastructure as code is very beneficial for configuration management

```bash
# Example: You need to upgrade a software package on a bunch of servers
without good configuration management: manual upgrade can lead to a lot of problems
with good configuration management: define the new version of software package in a configuration file or tool and automatically roll out the change to all of the servers
```

### Why do Configuration Management?
* `Save time`
* `Insight`
* `Maintainability`
* `Less Configuration Drift`

### Tools
* `Ansible - open source, decralative configuration, YAML, No control server needed, No agent needed` 
* `Puppet`
* `Chef`
* `Salt`

# Orchestration
* automation that supports processes and workflows, such as provisioning resources
* managing a complex infrastructure is less like being a builder and more like conducting an orchestra
* Instead of going out and creating piece of infrastructure, the conductor simply signals what need to be done and the orchestra perform it
```bash
# Example: Customer request more resource for a web service
operation engineer use an orchestration tool to request five more node
```

### Why do Orchestration?
* `Scalability`
* `Stability`
* `Save time`
* `Self-service`
* `Granula insight into resource usage`

### Tools
* `Docker swarm`
* `Kubernetes`
* `Terraform` :combine orchestration and IaC

# Monitoring
* The collection and presentation of data about the performance and stability of services and infrastructure : `chart`,`graph`,`alert`
* `Real-time notification`
* `Postmortem analysis`
  
### Why do Monitoring?
* `Fast recovery`
* `Better root cause analysis`
* `Visibility across teams`
* `Automated response`

# Microservices
* A microservice architecture breaks an application up into a collection of small,loosely-coupled services
* In a `monolithic architecture`,all features and services are part of one large application
* Microservices are small: each microservice implements only a small piece of an application's overall functionality
* Microservice are loosely-coupled: Different microservices interact with each other using stable and well-defined APIs. This means that they are `independent` of one another 

### Microservices vs Monolith
```bash
# Microservices คือการแบ่งระบบออกเป็นส่วนย่อย ๆ แทนที่จะรวมเป็นระบบเดียวอย่าง Monolithic การวางระบบแบบ Microservices แปลว่า แต่ละ Service จะสามารถ Deploy และ Scale ได้เองอย่างไม่จำเป็นต้องเชื่อมโยงกันทั้งหมด ถึงขนาดที่ว่า Microservices แต่ละตัว สามารถเขียนโดยคนละภาษาได้ และสามารถให้ทีมที่ต่างกันดูแลแต่ละส่วนแบบแยกกันได้
# Monolithic structure คือการติดตั้งระบบแบบเป็นกลุ่มเดียว ด้วยข้อดีนี้ของ Monolithic เอง ทำให้ระบบนี้เป็นที่นิยมใช้กันในบริษัทที่เพิ่งเริ่มต้น
```

* There are many different ways to structure and organize a microservice architecture
```bash
# Example, a pet shop application might have:
- A pet inventory service
- A customer details service
- An authencation service
- A pet adoption request service
- A payment processing service
```
* can all be built, deployed, scaled seperately

### Why use Microservices?
* Microservices encourage `Modularity`
* Technological flexibility
* Optimize scalability
```bash
# Microservice aren't always the best choice. For smaller app monolith might be easier to manage
```

# 
# The DevOps lifecycle and how DevOps works
* Stages of the DevOps process
* The DevOps lifecyle stretches from the beginning of software development through to delivery, maintenance, and security. The stages of the DevOps lifecycle are:

`Plan`
Organize the work that needs to be done, prioritize it, and track its completion.
```bash
Plan is the stage of DevOps that encompasses everything that happens before the first line of code is written. It’s about creating a product roadmap that guides upcoming development, helping the team organize resources and priorities, align, and track projects.
```

`Create`
Write, design, develop and securely manage code and project data with your team.
```bash
Create is the first stage of the CI/CD pipeline. This is where code is designed and developed using version control to coordinate changes made by multiple developers to the same code base. This is one of the keys to improving velocity.
```

`Verify`
Ensure that your code works correctly and adheres to your quality standards — ideally with automated testing.
```bash
Verify is a process focused on confirming the quality of code. To get feedback quickly to developers and testers, and instant insights into every commit, this process relies on security testing, code quality analysis, parallel execution, and automation. Enabling developers to find and fix flaws while they are developing has proven to be `more cost-effective and efficient`
```

`Package`
Package your applications and dependencies, manage containers, and build artifacts.
```bash
The Package stage comes after code has been created and tested. Packaging applications and dependencies, managing containers, and building artifacts maintains a consistent software supply chain.
```

`Secure`
Check for vulnerabilities through static and dynamic tests, fuzz testing, and dependency scanning.
```bash
Protect is about securing your applications and their runtime environment, from intrusions, and new vulnerabilities.
```

`Release`
Deploy the software to end users.
```bash
Release or deployment is about pushing code updates into the production environment. With DevOps, releases can be deployed as iterations are created, tested, and ready – and not as on a preplanned, static, bulk release date.
```

`Configure`
Manage and configure the infrastructure required to support your applications.
```bash
Configure is about setting up, managing, and maintaining application environments. Automated configuration management is designed to handle these complex environments across servers, networks, and storage systems.
```

`Monitor`
Track performance metrics and errors to help reduce the severity and frequency of incidents.
```bash
Monitor is a proactive, automated part of the process, focused on tracking software, infrastructure, and networks to trace status and raise alerts to problems. This increases security, reliability, and agility.
```

`Govern`
Manage security vulnerabilities, policies, and compliance across your organization.
```bash
Manage is about visibility and control across your end-to-end software development lifecycle by managing permissions, standardizing DevOps build and deployment processes, and automating guardrails to ensure security and compliance policies are met
```

* Some organizations string together a series of tools to gain all of this functionality, but that can be incredibly costly and complex to deploy, manage, and maintain.

# DevOps tools, concepts and fundamentals
* DevOps covers a wide range of practices across the application lifecycle. Teams often start with one or more of these practices in their journey to DevOps success.

`Version control`	The fundamental practice of tracking and managing every change made to source code and other files. Version control is closely related to source code management.
```bash
# Source Code Management (SCM)
This is how a repository of code is shared among many developers without one person’s changes negating another’s. The code is divided and managed into projects and groups of projects. An individual developer checks out existing code or adds code to what’s there and the SCM tool identifies conflicting edits to the same code and flags it for resolution. This process allows multiple developers to work on one project at once, a key to increasing the velocity of software updates. DevOps thrives on Git repositories, `an important distinction from old-school version control systems`, because of the powerful capabilities their modern architecture enables
```

`Agile`	Agile development means taking iterative, incremental, and lean approaches to streamline and accelerate the delivery of projects.

`Continuous Integration (CI)`	The practice of regularly integrating all code changes into the main branch, automatically testing each change, and automatically kicking off a build.
```bash
This is the step that enables iteration by committing changes to a shared source code repository early and often — many times a day — and automatically testing each change and kicking off a build.

Continuous integration is all about efficiency. By automating manual work and testing code more frequently, teams can iterate faster and deploy new features with fewer bugs more often. Other benefits of CI include identifying and fixing problems more easily, less context-switching for your team, and happier users and customers.

To get the most out of continuous integration, make sure
your setup includes these core elements:

# A source code repository with all the necessary files and scripts to create builds.
# Automated builds with scripts that include everything you need to build from a single command.
# Self-testing builds that automate your policies (forinstance, fail if any test fails).
# Frequent commits and iterations so there are fewer places for conflicts to hide.
# Stable testing environments that accurately reflect the production environmen.
# Visibility so every developer can access the latest executables and see any changes made to the repository.
```
```bash
# Automated testing
This is key to fully adopting DevOps and continuous integration — and releasing higher quality code more frequently. With testing built into your CI pipeline, every committed code change triggers a build, and then the build runs tests to ensure the changes pass all tests, policies, and code compliance standards you established for your application. With this in place, bugs are identified earlier and with greater context to simplify their resolution, your teams can deploy more frequently and confidently, and you minimize manual testing and reworking late in the process.
```

`Continuous Delivery (CD)`	Continuous delivery works in conjunction with continuous integration to automate the infrastructure provisioning and application release process. They are commonly referred to together as [CI/CD](/topics/ci-cd/).
```bash
Continuous delivery is a software development process that works in conjunction with continuous integration to automate the application release process. Once code has been tested and built as part of the CI process, continuous delivery takes over during the final stages to ensure it’s packaged with everything it needs to deploy to any environment at any time. Continuous delivery can cover everything from provisioning the infrastructure environment to deploying the tested application to test/ staging or production.

With continuous delivery, software is built so it can be deployed to production at any time. Then you can trigger the deployments manually or automate the process.

When continuous delivery is done well, your software release processes become boring — that is, they are low- risk, consistent, and repeatable. Then you can confidently plan release processes and schedules, automate infrastructure and deployments, and manage your cloud resources more effectively.
```

`Shift left`	A term for shifting security and testing much earlier in the development process. Doing this can help speed up development while simultaneously improving code quality.
```bash
A fundamental process for successful DevOps is incorporating security into the end-to-end automation. This is often referred to as DevSecOps. By integrating testing and the security review process earlier in the software development lifecycle, there is more opportunity to adequately address any security issues. If security testing is treated as an afterthought or doesn’t happen until code is ready for production, it can be difficult to go back and correct problems, and it’s often too late to fix them quickly and efficiently. This can lead to delayed deployments, vulnerabilities making it into production, greater technical debt, and inefficient silos between security and the rest of the DevOps teams

To shift security left, you’ll want to integrate security testing into your CI pipelines so code is continually tested, not only against other commits in the shared repository, but for overall security, as well. Some types of security testing you may want to include early on in your development lifecycle include:

# Static Application Security Testing (SAST)
# Dynamic Application Security Testing (DAST)
# Container and cluster image scanning
# Dependency scanning
# Secret detection
# Infrastructure-as-code (IAC) scanning
# API testing
```