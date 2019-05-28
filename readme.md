# graphql-hacker-news-node
tutorial about graphql server implementation

## Overview
GraphQL is the rising star of backend technologies. It replaces REST as an API design paradigm and is becoming the new standard for exposing the data and functionality of a server.

In this tutorial, you’ll learn how to build an idiomatic GraphQL server entirely from scratch. You are going to use the following technologies:

graphql-yoga: Fully-featured GraphQL server with focus on easy setup, performance & great developer experience. It is built on top of Express, apollo-server, graphql-js and more.
Prisma: Prisma replaces traditional ORMs. Use the Prisma client to implement your GraphQL resolvers and simplify database access
GraphQL Playground: “GraphQL IDE” that allows to interactively explore the functionality of a GraphQL API by sending queries and mutations to it. It’s somewhat similar to Postman which offers comparable functionality for REST APIs. Among other things, a GraphQL Playground…

… auto-generates a comprehensive documentation for all available API operations.
… provides an editor where you can write queries, mutations & subscriptions, with auto-completion(!) and syntax highlighting.
… lets you easily share your API operations.

[graphql-node Tutorial - Introduction](https://www.howtographql.com/graphql-js/0-introduction/)

## Playground

### feed
    query {
      feed(
          first: 3
        skip: 2
          filter: ".io"
        ) {
        count
        args {
          first
          skip
          last
          orderBy
          filter
        }
        links {
          id
          description
          url
        }
      }
    }
### signup
    mutation {
      signup(
        name: "Bugs Bunny"
        email: "bugs.bunny@prisma.io"
        password: "graphql"
      ) {
        token
        user {
          id
        }
      }
    }
### login
**the token will be used to set Authentication header**

    mutation {
      signup(
        name: "Bugs Bunny"
        email: "bugs.bunny@prisma.io"
        password: "graphql"
      ) {
        token
        user {
          id
        }
      }
    }
### post
set http header to {"Authorization": "Bearer ___your-login-token___"}

    mutation {
      post(
        url: "www.prisma.io"
        description: "Prisma replaces traditional ORMs !!!!!!!!!!!"
      ) {
        id
      }
    }
### new vote subscription
set http header to {"Authorization": "Bearer ___your-login-token___"}

    subscription {
      newVote {
        id
        link {
          url
          description
        }
        user {
          name
          email
        }
      }
    }
### vote
set http header to {"Authorization": "Bearer ___your-login-token___"}

    mutation {
      vote(linkId: "___your link id___") {
        link {
          url
          description
        }
        user {
          name
          email
        }
      }
    }



### link
    query {
      link (id: "___your link id___") {
        id
        url
        description
      }
    }





###






















