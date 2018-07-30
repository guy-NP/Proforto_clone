# Developer Handover Package
This package documents instructions for developers to implement Google Tag Manager (GTM) and its accompanied information object: dataLayer. The data layer contains all the information that you want to pass to GTM. Please follow this [link](https://developers.google.com/tag-manager/devguide) for the official documentation about details of implementing GTM.

## Package content

1. Plan hand-over moment
2. This developers package on GitHub
3. Solution Design Reference (SDR) containing both requirements and data logic and conventions (SDR-GA-GTM-PROFORTO.xlsx).
4. Visual reference (VisualRef-proforto.pdf)
5. Installing GTM JavaScript snippet and initial dataLayer set up
6. data layer object (dataLayer) syntax and format
   1. Page information
   2. Google's enhanced ecommerce actions
   3. Event information

### 1. Plan hand-over moment
Pick a time and date to discuss this Handover package with developers and project managers to make sure expectations are met. The goal is to confirm that developers understand this package and know what to do. Also the client needs to know when this part of the implementation is due and how much time it will cost. 

### 2. This developers package on GitHub
In the hand-over moment make sure this branch is complete and contains all the documents. 

### 3. Solution Design Reference (SDR) containing both requirements and data logic and conventions (SDR-GA-GTM-PROFORTO.xlsx).
Please follow the link to the [SDR-[PROFORTO].xlsx](../Analytics-SDR-GA-GTM-PROFORTO.xlsx) This document contains an overview of the elements that should be part of the data layer object. 
The first tab (requirements) details the requirements as discussed with the client (non-technical)
The second tab (Data layer object) of the SDR shows an overview of all name/value-pairs (objects and arrays) irrespective of the type of event or type of page. 
The third tab (digital touchpoints) grids __when__ specific elements of the data layer should be available (e.g. a confirmation page results in different populated variables then a product listing page). When necessary a visual reference is shown for more information on when and what data should be available. 
A fourth tab lists the different events object values that typically needs a more elaborate naming convention. 

### 4. Visual Reference 
Please follow the link to the [VisualRef-proforto.pdf](../proforto/VisualRef-proforto.pdf) This PDF contains references to special touchpoint that need clarification on what elements and values to expect in the data layer object.

### 5. Installing GTM JavaScript snippet and initial dataLayer set up
Before the GTM-container is loaded, set up the dataLayer-variable with an initial load:

```javascript
<script type="text/javascript">
var window.dataLayer = window.dataLayer || [];
</script>
```

#### Install GTM JavaScript snippet
Copy the code below and paste it on to every page of your website. Make sure the right GTM "container ID" is used for the designated environments. The table below lists the different GTM container IDs per website and/or environment.

Paste this code as high in the `<head>` of the page as possible:
```javascript
<!-- Google Tag Manager -->
<script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-XXXXXXX');</script>
<!-- End Google Tag Manager -->
```

Additionally, paste this code immediately after the opening `<body>` tag:
```javascript
<!-- Google Tag Manager (noscript) -->
<noscript><iframe src="https://www.googletagmanager.com/ns.html?id=GTM-XXXXXXX"
height="0" width="0" style="display:none;visibility:hidden"></iframe></noscript>
<!-- End Google Tag Manager (noscript) -->
```

Environment|URL|GTM Container ID
---|---|---
PROD|https://www.proforto.nl|GTM-TK999K
STAG|https://staging.proforto.nl/|GTM-5QF7ZG


For more information about installing the Google Tag Manager snippet, visit the [GTM Quick Start Guide](https://developers.google.com/tag-manager/quickstart).

### 6. data layer object (dataLayer) syntax and format
The folder [DataLayer snippets](https://github.com/ClickValue/DeveloperHandoverPackage_GA_GTM/tree/proforto/dataLayer_snippets) contains all relevant snippets to make sure the dataLayer structure is correct and according to Google documentation.

#### 6.1 Page information
The page information snippets contains the dataLayer structure relevant to all page-related information, such as page type and other page specific attributes. It also contains other page relevant information such as forms or filters that are applicable. 

#### 6.2 Google's enhanced ecommerce actions
This snippet shows all the relevant product related attributes and associated user actions such as purchase, add to cart or internal promotions. 

#### 6.3 Event information
One object within the dataLayer object is designed for user interactoins such as button clicks or other events that are custom to users interactions.
