---
title: Data in Gatsby
typora-copy-images-to: ./
disableTableOfContents: true
---ट्यूटोरियल च्या चार भाग आपले स्वागत आहे! अर्ध्या मार्गाने! आशा आहे की गोष्टी सुरू होत आहेत
खूप आरामदायक वाटत

## Recap of the first half of the tutorial

आतापर्यंत, आपण React.js कसे वापरावे हे शिकत आहात - हे करण्यास सक्षम असणे किती शक्तिशाली आहे
वेबसाइटसाठी सानुकूल बिल्डिंग ब्लॉक्स म्हणून कार्य करण्यासाठी आपले _ डाउन_ घटक तयार करा.

आपण CSS मॉड्यूल्स वापरुन स्टाईलिंग घटकांचे देखील शोध लावले आहेत.

## What's in this tutorial?

पुढील चार ट्यूटोरियलमध्ये (यासह), आपण गॅटस्बी डेटा लेयरमध्ये गोती घेत असाल, जे गॅटस्बीचे एक वैशिष्ट्यपूर्ण वैशिष्ट्य आहे जे आपल्याला मार्कडाउन, वर्डप्रेस, हेडलेस सीएमएस आणि इतर डेटा स्रोतांमधून सहजपणे साइट तयार करू देते. सर्व फ्लेवर्सचा.

