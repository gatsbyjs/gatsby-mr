---
title: Node API Helpers
description: Documentation on API helpers for creating nodes within Gatsby's GraphQL data layer
jsdoc: ["gatsby/src/utils/api-node-helpers-docs.js"]
apiCalls: NodeAPIHelpers
contentsHeading: Shared helpers
showTopLevelSignatures: true
---

पहिला Argument प्रत्येकाला पास झाला. [Gatsby’s Node APIs](/docs/node-apis/) एक वस्तू आहे containing एक जोड of helpers . Helpers shared by all Gatsby’s Node APIs are दस्तऐवज in [Shared helpers](#shared-helpers) विभाग.

```javascriptc
// in gatsby-node.js
exports.createPages = gatsbyNodeHelpers => {
  const { actions, reporter } = gatsbyNodeHelpers
  // use helpers
}
```

सामान्य convention is to destructure helpers right in argument यादी:

```javascript
// in gatsby-node.js
exports.createPages = ({ actions, reporter }) => {
  // use helpers
}
```

## Note

Some APIs provide additional helpers. For example `createPages` provides `graphql` function. Check documentation of specific APIs in [Gatsby Node APIs](/docs/node-apis/) for details.
