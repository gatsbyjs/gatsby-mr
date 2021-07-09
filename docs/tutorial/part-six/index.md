---
title: Transformer plugins
typora-copy-images-to: ./
disableTableOfContents: true
---

> हे ट्यूटोरियल गॅट्सबीच्या डेटा लेयर बद्दलच्या मालिकेचा एक भाग आहे. आपन हे एर्टिकल काळजीपुरवाक वाचल ही आपेक्षाा [भाग 4](/tutorial/part-four/) आणि [भाग 5](/tutorial/part-five/) येथे सुरू ठेवण्यापूर्वी.

## या ट्यूटोरियल मध्ये काय आहे?

मागील ट्युटोरियलमध्ये स्त्रोत प्लगइन डेटा कसा आणतात हे दर्शविले _into_ गॅटस्बीची डेटा सिस्टम या ट्यूटोरियल मध्ये, आपण ट्रान्सफॉर्मर प्लगइन कसे वापरु शिकू शकाल _transform_ स्त्रोत प्लगइनने आणलेली कच्ची सामग्री. सोर्स प्लगइन्स आणि ट्रान्सफॉर्मर प्लगइन यांचे संयोजन गॅटस्बी साइट तयार करताना आपल्याला आवश्यक असलेले सर्व डेटा सोर्सिंग आणि डेटा ट्रान्सफॉर्मेशन हाताळू शकते.

## ट्रान्सफॉर्मर प्लगइन्स

बर्याचदा, आपल्याला स्त्रोत प्लगइनवरून मिळणार्या डेटाचे स्वरूप आपण आपली वेबसाइट तयार करण्यासाठी वापरू इच्छित नाही.
फाईलसिस्टम स्त्रोत प्लगइन आपल्याला फायलींबद्दल डेटा क्वेरी करू देते परंतु आपण फायलींमध्ये डेटा क्वेरी करू इच्छित असल्यास काय करावे?

हे शक्य करण्यासाठी, Gatsby ट्रान्सफॉर्मर प्लगइनचे समर्थन करते  जे कच्चा डेटा आयत कर्तेचे करतात
स्त्रोत प्लगइन आणि सामग्री सामग्री _transform_ it काहीतरी अधिक वापरण्यायोग्य.

उदाहरणार्थ, मार्कडाउन फायली.मार्कडाऊन लिहिणे चांगले आहे परंतु जेव्हा आपण तयार करता तेव्हा
त्यामध्ये पृष्ठ, आपल्याला मार्कडाउन असणे आवश्यक आहे HTML.

आपल्या साइटवर एक मार्कडाउन फाइल जोडा
`src/pages/sweet-pandas-eating-sweets.md`(हे आपले पहिले मार्कडाउन होईल
ब्लॉग पोस्ट) आणि कसे शिका _transform_ ट्रान्सफॉर्म प्लगइन वापरून HTML आणि
GraphQL.

```markdown:title=src/pages/sweet-pandas-eating-sweets.md
---
title: "Sweet Pandas Eating Sweets"
date: "2017-08-10"
---

Pandas are really sweet.

Here's a video of a panda eating sweets.

<iframe width="560" height="315" src="https://www.youtube.com/embed/4n0xNbfJLR8" frameborder="0" allowfullscreen></iframe>
```

एकदा आपण फाइल जतन केल्यानंतर, पहा `/my-files/` पुन्हा-नवीन मार्कडाउन फाइल आहे
आत टेबल हे Gatsby ची एक अतिशय शक्तिशाली वैशिष्ट्य आहे. पूर्वीसारखे
`siteMetadata` उदाहरण, स्त्रोत प्लगइन थेट डेटा रीलोड करू शकतात.
`gatsby-source-filesystem` नेहमी जोडण्यासाठी आणि जेव्हा नवीन फायलींसाठी स्कॅन करत आहे
ते आहेत, आपल्या क्वेरी पुन्हा चालवा.

ट्रान्सफॉर्म प्लगइन जोडा जे मार्कडाउन फायली बदलू शकते:

```shell
npm install --save gatsby-transformer-remark
```

Then add it to the `gatsby-config.js` like normal:

```javascript:title=gatsby-config.js
module.exports = {
  siteMetadata: {
    title: `Pandas Eating Lots`,
  },
  plugins: [
    {
      resolve: `gatsby-source-filesystem`,
      options: {
        name: `src`,
        path: `${__dirname}/src/`,
      },
    },
    `gatsby-transformer-remark`, // highlight-line
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

रीस्टार्ट development सर्व्हर नंतर रीफ्रेश करा (किंवा पुन्हा उघडा) GraphiQL आणि स्वयंपूर्ण पहा:

![markdown-autocomplete](markdown-autocomplete.png)

Select `allMarkdownRemark` again and run it as you did for `allFile`. You'll
see there the markdown file you recently added. Explore the fields that are
available on the `MarkdownRemark` node.

![markdown-query](markdown-query.png)

ठीक आहे!आशा आहे की, काही मूलभूत गोष्टी ठिकाणी पडू लागतात. Source प्लगइन डेटा आणतात Gatsby च्या डेटा प्रणाली आणि ट्रान्सफॉर्मर प्लगइन कच्ची सामग्री बदलतात
Source प्लगइन द्वारे आणले. ही नमुना सर्व डेटा सोर्सिंग हाताळू शकते
Gatsby साइट तयार करताना डेटा बदलणे आपल्याला आवश्यक असू शकते.

## आपल्या साइटच्या मार्कडाउन फायलींची सूची तयार करा `src/pages/index.js`

आता आपल्याला पुढील पृष्ठावर आपल्या मार्कडाउन फायलींची सूची तयार करावी लागेल.बर्याच ब्लॉग प्रमाणे, आपण प्रत्येक ब्लॉग पोस्टकडे निर्देश करणार्या समोरच्या पृष्ठावरील दुव्यांची सूची समाप्त करू इच्छित आहात.
With GraphQL you can _query_ मार्कडाउन ब्लॉगच्या वर्तमान यादीसाठी
पोस्ट म्हणून आपल्याला स्वतःची सूची मॅन्युअली ठेवण्याची आवश्यकता नाही.

Like with the `src/pages/my-files.js` page, replace `src/pages/index.js` with
the following to add a GraphQL query with some initial HTML and styling.

```jsx:title=src/pages/index.js
import React from "react"
import { graphql } from "gatsby"
import { css } from "@emotion/core"
import { rhythm } from "../utils/typography"
import Layout from "../components/layout"