**NOTE:** गॅटस्बीचा डेटा स्तर ग्राफिक द्वारा समर्थित आहे. सखोल ट्यूटोरियल साठी
आलेख, आम्ही शिफारस करतो [ग्राफिक कसे करावे] (https://www.howtographicql.com/).

## Data in Gatsby

वेबसाइटचे चार भाग आहेत: एचटीएमएल, सीएसएस, जेएस आणि डेटा. पहिल्या सहामाहीत
पहिल्या तीनवर लक्ष केंद्रित केले. आता गॅटस्बी मधील डेटा कसा वापरायचा ते पाहू
साइट.

**What is data?**

संगणकाच्या विज्ञान शास्त्राचे उत्तर असे असेलः डेटा म्हणजे `" तार "things,
पूर्णांक (`42`), ऑब्जेक्ट्स (` {पिझ्झा: खरे} `), इ.

गॅटस्बीमध्ये काम करण्याच्या उद्देशाने, तथापि, अधिक उपयुक्त उत्तर आहे
"रिएक्ट घटकाच्या बाहेर राहणारी प्रत्येक गोष्ट".

आतापर्यंत, आपण मजकूर लिहित आहात आणि घटकांमध्ये_निर्देशित_ प्रतिमा जोडत आहात.
बर्‍याच वेबसाइट्स बनविण्याचा हा एक एक्सेलेंट_ मार्ग आहे. परंतु, बर्‍याचदा आपण संचयित करू इच्छिता
डेटा _outside_ घटक आणि नंतर घटक _ डेटा _ घटक म्हणून आणा
आवश्यक

आपण वर्डप्रेससह साइट तयार करत असल्यास (जेणेकरून इतर योगदानकर्ते)
सामग्री जोडण्यासाठी आणि देखरेखीसाठी एक चांगला इंटरफेस आहे) आणि गॅटस्बी, _डेटा_
साइटसाठी (पृष्ठे आणि पोस्ट) वर्डप्रेसमध्ये आहेत आणि आपण तो डेटा _ पुल _ करा
आवश्यक, आपल्या घटकांमध्ये.

डेटा फाईल प्रकारात मार्कडाउन, सीएसव्ही इत्यादी तसेच डेटाबेसमध्येही राहू शकतो
आणि सर्व प्रकारच्या एपीआय.

** गॅटस्बीचा डेटा स्तर आपल्याला यावरून (आणि इतर कोणताही स्रोत) डेटा खेचू देतो
थेट आपल्या घटकांमध्ये ** - आपल्याला पाहिजे असलेल्या आकार आणि फॉर्ममध्ये.

## Using Unstructured Data vs GraphQL

### Do I have to use GraphQL and source plugins to pull data into Gatsby sites?

नक्कीच नाही! आपण ग्राफिक्स डेटा लेयरऐवजी गॅट्सबी पृष्ठांवर थेट अप्रबंधित डेटा खेचण्यासाठी नोड `क्रिएटपेजेस` एपीआय वापरू शकता. छोट्या साइटसाठी ही एक चांगली निवड आहे, तर ग्राफिक्यूएल आणि सोर्स प्लगइन अधिक जटिल साइटसह वेळ वाचविण्यात मदत करू शकतात.

नोड `क्रिएटपेजेस` एपीआय वापरुन आपल्या गॅटस्बी साइटमध्ये डेटा कसा काढायचा आणि एखादी उदाहरण साइट पहाण्यासाठी शिकण्यासाठी [ग्राफिक्सशिवाय गॅटस्बी वापरणे] (/ डॉक्स / वापरणे-गॅट्सबी-विना-ग्राफिकएल /) मार्गदर्शक पहा!

### When do I use unstructured data vs GraphQL?

आपण एखादी छोटी साइट तयार करत असल्यास, त्यास तयार करण्याचा एक प्रभावी मार्ग म्हणजे `क्रिएटपेजेस` एपीआय वापरुन या मार्गदर्शकात नमूद केल्यानुसार अ-संरचित डेटा खेचणे आणि नंतर जर साइट नंतर अधिक जटिल झाली तर आपण आणखी इमारतीकडे जा जटिल साइट किंवा आपण आपला डेटा बदलू इच्छित असाल तर या चरणांचे अनुसरण करा:
1. आपण वापरू इच्छित असलेले स्त्रोत प्लगइन आणि / किंवा ट्रान्सफॉर्मर प्लगइन आधीपासून विद्यमान आहेत किंवा नाही हे पाहण्यासाठी [प्लगइन लायब्ररी] (/ प्लगइन /) पहा.
२. ते अस्तित्वात नसल्यास, [प्लगिन प्रमाणीकरण] (/ डॉक्स / तयार करणे-प्लगइन /) मार्गदर्शक वाचा आणि आपल्या स्वतःच्या इमारतीचा विचार करा!

### How Gatsby's data layer uses GraphQL to pull data into components

रीएक्ट घटकांमध्ये डेटा लोड करण्यासाठी बरेच पर्याय आहेत. सर्वात एक
यापैकी लोकप्रिय आणि शक्तिशाली असे तंत्रज्ञान म्हटले जाते
[ग्राफिकल] (https://ographicql.org/).

उत्पादन अभियंत्यांना आवश्यक असलेल्या डेटामध्ये _पुल_ करण्यात मदत करण्यासाठी ग्राफिकचा शोध फेसबुकवर लागला होता
घटक.

आलेख एक ** क्यू ** उरी ** एल ** इंग्रजी (त्याच्या नावाचा _क्यूएल_अ भाग) आहे. जर तुम्ही असाल
एसक्यूएलशी परिचित, हे अगदी अशाच प्रकारे कार्य करते. विशेष वाक्यरचना वापरुन, आपण वर्णन करा
आपल्याला आपल्या घटकामध्ये हवा असलेला डेटा आणि नंतर तो डेटा दिला जातो
तुला.

घटकांना आवश्यक असलेला डेटा घोषित करण्यासाठी घटक सक्षम करण्यासाठी गॅटस्बी ग्राफिकल वापरते.

## Create a new example site

ट्यूटोरियलच्या या भागासाठी आणखी एक नवीन साइट तयार करा. आपण "पांडास खाण्याचे बरेच" नावाचा एक मार्कडाउन ब्लॉग तयार करणार आहात. पांडे भरपूर खाल्ले जाणारे सर्वोत्कृष्ट चित्रे आणि व्हिडिओ दाखविण्यासाठी हे समर्पित आहे. मार्गावर, आपण ग्राफिकल आणि गॅटस्बीच्या मार्कडाउन समर्थनात आपले बोट बुडवाल.

एक नवीन टर्मिनल विंडो उघडा आणि `ट्यूटोरियल-भाग-चार called नावाच्या निर्देशिकेत नवीन गॅटस्बी साइट तयार करण्यासाठी पुढील आज्ञा चालवा. नंतर नवीन निर्देशिका वर नॅव्हिगेट करा:

```shell
gatsby new tutorial-part-four https://github.com/gatsbyjs/gatsby-starter-hello-world
cd tutorial-part-four
```

नंतर प्रोजेक्टच्या मुळाशी काही इतर आवश्यक अवलंबन स्थापित करा. आपण टाइपोग्राफी थीम वापरू
"Kirkham", आणि आपण प्रयत्न कराल CSS-in-JS library, ["Emotion"](https://emotion.sh/):

```shell
npm install --save gatsby-plugin-typography typography react-typography typography-theme-kirkham gatsby-plugin-emotion @emotion/core
```

आपण ज्यात संपले त्यासारखी साइट सेट करा[Part Three](/tutorial/part-three). या साइटमध्ये लेआउट घटक आणि दोन पृष्ठ घटक असतील:

```jsx:title=src/components/layout.js
import React from "react"
import { css } from "@emotion/core"
import { Link } from "gatsby"

import { rhythm } from "../utils/typography"

export default ({ children }) => (
  <div
    css={css`
      margin: 0 auto;
      max-width: 700px;
      padding: ${rhythm(2)};
      padding-top: ${rhythm(1.5)};
    `}
  >
    <Link to={`/`}>
      <h3
        css={css`
          margin-bottom: ${rhythm(2)};
          display: inline-block;
          font-style: normal;
        `}
      >
        Pandas Eating Lots
      </h3>
    </Link>
    <Link
      to={`/about/`}
      css={css`
        float: right;
      `}
    >
      About
    </Link>
    {children}
  </div>
)
```

```jsx:title=src/pages/index.js
import React from "react"
import Layout from "../components/layout"

export default () => (
  <Layout>
    <h1>Amazing Pandas Eating Things</h1>
    <div>
      <img
        src="https://2.bp.blogspot.com/-BMP2l6Hwvp4/TiAxeGx4CTI/AAAAAAAAD_M/XlC_mY3SoEw/s1600/panda-group-eating-bamboo.jpg"
        alt="Group of pandas eating bamboo"
      />
    </div>
  </Layout>
)
```

```jsx:title=src/pages/about.js
import React from "react"
import Layout from "../components/layout"

export default () => (
  <Layout>
    <h1>About Pandas Eating Lots</h1>
    <p>
      We're the only site running on your computer dedicated to showing the best
      photos and videos of pandas eating lots of food.
    </p>
  </Layout>
)
```

```javascript:title=src/utils/typography.js
import Typography from "typography"
import kirkhamTheme from "typography-theme-kirkham"

const typography = new Typography(kirkhamTheme)

export default typography
export const rhythm = typography.rhythm
```

`gatsby-config.js` (must be in the root of your project, not under src)

```javascript:title=gatsby-config.js
module.exports = {
  plugins: [
    `gatsby-plugin-emotion`,
    {
      resolve: `gatsby-plugin-typography`,
      options: {
        pathToConfigModule: `src/utils/typography`,
      },
    },
  ],
}
```

Add the above files and then run `gatsby develop`, per usual, and you should see the following:

![start](start.png)

You have another small site with a layout and two pages.

Now you can start querying 😋

## Your first GraphQL query

When building sites, you'll probably want to reuse common bits of data -- like the _site title_ for example. Look at the `/about/` page. You'll notice that you have the site title (`Pandas Eating Lots`) in both the layout component (the site header) as well as in the `<h1 />` of the `about.js` page (the page header).

But what if you want to change the site title in the future? You'd have to search for the title across all your components and edit each instance. This is both cumbersome and error-prone, especially for larger, more complex sites. Instead, you can store the title in one location and reference that location from other files; change the title in a single place, and Gatsby will _pull_ your updated title into files that reference it.

The place for these common bits of data is the `siteMetadata` object in the `gatsby-config.js` file. Add your site title to the `gatsby-config.js` file:

```javascript:title=gatsby-config.js
module.exports = {
  // highlight-start
  siteMetadata: {
    title: `Title from siteMetadata`,
  },
  // highlight-end
  plugins: [
    `gatsby-plugin-emotion`,
    {
      resolve: `gatsby-plugin-typography`,
      options: {
        pathToConfigModule: `src/utils/typography`,
      },
    },
  ],
}
```

Restart the development server.

### Use a page query

Now the site title is available to be queried; Add it to the `about.js` file using a [page query](/docs/page-query):

```jsx:title=src/pages/about.js
import React from "react"
import { graphql } from "gatsby" // highlight-line
import Layout from "../components/layout"

// highlight-next-line
export default ({ data }) => (
  <Layout>
    <h1>About {data.site.siteMetadata.title}</h1> {/* highlight-line */}
    <p>
      We're the only site running on your computer dedicated to showing the best
      photos and videos of pandas eating lots of food.
    </p>
  </Layout>
)

// highlight-start
export const query = graphql`
  query {
    site {
      siteMetadata {
        title
      }
    }
  }
`
// highlight-end
```

It worked! 🎉

![Page title pulling from siteMetadata](site-metadata-title.png)

The basic GraphQL query that retrieves the `title` in your `about.js` changes above is:

```graphql:title=src/pages/about.js
{
  site {
    siteMetadata {
      title
    }
  }
}
```

> 💡 In [part five](/tutorial/part-five/#introducing-graphiql), you'll meet a tool that lets us interactively explore the data available through GraphQL, and help formulate queries like the one above.

Page queries live outside of the component definition -- by convention at the end of a page component file -- and are only available on page components.

### Use a StaticQuery

[StaticQuery](/docs/static-query/) is a new API introduced in Gatsby v2 that allows non-page components (like your `layout.js` component), to retrieve data via GraphQL queries.
Let's use its newly introduced hook version — [`useStaticQuery`](/docs/use-static-query/).

Go ahead and make some changes to your `src/components/layout.js` file to use the `useStaticQuery` hook and a `{data.site.siteMetadata.title}` reference that uses this data. When you are done, your file will look like this:

```jsx:title=src/components/layout.js
import React from "react"
import { css } from "@emotion/core"
// highlight-next-line
import { useStaticQuery, Link, graphql } from "gatsby"

import { rhythm } from "../utils/typography"
// highlight-start
export default ({ children }) => {
  const data = useStaticQuery(
    graphql`
      query {
        site {
          siteMetadata {
            title
          }
        }
      }
    `
  )
  return (
    // highlight-end
    <div
      css={css`
        margin: 0 auto;
        max-width: 700px;
        padding: ${rhythm(2)};
        padding-top: ${rhythm(1.5)};
      `}
    >
      <Link to={`/`}>
        <h3
          css={css`
            margin-bottom: ${rhythm(2)};
            display: inline-block;
            font-style: normal;
          `}
        >
          {data.site.siteMetadata.title} {/* highlight-line */}
        </h3>
      </Link>
      <Link
        to={`/about/`}
        css={css`
          float: right;
        `}
      >
        About
      </Link>
      {children}
    </div>
    // highlight-start
  )
}
// highlight-end
```

Another success! 🎉

![Page title and layout title both pulling from siteMetadata](site-metadata-two-titles.png)

Why use two different queries here? These examples were quick introductions to
the query types, how they are formatted, and where they can be used. For now,
keep in mind that only pages can make page queries. Non-page components, such as
Layout, can use StaticQuery. [Part 7](/tutorial/part-seven/) of the tutorial explains these in greater
depth.

But let's restore the real title.

One of the core principles of Gatsby is that _creators need an immediate connection to what they're creating_ ([hat tip to Bret Victor](http://blog.ezyang.com/2012/02/transcript-of-inventing-on-principle/)). In other words, when you make any change to code you should immediately see the effect of that change. You manipulate an input of Gatsby and you see the new output showing up on the screen.

So almost everywhere, changes you make will immediately take effect. Edit the `gatsby-config.js` file again, this time changing the `title` back to "Pandas Eating Lots". The change should show up very quickly in your site pages.

![Both titles say Pandas Eating Lots](pandas-eating-lots-titles.png)

## What's coming next?

Next, you'll be learning about how to pull data into your Gatsby site using
GraphQL with source plugins in [part five](/tutorial/part-five/) of the
tutorial.
