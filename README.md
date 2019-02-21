# Developer Handover Package
This package documents instructions for developers to implement Adobe Launch and its accompanied information object: dataLayer. The data layer contains all the information that you want to pass to Launch. Please follow this [link](https://docs.adobelaunch.com/) for the official documentation about details of implementing Launch.

## Package content

1. Plan hand-over moment
2. This developers package on GitHub
3. Solution Design Reference (SDR) containing both requirements and data logic and conventions (SDR-Adobe-Launch-PROMINENT.xlsx).
4. Visual reference (VisualRef-prominent.pdf)
5. Installing Launch JavaScript snippet and initial dataLayer set up
6. data layer object (dataLayer) syntax and format
   1. Page information
   2. Ecommerce actions
   3. Event information

### 1. Plan hand-over moment
Pick a time and date to discuss this Handover package with developers and project managers to make sure expectations are met. The goal is to confirm that developers understand this package and know what to do. Also the client needs to know when this part of the implementation is due and how much time it will cost. 

### 2. This developers package on GitHub
In the hand-over moment make sure this branch is complete and contains all the documents. 

### 3. Solution Design Reference (SDR) containing both requirements and data logic and conventions (SDR-Adobe-Launch-PROMINENT.xlsx).
Please follow the link to the [SDR-[PROFORTO].xlsx](../master/Analytics-SDR-GA-GTM-PROFORTO.xlsx) This document contains an overview of the elements that should be part of the data layer object. Follwo this link for [Google Spreadsheet.](https://docs.google.com/spreadsheets/d/1sqBT_3kKL7VhhIzd7xy__8IYThK-UHr1LXtKzK23a2Y/edit#gid=1606015312)
The first tab (analytics requirements) details the requirements as discussed with the client (non-technical).
The second tab (Data layer object) of the SDR shows an overview of all name/value-pairs (objects and arrays) irrespective of the type of event or type of page. 
The third tab (digital touchpoints) grids __when__ specific elements of the data layer should be available (e.g. a confirmation page results in different populated variables then a product listing page). When necessary a visual reference is shown for more information on when and what data should be available. 
A fourth tab lists the different events object values that typically needs a more elaborate naming convention. 

### 4. Visual Reference 
Please follow the link to the [VisualRef-proforto.pdf](../master/VisualRef-proforto.pdf). This PDF contains references to special touchpoint that need clarification on what elements and values to expect in the data layer object.

### 5. Installing Launch JavaScript snippet and initial dataLayer set up
Before the Launch-library is loaded, set up the dataLayer-variable with an initial load:

```javascript
<script type="text/javascript">
var window.dataLayer = window.dataLayer || [];
</script>
```

#### Install Launch JavaScript snippet
Copy the code below and paste it on to every page of your website. Make sure the right Launch "environment ID" is used for the designated environments. The table below lists the different Launch environment IDs per website and/or environment.

Paste this code as high in the `<head>` of the page as possible:
```javascript
<!-- Launch DEV -->
<script src="//assets.adobedtm.com/launch-EN17941c21e3c84b3d888c41ae2cb125f1.min.js" async></script>
<!-- End Launch DEV -->
```

Optionally, paste this code before the closing `</body>` tag when using sync library:
```javascript
<script type="text/javascript">_satellite.pageBottom();</script>
```

Environment|URL|Launch Container ID
---|---|---
PROD|https://www.prominent.nu|/launch-EN17941c21e3c84b3d888c41ae2cb125f1.min.js
STAG|https://staging.prominent.nu/|/launch-EN0fe65624b94241deba23929a2ae332bf-staging.min.js
DEV|https://development.prominent.nu/|/launch-EN62c9a462e3f64dbe89e062db9b7e74d2-development.min.js


### 6. data layer object (dataLayer) syntax and format
The folder [DataLayer snippets](https://github.com/ClickValue/Proforto_SDR/tree/master/dataLayer_snippets) contains all relevant snippets to make sure the dataLayer structure is correct.

#### 6.1 Page information
The page information snippets contains the dataLayer structure relevant to all page-related information, such as page type and other page specific attributes. It also contains other page relevant information such as forms or filters that are applicable. 

#### 6.2 Ecommerce actions
This snippet shows all the relevant product related attributes and associated user actions such as purchase, add to cart or internal promotions. 

#### 6.3 Event information
One object within the dataLayer object is designed for user interactoins such as button clicks or other events that are custom to users interactions.
