# test_graphql
GraphQl SDL Query Mutations

```
#Query Get
query GetUser{
  user(id: "/api/v1/users/1") {
    id
  }
  users{
    edges {
      node {
	id
        email
        username
      }
    }
  }
}

#Mutation Create
mutation CreateUser{
  createUser(input: {
    email: "lee@gmail.com", 
    username: "lee@gmail.com", 
    role: "ROLE_USER",
    password: "bonjour",
    enabled: true,
  }) {
    user{
        id
      email
      username
      role
      reference
      enabled
      created
      updated
    }
  }
}

#Mutation Delete
mutation DeleteUser{
  deleteUser(input: {id: "/api/v1/users/7"}) {
    user{
        id
      email
    }
  }
}

```

# config graphql Api Platform
composer req webonyx/graphql-php

### config/packages/api_platform.yaml
api_platform:
    mapping:
        paths: ['%kernel.project_dir%/src/Entity']
    patch_formats:
        json: ['application/merge-patch+json']
    swagger:
        versions: [3]

    #Format
    formats:
        jsonld:  ['application/ld+json']
        jsonhal: ['application/hal+json']
        xml:     ['application/xml', 'text/xml']
        json:    ['application/json']
        yaml:    ['application/x-yaml']
        csv:     ['text/csv']
        html:    ['text/html']

    #GraphQl
    graphql:
        default_ide: graphql-playground
        graphql_playground:
            enabled: false
        graphiql:
            enabled: true

### config/routes/api_platform.yaml
```
graphiql:
    path: /docs/graphiql
    methods: GET
    controller: api_platform.graphql.action.graphiql
```
    
