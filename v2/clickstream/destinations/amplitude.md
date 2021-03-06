---
title: Amplitude
sidebar: platform_sidebar
---

MetaRouter makes it easy to send your data to Amplitude. Once you follow the steps below, your data will be routed through our platform and pushed to Amplitude in the appropriate format.

## What is Amplitude and how does it work?

Amplitude is a behavioral data analytics tool that enables real-time cross-platform analytics so that marketers can view user activity on a dashboard. It also funnels audiences by custom events and actions like checkout completed, items added to cart, or payment entered. It integrates very nicely with Amazon Redshift for data access so that data scientists can analyze user drop off over time.

Implementing Amplitude natively in your stack requires a good amount of developer work; sending them user data requires mapping out your events and user traits to be collected and deciding which libraries and SDKs you'll need to use. You'll then need to install your libraries and SDKs of choice on all of your products.

[Learn more about Amplitude](https://amplitude.com/)

## Why send data to Amplitude using MetaRouter?

If you want to try out any other analytics application, implementing native event tracking for Amplitude is a waste of time. Going through the process of selecting and installing libraries and SDKs just for one tool will take your engineers a lot of time. Furthermore, if you plan to add more tools to your stack, the event tracking and custom coding work is going to be redundant and frustrating.

Integrating Amplitude with MetaRouter means that you will just need to install MetaRouter and enable Amplitude in your MetaRouter UI. You will only need to set up one event tracking library (MetaRouter's), and then you will be able to route and send data to Amplitude and any other destination of your choice without writing custom code for each one.

## Getting Started with Amplitude and MetaRouter

### Amplitude Side

To get started sending events to Amplitude, all you need is your API Key. After signing up for an Amplitude account, a page will load asking you to create an organization.

![amplitude1](../../../images/amplitude1.png)

You will then be prompted to create your first application. This application will function as your project to receive events from MetaRouter.

![amplitude2](../../../images/amplitude2.png)

After this application is created, an API Key will be generated and presented in your dashboard.

![amplitude3](../../../images/amplitude3.png)

### MetaRouter Side

Add this API Key to the Amplitude connector on the MetaRouter dashboard and give your new connection a unique name. Your pipeline will be activated once you click `Save`.

You can now go back into your amplitude account and see your user activity! To see exactly what events are being sent over, you can click around the `Events` and `User Activity` tabs.

### Additional Features

Note that MetaRouter will not pass `page` or `screen` calls by default. See the options below for enabling those specific calls.

* `Track All Pages` - Checking this box sends all `page` and `screen` calls to amplitude as `Loaded a Page`. This feature works with all source types.
* `Track Named Pages`- Checking this box will send all *named* `page` and `screen` calls to Amplitude. In your Amplitude dashboard, these will appear as `Loaded (Category) (Name) Page` or `Loaded (Category) (Name) Screen `. This feature works with Android, Server, and Web sources.
* `Track Categorized Pages` - Checking this box means that every time you call `page` or `screen` and provide a `category`, an event will be sent. It will appear in Amplitude as `Viewed (Category)Page` or `Viewed (Category) Screen`. This feature works with all source types.
* `Track UTM Properties` - Checking this box will track UTM properties found in the querystring to Amplitude. This feature is only available for Web sources.
* `Batch Events` - Checking this box causes events to be batched together and uploaded only if the number of unsent events is greater than or equal to the `Event Upload Threshold` or after the `Event Upload Period Millis` milliseconds have passed since the first unsent event was logged. You can set these parameters in the fields at the bottom of the Destination settings in the UI.
* `Use logRevenueV2 API` - This allows for the tracking of event properties with the revenue event. For example, you would be able to track a certain event and attach `price` and `quantity` properties to it. This feature will then log total revenue (`price`*`quantity`). 
* `Force Https` - If true, the events will always be uploaded to HTTPS endpoint. Otherwise the SDK will use the embedding site’s protocol.
* `Track GCLID` - If true, captures the gclid url parameter as well as the user’s initial_gclid via a set once operation.
* `Save Referrer Once Per Session` - If true then includeGclid, includeReferrer, and includeUtm will only track their respective properties once per session. New values that come in during the middle of the user’s session will be ignored. Set to false to always capture new values.
* `Set Device ID From URL Parameter` - If true, the SDK will parse device ID values from url parameter amp_device_id if available.
* `Map Query Params to Custom Property` - When sending data via server side, you can send the custom query params that are automatically collected by analytics.js (or whatever you manually send under context.page.search), by entering a custom property name you would like to map that under on the left hand side. On the right hand side, please choose whether you want the query params to be set on the user profile or event metadata level. Whatever you put on the left hand side we will map the entire query parameters string from the context.page.url. NOTE: Do not add more than one row. Adding more than one row in this setting will have no effect.

