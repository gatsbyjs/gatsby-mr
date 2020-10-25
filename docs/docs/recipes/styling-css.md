---
title: "Recipes: Styling with CSS"
tableOfContentsDepth: 1
---

आपल्या वेबसाइटवर शैली जोडण्याचे बरेच मार्ग आहेत; अधिकृत आणि समुदाय प्लगइनद्वारे गॅट्सबी जवळजवळ प्रत्येक संभाव्य पर्यायाचे समर्थन करते.

## global CSS फायल विना वापरण्यासाठी

### पूर्व शर्ती

- [Gatsby site](/docs/quick-start/) index page component
- `gatsby-browser.js` फाईल

### दिशानिर्देश

1. global CSS फाईल म्हणून src/styles/global.css तयार करा आणि खालील फाईलमध्ये पेस्ट करा :

```css:title=src/styles/global.css
html {
  background-color: lavenderblush;
}

p {
  color: maroon;
}
```

2. आयात करा global CSS file मध्ये `gatsby-browser.js` खालील प्रमाणे फाइल करा:

```javascript:title=gatsby-browser.js
import "./src/styles/global.css"
```

> **टीप:** आपण याचा वापर देखील करू शकता `require('./src/styles/global.css')` आयात करण्यासाठी global CSS file आपल्या मध्ये `gatsby-config.js` फाईल.

3. चालवा `gatsby-develop` देखणे global styling आपल्या वेबसाइटवर लागू केले जात आहे.

> **टीप:** आपण आपल्या साइटच्या स्टाईलसाठी सीएसएस-इन-जेएस वापरत असल्यास हा दृष्टिकोन सर्वात योग्य नाही, अशा परिस्थितीत सर्व सामायिक घटकांसह लेआउट पृष्ठ वापरावे. हे पुढील कृती मध्ये समाविष्ट आहे.

### अतिरिक्त संसाधने

