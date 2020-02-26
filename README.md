# graphql-inspector-for-graphql-plugin

## Presentation

Generate the runtime from the GraphQL inspector schema, to be used in the graphql-maven-plugin-project and graphql-gradle-plugin-project. This allows use of the GraphQL inspector in the code generated by these plugins.

The generated code is based on the GraphQL specification, available [here](http://spec.graphql.org/June2018/#sec-Introspection)

This project generates the _com.graphql_java_generator.introspection_ package that is used in the _graphql-java-runtime_ module of the GraphQL Maven and Gradle Plugins.

## Why is this project independent?

This project should be embedded in the graphql-maven-plugin-project project.

To avoid a cycle dependency, it should be within the graphql-maven-plugin-logic module. But its pom is already complex, and generating the _com.graphql_java_generator.introspection_ package would add useless complexity there.

A the GraphQL introspection schema is rather stable, this project is left independent.

The main impact on the generated code would be the GraphQL plugin itself. 

If the generated code for introspection changes too often, then it will be integrated in the graphql-maven-plugin-logic module.