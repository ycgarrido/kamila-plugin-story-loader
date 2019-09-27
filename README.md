# gatsby-transformer-javascript-frontmatter

Parses Stories files to extract content.

## Install

`npm install --save-dev @kamila-lab/story-loader`

## How to use

To use this plugin you also need [gatsby-source-filesystem](https://github.com/gatsbyjs/gatsby/tree/master/packages/gatsby-source-filesystem) installed and configured.

```javascript
// In your gatsby-config.js
module.exports = {
  plugins: [
    {
      resolve: `gatsby-source-filesystem`,
      options: {
        path: `./.stories/`
      }
    },
    "@kamila-lab/story-loader"
  ]
};
```

## Parsing algorithm

In a `index.story.js` (or `index.story.jsx` / `index.story.ts` / `index.story.tsx`) file.

```javascript
export default {
  name: "Sorting",
  summary: "",
  code: `<Icon icon="icon icon-switch"/>`
};
```

## How to query

You'd be able to query your frontmatter like:

```graphql
{
  allStories {
    nodes {
      story {
        code
        component
        name
        summary
      }
    }
  }
}
```

Which would return something like:

```javascript
{
  "data": {
    "allStories": {
      "nodes": [
        "story": {
          "component": {
            "code": `<Icon icon="icon icon-switch"/>`,
            "name":"Sorting",
            "summary":""
          }
        }
      ]
    }
  }
}
```