- अजून [adding global styles without a layout component](/docs/global-css/#adding-global-styles-without-a-layout-component)

## वापरत आहे global styles आत मधॆ layout component

### पूर्व शर्ती

- विद्यमान [Gatsby site](/docs/quick-start/) सह index page component

### दिशानिर्देश

आपण जोडू शकता global styles एक [shared layout component](/tutorial/part-three/#your-first-layout-component). हा घटक हेडर किंवा फूटर सारख्या साइटवर सामान्य असलेल्या गोष्टींसाठी वापरला जातो.

1. आपल्याकडे आधीपासूनच एक नसल्यास, आपल्या वेबसाइटवर एक नवीन निर्देशिका तयार करा `/src/components`.

2. घटकांच्या निर्देशिकेत दोन फाईल्स तयार करा. `layout.css` आणि `layout.js`.

3. खालील गोष्टी जोडा `layout.css`:

```css:title=/src/components/layout.css
body {
  background: red;
}
```

4. सुधारणे `layout.js` आयात करण्यासाठी CSS file आणि output layout markup:

```jsx:title=/src/components/layout.js
import React from "react"
import "./layout.css"

export default ({ children }) => <div>{children}</div>
```

5. आता आपल्या वेबसाइटचे मुख्यपृष्ठ येथे संपादित करा `/src/pages/index.js` आणि नवीन वापरा layout component:

```jsx:title=/src/pages/index.js
import React from "react"
import Layout from "../components/layout"

export default () => <Layout>Hello world!</Layout>
```

### अतिरिक्त संसाधने

- [मानक स्टीलिंग Global CSS Files](/docs/global-css/)
- [बद्दल अधिक layout components](/tutorial/part-three)

## वापरत आहे Styled Components

### पूर्व शर्ती

- विद्यमान [Gatsby site](/docs/quick-start/) सह index page component
- [gatsby-plugin-styled-components, styled-components, and babel-plugin-styled-components](/packages/gatsby-plugin-styled-components/) मध्ये स्थापित `package.json`

### दिशानिर्देश

1. आत आपल्या `gatsby-config.js` फाइल जोडा `gatsby-plugin-styled-components`

```javascript:title=gatsby-config.js
module.exports = {
  plugins: [`gatsby-plugin-styled-components`],
}
```

2. अनुक्रमणिका पृष्ठ घटक उघडा (`src/pages/index.js`) आणि आयात करा `styled-components` पॅकेज

3. प्रत्येक घटक प्रकारासाठी स्टाईल ब्लॉक तयार करुन घटकांचे शैली

4. जेएसएक्समध्ये शैलीकृत घटक समाविष्ट करून पृष्ठावर अर्ज करा

```jsx:title=src/pages/index.js
import React from "react"
import styled from "styled-components" //highlight-line

const Container = styled.div`
  margin: 3rem auto;
  max-width: 600px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
`

const Avatar = styled.img`
  flex: 0 0 96px;
  width: 96px;
  height: 96px;
  margin: 0;
`

const Username = styled.h2`
  margin: 0 0 12px 0;
  padding: 0;
`

const User = (props) => (
  <>
    <Avatar src={props.avatar} alt={props.username} />
    <Username>{props.username}</Username>
  </>
)

export default () => (
  <Container>
    <h1>About Styled Components</h1>
    <p>Styled Components is cool</p>
    <User
      username="Jane Doe"
      avatar="https://s3.amazonaws.com/uifaces/faces/twitter/adellecharles/128.jpg"
    />
    <User
      username="Bob Smith"
      avatar="https://s3.amazonaws.com/uifaces/faces/twitter/vladarbatov/128.jpg"
    />
  </Container>
)
```

4. चालवा `gatsby develop` बदल पाहण्यासाठी

### अतिरिक्त संसाधने

- [वापरण्याबद्दल अधिक Styled Components](/docs/styled-components/)
- [Egghead पाठ](https://egghead.io/lessons/gatsby-style-gatsby-sites-with-styled-components)

## वापरत आहे CSS Modules

### पूर्व शर्ती

- विद्यमान [Gatsby site](/docs/quick-start/) एक सह index page component

### दिशानिर्देश

1. तयार CSS module `src/pages/index.module.css` आणि मॉड्यूलमध्ये खालील पेस्ट करा:

```css:title=src/pages/index.module.css
.feature {
  margin: 2rem auto;
  max-width: 500px;
}
```

2. जेएसएक्स ऑब्जेक्ट म्हणून सीएसएस मॉड्यूल आयात करा `style` मध्ये `index.js` पृष्ठ सुधारित करून फाईल करा जेणेकरून ते पुढीलप्रमाणे दिसते:

```jsx:title=src/pages/index.js
import React from "react"

// highlight-start
import style from "./index.module.css"

export default () => (
  <section className={style.feature}>
    <h1>Using CSS Modules</h1>
  </section>
)
// highlight-end
```

3. चालवा `gatsby develop` बदल पहा.

**Note:**
फाईल एक्सटेंशन असल्याचे लक्षात घ्या `.module.css` त्याऐवजी `.css`,जी गॅटस्बीला सांगते की हे सीएसएस मॉड्यूल आहे.

### अतिरिक्त संसाधने

- अजून [वापरत आहे CSS Modules](/tutorial/part-two/#css-modules)
- [वापरण्यावर थेट उदाहरण CSS modules](https://github.com/gatsbyjs/gatsby/blob/master/examples/using-css-modules)

## वापरत आहे Sass/SCSS

सस म्हणजे सीएसएसचा विस्तार आहे जो आपल्याला नेस्टेड नियम, चल, मिक्सिन आणि बरेच काही यासारख्या प्रगत वैशिष्ट्यांसह देतो.

ससकडे 2 वाक्यरचना आहेत. सर्वात सामान्यपणे वापरलेला वाक्यरचना "एससीएसएस" आहे आणि तो सीएसएसचा सुपरसेट आहे. म्हणजेच सर्व वैध सीएसएस वाक्यरचना, वैध एससीएसएस वाक्यरचना आहे. एससीएसएस फायली विस्तार वापरतात `.scss`

Sass संकलित करेल `.scss` आणि `.sass` मैत्रिणी `.css`
आपल्यासाठी फायली, जेणेकरून आपण आपल्या स्टाईलशीट अधिक प्रगत वैशिष्ट्यांसह लिहू शकता.

### पूर्व शर्ती

- [Gatsby site](/docs/quick-start/).

### दिशानिर्देश

1. गॅट्सबी प्लगइन स्थापित करा [gatsby-plugin-sass](https://www.gatsbyjs.org/packages/gatsby-plugin-sass/) आणि `node-sass`.

`npm install --save node-sass gatsby-plugin-sass`

2. आपल्यामध्ये प्लगइन समाविष्ट करा `gatsby-config.js` फाईल.

```javascript:title=gatsby-config.js
plugins: [`gatsby-plugin-sass`],
```

3. आपली स्टाईलशीट `.sass` किंवा` .scss` फायली म्हणून लिहा आणि त्या आयात करा. आपल्याला शैली कशी आयात करावीत हे माहित नसल्यास एक कटाक्ष टाका [Styling with CSS](/docs/recipes/#2-styling-with-css)

```css:title=styles.scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}
```

```css:title=styles.sass
$font-stack:    Helvetica, sans-serif
$primary-color: #333

body
  font: 100% $font-stack
  color: $primary-color
```

```javascript
import "./styles.scss"
import "./styles.sass"
```

_नोट: आपण सीएसएस मॉड्यूलविषयी पूर्वीच्या रेसिपीमध्ये नमूद केल्याप्रमाणे, सेस / एससीएसएस फायली मॉड्यूल म्हणून देखील वापरू शकता, difference .css`ऐवजी विस्तार`.scss` किंवा` .sass`_ असावेत.

### अतिरिक्त संसाधने

- [.Sass आणि .scss मधील फरक](https://responsivedesign.is/articles/difference-between-sass-and-scss/)
- [अधिकृत Sass वेबसाइटवरील सस मार्गदर्शक](https://sass-lang.com/guide)
- [काही अधिक स्पष्टीकरण आणि अधिक संसाधनांसह ससवरील अधिक संपूर्ण इन्स्टॉलेशन ट्यूटोरियल](https://www.gatsbyjs.org/docs/sass/)

## स्थानिक फॉन्ट जोडणे

### पूर्व शर्ती

- [Gatsby site](/docs/quick-start/)
- एक फाँट फाइल: `.woff2`, `.ttf`, इ.

### दिशानिर्देश

1. आपल्या गॅटस्बी प्रोजेक्टमध्ये फॉन्ट फाईल कॉपी करा, जसे की `src/fonts/fontname.woff2`.

```text
src/fonts/fontname.woff2
```

2. फॉन्ट मालमत्ता आपल्या गॅटस्बी साइटमध्ये बंडल करण्यासाठी सीएसएस फाईलमध्ये आयात करा:

```css:title=src/css/typography.css
@font-face {
  font-family: "Font Name";
  src: url("../fonts/fontname.woff2");
}
```

**टीप:** संबंधित सीएसएसवरून फॉन्टचे नाव संदर्भित असल्याचे सुनिश्चित करा.:

```css:title=src/components/layout.css
body {
  font-family: "Font Name", sans-serif;
}
```

एचटीएमएल `बॉडी` घटकांना लक्ष्य करून, आपला फॉन्ट पृष्ठावरील बर्‍याच मजकूरावर लागू होईल. अतिरिक्त सीएसएस इतर घटकांना लक्ष्य करू शकते, जसे की are बटण`किंवा`मजकूर.

फॉन्ट वरील चरणांचे अद्यतनित करीत नसल्यास संबंधित सीएसएसमध्ये विद्यमान फॉन्ट-कुटूंब पुनर्स्थित करणे सुनिश्चित करा.

### अतिरिक्त संसाधने

- अजून [फायलींमध्ये मालमत्ता आयात करीत आहे](/docs/importing-assets-into-files/)

## वापरत आहे Emotion

[Emotion](https://emotion.sh) एक शक्तिशाली सीएसएस-इन-जेएस लायब्ररी आहे जे इनलाइन सीएसएस शैली आणि स्टाईल केलेल्या घटकांना समर्थन देते. आपण प्रत्येक स्टाईलिंग वैशिष्ट्य स्वतंत्रपणे किंवा त्याच फाईलमध्ये एकत्र वापरू शकता.

### पूर्व शर्ती

- [Gatsby site](/docs/quick-start)

### पूर्व शर्ती

1. स्थापित करा [Gatsby Emotion plugin](/packages/gatsby-plugin-emotion/) आणि Emotion packages.

```shell
npm install --save gatsby-plugin-emotion @emotion/core @emotion/styled
```

2. जोडा `gatsby-plugin-emotion` आपल्या प्लगइन `gatsby-config.js` फाईल:

```javascript:title=gatsby-config.js
module.exports = {
  plugins: [`gatsby-plugin-emotion`],
}
```

3. आपल्याकडे आधीपासूनच एक नसल्यास, आपल्या गॅटस्बी साइटवर एक पृष्ठ तयार करा `src/pages/emotion-sample.js`.

भावनांचे `css` कोर पॅकेज आयात करा. त्यानंतर आपण जोडण्यासाठी `css` प्रॉप वापरू शकता [Emotion object styles](https://emotion.sh/docs/object-styles)
घटकांमधील कोणत्याही घटकास:

```jsx:title=src/pages/emotion-sample.js
import React from "react"
import { css } from "@emotion/core"

export default () => (
  <div>
    <p
      css={{
        background: "pink",
        color: "blue",
      }}
    >
      This page is using Emotion.
    </p>
  </div>
)
```

4. वापरणे Emotion's [styled components](https://emotion.sh/docs/styled),पॅकेज आयात करा आणि त्यांना `स्टाईलड फंक्शनचा वापर करून परिभाषित करा.

```jsx:title=src/pages/emotion-sample.js
import React from "react"
import styled from "@emotion/styled"

const Content = styled.div`
  text-align: center;
  margin-top: 10px;
  p {
    font-weight: bold;
  }
`

export default () => (
  <Content>
    <p>This page is using Emotion.</p>
  </Content>
)
```

### अतिरिक्त संसाधने

- [गॅटस्बी मध्ये Emotion वापरणे](/docs/emotion/)
- [Emotion website](https://emotion.sh)
- [भावना आणि गॅटस्बीसह प्रारंभ करणे](https://egghead.io/lessons/gatsby-getting-started-with-emotion-and-gatsby)

## गूगल फॉन्ट वापरणे

आपले स्वतःचे होस्टिंग [Google Fonts](https://fonts.google.com/)
प्रोजेक्ट अंतर्गत स्थानिक अर्थ म्हणजे आपली साइट लोड होते तेव्हा ते नेटवर्कवर आणणे आवश्यक नसते, डेस्कटॉपवर आपल्या साइटची गती निर्देशांक ~ 300 मिलीसेकंद आणि 3 जी वर 1+ सेकंदाने वाढवते. केवळ कार्यप्रदर्शनासाठी सानुकूल फॉन्ट वापर मर्यादित ठेवण्याची देखील शिफारस केली जाते.

### पूर्व शर्ती

- [Gatsby site](/docs/quick-start)
- [Gatsby CLI](/docs/gatsby-cli/)
- वरून फॉन्ट पॅकेज निवडत आहे [the typefaces project](https://github.com/KyleAMathews/typefaces)

### दिशानिर्देश

1. चालवा `npm install --save typeface-your-chosen-font`, बदलत आहे `your-chosen-font` आपण स्थापित करू इच्छित फॉन्टच्या नावासह [the typefaces project](https://github.com/KyleAMathews/typefaces).

लोकप्रिय 'सोर्स सॅन्स प्रो' फॉन्ट लोड करण्याचे उदाहरणः
`npm install --save typeface-source-sans-pro`.

2. जोडा `import "typeface-your-chosen-font"` लेआउट टेम्पलेट, पृष्ठ घटक किंवा वर `gatsby-browser.js`.

```jsx:title=src/components/layout.js
import "typeface-your-chosen-font"
```

3. एकदा ते आयात झाल्यानंतर आपण सीएसएस स्टाईलशीट, सीएसएस मॉड्यूल किंवा सीएसएस इन-जेएस मधील फॉन्ट नावाचा संदर्भ घेऊ शकता.

```css:title=src/components/layout.css
body {
  font-family: "Your Chosen Font";
}
```

_नोट: तर वरील उदाहरणांसाठी, संबंधित सीएसएस घोषणापत्र असेल `font-family: 'Source Sans Pro';`_

### अतिरिक्त संसाधने

- [Typography.js](/docs/typography-js/) - गॅटस्बी साइटवर गूगल फॉन्ट वापरण्यासाठी दुसरा पर्याय

- [The Typefaces Project Docs](https://github.com/KyleAMathews/typefaces/blob/master/README.md)
- [Live example on Kyle Mathews' blog](https://www.bricolage.io/typefaces-easiest-way-to-self-host-fonts/)

## वापरत आहे Font Awesome

वापरत आहे [Font Awesome](https://fontawesome.com/) आपल्या साइटवरील वापरासाठी आपल्याला हजारो चिन्हांमध्ये प्रवेश देते. गॅटस्बी साइट प्रतिक्रिया साइट असल्याने, वापरण्याची शिफारस केली जाते [react-fontawesome](https://github.com/FortAwesome/react-fontawesome) SVG ग्रंथालय.

### पूर्व शर्ती

- [Gatsby CLI](/docs/gatsby-cli/)
- [Gatsby site](/docs/quick-start)

### दिशानिर्देश

1. स्थापित करा `react-fontawesome` dependencies.

```shell
npm install @fortawesome/fontawesome-svg-core  @fortawesome/free-brands-svg-icons @fortawesome/react-fontawesome
```

> Note that there are multiple icon libraries within `react-fontawesome`. You may also be interested in `free-regular-svg-icons` and `free-solid-svg-icons` which you would install the same way.

2. आयात करा `FontAwesomeIcon` घटक आणि आपण वापरू इच्छित चिन्ह. त्यानंतर आपल्या जेएसएक्स फायलींमध्ये घटक म्हणून चिन्हाचा थेट वापर करा:

```jsx:title=index.js
import { FontAwesomeIcon } from "@fortawesome/react-fontawesome"
import { faReact } from "@fortawesome/free-brands-svg-icons"

const IndexPage = () => (
  <Layout>
    <FontAwesomeIcon icon={faReact} /> //highlight-line
  </Layout>
)

export default IndexPage
```

> हे उदाहरण एकल, विशिष्ट चिन्ह आयात करते आणि सुधारित कामगिरीसाठी वापरते. एक पर्याय म्हणून, आपण हे करू शकता [import the icons and build a library](https://github.com/FortAwesome/react-fontawesome#build-a-library-to-reference-icons-throughout-your-app-more-conveniently).

### अतिरिक्त संसाधने

- [Font Awesome](https://fontawesome.com/)
- [react-fontawesome](https://github.com/FortAwesome/react-fontawesome)
