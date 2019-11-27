Related to issue - https://github.com/gatsbyjs/gatsby/issues/19748

## Some info

1. Site based on Gatsby Default starter - created using "gatsby new test-site"
2. Site builds using "gatsby develop"
3. Currently using gatsby@2.17.16
4. Can see the image nodes genetated by using the following graphql query in http://localhost:8000/___graphql

```
query MyQuery {
  allMarkdownRemark {
    edges {
      node {
        frontmatter {
          featuredImage {
            childImageSharp {
              fluid {
                src
                srcSet
              }
            }
          }
        }
      }
    }
  }
}
```

5. change the gatsby version to => gatsby@2.18.0 and the same query fails with the error:

```
{
  "errors": [
    {
      "message": "Field \"featuredImage\" must not have a selection since type \"String\" has no subfields.",
      "locations": [
        {
          "line": 6,
          "column": 25
        }
      ],
      "stack": [
        "GraphQLError: Field \"featuredImage\" must not have a selection since type \"String\" has no subfields.",
        "    at Object.Field (/Users/johnspurgin/Documents/Git/Gatsby/test-site/node_modules/graphql/validation/rules/ScalarLeafs.js:42:33)",
        "    at Object.enter (/Users/johnspurgin/Documents/Git/Gatsby/test-site/node_modules/graphql/language/visitor.js:324:29)",
        "    at Object.enter (/Users/johnspurgin/Documents/Git/Gatsby/test-site/node_modules/graphql/language/visitor.js:375:25)",
        "    at visit (/Users/johnspurgin/Documents/Git/Gatsby/test-site/node_modules/graphql/language/visitor.js:242:26)",
        "    at validate (/Users/johnspurgin/Documents/Git/Gatsby/test-site/node_modules/graphql/validation/validate.js:73:24)",
        "    at getGraphQLParams.then.then.optionsData (/Users/johnspurgin/Documents/Git/Gatsby/test-site/node_modules/express-graphql/index.js:121:32)",
        "    at process._tickCallback (internal/process/next_tick.js:68:7)"
      ]
    }
  ]
}
```
