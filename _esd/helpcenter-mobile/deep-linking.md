---
title: Deep Linking
layout: page
parent: _esd/helpcenter-mobile.md
categories: [Ecosystem, Analytics, Mobile, Android, iOS, deep linking]
---

## What is Deep Linking?

Deep linking enables mobile apps to accept incoming links to a specific location in the app. A mobile app may be linked from multiple sources, including:

*   Other mobile apps: Apps can use HTTP schemes to connect to your mobile app, like any website might connect to your website.
*   Mobile websites: Your website can provided 1-1 relevancy between web and mobile app pages. For example, a link to your mobile web can open up in your mobile app if the app is installed.
*   Search engines: All major search engines including Google support app indexing. If your app supports Deep Linking, users can access app directly from the search engine results.
*   Advertisements: Users can tap on ads and land on your mobile app, just like a normal website.
*   Emails: Newsletters, receipts, confirmations and more can link to your app when viewed on a mobile device.

All major platforms, including Android and iOS, support deep linking. This documentation scope covers Android and iOS deep linking. Here's how app-to-app deep linking works:

1.  Host App is configured to accept links from external apps.
2.  Linking App configures a UI that initiates a link to the Host App.
3.  The Linking App sends a request to Host App to open a certain page.
4.  The Host App accepts the request and opens the page.

Here's how ad, email, web and search engine deep linking works:

1.  Host App is configured to accept links from external apps.
2.  External sources can send a request to specific content within the app.
3.  The Host App accepts these links and parses the information given in them to show the specific content.

Deep Linking enables you to link to other Rakuten apps, mobile web pages and App Store pages.

## Why should I use Deep Linking?

#### Drive more traffic to your app

Deep Linking can greatly increase your app's exposure, as enabling deep linking also enables the contents of your app to be listed in Google search results. Deep linking creates opportunities to have affiliates, marketers, and other applications link to your app.

#### Increase app installs

Increased user traffic also means an increased number of installs. Users who discover your app through other resources they trust may be more willing to install your app.

#### Improve app usability

Deep linking enables app users to use features available in other Rakuten Ecosystem Mobile applications that may not be available in your application, increasing the overall usability of your application. For example, Rakuten Point Club uses deep linking to connect to the Rakuten Point Partner app to show the unique Application A, an application built to work with user-generated content that can deep link to Application B, an application built to translate user-generated content into other languages. Users of Application A can now expand their audience to speakers of other languages, and the Application A user experience is improved and expanded. Additionally, traffic is driven to Application B, an application in the same ecosystem.

## How do I plan for Deep Linking implementation?

Consider the following questions before implementing deep linking in your app:

#### What pages do you want other apps to link to?

You may want to consider app content that would be valuable to users who have not heard of your application. Example: The app generates a one time bar code unique for every user, and point-of-sale apps can link to my app to view the bar code. Other parts of the app, such as the About or Support sections, may not be as valuable for deep linking.

### In what use cases will other apps will link to your app?

*   Which particular pages would a user want to link to in your app?
*   What task would the user be performing while linking up?

#### Do I have corresponding mobile web pages for these pages?

*   A corresponding mobile page helps you have 1-1 deep linking to your native mobile app.

#### What parts of your mobile app do you want to hide from search engines or other apps?

You can exclude certain parts of your app from being indexed by search engines or being linked to from other apps.

#### What if my mobile app does not have a mobile web interface ?

Currently, deep linking is only available for the apps which have a corresponding mobile website. Similarly, Apple's universal links are currently only available for apps with corresponding mobile web interface.

## Can I use a Deep Link Framework for deep linking?

Rakuten Ecosystem Mobile recommends using native Android and iOS capabilities. There are two primary reasons for using native Android and iOS capabilities:

1.  Most of the frameworks have an underlying clause where they use the deep linking data generating from our apps to their advantage. While they promise not to disclose this data to anyone, there are many possibilities through which this data could potentially be disclosed to our competitors. For example, if a competitor acquires the framework that we are using, then this data will be legally available to them and they can view sensitive details. This can include products or campaigns, or customer segment responses to products and campaigns.
2.  All frameworks use underlying native Android and iOS components. Their unique selling points is usually not app indexing itself, but activitiesÂ associatedÂ with deep linking, such as segmention of data, tracking certain use cases andÂ parameterizing.

