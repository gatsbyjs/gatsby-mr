---
title: Gatsby Node APIs
description: pages तयार करण्यासारख्या सामान्य वापरासाठी Gatsby बिल्ड प्रक्रियेत वापरल्या जाणार्‍या नोड एपीआयवरील documentation 
jsdoc: ["gatsby/src/utils/api-node-docs.js"]
apiCalls: NodeAPI
---

ग्राफ्स डेटा लेयरमध्ये आपल्या साइटचा डेटा नियंत्रित करण्यासाठी Gatsby प्लगइन आणि साइट बिल्डर्सना बरेच एपीआय देते.

## एसिंक प्लगइन

ऑपरेशन async आपल्या प्लगइन कामगिरी (डिस्क I / O, डेटाबेस प्रवेश, दूरस्थ एपीआय कॉल, इ) आपण एकतर एक वचन परत किंवा कॉल करा 3 युक्तिवाद झाली वापर करणे आवश्यक आहे, तर. Gatsby प्लगइन बरोबर काही API पूर्ण होत तेव्हा काम, प्रथम पूर्ण करण्यासाठी मागील एपीआय आवश्यक माहित असणे आवश्यक आहे. अधिक माहिती साठी [डिबगिंग Async लाइफसायकल] (/docs/debugging-async-lifecycles/) पहा. 

```javascript
// Promise API
exports.createPages = () => {
  return new Promise((resolve, reject) => {
    // do async work
  })
}

// Callback API
exports.createPages = (_, pluginOptions, cb) => {
  // do Async work
  cb()
}
```

जर आपले प्लगइन एसिंक कार्य करत नसेल तर आपण थेट परत येऊ शकता.

## वापर

आपल्या प्रकल्पाचा मूळ मध्ये `gatsby-node.js` नावाची फाइल त्यांना निर्यात करून हे APIs कोणत्याही अंमलबजावणी.
