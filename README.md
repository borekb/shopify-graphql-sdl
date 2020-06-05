# Shopify Storefront GraphQL API as an SDL

This is an SDL representation of [Shopify's Storefront API](https://shopify.dev/docs/storefront-api).

## How to construct / update

1. Run the introspection query below in [Storefront's GraphiQL](https://shopify.dev/tools/graphiql-storefront-api).
2. Save the result to `temp.json`
3. Run `npx graphql-introspection-json-to-sdl temp.json > shopify-storefront.graphql`
