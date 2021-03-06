---
title: Getting Started
menu: docs_basics
weight: 130
---

# Getting Started

Let’s write our first actix web application!

## Hello, world!

Start by creating a new binary-based Cargo project and changing into the new directory:

```bash
cargo new hello-world
cd hello-world
```

Now, add `actix-web` as dependencies of your project by ensuring your `Cargo.toml`
contains the following:

```ini
[dependencies]
actix-web = "{{< actix-version "actix-web" >}}"
```

In order to implement a web server, we first need to create a request handler.

A request handler is a function that accepts an `HttpRequest` instance as its only parameter
and returns a type that can be converted into `HttpResponse`:

Filename: `src/main.rs`

{{< include-example example="getting-started" section="setup" >}}

Next, create an `Application` instance and register the request handler with
the application's `resource` on a particular *HTTP method* and *path* and
after that, the application instance can be used with `HttpServer` to listen
for incoming connections. The server accepts a function that should return an
`HttpHandler` instance.  For simplicity `server::new` could be used, this
function is shortcut for `HttpServer::new`:

{{< include-example example="getting-started" section="main" >}}

That's it! Now, compile and run the program with `cargo run`.
Head over to ``http://localhost:8088/`` to see the results.

If you want, you can have an automatic reloading server during development
that recompiles on demand.  To see how this can be accomplished have a look
at the [autoreload pattern](../autoreload/).
