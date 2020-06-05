# Shopify Storefront GraphQL API as an SDL

This is an SDL representation of [Shopify's Storefront API](https://shopify.dev/docs/storefront-api).

## How to construct / update

1. Run [this introspection query](https://community.shopify.com/c/Shopify-APIs-SDKs/Possible-to-import-Shopify-s-GraphQL-Schema-SDL-into-Postman/m-p/574265/highlight/true#M38432) in [Storefront's GraphiQL](https://shopify.dev/tools/graphiql-storefront-api).
2. Save the result to `temp.json`
3. Run `npx graphql-introspection-json-to-sdl temp.json > shopify-storefront.graphql`

<details><summary>The introspection query</summary>

```graphql
query IntrospectionQuery {
    __schema {
      queryType { name }
      mutationType { name }
      subscriptionType { name }
      types {
        ...FullType
      }
      directives {
        name
        description
        args {
          ...InputValue
        }
        locations
      }
    }
  }

  fragment FullType on __Type {
    kind
    name
    description
    fields(includeDeprecated: true) {
      name
      description
      args {
        ...InputValue
      }
      type {
        ...TypeRef
      }
      isDeprecated
      deprecationReason
    }
    inputFields {
      ...InputValue
    }
    interfaces {
      ...TypeRef
    }
    enumValues(includeDeprecated: true) {
      name
      description
      isDeprecated
      deprecationReason
    }
    possibleTypes {
      ...TypeRef
    }
  }

  fragment InputValue on __InputValue {
    name
    description
    type { ...TypeRef }
    defaultValue
  }

  fragment TypeRef on __Type {
    kind
    name
    ofType {
      kind
      name
      ofType {
        kind
        name
        ofType {
          kind
          name
        }
      }
    }
  }
```

[Source](https://community.shopify.com/c/Shopify-APIs-SDKs/Possible-to-import-Shopify-s-GraphQL-Schema-SDL-into-Postman/m-p/574265/highlight/true#M38432).

</details>