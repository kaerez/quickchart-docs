---
title: How to Create App Store QR Codes
sidebar_label: App Store QR Codes
tags: ['qr codes']
---

import Author from '@site/documentation/components/Author';
import CodeWithHighlights from '@site/documentation/components/CodeWithHighlights';
import Admonition from '@theme/Admonition';

# Creating App Store QR Codes

Generate QR codes that, when scanned, direct users to your app's listing on the Apple App Store, Google Play Store, or other app marketplaces. These QR codes make it easy for users to discover and download your app without having to search for it manually.

## App Store QR Code Formats

Different app stores use different URL formats:

### 1. Apple App Store

For iOS apps, use the App Store link format:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://apps.apple.com/**country**/app/**app-name**/**id**" />

Or the shorter format:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://apps.apple.com/app/**id**" />

For example:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://apps.apple.com/us/app/instagram/id389801252" />

<img loading="lazy" src="https://quickchart.io/qr?text=https://apps.apple.com/us/app/instagram/id389801252" />

### 2. Google Play Store

For Android apps, use the Play Store link format:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://play.google.com/store/apps/details?id=**package_name**" />

For example:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://play.google.com/store/apps/details?id=com.instagram.android" />

<img loading="lazy" src="https://quickchart.io/qr?text=https://play.google.com/store/apps/details?id=com.instagram.android" />

### 3. Universal App Links

For a single QR code that works across both platforms, you can use app landing pages or URL shorteners that detect the device and redirect to the appropriate store:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://yourappwebsite.com/download" />

Or use a service like [Firebase Dynamic Links](https://firebase.google.com/docs/dynamic-links) which can create intelligent app links.

## Finding Your App IDs

### Apple App Store ID

To find your iOS app's ID:
1. Go to the App Store and navigate to your app
2. Look at the URL in your browser - it will contain the ID after `/id` (e.g., `.../id389801252`)

### Google Play Package Name

To find your Android app's package name:
1. Go to the Google Play Store and navigate to your app
2. Look at the URL in your browser - it will contain the package name after `?id=` (e.g., `...?id=com.instagram.android`)

## Creating App Store QR Codes in Spreadsheets

You can generate app store QR codes in bulk using spreadsheets. Here's an example formula:

```
="https://quickchart.io/qr?text=" & ENCODEURL("https://apps.apple.com/app/id" & A2)
```

Where:
- Column A contains the App Store IDs

For Google Play:

```
="https://quickchart.io/qr?text=" & ENCODEURL("https://play.google.com/store/apps/details?id=" & B2)
```

Where:
- Column B contains the package names

For more details on using spreadsheets, see our guide on [generating QR codes in Excel and Google Sheets](/documentation/generate-qr-codes-excel-google-sheets/).

## Advanced App Store Parameters

### Apple App Store Parameters

App Store links support additional parameters:

- `?mt=8` - Traditional parameter to specify it's an iOS app (usually optional now)
- `?pt=123456` - Affiliate token for tracking (if you're part of the affiliate program)
- `?ct=your_campaign` - Campaign token for analytics

Example with affiliate tracking:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://apps.apple.com/us/app/id389801252?pt=123456&ct=qr_promotion" />

### Google Play Store Parameters

Play Store links support referral parameters:

- `&referrer=utm_source%3Dqrcode` - Track installs from QR codes
- Add UTM parameters for campaign tracking

Example with campaign tracking:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://play.google.com/store/apps/details?id=com.instagram.android&referrer=utm_source%3Dqrcode%26utm_medium%3Dmarketing%26utm_campaign%3Dspring_promo" />

## App Store Short Links

Both app stores offer shorter URL formats which are useful for creating less dense QR codes:

### Apple App Short Links

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://apple.co/3aBcDeF" />

To create these, use the [Apple App Store Marketing Tools](https://tools.applemediaservices.com/app-store/).

### Google Play Short Links

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://play.google.com/store/apps/details?id=com.example.app&shortlink=abcdef" />

## Customization Options

You can customize your app store QR codes using any of the [standard QR code parameters](/documentation/qr-codes/#qr-code-parameters). Here's an example with custom styling:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://apps.apple.com/app/id389801252&**dark=**4285f4&**caption=**Download Our App&**captionFontSize=**15" />

<img loading="lazy" src="https://quickchart.io/qr?text=https://apps.apple.com/app/id389801252&dark=4285f4&caption=Download Our App&captionFontSize=15" />

## Pre-Installation Deep Links

For advanced use cases, you can create QR codes that not only direct users to download your app but also perform a specific action once the app is installed:

### iOS Universal Links

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://yourappwebsite.com/special-offer" />

### Android App Links

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://yourdomain.com/special-offer" />

<Admonition type="info">
  For deep links to work, your app must be configured to handle universal links (iOS) or app links (Android). This requires additional setup in your app and web server.
</Admonition>

## Best Practices

1. **Use short URLs** - The simpler the URL, the less dense the QR code will be, making it easier to scan.
2. **Include branding** - Add your app icon nearby or use a logo in the QR code to increase recognition.
3. **Track installations** - Use referral parameters to measure the effectiveness of your QR codes.
4. **Test thoroughly** - Scan your QR codes on both iOS and Android devices to ensure they work correctly.
5. **Call to action** - Include text near the QR code that explains what it's for, e.g., "Scan to download our app."

## Use Cases

- **Marketing materials** - Include app QR codes on flyers, posters, and business cards
- **Product packaging** - Add QR codes to physical products to encourage app downloads for enhanced features
- **Trade shows** - Display QR codes at your booth for quick app downloads
- **Print advertisements** - Include QR codes in magazine and newspaper ads
- **In-store displays** - Add QR codes to in-store displays for app-exclusive discounts or features
- **Business locations** - Display QR codes in restaurants, stores, or offices for loyalty programs

## Need help?

For questions about generating app store QR codes, visit our [community forum](https://community.quickchart.io/).

To learn more about QR code customization options, check out the [QR code API documentation](/documentation/qr-codes/).

<Author />