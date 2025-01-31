Software Engineer Intern Task
======================

At Carex, we have a lot of services that need to work together to deliver our product.
Some of these services talk to third-party providers to perform their operations – for
example performing background checks, sending messages or emails, etc.

In a lot of cases - due to business, compliance or technical reasons - we need to support
multiple third-party providers for the same operation, some of which have wildy different
specifications, ranging from simple REST APIs to SOAP.

To maintain our sanity, we abstract these third-parties behind interfaces and expose
consistent APIs for the rest of the system to consume. Each service should be able to
pick sensible defaults (and fallbacks, if, for example, a provider is unavailable) or
allow the consumer to specify the provider if they wish to do so.

Mission
-------

Your mission, should you choose to accept it, is to build a microservice called `shorter`, 
which supports two URL shortening providers: [bit.ly](https://dev.bitly.com/) and [tinyurl.com](https://gist.github.com/MikeRogers0/2907534).
You don't need to actually sign up to these providers, just implement their API. The
service exposes a single endpoint: `POST /shortlinks`. The endpoint should receive
JSON with the following schema:

| param    | type   | required | description                        |
|----------|--------|----------|------------------------------------|
| url      | string | Y        | The URL to shorten                 |
| provider | string | N        | The provider to use for shortening |

The response should be a `Shortlink` resource containing:

| param    | type   | required | description                        |
|----------|--------|----------|------------------------------------|
| url      | string | Y        | The original URL                   |
| link     | string | Y        | The shortened link                 |

For example:
```json
{
    "url": "https://example.com",
    "link": "https://bit.ly/8h1bka"
}
```

You are free to decide how to pick between the providers if one is not requested and what
your fallback strategy is in case your primary choice fails. Your endpoint needs to return
a JSON response with a sensible HTTP status in case of errors or failures. You can choose any language or framework you liked as long as provide enough documentation to run the project

What you need to do
-------------------

1. Choose a language and choose a http framework for it.
2. Build the `POST /shortlinks` endpoint.
3. Write some tests. 

Deliverable
-----------

You should deliver your solution as a Pull Request in your repo. Document your design choices and anything else you think we need to know in the PR description.

What we look for
----------------

In a nutshell, we're looking for tidy, production-quality code, a scalable design and sensible
tests (unit tests, integration tests or both?). Imagine that your code will be read by other 
developers in your team – keep them happy :-)


Disclaimer
----------

We will not use any of this code for any of Carex's applications.
