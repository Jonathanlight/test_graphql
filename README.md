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