The Rakuten Ecosystem Mobile Team evaluated different frameworks including Branch.io and Circuit, but decided not to use them due to their data privacy policies. Â 

## How do I implement Deep Linking for iOS?

iOS endorses the use of universal links for deep linking. If a user has the app installed, the link is opened up in the app. If the user does not have the app installed, it is opened up in Safari. HTTP links can now be opened by native applications directly, rather than in the browser.Â This allows linking from anywhere into native apps,Â and makes deep-linking completely transparent.

| Main Points |
| -- |
| In addition to custom URL schemes, iOS 9 now supports normal http/https links for deep-linking (much like Android'sÂ _intents_). |
| This makes deep-linking into applications completely transparent. |
| Google App Indexing is not needed on iOS 9, since links shown in the browser are also deep links whenever the app is installed. |
| |

#### On Web:

*   On the website, anÂ `apple-app-site-association`Â file lists which applications are allowed to open certain URLs natively. The file must be accessible though HTTPS.

#### On App:

*   On iOS, the application associates itself with the website through the application's entitlements.

| Example: Rakuten Ichiba |
| -- |
| [https://item.rakuten.co.jp/apple-app-site-association](https://item.rakuten.co.jp/apple-app-site-association)Â could contain this |
| With this code, the Rakuten Ichiba application would declareÂ `[item.rakuten.co.jp](http://item.rakuten.co.jp/)`Â as an Associated Domain, in Xcode. It also needs to implement a method (`application:continueUserActivity:restorationHandler:`) to handle the links. This is the same method required by the application content indexing APIs. When any Rakuten Ichiba product page is opened from anywhere (Safari, email app, old-style webviews, new-style webviews, overlaid Safari controller, even programmatically) if the app is installed, it will open the product in the native Rakuten Ichiba native application |
``` 
{
      "applinks": {
        "apps": [],
        "details": [
          {
            "appID": "87CT3T3CK2.jp.co.rakuten.ichiba",
            "paths": [ "/*" ]
          }
        ]
      }
    }'
```

#### **References:**

*   [https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html](https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/AppSearch/UniversalLinks.html)

## Smart App Banners

Smart App Banners promote a native app from a product page, offering to open the current item. Mobile Safari can display a promotional card at the top of any website or product page that either deep links into a native app or offers to install it: confluence-embedded-file-wrapper">confluence-embedded-file-wrapper">![](https://confluence.rakuten-it.com/confluence/download/attachments/640750679/smartbanner_2x.png?version=1&modificationDate=1441258370627&api=v2)

![Smart Banner](../images/img_smartbanner.png)

| Main Points |
| -- |
| Supported since iOS 6 |
| Can open the app with custom parameters, thus enabling deep-linking.  |
| Complementary to iOS 9 universal links |
| |

#### In Web:

*   On the web site, pages must have the followingÂ `<meta>`Â element in theirÂ `<head>`:
    *   `<meta name="apple-itunes-app" content="app-id=myAppStoreID, affiliate-data=myAffiliateData, app-argument=myURL">`
*   The web server must allow theÂ `Applebot`Â web crawler in itsÂ `robots.txt`Â file.
*   As an alternative to the aboveÂ `<meta>`Â element, bothÂ [Twitter Cards](https://dev.twitter.com/cards/markup)Â andÂ [AppLinks](http://applinks.org/)Â can be used to markup the web page.

| Example: Rakuten Ichiba |
| -- |
| The page atÂ [http://item.rakuten.co.jp/dvdoutlet/4988113748018-0](http://item.rakuten.co.jp/dvdoutlet/4988113748018-0)Â should have this line inserted: `<meta name="apple-itunes-app" content="app-id=419267350, app-argument=rakuten-ichiba-app%3A%2F%[2Fwww.rakuten.co.jp](http://2fwww.rakuten.co.jp/)%2Fitem_detail%3Fitem_code%3D4988113748018-0">` The page atÂ [http://www.rakuten.co.jp/](http://www.rakuten.co.jp/)Â should have this line inserted: `<meta name="apple-itunes-app" content="app-id=419267350">`|
| **Result:** |
| When a user browses Rakuten Ichiba, if they don't have the app installed it will show a card inviting them to install it. |
| If they have it installed and are using iOS 7/8, it will show an "Open with app" card that will invoke the Rakuten Ichiba native application with theÂ `rakuten-ichiba-app://`Â URL embedded in the product page.rb |
| If they have it installed and are using iOS 9, they will never see this card because Universal Links will already have opened the item in the native Rakuten Ichiba application.|
| |

## Spotlight Search (Application content indexing) and HandOff Framework

Visit the [Spotlight search page](https://confluence.rakuten-it.com/confluence/pages/viewpage.action?pageId=841816960) for further details/

## Example use cases

*   Make the most-recently-accessed Ichiba products accessible from the system search bar.
*   Make past Ichiba orders accessible from the system search bar.
*   Make on-device Kobo books searchable.

## Deep linking betweenÂ applications

### 1) Show information that has a web version

Example scenario: an application wants to open anÂ item into Rakuten Books.

#### iOS 9

Open the URL to the web content (such asÂ `[http://books.rakuten.co.jp/rb/13376206/](http://books.rakuten.co.jp/rb/13376206/)`), and let Universal Links and Smart App Banners open your content in the native Books app or offer users to install it.

#### Previous versions

UseÂ [AppLinks](http://applinks.org/)Â to fetch your web content in the background and retrieve the information it needs to open the destination app or fallback to either opening the AppStore or the web version. On the web site, add AppLinks markup to each product page. On iOS, use the default call back URLÂ to open a deep-link using AppLinks.

### 2) {erform an action in the other app

Use theÂ [x-callback-url](http://x-callback-url.com/)Â protocol to support a standard way of handling data and back buttons. This requires knowing the URL scheme of the destination application beforehand.
| |
| Note |
| ---- |
| AppLinks deep-linking URLs can be constructed in a way that complies with the x-callback-url standard. The former is more of a content discovery protocol, whereas the latter is a deep-linking protocol. |
| |

 
## How do I implement Deep Linking for Android ?

To enable Deep Linking in your Android app, you must:

*   Add intent filters
*   Add activity logic

This is valid for:

*   Search results
*   Query autocompletions
*   Now on Tap search

## Declare Intents

In order for deep links from Google Search results OR from other mobile apps to trigger content views within your app, your app mustÂ declare intent filters. These intent filters are part of your Application Manifest. You can either haveÂ Â HTTP or custom scheme URIs for its content.Â Google recommends using HTTP schemes over Custom Schemes. HTTP filters formatted asÂ [http://recipe-app.com](http://recipe-app.com/)Â and custom filters are formatted asÂ recipe-app://Â .

**Supporting HTTP URIs**

If your app supports HTTP deep links,Â you may want to keep two things in mind:

*   Google can index your app contents without webpage markup (alternate tag). Therefore, you do not need to implement webpage markup (it is optional)
*   There are three types of android:scheme:
    1.  android:paths,Â 
    2.  android:pathPrefixsÂ 
    3.  android:pathPatterns3. Â 

android:path:Â The path attribute specifies a complete path that is matched against the complete path in an Intent object.Â 

| Example: android:path attribute |
| -- |
|< data android:scheme="http" android:host="[recipe-app.com](http://recipe-app.com/)" android:path="/recipes" />
| |

OnlyÂ [http://recipe-app.com/recipes/](http://recipe-app.com/recipes/)Â is allowed to respond to app indexing. s4">android:pathPrefix:Â pathPrefix attribute specifies a partial path that is matched against only the initial part of the path in the Intent object.Â 


| Example: android:pathPrefix: |
| -- |
| < data android:scheme="http" android:host="[recipe-app.com](http://recipe-app.com/)" android:pathPrefix="/recipes" /> |

All the pages below [http://recipe-app.com/recipes/](http://recipe-app.com/recipes/) directory and URL itself are allowed to respond to app indexing.

android:pathPattern:Â pathPattern attribute specifies a complete path that is matched against the complete path in the Intent object, but it can contain wildcards. 

See theÂ Google Developers guidelines for more details:Â [http://developer.android.com/intl/ja/guide/topics/manifest/data-element.html#path](http://developer.android.com/intl/ja/guide/topics/manifest/data-element.html#path)

| Example: Rakuten Ichiba |
| -- |

```
<span class="tag">&lt;activity<span class="pln">
  <span class="atn">android:name<span class="pun">=<span class="atv">"com.example.android.Rakuten"<span class="pln">
  <span class="atn">android:label<span class="pun">=<span class="atv">"@string/item_detail"<span class="pln"> <span class="tag">&gt;<span class="pln">
  <span class="tag">&lt;intent-filter<span class="pln"> <span class="atn">android:label<span class="pun">=<span class="atv">"@string/filter_item_viewdetail"<span class="tag">&gt;<span class="pln">
    <span class="tag">&lt;action<span class="pln"> <span class="atn">android:name<span class="pun">=<span class="atv">"android.intent.action.VIEW"<span class="pln"> <span class="tag">/&gt;<span class="pln">
    <span class="tag">&lt;category<span class="pln"> <span class="atn">android:name<span class="pun">=<span class="atv">"android.intent.category.DEFAULT"<span class="pln"> <span class="tag">/&gt;<span class="pln">
    <span class="tag">&lt;category<span class="pln"> <span class="atn">android:name<span class="pun">=<span class="atv">"android.intent.category.BROWSABLE"<span class="pln"> <span class="tag">/&gt;<span class="pln">
    <span class="com">&lt;!-- Accepts URIs that begin with "ichiba-app://recipes" --&gt;<span class="pln">
    <span class="tag">&lt;data<span class="pln"> <span class="atn">android:scheme<span class="pun">=<span class="atv">"items"
```

```
<span class="pln"> <span class="atn">android:host<span class="pun">=<span class="atv">"<span class="com">rakuten.co.jp<span class="atv">"<span class="pln"> <span class="tag">/&gt; |
```

```
<span class="pln">Â  Â  Â <span class="tag">&lt;/intent-filter&gt;<span class="pln"> |
<span class="tag">&lt;intent-filter<span class="pln">Â <span class="atn">android:label<span class="pun">=<span class="atv">"@string/filter_item_viewdetail"<span class="tag">&gt;<span class="pln">  |
<span class="tag">&lt;action<span class="pln">Â <span class="atn">android:name<span class="pun">=<span class="atv">"android.intent.action.VIEW"<span class="pln">Â <span class="tag">/&gt;<span class="pln"> |
<span class="tag">&lt;category<span class="pln">Â <span class="atn">android:name<span class="pun">=<span class="atv">"android.intent.category.DEFAULT"<span class="pln">Â <span class="tag">/&gt;<span class="pln"> |
<span class="tag">&lt;category<span class="pln">Â <span class="atn">android:name<span class="pun">=<span class="atv">"android.intent.category.BROWSABLE"<span class="pln">Â <span class="tag">/&gt;<span class="pln"> |
<span class="com">&lt;!-- Accepts URIs that begin with "http://rakuten.co.jp/recipes" --&gt;<span class="pln"> |
<span class="tag">&lt;data<span class="pln">Â <span class="atn">android:scheme<span class="pun">=<span class="atv">"http"<span class="pln"> |
<span class="atn">android:host<span class="pun">=<span class="atv">"<span class="com">rakuten.co.jp" |
```

Once you have added intent filters with URIs for activity content to your app manifest, Android is able to route anyÂ `[Intent](https://developer.android.com/reference/android/content/Intent.html)`Â that has matching URIs to your app at runtime.

## Handling Deep Link Intents

AfterÂ the system starts the app activity through an intent filter, use the data provided by the Intent to determine your app's view response. Call theÂ `getData()`Â andÂ `getAction()`Â methods to retrieve the data and action associated with the incoming Intent. You can call these methods at any time during the lifecycle of the activity, but you should generally do so during early callbacks such asÂ `onCreate()`Â orÂ `onStart()`. SeeÂ [Support HTTP URLs in Your App](https://firebase.google.com/docs/app-indexing/android/app)Â for moreÂ information.

## Publishing Deep Links

You can either use the Google's App Indexing API or provide access to Google Bot. SeeÂ [Add the App Indexing API](https://firebase.google.com/docs/app-indexing/android/activity)Â for more information.

*   Google Developer:Â [https://developer.android.com/training/app-indexing/deep-linking.html](https://developer.android.com/training/app-indexing/deep-linking.html)
*   Android Developer:Â [https://developers.google.com/app-indexing/android/app](https://developers.google.com/app-indexing/android/app)
*   Codelabs:Â [http://search-codelabs.appspot.com/codelabs/android-deep-linking#1](http://search-codelabs.appspot.com/codelabs/android-deep-linking#1)

##### Requirements for Android:

*   Currently, apps should not be above API index 17 as requirement for App indexing. Â However,Â this does not stopsus from implementing deep links or app indexing.

# What KPIs should I track for Deep Linking ?

*   The most important KPI isÂ the performance of your deep linking efforts. How many deep links did your app receive?
*   Another important factor isÂ the segmentation of the traffic sources for deep linking. Who is sending deep link requests?
*   Other custom KPIs can also be setup and tracked using deep links.

## How do I track KPIs?

### For iOS:

Here are listed a few ways to track and report deep linking data:


|Condition | Event |
| -------- | ----- |
| The URL returned by the GoogleAppIndexing SDK is different from the URL passed to it. | The user opened the application through a deep-link found in a Google Web Search result page. |
| The URL the app is processing usesÂ `http://`Â or `https://`Â schemes. | The user opened the application using universal links.Â The identifier of the application that initiated the launch of our app is provided by iOS. Other information can be passed by the initiator using query string parameters (e.g.Â `&foo=bar`). |
| The URL the app is processing uses a custom URL scheme | This is application-dependent. If the link conforms to x-callback-url, more information can be retrieved, such as the URL meant to be called back when the user presses the back button. |
|  |  |


## How do I test Deep Linking?

## Testing Your Deep Links

At Code level, on Android, theÂ Android Studio lint (version 1.3+) automatically flags deep link syntax errors for your intent filters. However,Â this only checks for errors in code. For full circle debugging, most simulators on the market only support running one mobile application at a time, which makes testing deep linkingdifficult. Usually, deep linkingÂ must be tested on a real device. However, services do exist that help you automate on-device testing.

### Xamarin

One service,Â [Xamarin](http://xamarin.com/), runs real devices in the cloud. It allows you to run tests on devices of your choice and supports automation tests withÂ [Cucumber](https://cukes.info/).

### Cucumber

[Cucumber](https://cukes.info/)Â requires specifications in the form ofÂ Behavior Driven Development (BDD)Â scenarios. Â You can accessÂ BDDÂ scenarios used for theÂ Deep LinkingÂ example in the QA app bundled in theÂ SDK source code [here](https://confluence.rakuten-it.com/confluence/display/REM/BDD+Specifications+for+testing+Deep+Linking+in+QA+App). Use these files as a template to writeÂ Deep LinkingÂ scenarios forÂ [Cucumber](https://cukes.info/).

## How can Rakuten Ecosystem Mobile help meÂ achieve myÂ deep linking targets?

### Generating Deep Links for your mobile web

TheÂ Deep Linking Configuration ServiceÂ in REMS will automatically configure yourÂ Meta Pages.Â This is especially helpful if you have a large numbers of mobile web pages accepting links from native mobile apps, or native mobile apps accepting links from other native apps. To access theÂ Deep Linking Configuration Service:

1.  ContactÂ via
[Inquiry Form](https://developers.rakuten.com/hc/en-us/requests/new?ticket_form_id=399907)Â to get access toÂ Ecosystem Mobile Services.
2.  Add your application as aÂ Service.
3.  Create aÂ Meta Page.

### Sample Application

TheÂ Ecosystem Demo Application, provided in theÂ SDK source repositoryÂ is a sample app that implements an end-to-end deep linking module. If you need access to theÂ Ecosystem DemoÂ ApplicationÂ on your personal phone, query Â via
[Inquiry Form](https://developers.rakuten.com/hc/en-us/requests/new?ticket_form_id=399907)Â for a Hockey app invite. You can reference theÂ Ecosystem DemoÂ ApplicationÂ code to set up deep linkingÂ in your own mobile application.

### Additional Resources

[SDK Reference Documentation](---) [Google App indexing FAQs](https://developers.google.com/app-indexing/support/faq) For all other inquiries, contact us viaÂ [Inquiry Form](https://developers.rakuten.com/hc/en-us/requests/new?ticket_form_id=399907)