# FAQ

[[toc]]

## General

### What are services?

Services are service-oriented self-contained applications that are highly specialized and reusable services.
These services can be algorithms, APIs or specialized functions. In Asyncy world, it's anything you can wrap in a Docker container. Services are independently deployable, scalable and manage their own metrics, logs and other operations.

> <small>Next: [Open Microservice Guide](http://microservice.guide/) &mdash; the open guide and standard for implementation and design of microservices.</small>

### Who maintains the services?

The project contributors maintain the service. This may be open-source projects, vendor built projects, or private projects.

For example, a Twitter library written in Python can be built in a Docker container and deployed on Asyncy in minutes. The Twitter library is already maintained by the contributors, there is very little extra work to make the service compatible in Asyncy.

### How difficult is it to build my own services?

Use any programming language necessary to build your service just like you would a library, package, or application.

> <small>Blog: [Building Smarter Microservices](https://blog.asyncy.com/designing-smarter-microservices/) &mdash; A guide for building your first microservice.</small>

## Storyscript

### Why did Asyncy design a new programming language?

In short: programming languages solve problems; there was no language to solve the problem we were tackling. Storyscript's design was about transparency and readability. We designed Storyscript to be familiar by using some of the most loved features in popular programming languages. For a full description, continue to our blog post below.

> <small>Blog: [Why Storyscript](https://blog.asyncy.com/why-storyscript/)</small>

### What is Storyscript used for?

Storyscript is a language for communication between services. It's designed to be feature-focused and goal-oriented. Storyscript is devops+architecture as code (no more configuring Kubernetes or infrastructure).

1. Application Backend
1. BPM (Business Process Management)
1. Asynchronous long-running logic
1. Workflows
1. CI/CD pipelines
1. Automation (event reactions, monitoring, alerting, etc.)

### How are Storyscripts started?

Storyscripts can start in many ways, here are just a couple examples:

1. HTTP request
1. Cron
1. Frontend user click button
1. API request
1. Webhook
1. IOT devices
1. Stream (event from logs, metrics)
1. Pub/sub
1. Smart Button or Alexa command
1. Text message or phone call
1. Another 3rd party application


### What are service aliases?

Services must be registered with the [Asyncy Hub](https://hub.asyncy.com) to be used in Storyscript. A service may specify aliases which are short title of the service (`myteam/asyncy-foobar-service` can choose `foobar` as an alias).

During the service discovery phase developers will select certain services which end up getting tracked in the `asyncy.yml` file.

```yaml{3,4}
# asyncy.yml
services:
  foobar:
    image: myteam/asyncy-foobar-service
    tag: v1.123
```

In Storyscript you can call upon this service like this:

```coffeescript
result = foobar do_this fruit:'apple' animal:'cat'
```

### Can Storyscript run asynchronously?

**Yes**. For example, during an HTTP request once the response if finished the remaining script is inherently asynchronous. When a Storyscript runs it is asynchronous from another Storyscript execution. Specific line(s) in the Storyscript may be executed asynchronously.

### What happens with a Storyscript crashes?

Things don't always go according to plan. When a Storyscript exits because of an error it's captured, detailed and recorded in the [Asyncy App](https://app.asyncy.com). The Storyscript data can be altered and the Storyscript restarted from any line the user desires to complete the process.

### Are Storyscripts stateless or stateful?

Storyscripts are stateless. An application may use stateful services but the Storyscript itself, by design, is stateless.

### Is Storyscript compiled or interpreted?

Storyscript is interpreted into architecture, it is not compiled into a lower-level language.

## Asyncy


### Is Asyncy a serverless environment?

**Yes**, Asyncy is a serverless execution environment. The Asyncy Platform provides an HTTP gateway which executes Storyscript in a serverless design.

### Is Asyncy a Paas, Baas, or Faas?

Asyncy is a **Platform as a Service** (aka PaaS) which has functionality of Backend as a Service (BaaS) and Functions as a Service (FaaS). Hard to put one label on it.

### Does Asyncy use Kubernetes under-the-hood?

**Yes**, Kubernetes is used to orchestrate containers. See the full [Asyncy Stack](https://asyncy.com/platform#stack).

### How much Kubernetes or devops experience is required?

**None.** Asyncy interacts with Kubernetes so you don't need to. It manages scaling, security, routing, networks and much more.

### Where are Storyscript's and other code stored?

Deployments to Asyncy **must** be git-backed. When deploying source code to Asyncy it will clone the repository and generate a release slug which is used in the platform for deployments.

### How are services managed?

When the Application is deployed all containers are pulled, started and scaled intelligently. Asyncy monitors service metrics, scales dynamically and load-balances between nodes automatically.

### Is Asyncy used for prototypes only?

**No**, the Asyncy Platform is a dynamically-scalable, robust, production-grade platform. It can also be used for on-premise deployments.


### Does Asyncy provide file storage?

**Yes**. Applications have a temporary volume that contains the applications repository source code and can be a temporary file storage. Applications may optionally have persistent storage which is flexible based on the application or service needs.

### Does the Asyncy Platform come with a persistent database?

**No**, databases are unfortunately not one-size-fits-all. Yet, it's quite simple to create persistent database or user a database backed by the cloud provider.

### Can I bring my own database?

**Yes***. We recommend using the cloud providers database, such as Google Cloud SQL or AWS RDS. But you can run and managing your own database on the Asyncy Platform.

### Can I run Asyncy on my own cloud?

**Yes**. Details coming soon.

### Is Asyncy open source?

*Every bit and byte*. The entire Asyncy Platform is open source on [GitHub](https://github.com/asyncy).

### Is there a managed Asyncy?

**Yes**, we call this the **Asyncy Cloud**. Currently in Private Beta, please contact us for an invitation.

### What is the pricing for Asyncy Cloud?

We plan to offer **highly transparent** pricing for our Asyncy Cloud offering. Details coming soon.

### Does Asyncy offer training?

**Yes**. Details coming soon.

### Does Asyncy offer support?

> During Beta we offer [support](/support/) for **free**. :heart:

Asyncy offers a variety of support options ranging from community support to premium support. More details will arrive during Beta.

### Does Asyncy have a Service Level Agreement (SLA)?

After Beta. For sure!

### What are the vendor lock-in risks?

All technology has a level of vendor lock-in, it's unavoidable. Asyncy is focused at building an open platform to reduce vendor lock-in concerns as much as possible. Our core mission depends on our ability to reduce vendor lock-in.

1. **Open Source** &mdash; Asyncy is 100% open sourced under various licenses that provide transparency and portability to on-premise commercial applications.
1. **Open Language** &mdash; Storyscript is MIT licensed and designed to be highly portable and platform-agnostic. A vendor could use the output of Storyscript to build their own platform.
1. **Open Services** &mdash; Thanks to the Open Microservice Guide all microservices are, by design, not unique to Asyncy.
2. **Open Standards** &mdash; The microservices used by Asyncy are designed in a platform-agnostic way using the principles and guidelines outlined in the [Open Microservice Guide](https://microservice.guide).

Please contact [legal@asyncy.com](mailto:legal@asyncy.com) for questions and concerns.
