---
title: Node Model
description: Documentation explaining the model of nodes in Gatsby's GraphQL data layer
jsdoc: ["gatsby/src/schema/node-model.js"]
apiCalls: NodeModel
contentsHeading: Methods
---

Gatsby ने त्याचे अंतर्गत data store आणि query capabilities चे प्रदर्शन GraphQL field resolvers `context.nodeModel` वर केले अहे. 


## उदाहरणार्थ 

```javascript:title=gatsby-node.js
createResolvers({
  Query: {
    mood: {
      type: `String`,
      resolve(source, args, context, info) {
        const coffee = context.nodeModel.getAllNodes({ type: `Coffee` })
        if (!coffee.length) {
          return 😞
        }
        return 😊
      },
    },
  },
})
```
