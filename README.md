## Features

Capterra doesn't provide a very flexible or free API, but this scraper acts as an unofficial Capterra API to help you extract the data you need, when you need it, and at scale.

Capterra Scraper supports the following features:

-   **Search any keyword**

-   **Scrape lists**

-   **Scrape resources**

-   **Scrape categories**

-   **Scrape products**

-   **Scrape reviews**

Capterra provides a "Best business software. With software reviews, ratings infographics, and the most comprehensive list of the top". Scraping that content and extracting it in structured format could give you invaluable business insights and an edge over the competition.

## Tutorial

Check out this blog post on [how to extract data from Capterra with unofficial Capterra API](https://blog.apify.com/how-to-scrape-capterra/) for more information on the scraper.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests, you can create an issue from [here](https://github.com/epctex/capterra-scraper/issues).

### Upcoming changes

-   Retrieve comparisons.
-   Enrich reviews and output of the products.

## Setup & usage

You can see how this actor works in these videos:

### Start URLs

Watch how to set up Start URLs for Capterra Scraper [here](https://youtu.be/5UQJOJ0Q5Ws).

[![Apify - Capterra Scraper - Start URLs](https://i.imgur.com/NNYQIW4.png)](https://youtu.be/5UQJOJ0Q5Ws)

You can check the output of this video [here](https://api.apify.com/v2/datasets/cZVwlB36TtAcxQCfX/items?clean=true&format=json).

### Search

Watch how to set up Search for Capterra Scraper [here](https://www.youtube.com/watch?v=xv-k-YkXIRQ).

[![Apify - Capterra Scraper - Search](https://i.imgur.com/fV29q7g.png)](https://www.youtube.com/watch?v=xeOJCSU-0ME)

You can check the output of this video [here](https://api.apify.com/v2/datasets/VWn9Nu1KhxCJjnOma/items?clean=true&format=json).

## Input parameters

The input of this scraper should be JSON containing the list of pages o that should be visited. Required fields are:

| Field          | Type    | Description                                                                                                                                                                              |
| -------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| startUrls      | Array   | (optional) List of Capterra URLs. You should only provide search or detail URLs.                                                                                                         |
| includeReviews | Boolean | (optional) Adding reviews into the product objects is optional and by default it is `false`. If you want to scrape the reviews of the companies, then you can set this option as `true`. |
| maxItems       | Integer | (optional) You can limit scraped products. This should be useful when you search big lists.                                                                                              |
| search         | String  | (optional) Keyword that you want to search on Capterra.                                                                                                                                  |
| endPage        | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`.                                                                                                          |
| proxy          | Object  | Proxy configuration.                                                                                                                                                                     |
| customMapFunction | String  | (optional) Function that takes each objects handle as argument and returns object with executing the function                                                                                                                     |


This solution **requires the use of proxy servers**, either your own proxy servers or [Apify Proxy](https://www.apify.com/docs/proxy).

### Tips

When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startURL**.

If you would like to scrape only the first page of a list, then add the link for the page and have the `endPage` as 1.

Please also keep in mind that the `includeReviews` parameter will add multiple requests per product. That's why the number of requests or CUs that are consumed might be higher if you set this option as `true`.

## Compute unit consumption

Capterra Scraper is optimized to run extremely fast and scrape many as listings as possible, so it forefronts all listing detail requests. If the actor doesn't get blocked very often, it will scrape 100 listings in 2 minutes and consume ~0.07-0.08 compute units.

### Capterra Scraper input example

```json
{
    "startUrls": [
        "https://www.capterra.com/p/210664/CRYENGINE/",
        "https://www.capterra.com/search/?search=game%20engine"
    ],
    "search": "Game engine",
    "includeReviews": false,
    "proxy": {
        "useApifyProxy": true
    },
    "maxItems": 50
}
```

## During the run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.

When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

## Capterra export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node.js/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Capterra actor.

## Scraped Capterra product example

The structure of each item in Capterra product looks like this:

```json
{
    "productId": 210664,
    "alternativeProducts": [
        {
            "productId": 76113,
            "slug": "Wrike",
            "name": "Wrike",
            "url": "https://ad.doubleclick.net/ddm/trackclk/N1344363.813334CAPTERRA.COM/B24662437.285026937;dc_trk_aid=478661123;dc_trk_cid=139366293;dc_lat=;dc_rdid=;tag_for_child_directed_treatment=;tfua=;",
            "shortDescription": "Wrike is a project management software with prebuilt templates, Gantt charts, Kanban boards, automated approvals, proofing, and more.",
            "bestFor": "Perfect fit for Mid-sized and Enterprise companies that embrace teamwork, run multiple projects, & clients. Tailor Wrike to your needs with custom workflows, fields, & reports. ",
            "longDescription": "Wrike is an award-winning project management software trusted by 20,000+ companies worldwide. Streamline your game development using product launch templates, Kanban boards, Gantt charts, time tracking, custom request forms with auto-assignment, performance reports, and shared workflows all in one place. Accelerate your game development with Wrike's 400+ integrations and visual proofing. Customize your workflows to see progress at every step. Increase your on-time delivery with Wrike.",
            "reviewsTotal": 1690,
            "isUpgraded": true,
            "overallRating": 4.2,
            "easeOfUseRating": 4,
            "customerServiceRating": 4.3,
            "functionalityRating": 4.2,
            "valueForMoneyRating": 4,
            "recommendationRating": 7.9,
            "vendor": {
                "id": 2044982,
                "name": "Wrike",
                "url": "http://www.wrike.com",
                "yearFounded": 2007,
                "location": "United States",
                "optedOutOfReviews": false,
                "isHitLimit": false,
                "enabled": true,
                "hasVendorLevelPage": false
            },
            "category": {
                "id": 30951,
                "shortName": "gamedev",
                "longName": "Game Development",
                "htmlName": "game-development-software",
                "enabled": true
            },
            "reviewCount": 1690,
            "showUpgraded": true,
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/f7d6685a-9008-4905-bb9e-83a39fe2c19e.png?auto=format&size=50",
            "urlSignature": "70460cca6e8a87d1867bfa46942995cf50d89fb6",
            "productUrl": "/p/76113/Wrike",
            "shortlistBadges": [],
            "pricingAmount": "9.80",
            "currencySymbol": "$",
            "feeSchedule": "Per-Month",
            "pricingSnippet": [],
            "pricingModel": "Per User"
        }
    ],
    "name": "CRYENGINE",
    "productType": "B",
    "productUrl": "/p/210664/CRYENGINE",
    "slug": "CRYENGINE",
    "formerlyKnownAs": "CRYENGINE",
    "url": "https://www.cryengine.com/",
    "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/4c8d3fa4-b3a5-417a-8821-6724b8a5401a.png?auto=format&size=150",
    "reviewUrl": "https://reviews.capterra.com/new/210664",
    "isUpgraded": false,
    "overallRating": 4.8,
    "easeOfUseRating": 3.2,
    "customerServiceRating": 4,
    "functionalityRating": 4.2,
    "valueForMoneyRating": 4.8,
    "recommendationRating": 8,
    "bestFor": "CRYENGINE is a software environment for game developers who want to create products with high visual quality. The package is aimed at larger game development teams.",
    "featuredIn": [],
    "shortDescription": "CRYENGINE is a comprehensive solution for the creation of high-quality 3D and virtual reality game software in development teams",
    "longDescription": "CRYENGINE, distributed by Crytek GmbH, is a development environment for computer games. One of its essential features is a powerful rendering engine, which is characterized by its visual quality. The product includes many tools which are important in today's game development genres, such as a physics engine and AI tools. Due to the complex nature of the software, it is aimed at teams of a certain size and users with high expectations.",
    "startingPrice": "Crytek GmbH is available for free and 5% royalty is applied on project shipment. Contact Crytek GmbH for further pricing details.",
    "pricing": null,
    "pricingDetails": "Crytek GmbH is available for free and 5% royalty is applied on project shipment. Contact Crytek GmbH for further pricing details.",
    "pricingAmount": null,
    "feeSchedule": null,
    "pricingModel": "Per Feature",
    "pricingOverview": "<span class=\"nb-mr-3xs\">They do not have a free version.</span> <span class=\"nb-mr-3xs\">CRYENGINE <span class=\"nb-font-bold\">does not offer a free trial</span>.</span>",
    "pricingAdditionalInfo": "<span class=\"nb-mr-3xs\">See additional pricing details below.</span>",
    "platform": [
        {
            "enabled": true,
            "name": "Cloud, SaaS, Web-Based"
        },
        {
            "enabled": false,
            "name": "Desktop Mac"
        },
        {
            "enabled": true,
            "name": "Desktop Windows"
        },
        {
            "enabled": false,
            "name": "Desktop Linux"
        },
        {
            "enabled": false,
            "name": "On-Premise Windows"
        },
        {
            "enabled": false,
            "name": "On-Premise Linux"
        },
        {
            "enabled": false,
            "name": "Desktop Chromebook"
        },
        {
            "enabled": false,
            "name": "Mobile Android"
        },
        {
            "enabled": false,
            "name": "Mobile iPhone"
        },
        {
            "enabled": false,
            "name": "Mobile iPad"
        }
    ],
    "training": [
        {
            "enabled": false,
            "name": "In-Person"
        },
        {
            "enabled": false,
            "name": "Live Online"
        },
        {
            "enabled": false,
            "name": "Webinars"
        },
        {
            "enabled": false,
            "name": "Documentation"
        },
        {
            "enabled": true,
            "name": "Videos"
        }
    ],
    "support": [
        {
            "enabled": true,
            "name": "Email Help Desk"
        },
        {
            "enabled": true,
            "name": "FAQ Forum"
        },
        {
            "enabled": true,
            "name": "Knowledgebase"
        },
        {
            "enabled": true,
            "name": "Phone Support"
        }
    ],
    "features": [
        {
            "categoryName": "Game Development",
            "categoryFeatures": [
                {
                    "name": "2D Drawing",
                    "value": false,
                    "id": "886d57ba-ceae-4c47-8235-7e169c3f9cf3",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": "Create 2-dimensional games"
                },
                {
                    "name": "3D Games",
                    "value": false,
                    "id": "ee0fead1-450c-43a6-8ba7-1920ed521393",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": "Create 3-dimensional games"
                },
                {
                    "name": "IT Asset Management",
                    "value": false,
                    "id": "ad2f5613-a7c7-47ff-bf8f-bd1c147a30e6",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": "Inventories and tracks changes to hardware and software configurations."
                },
                {
                    "name": "In-App Purchase",
                    "value": false,
                    "id": "9ae1e452-660e-49e6-a6a8-2fde47d3ba20",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": "Provide players with in-app purchase options."
                },
                {
                    "name": "In-Game Analytics",
                    "value": false,
                    "id": "0cdae92e-de21-4f20-ae7c-a1087df28326",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": "Report on game usage and gaming statistics."
                },
                {
                    "name": "Multi-player Gaming Network",
                    "value": false,
                    "id": "e2be0b32-316e-4302-8996-9f9e213c7ab2",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": "Manage networking aspects of multiple games."
                },
                {
                    "name": "Physics Simulation",
                    "value": false,
                    "id": "b1148bfe-c68a-4ceb-93b3-6214f5ff22ef",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": "Implement laws of physics in the game, such as collision, gravity, bouncing, and sliding."
                },
                {
                    "name": "Player Management",
                    "value": false,
                    "id": "ffc8768e-c2e6-4477-9d5e-52372447f020",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": "Manage movement and changes in the characters of a game."
                },
                {
                    "name": "Prototype Creation",
                    "value": false,
                    "id": "7b02a7b5-2c4b-49fa-b948-a40834914079",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": "Create, manage and provide access to prototypes used in the games."
                },
                {
                    "name": "Virtual Reality",
                    "value": false,
                    "id": "efcc2cc8-c612-4a99-8d4d-f18e827f027d",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": "Manage development tasks for games that involve virtual reality."
                }
            ]
        },
        {
            "categoryName": "Animation",
            "categoryFeatures": [
                {
                    "name": "2D Drawing",
                    "value": false,
                    "id": "886d57ba-ceae-4c47-8235-7e169c3f9cf3",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "3D Modeling",
                    "value": false,
                    "id": "f5ea5390-3d90-4d3c-974b-4fbb7ab31af6",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Animations & Transitions",
                    "value": true,
                    "id": "fb3ba3c4-66d7-4135-888f-942a02399e8f",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": false,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Content Library",
                    "value": false,
                    "id": "58a7266d-b84c-4e92-9ca4-18028246718c",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Digital Asset Management",
                    "value": false,
                    "id": "620e0d4a-1589-4a6e-a5d9-c69c232b95dc",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Drag & Drop",
                    "value": false,
                    "id": "ef4e7adb-17df-4712-bd53-957772beafad",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Media Import",
                    "value": true,
                    "id": "4a17c902-4376-4836-8136-67a800e82f34",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": false,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Pre-built Templates",
                    "value": false,
                    "id": "4fcf7cb6-2c24-438a-bb77-4a7c141c1bc9",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Rendering",
                    "value": false,
                    "id": "53339250-c547-45b0-a229-68fdb768b8c0",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Search",
                    "value": false,
                    "id": "5043da21-96c0-4156-b4c3-958b3b3f6a6b",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Text Overlay",
                    "value": false,
                    "id": "eed1088c-ec01-4d3f-b0c1-acdd80e066d5",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Video Content",
                    "value": false,
                    "id": "8a25a900-8ba0-4439-9819-9f4b8c714cd4",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Video Editing",
                    "value": false,
                    "id": "29017c15-3f94-47be-a1fc-964e4652cc1b",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                }
            ]
        },
        {
            "categoryName": "Virtual Reality (VR)",
            "categoryFeatures": [
                {
                    "name": "Application Development",
                    "value": false,
                    "id": "4be94187-895f-43a0-908d-a7d19b265eb6",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": "Build unique software tools based on your specific requirements"
                },
                {
                    "name": "Augmented / Mixed Reality",
                    "value": false,
                    "id": "69ea160c-2540-409c-b949-db4020c20851",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Collaboration Tools",
                    "value": false,
                    "id": "97efb0d3-9a23-4408-90d4-4db1e3830fbd",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Content Creation",
                    "value": false,
                    "id": "d0cd6a86-55be-4df5-ae29-daf70eb859ec",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Cross-Device Publishing",
                    "value": false,
                    "id": "acb6aaa6-8955-4c57-8c75-ed6e7ba2b8ec",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Drag & Drop",
                    "value": false,
                    "id": "ef4e7adb-17df-4712-bd53-957772beafad",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Immersive Environment",
                    "value": true,
                    "id": "ad248dfc-f112-4faa-9fc2-8140e396fc17",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": false,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Process Simulation",
                    "value": false,
                    "id": "9a7e7a2e-0d5e-49d3-98d9-01e3415b999d",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Product Visualization",
                    "value": false,
                    "id": "83fe1076-a7ba-4bfe-af74-f20f600f4b26",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": true,
                    "definition": null
                },
                {
                    "name": "Social Sharing",
                    "value": false,
                    "id": "285cc589-9f80-4e3a-93d7-a7fb0fad0616",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "User Interaction Tracking",
                    "value": false,
                    "id": "14cf089f-b576-4a25-b32e-bd1c203a3d94",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Virtual Meetings",
                    "value": false,
                    "id": "a91b4bb6-f99e-4b39-bd3a-cc0331f105c8",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                },
                {
                    "name": "Virtual Prototyping",
                    "value": false,
                    "id": "e35f7667-025d-43ac-95be-7bdb4f958520",
                    "avg_rating": null,
                    "cnt_rating": null,
                    "avg_importance": null,
                    "cnt_importance": null,
                    "cnt_time_used": null,
                    "pct_time_used": null,
                    "cnt_time_critical": null,
                    "pct_time_critical": null,
                    "is_key_feature": true,
                    "is_top_feature": false,
                    "definition": null
                }
            ]
        }
    ],
    "comparisonProducts": [
        {
            "productId": 76113,
            "name": "Wrike",
            "url": "https://ad.doubleclick.net/ddm/trackclk/N1344363.813334CAPTERRA.COM/B24662437.285026937;dc_trk_aid=478661123;dc_trk_cid=139366293;dc_lat=;dc_rdid=;tag_for_child_directed_treatment=;tfua=;",
            "slug": "Wrike",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/f7d6685a-9008-4905-bb9e-83a39fe2c19e.png?auto=format&size=50",
            "shortDescription": "Wrike is a project management software with prebuilt templates, Gantt charts, Kanban boards, automated approvals, proofing, and more.",
            "vendorName": "Wrike",
            "overallRating": 4.2,
            "reviewCount": 1690
        },
        {
            "productId": 158591,
            "name": "Unity",
            "url": "https://unity.com/",
            "slug": "Unity",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/05df2ddf-1ab4-4f66-95cf-e1fcfcbedc28.png?auto=format&size=50",
            "shortDescription": "On-premise game engine that helps developers assemble assets, create games & experiences in 3D, manage crashes, and more.",
            "vendorName": "Unity Technologies",
            "overallRating": 4.7,
            "reviewCount": 491
        },
        {
            "productId": 152766,
            "name": "CoolaData",
            "url": "https://www.cooladata.com/solutions/game-analytics?utm_source=capterra&utm_medium=cpc&utm_campaign=software-directory&utm_term=capterra-game-development&utm_content=demo-request",
            "slug": "CoolaData",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/ed46cc70-0f33-4245-b3d3-05d7d0f696a3.png?auto=format&size=50",
            "shortDescription": "Cooladata is a data warehousing and visualization solution optimized for gaming companies. Ideal for small to mid-sized data teams.",
            "vendorName": "Cooladata",
            "overallRating": 4.9,
            "reviewCount": 9
        },
        {
            "productId": 210494,
            "name": "Incredibuild",
            "url": "https://www.incredibuild.com/?utm_medium=cpc&utm_source=capterra&utm_content=Game-Development&utm_campaign=21-03-GL-DP-Capterra_Pilot-1252",
            "slug": "Incredibuild",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/6e9e1e1c-0863-4545-ac73-4b80e2b9c29a.png?auto=format&size=50",
            "shortDescription": "Incredibuild enables game developers/artists to accelerate their compilations, shaders compilations (10x faster), and more.",
            "vendorName": "Incredibuild Software",
            "overallRating": 4.6,
            "reviewCount": 9
        }
    ],
    "similarProducts": [
        {
            "productId": 76113,
            "name": "Wrike",
            "url": "https://ad.doubleclick.net/ddm/trackclk/N1344363.813334CAPTERRA.COM/B24662437.283028211;dc_trk_aid=476749289;dc_trk_cid=139366293;dc_lat=;dc_rdid=;tag_for_child_directed_treatment=;tfua=;",
            "slug": "Wrike",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/f7d6685a-9008-4905-bb9e-83a39fe2c19e.png?auto=format&size=50",
            "shortDescription": "Wrike is a project management software with prebuilt templates, Gantt charts, Kanban boards, automated approvals, proofing, and more.",
            "vendorName": "Wrike",
            "overallRating": 4.2,
            "reviewCount": 1690
        },
        {
            "productId": 101288,
            "name": "Microsoft Visual Studio",
            "url": "https://visualstudio.microsoft.com/",
            "slug": "Visual-Studio",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/1b6d695a-be0d-4aaf-920f-675585b5bb9c.png?auto=format&size=50",
            "shortDescription": "App and game development platform that enables businesses to develop, edit, and test apps using tools and techniques.",
            "vendorName": "Microsoft",
            "overallRating": 4.6,
            "reviewCount": 2136
        },
        {
            "productId": 123836,
            "name": "Google Cloud Platform",
            "url": "https://cloud.google.com/",
            "slug": "Google-Cloud-Platform",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/00f70353-5158-4088-92e5-71ef7b5c278c.png?auto=format&size=50",
            "shortDescription": "Cloud Platform is a set of modular cloud-based services that allow you to create anything from simple websites to complex applications.",
            "vendorName": "Google",
            "overallRating": 4.7,
            "reviewCount": 1124
        },
        {
            "productId": 167519,
            "name": "Blender",
            "url": "https://www.blender.org",
            "slug": "Blender",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/c2324cde-d427-40cc-9ce6-c3a64163ddce.png?auto=format&size=50",
            "shortDescription": "Ultra-realistic rendering system that includes GPU & CPU rendering, modeling, video editor, sculpting, simulations, and more.",
            "vendorName": "Blender Foundation",
            "overallRating": 4.6,
            "reviewCount": 630
        },
        {
            "productId": 158599,
            "name": "Unreal Engine",
            "url": "https://www.unrealengine.com",
            "slug": "Unreal-Engine",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/c56e426e-7b6d-451a-a268-2f8925d48301.png?auto=format&size=50",
            "shortDescription": "Game development suite that helps create 3D films, visualizations, training simulations, persona animations, and more.",
            "vendorName": "Epic Games",
            "overallRating": 4.8,
            "reviewCount": 257
        },
        {
            "productId": 171048,
            "name": "Wolfram Mathematica",
            "url": "http://www.wolfram.com/mathematica",
            "slug": "Wolfram-Mathematica",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/4391aeab-6c30-4d36-a1b4-619501fefbaa.png?auto=format&size=50",
            "shortDescription": "Technical computing system that provides tools for image processing, geometry, visualization, machine learning, data mining, and more.",
            "vendorName": "Wolfram",
            "overallRating": 4.6,
            "reviewCount": 147
        },
        {
            "productId": 201543,
            "name": "Construct 3",
            "url": "https://www.construct.net",
            "slug": "Construct-3",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/d54fe0e3-bcac-4dae-b56c-a63a4b324c1c.png?auto=format&size=50",
            "shortDescription": "Game development software that runs in the browser and is used by schools, indie developers and game making companies globally.",
            "vendorName": "Scirra",
            "overallRating": 4.7,
            "reviewCount": 116
        },
        {
            "productId": 158594,
            "name": "GameMaker: Studio",
            "url": "http://www.yoyogames.com/gamemaker",
            "slug": "GameMaker-Studio",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/e1110207-96dd-4136-8c6b-ee5d33e71b3c.png?auto=format&size=50",
            "shortDescription": "Multi-platform game development system with drag & drop capabilities, built-in shader editing, user engagement and real-time analytics.",
            "vendorName": "YoYo Games",
            "overallRating": 4.4,
            "reviewCount": 78
        },
        {
            "productId": 164141,
            "name": "XSplit Broadcaster",
            "url": "https://www.xsplit.com",
            "slug": "XSplit-Broadcaster",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/b5a3e9bd-e4da-45ad-8d20-1ed648b9f2b6.png?auto=format&size=50",
            "shortDescription": "Live streaming system for broadcasting and video production with high fidelity sound.",
            "vendorName": "SplitmediaLabs",
            "overallRating": 4.1,
            "reviewCount": 49
        },
        {
            "productId": 206897,
            "name": "3ds Max",
            "url": "https://www.autodesk.com/products/3ds-max/overview?support=ADVANCED",
            "slug": "3ds-Max",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/580cea03-c814-4126-9c92-69013659720e.png?auto=format&size=50",
            "shortDescription": "Produce professional 3D models and renders for design visualization, game development, and animation with 3ds Max's robust design tools",
            "vendorName": "Autodesk",
            "overallRating": 4.7,
            "reviewCount": 41
        },
        {
            "productId": 157216,
            "name": "Amazon Lumberyard",
            "url": "https://aws.amazon.com/lumberyard/",
            "slug": "Amazon-Lumberyard",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/8d1670b0-6b26-4ce7-83bf-3594848a0f8c.png?auto=format&size=50",
            "shortDescription": "3D game engine designed to build games and fan communities and offers VR preview mode, visual scripting tools, and Twitch integration.",
            "vendorName": "Amazon Web Services",
            "overallRating": 4.3,
            "reviewCount": 30
        },
        {
            "productId": 174325,
            "name": "Helix Core",
            "url": "http://info.perforce.com/try-perforce-helix-core-free.html",
            "slug": "Helix-Core",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/ed99a7ca-e89c-4210-bd05-e4ba9950c124.png?auto=format&size=50",
            "shortDescription": "Cloud-based application development solution that allows businesses to track and manage changes to source code, digital assets & more.",
            "vendorName": "Perforce",
            "overallRating": 4.6,
            "reviewCount": 27
        },
        {
            "productId": 236736,
            "name": "Adobe AIR",
            "url": "https://airsdk.harman.com/",
            "slug": "Adobe-AIR",
            "logoUrl": "https://gdm-catalog-fmapi-prod.imgix.net/ProductLogo/4098fdd6-aca4-4df8-934a-d246ea377f09.png?auto=format&size=50",
            "shortDescription": "Adobe AIR, provided by HARMAN, is a cross-platform runtime system.",
            "vendorName": "HARMAN",
            "overallRating": 4.7,
            "reviewCount": 23
        }
    ],
    "media": [
        {
            "type": "IMAGE",
            "url": "https://gdm-catalog-fmapi-prod.imgix.net/ProductScreenshot/53aad1b9-2763-42c3-b913-86a7ae466ee6.jpeg?auto=format",
            "caption": null,
            "weight": 1
        },
        {
            "type": "IMAGE",
            "url": "https://gdm-catalog-fmapi-prod.imgix.net/ProductScreenshot/00d2dac2-fbd8-4b8d-b979-d7c986d40188.jpeg?auto=format",
            "caption": null,
            "weight": 2
        },
        {
            "type": "IMAGE",
            "url": "https://gdm-catalog-fmapi-prod.imgix.net/ProductScreenshot/eb315e5b-ad89-4c6c-9e96-c13222c988be.jpeg?auto=format",
            "caption": null,
            "weight": 3
        }
    ],
    "category": {
        "id": 30951,
        "shortName": "gamedev",
        "longName": "Game Development",
        "htmlName": "game-development-software",
        "enabled": true
    },
    "categories": [
        {
            "html_name": "animation-software",
            "short_name": "animation",
            "id": 32795,
            "long_name": "Animation",
            "enabled": true
        },
        {
            "html_name": "game-development-software",
            "short_name": "gamedev",
            "id": 30951,
            "long_name": "Game Development",
            "enabled": true
        },
        {
            "html_name": "vr-software",
            "short_name": "vr",
            "id": 31659,
            "long_name": "Virtual Reality (VR)",
            "enabled": true
        }
    ],
    "bestCategoryShortName": "gamedev",
    "isBestCategory": true,
    "bestCategory": "game-development-software",
    "highestCpcCategoryShortName": null,
    "isHighestCpcCategory": false,
    "vendor": {
        "id": 2151455,
        "name": "Crytek GmbH",
        "url": "https://www.cryengine.com/",
        "yearFounded": null,
        "location": "Germany",
        "optedOutOfReviews": false,
        "isHitLimit": false,
        "enabled": true,
        "hasVendorLevelPage": false
    },
    "enabled": true,
    "relatedResources": [],
    "ranking": null,
    "breadcrumbs": [
        {
            "name": "Home",
            "href": "https://www.capterra.com/"
        },
        {
            "name": "Game Development Software",
            "href": "https://www.capterra.com/game-development-software/"
        },
        {
            "name": "CRYENGINE",
            "href": "https://www.capterra.com/p/210664/CRYENGINE/"
        }
    ],
    "links": [],
    "showCtaLinks": false,
    "showUpgraded": false,
    "isPerUser": false,
    "hasFreeVersion": false,
    "hasFreeTrial": false,
    "relatedCategories": [
        {
            "shortName": "gamedev",
            "longName": "Application Development",
            "htmlName": "application-development-software",
            "linkName": "application-development",
            "productCount": 166,
            "shortDescription": "Find and compare top Application Development software on Capterra, with our free and interactive tool. Quickly browse through hundreds of Application Development tools and systems and narrow down your top choices. Filter by popular features, pricing options, number of users, and read reviews from real users and find a tool that fits your needs. ",
            "longDescription": "<a href=\"/application-development-software\">Application Development software</a> assists developers with the deployment of software applications.  Application Development solutions aid in the creation of custom solutions for an organization's technology and information infrastructure.  Typically, application development software is geared to work with a variety of common programming languages and platforms.  <a href=\"/application-development-software\">Application Development software</a> is related to <a href=\"/bug-tracking-software\">Bug Tracking software</a> and <a href=\"/license-management-software\">License Management software</a>."
        },
        {
            "shortName": "gamedev",
            "longName": "Artificial Intelligence",
            "htmlName": "artificial-intelligence-software",
            "linkName": "artificial-intelligence",
            "productCount": null,
            "shortDescription": "Find and compare top Artificial Intelligence software on Capterra, with our free and interactive tool. Quickly browse through hundreds of Artificial Intelligence tools and systems and narrow down your top choices. Filter by popular features, pricing options, number of users, and read reviews from real users and find a tool that fits your needs. ",
            "longDescription": "Artificial Intelligence software mimics human behavior and learning patterns.  It can be utilized in a variety of business areas, from customer service and sales (in the form of chatbots) to data analysis and IT tasks automation."
        },
        {
            "shortName": "gamedev",
            "longName": "Augmented Reality",
            "htmlName": "augmented-reality-software",
            "linkName": "augmented-reality",
            "productCount": null,
            "shortDescription": "Find and compare top Augmented Reality software on Capterra, with our free and interactive tool. Quickly browse through hundreds of Augmented Reality tools and systems and narrow down your top choices. Filter by popular features, pricing options, number of users, and read reviews from real users and find a tool that fits your needs. ",
            "longDescription": "Augmented Reality software helps create computer-enhanced immersive experiences for virtual tours, gaming environments, and training simulations. Augmented Reality tools can also be used in retail to help customers virtually try the product before the purchase is made."
        },
        {
            "shortName": "gamedev",
            "longName": "Gamification",
            "htmlName": "gamification-software",
            "linkName": "gamification",
            "productCount": null,
            "shortDescription": "Find and compare top Gamification software on Capterra, with our free and interactive tool. Quickly browse through hundreds of Gamification tools and systems and narrow down your top choices. Filter by popular features, pricing options, number of users, and read reviews from real users and find a tool that fits your needs. ",
            "longDescription": "<a href=\"/gamification-software\">Gamification software</a> promotes user engagement with social recognition, fun activities, and achievement rewards. Most gamification platforms can be used for employees, students, or customers to motivate completion of tasks and improve performance. Related tools can be found in the <a href='/training-software\">Training software</a>, <a href=\"/learning-management-system-software\">LMS software</a>, <a href=\"call-center-software\">Call Center software</a>, <a href=\"/performance-appraisal-software\">Performance Appraisal software</a>, <a href=\"/sales-enablement-software\">Sales Enablement software</a>, <a href=\"community-software\">Community software</a>, <a href=\"/employee-engagement-software\">Employee Engagement software</a>, <a href=\"customer-engagement-software\">Customer Engagement software</a>, and <a href=\"contest-software\">Contest software</a> categories."
        },
        {
            "shortName": "gamedev",
            "longName": "Virtual Reality (VR)",
            "htmlName": "vr-software",
            "linkName": "vr",
            "productCount": null,
            "shortDescription": "Find and compare top Virtual Reality (VR) software on Capterra, with our free and interactive tool. Quickly browse through hundreds of VR tools and systems and narrow down your top choices. Filter by popular features, pricing options, number of users, and read reviews from real users and find a tool that fits your needs.",
            "longDescription": "VR, or Virtual Reality, software is used to create immersive 3D environments that could be used for training or product prototyping. Additionally, immercive and interctive VR environments are often used in entertainment industry."
        }
    ],
    "reviewsSnippet": [],
    "pricingSnippet": [],
    "recommendedProducts": [
        {
            "name": "GameGuru",
            "slug": "game-guru",
            "category": {
                "id": 30951,
                "shortName": "gamedev",
                "longName": "Game Development",
                "htmlName": "game-development-software",
                "enabled": true
            },
            "productId": 190727,
            "pricing": null,
            "url": "https://www.game-guru.com",
            "reviewsTotal": 5,
            "isUpgraded": false,
            "overallRating": 4,
            "logoUrl": "https://cdn0.capterra-static.com/logos/150/2133502-1564083478.png",
            "productUrl": "/p/190727/game-guru",
            "recScore": 1,
            "algoName": "pct_to_p2_bayes",
            "vendor": {
                "id": 2133502,
                "name": "The Game Creators",
                "url": "https://www.game-guru.com",
                "yearFounded": null,
                "location": "United Kingdom",
                "optedOutOfReviews": false,
                "isHitLimit": false,
                "enabled": true,
                "hasVendorLevelPage": false
            },
            "urlSignature": null
        },
        {
            "name": "devtodev",
            "slug": "devtodev",
            "category": {
                "id": 30951,
                "shortName": "gamedev",
                "longName": "Game Development",
                "htmlName": "game-development-software",
                "enabled": true
            },
            "productId": 164843,
            "pricing": null,
            "url": "https://www.devtodev.com",
            "reviewsTotal": 3,
            "isUpgraded": false,
            "overallRating": 5,
            "logoUrl": "https://cdn0.capterra-static.com/logos/150/2115109-1499112224.png",
            "productUrl": "/p/164843/devtodev",
            "recScore": 2,
            "algoName": "pct_to_p2_bayes",
            "vendor": {
                "id": 2115109,
                "name": "devtodev",
                "url": "https://www.devtodev.com/",
                "yearFounded": 2014,
                "location": "Lithuania",
                "optedOutOfReviews": false,
                "isHitLimit": false,
                "enabled": true,
                "hasVendorLevelPage": false
            },
            "urlSignature": null
        },
        {
            "name": "3D Crafter",
            "slug": "3D-Crafter",
            "category": {
                "id": 30951,
                "shortName": "gamedev",
                "longName": "Game Development",
                "htmlName": "game-development-software",
                "enabled": true
            },
            "productId": 167521,
            "pricing": "$39.95 Flat Rate/one-time",
            "url": "http://amabilis.com",
            "reviewsTotal": 2,
            "isUpgraded": false,
            "overallRating": 3.5,
            "logoUrl": "https://cdn0.capterra-static.com/logos/150/2116702-1506451138.png",
            "productUrl": "/p/167521/3D-Crafter",
            "recScore": 3,
            "algoName": "pct_to_p2_bayes",
            "vendor": {
                "id": 2116702,
                "name": "Amabilis Software",
                "url": "http://amabilis.com",
                "yearFounded": null,
                "location": "Canada",
                "optedOutOfReviews": false,
                "isHitLimit": false,
                "enabled": true,
                "hasVendorLevelPage": false
            },
            "urlSignature": null
        },
        {
            "name": "GameBook ",
            "slug": "GameBook",
            "category": {
                "id": 10007,
                "shortName": "conman",
                "longName": "Content Management",
                "htmlName": "content-management-software",
                "enabled": true
            },
            "productId": 182459,
            "pricing": null,
            "url": "https://gamebook.io",
            "reviewsTotal": 2,
            "isUpgraded": false,
            "overallRating": 3.5,
            "logoUrl": "https://cdn0.capterra-static.com/logos/150/2127613-1547212739.png",
            "productUrl": "/p/182459/GameBook",
            "recScore": 4,
            "algoName": "pct_to_p2_bayes",
            "vendor": {
                "id": 2127613,
                "name": "Experimental Game",
                "url": "https://gamebook.io",
                "yearFounded": null,
                "location": "Germany",
                "optedOutOfReviews": false,
                "isHitLimit": false,
                "enabled": true,
                "hasVendorLevelPage": false
            },
            "urlSignature": null
        },
        {
            "name": "Incredibuild",
            "slug": "Incredibuild",
            "category": {
                "id": 30951,
                "shortName": "gamedev",
                "longName": "Game Development",
                "htmlName": "game-development-software",
                "enabled": true
            },
            "productId": 210494,
            "pricing": null,
            "url": "https://www.incredibuild.com/?utm_medium=cpc&utm_source=capterra&utm_content=homepage&utm_campaign=21-03-GL-DP-Capterra_Pilot-1252",
            "reviewsTotal": 9,
            "isUpgraded": true,
            "overallRating": 4.6,
            "logoUrl": "https://cdn0.capterra-static.com/logos/150/2151323-1603349050.png",
            "productUrl": "/p/210494/Incredibuild",
            "recScore": 5,
            "algoName": "pct_to_p2_bayes",
            "vendor": {
                "id": 2151323,
                "name": "Incredibuild Software",
                "url": "http://www.incredibuild.com",
                "yearFounded": 2012,
                "location": "Israel",
                "optedOutOfReviews": false,
                "isHitLimit": true,
                "enabled": true,
                "hasVendorLevelPage": false
            },
            "urlSignature": "93418b085df3845a3865b36fcb42e5cd24a4d5b5"
        }
    ],
    "badges": [],
    "internationalProduct": {
        "usProductId": 210664,
        "productId": 210664,
        "slug": "CRYENGINE"
    },
    "faqSection": {
        "enabled": false,
        "questionnaire": [null, null, null]
    },
    "videoReviews": [],
    "targetUsers": [],
    "shortlistBadges": [],
    "reviewCount": 4,
    "reviewsTotal": 4,
    "creditCardRequired": null,
    "currencyCode": "USD",
    "currencySymbol": "$",
    "pricingRating": 1,
    "productUrlAsSignedHash": "652a3b529ed25590a5ffc195b951042178080bad",
    "pricingLink": null,
    "freeLink": null,
    "reviews": [
        {
            "reviewId": "3009266",
            "customerSupportRating": null,
            "switchingReasons": "For better graphics and flexible licensing",
            "completenessScore": 1.100000023841858,
            "recommendationRating": 10,
            "anonymityOn": false,
            "sourceSite": "Capterra",
            "slug": "CRYENGINE",
            "translation": {
                "switchingReasons": null,
                "chosenReasons": null,
                "generalComments": null,
                "consText": null,
                "adviceToOthers": null,
                "title": null,
                "prosText": null
            },
            "easeOfUseRating": 4,
            "isPublished": true,
            "suggestedLocalProductId": [
                "158594",
                "157216",
                "158592",
                "234433",
                "158594",
                "157216"
            ],
            "alternativeProducts": [
                {
                    "productId": 158592,
                    "productSlug": "GDevelop",
                    "productName": "GDevelop"
                },
                {
                    "productId": 234433,
                    "productSlug": "Kivy",
                    "productName": "Kivy"
                },
                {
                    "productId": 158594,
                    "productSlug": "GameMaker-Studio",
                    "productName": "GameMaker: Studio"
                },
                {
                    "productId": 157216,
                    "productSlug": "Amazon-Lumberyard",
                    "productName": "Amazon Lumberyard"
                }
            ],
            "vendorResponse": {
                "name": "Crytek GmbH",
                "date": null,
                "text": null
            },
            "globalReviewId": "Capterra___3009266",
            "switchedProducts": [
                {
                    "productId": 158594,
                    "productSlug": "GameMaker-Studio",
                    "productName": "GameMaker: Studio"
                },
                {
                    "productId": 157216,
                    "productSlug": "Amazon-Lumberyard",
                    "productName": "Amazon Lumberyard"
                }
            ],
            "reviewer": {
                "companySize": "51-200 employees",
                "role": ["1", "2", "4", "8"],
                "jobTitle": "CEO",
                "timeUsedProduct": "2+ years",
                "companyName": "Curl Labs",
                "fullName": "Nabin P.",
                "frequencyUsedProduct": "Daily",
                "industry": "Computer Software",
                "verifiedLinkedIn": true,
                "profilePicUrl": "75bd4d7a9d6c80811a916ad50e15a311.jpeg"
            },
            "functionalityRating": 5,
            "chosenReasons": null,
            "generalComments": "With CryEngine, we are able to render the most realistic 3D models and animation for immersive games.",
            "language": "en",
            "@version": "1",
            "productName": "CRYENGINE",
            "statusName": "Published",
            "title": "Engine to develop immersive games",
            "@timestamp": "2021-11-27T07:57:37.713Z",
            "vendorId": 2151455,
            "writtenOn": "2021-08-11 09:47:01 -0400",
            "adviceToOthers": "",
            "productId": 210664,
            "prosText": "CryEngine is the most advanced graphics rendering game engine for realistic game development. It comes with a WYSWYP sandbox allowing you to develop and test your game seamlessly. Features realistic physics simulation, real-time illumination, and easy to use audio translation layer. CryEngine is free to use for production and just needs 5% of the profit made while using it commercially.",
            "overallRating": 5,
            "incentivized": "NoIncentive",
            "valueForMoneyRating": 5,
            "consText": "CryEngine can be difficult to learn with limited documentation and a small development community. The gameplay framework is a bit inflexible. Unsuitable for small projects due to performance and scalability issues."
        },
        {
            "reviewId": "2535627",
            "customerSupportRating": 4,
            "switchingReasons": null,
            "completenessScore": 1.090000033378601,
            "recommendationRating": 8,
            "anonymityOn": false,
            "sourceSite": "Capterra",
            "slug": "CRYENGINE",
            "translation": {
                "switchingReasons": null,
                "chosenReasons": null,
                "generalComments": null,
                "consText": null,
                "adviceToOthers": null,
                "title": null,
                "prosText": null
            },
            "easeOfUseRating": 3,
            "isPublished": true,
            "suggestedLocalProductId": ["210413"],
            "alternativeProducts": [],
            "vendorResponse": {
                "name": "Crytek GmbH",
                "date": null,
                "text": null
            },
            "globalReviewId": "Capterra___2535627",
            "switchedProducts": [
                {
                    "productId": 210413,
                    "productSlug": "Panda3D",
                    "productName": "Panda3D"
                }
            ],
            "reviewer": {
                "companySize": "11-50 employees",
                "role": ["1", "4", "8"],
                "jobTitle": "Game Developer",
                "timeUsedProduct": "6-12 months",
                "companyName": "Hashstash",
                "fullName": "Vishrut S.",
                "frequencyUsedProduct": "Weekly",
                "industry": "Computer Games",
                "verifiedLinkedIn": false,
                "profilePicUrl": null
            },
            "functionalityRating": 4,
            "chosenReasons": null,
            "generalComments": "It has been a good experience using CRYENGINE. It does tick all the boxes for a competent 3D game engine with awesome features, but it lacks in learning materials, documentation and a stellar community that some other game engines enjoy. ",
            "language": "en",
            "@version": "1",
            "productName": "CRYENGINE",
            "statusName": "Published",
            "title": "One of the best to use, Not the easiest to learn",
            "@timestamp": "2021-11-27T08:03:26.583Z",
            "vendorId": 2151455,
            "writtenOn": "2020-11-29 02:03:08 -0500",
            "adviceToOthers": "",
            "productId": 210664,
            "prosText": "CRYENGINE offers so much out of the box for game developers, like a tool bag full of features, ready and waiting to be put on your game. What I liked the most about it is the Realtime lighting and the state of the art Physics engine, along with the Powerful particle system. These are all features that would take a lot of time to be implemented from scratch and require quite some tinkering to achieve on other game engines. You get the latest and the greatest when using CRYENGINE, and it has powered some great AAA titles in the recent years, namelyCrysis, Kingdom Come and the Sniper Ghost games. ",
            "overallRating": 5,
            "incentivized": "NoIncentive",
            "valueForMoneyRating": 5,
            "consText": "The engine itself is excellent, but it is impaired by its poor documentation. The documentation is thin, and has archaic examples and code. Trying to do something when you are new will mostly lead you down a rabbit hole. The community is kind of non-existent and the resources/tutorials are sparse. So, that leads to the learning curve being high and few users. This needs to be addressed."
        },
        {
            "reviewId": "2554010",
            "customerSupportRating": 4,
            "switchingReasons": null,
            "completenessScore": 1.0800000429153442,
            "recommendationRating": 7,
            "anonymityOn": false,
            "sourceSite": "Capterra",
            "slug": "CRYENGINE",
            "translation": {
                "switchingReasons": null,
                "chosenReasons": null,
                "generalComments": null,
                "consText": null,
                "adviceToOthers": null,
                "title": null,
                "prosText": null
            },
            "easeOfUseRating": 3,
            "isPublished": true,
            "suggestedLocalProductId": ["210413"],
            "alternativeProducts": [],
            "vendorResponse": {
                "name": "Crytek GmbH",
                "date": null,
                "text": null
            },
            "globalReviewId": "Capterra___2554010",
            "switchedProducts": [
                {
                    "productId": 210413,
                    "productSlug": "Panda3D",
                    "productName": "Panda3D"
                }
            ],
            "reviewer": {
                "companySize": "11-50 employees",
                "role": ["1", "8"],
                "jobTitle": "Game Developer",
                "timeUsedProduct": "Less than 6 months",
                "companyName": "Hashstash",
                "fullName": "Binigya D.",
                "frequencyUsedProduct": "Monthly",
                "industry": "Computer Games",
                "verifiedLinkedIn": false,
                "profilePicUrl": null
            },
            "functionalityRating": 4,
            "chosenReasons": null,
            "generalComments": "It has been a good experience with CRYENGINE, and it will be my choice when making a AAA quality FPS game with a fun world to explore. ",
            "language": "en",
            "@version": "1",
            "productName": "CRYENGINE",
            "statusName": "Published",
            "title": "A fantastic Game Engine with few chinks in its armour",
            "@timestamp": "2021-11-27T07:37:27.886Z",
            "vendorId": 2151455,
            "writtenOn": "2020-12-07 03:27:18 -0500",
            "adviceToOthers": "",
            "productId": 210664,
            "prosText": "I really like how you can create graphically stunning games with a focus on FPS and terrain with CRYENGINE. Also, the Physics engine here is really robust and I love the destruction models built in to it, along with the water simulation and vegetation touch bending feature. These features together can get you on the fast track of making a very fun game. Finally, I loved that a good chunk of game assets that were used in CRYTEK games were already available to use in the marketplace.",
            "overallRating": 4,
            "incentivized": "NoIncentive",
            "valueForMoneyRating": 4,
            "consText": "What I liked the least about CRYENGINE is its daunting learning curve. You will need to take your time and learn how to use this massive game engine, it is not as user friendly at the start when compared to Unity or even Unreal. Another bigger and major concern is the inflexibility of this engine. It is primarily suited for FPS games with a focus on outdoor terrain, and trying to make other types of games will take some effort. Finally, the community and learning resources are scant for this engine, which hinders the overall experience of using CRYENGINE. "
        },
        {
            "reviewId": "2705304",
            "customerSupportRating": null,
            "switchingReasons": null,
            "completenessScore": 1.0700000524520874,
            "recommendationRating": 7,
            "anonymityOn": true,
            "sourceSite": "Capterra",
            "slug": "CRYENGINE",
            "translation": {
                "switchingReasons": null,
                "chosenReasons": null,
                "generalComments": null,
                "consText": null,
                "adviceToOthers": null,
                "title": null,
                "prosText": null
            },
            "easeOfUseRating": 3,
            "isPublished": true,
            "suggestedLocalProductId": [],
            "alternativeProducts": [],
            "vendorResponse": {
                "name": "Crytek GmbH",
                "date": null,
                "text": null
            },
            "globalReviewId": "Capterra___2705304",
            "switchedProducts": [],
            "reviewer": {
                "companySize": "201-500 employees",
                "role": ["1"],
                "jobTitle": null,
                "timeUsedProduct": "I used a free trial",
                "companyName": null,
                "fullName": "Verified Reviewer",
                "frequencyUsedProduct": "Weekly",
                "industry": "Oil & Energy",
                "verifiedLinkedIn": true,
                "profilePicUrl": null
            },
            "functionalityRating": 4,
            "chosenReasons": null,
            "generalComments": "Overall if you want great visuals and complex textures in your game this is one of the best game engine to approach.",
            "language": "en",
            "@version": "1",
            "productName": "CRYENGINE",
            "statusName": "Published",
            "title": "Best Visuals in the business",
            "@timestamp": "2021-11-27T08:44:09.130Z",
            "vendorId": 2151455,
            "writtenOn": "2021-02-18 17:26:32 -0500",
            "adviceToOthers": "",
            "productId": 210664,
            "prosText": "Cryengine is most famous for the visuals it provides and once was the staple in the industry. With its considerable revenue model, it's one of the best game engines to use to create a visually stunning game.",
            "overallRating": 5,
            "incentivized": "NoIncentive",
            "valueForMoneyRating": 5,
            "consText": "The only drawback which I faced was that since CryEngine is not so popular spread among indie developers it's comparatively hard to use than its competitors and also has a smaller community."
        }
    ],
    "countryCode": "US",
    "seoTestData": {}
}
```
