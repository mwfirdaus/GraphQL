# GraphQL
Learn GraphQL by writing full-stack JavaScript applications with Node.js, Express, Apollo Server, React, Apollo Client.

# Introduction
## What's is GraphQL
<img width="1340" alt="image" src="https://user-images.githubusercontent.com/85268263/155052300-a11defc0-e89a-43eb-b7d4-75a586cf941a.png">
GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.

## Defining a Schema

```sh
yusuf@Yusufs-MacBook-Pro GraphQL % node server.js
{
  kind: 'Document',
  definitions: [
    {
      kind: 'ObjectTypeDefinition',
      description: undefined,
      name: [Object],
      interfaces: [],
      directives: [],
      fields: [Array]
    }
  ],
  loc: Location {
    start: 0,
    end: 49,
    source: Source {
      body: '\n    type Query {\n        greeting: String\n    }\n',
      name: 'GraphQL request',
      locationOffset: [Object]
    }
  }
}
```

```sh
yusuf@Yusufs-MacBook-Pro GraphQL % node server.js
server running on http://localhost:9000/
```

<img width="912" alt="image" src="https://user-images.githubusercontent.com/85268263/155063419-aa07d72e-0e4b-410f-8dbb-7b8fb51c9dc6.png">

## Http Request

```js
const GRAPHQL_URL = "http://localhost:9000/";

async function fetchGreeting() {
    const response = await fetch(GRAPHQL_URL, {
        method: 'POST',
        headers: {
            'content-type': 'application/json'
        },
        body: JSON.stringify({
            query: `
                query {
                    greeting
                }
            `
        })
    });
    const { data } = await response.json();
    console.log(data);
    return data;
}

fetchGreeting().then(greeting => {
    const title = document.querySelector('h1');
    title.textContent = greeting.greeting;
});
```
# Apollo Server
Apollo Server is an open-source, spec-compliant GraphQL server that's compatible with any GraphQL client, including Apollo Client. It's the best way to build a production-ready, self-documenting GraphQL API that can use data from any source.

![image](https://user-images.githubusercontent.com/85268263/155081410-0978672c-a8e3-4306-8ad3-b144a08d2709.png)

You can use Apollo Server as:
* A stand-alone GraphQL server, including in a serverless environment
* An add-on to your application's existing Node.js middleware (such as Express or Fastify)
* A gateway for a federated graph

Apollo Server provides:
* Straightforward setup, so your client developers can start fetching data quickly
* Incremental adoption, allowing you to add features as they're needed
* Universal compatibility with any data source, any build tool, and any GraphQL client
* Production readiness, enabling you to ship features faster