export default ({ data }) => {
  console.log(data)
  return (
    <Layout>
      <div>
        <h1
          css={css`
            display: inline-block;
            border-bottom: 1px solid;
          `}
        >
          Amazing Pandas Eating Things
        </h1>
        <h4>{data.allMarkdownRemark.totalCount} Posts</h4>
        {data.allMarkdownRemark.edges.map(({ node }) => (
          <div key={node.id}>
            <h3
              css={css`
                margin-bottom: ${rhythm(1 / 4)};
              `}
            >
              {node.frontmatter.title}{" "}
              <span
                css={css`
                  color: #bbb;
                `}
              >
                — {node.frontmatter.date}
              </span>
            </h3>
            <p>{node.excerpt}</p>
          </div>
        ))}
      </div>
    </Layout>
  )
}

export const query = graphql`
  query {
    allMarkdownRemark {
      totalCount
      edges {
        node {
          id
          frontmatter {
            title
            date(formatString: "DD MMMM, YYYY")
          }
          excerpt
        }
      }
    }
  }
`
```

आता पुढील पृष्ठ असे दिसले पाहिजे:

![frontpage](frontpage.png)

परंतु आपला एक ब्लॉग पोस्ट थोडा एकटा दिसत आहे. तर दुसरा एक जोडा
`src/pages/pandas-and-bananas.md`

```markdown:title=src/pages/pandas-and-bananas.md
---
title: "Pandas and Bananas"
date: "2017-08-21"
---

Do Pandas eat bananas? Check out this short video that shows that yes! pandas do
seem to really enjoy bananas!

<iframe width="560" height="315" src="https://www.youtube.com/embed/4SZl1r2O_bY" frameborder="0" allowfullscreen></iframe>
```

![two-posts](two-posts.png)

जे छान दिसते! तारिही… पोस्ट ऑर्डर चुकीचे आहे.

पण हे निराकरण करणे सोपे आहे. काही प्रकारचे कनेक्शन करताना, आपण पास करू शकता
विविध प्रकारच्या वितर्क to GraphQL query. आपण करू शकता `sort` आणि `filter` नोड्स, सेट किती
नोड्स to `skip`, आणि निवडा `limit` किती नोड पुनर्प्राप्ती. ऑपरेटर या शक्तिशाली संच सह,
आपण आवश्यक स्वरूपात आपल्याला पाहिजे असलेले कोणतेही डेटा निवडू शकता.

In your index page's GraphQL query, change `allMarkdownRemark` to
`allMarkdownRemark(sort: { fields: [frontmatter___date], order: DESC })`. टीपः दरम्यान 3 underscores आहेत `frontmatter` आणि `date`._ हे जतन करा आणि क्रमवारी ऑर्डर निश्चित करणे आवश्यक आहे.

GraphiQL उघडण्याचा प्रयत्न करा आणि वेगळ्या प्रकारच्या पर्यायांसह खेळण्याचा प्रयत्न करा. आपण क्रमवारी लावू शकता
`allFile` कनेक्शन सोबत इतर कनेक्शन.

आमच्या क्वेरी ऑपरेटरवर अधिक दस्तऐवजीकरण, अन्वेषण आमचे [GraphQL reference guide.](/docs/graphql-reference/)

## आव्हान

ब्लॉग पोस्ट असलेली एक नवीन पृष्ठ तयार करण्याचा प्रयत्न करा आणि मुख्यपृष्ठावर ब्लॉग पोस्टच्या सूचीमध्ये काय होते ते पहा!

## पुढे काय येत आहे?

हे उत्तम आहे! आपण नुकतीच एक छान अनुक्रमणिका पृष्ठ तयार केले आहे जेथे आपण आपल्या मार्कडाउन फायली क्वेरी करीत आहात
आणि ब्लॉग पोस्ट शीर्षक आणि उतारांची सूची तयार करणे. परंतु आपण फक्त उतार पाहू इच्छित नाही, आपल्याला आपल्या मार्कडाउन फायलींसाठी वास्तविक पृष्ठे पाहिजे आहेत.

आपण react घटक ठेवून पृष्ठे तयार करणे सुरू ठेवू शकता `src/pages`. तथापि, आपण पुढे,
कसे करावे ते शिका _programmatically_ पासून पृष्ठे तयार करा _data_. Gatsby is _not_
बर्याच स्थिर साइट जनरेटरसारख्या फायलींपासून पृष्ठे तयार करण्यासाठी मर्यादित. Gatsby आपल्याला वापरु देते GraphQL आपल्या कथेसाठी _data_ आणि _map_ क्वेरी परिणाम _pages_—all बिल्ड वेळी.
ही खरोखर शक्तिशाली कल्पना आहे. आपण त्याचे परिणाम एक्सप्लोर करत आहात आणि
पुढील ट्युटोरियलमध्ये याचा वापर करण्याचे मार्ग, जेथे आपण ते कसे शिकाल [programmatically create pages from data](/tutorial/part-seven/).
