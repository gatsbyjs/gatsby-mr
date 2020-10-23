---
title: Node Model
description: Gatsby's ग्राफक्यूएल डेटा लेयरमधील नोड्सचे मॉडेल स्पष्ट करणारे दस्तऐवजीकरण
jsdoc: ["gatsby/src/schema/node-model.js"]
apiCalls: NodeModel
contentsHeading: Methods
---

Gatsby त्याचे अंतर्गत डेटा स्टोअर आणि क्वेरी क्षमता `context.node Model` वर ग्राफक्यूएल फील्ड रेझोलॉवरवर उघडकीस आणल्या.

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
