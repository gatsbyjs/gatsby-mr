---
title: Adding a Service Worker/सेवा कामगार जोडत आहे
---

## सर्विस वर्कर्स म्हणजे काय

एक सर्व्हिस वर्कर एक स्क्रिप्ट आहे जी आपला ब्राउझर पार्श्वभूमीवर चालते, वेब पेज पासून ती विभक्त नसते, वेब पेज किंवा वापरकर्त्याच्या संवादाची आवश्यकता नसलेल्या वैशिष्ट्यांसाठी दरवाजा उघडते.थोड़े ख़राब कनेक्शनमध्ये आपल्या साइटची उपलब्धता वाढवतात आणि एक चांगला वापरकर्ता अनुभव तयार करतात.

हे पुश नोटिफिकेशना आणि बैकग्राउंड सिंक यासारख्या वैशिष्ट्यांचे समर्थन करते.

## `gatsby-plugin-offline` च्या बरोबर Gatsby मध्ये service worker चा उपयोग करणे

Gatsby [gatsby-plugin-offline](https://www.npmjs.com/package/gatsby-plugin-offline) मध्ये सर्व्हिस वर्कर तयार करण्यासाठी आणि लोड करण्यासाठी चांगले प्लगइन इंटरफेस प्रदान करते.

आपण या प्लगइन चा उपयोग [manifest plugin](https://www.npmjs.com/package/gatsby-plugin-manifest) सह करू शकता.(मॅनिफेस्ट प्लगइन नंतर ऑफलाइन प्लगइनची सूची निश्चित करा जेणेकरुन मॅनिफेस्ट फाइल सर्व्हिस वर्करमध्ये समाविष्ट केली जाईल).

## `gatsby-plugin-offline` इनस्टॉल करणे

`npm install --save gatsby-plugin-offline`

या प्लगइन ला आपल्या `gatsby-config.js` या मध्ये ऍड करा.

```javascript:title=gatsby-config.js
plugins: [`gatsby-plugin-offline`]
```

## संदर्भ

- [सर्विस वर्कर: एक परिचय](https://developers.google.com/web/fundamentals/primers/service-workers/)
- [सर्विस वर्कर API](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)
