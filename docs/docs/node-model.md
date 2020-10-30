---
title: Node Model
description: Gatsby's GraphQL डेटा लेयरमधील नोड्सचे मॉडेल स्पष्ट करणारे दस्तऐवजीकरण
jsdoc: ["gatsby/src/schema/node-model.js"]
apiCalls: NodeModel
contentsHeading: Methods
---

Gatsby `context.nodeModel` वर GraphQL क्षेत्रात निराकरणकर्ता त्याच्या अंतर्गत डेटा संचयित आणि क्वेरी क्षमता पोहचवतो.

## वापर उदाहरणे

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
