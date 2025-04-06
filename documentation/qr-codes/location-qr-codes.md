---
title: How to Create Location QR Codes
sidebar_label: Location QR Codes
tags: ['qr codes']
---

import Author from '@site/documentation/components/Author';
import CodeWithHighlights from '@site/documentation/components/CodeWithHighlights';
import Admonition from '@theme/Admonition';

# Creating Location QR Codes

Generate QR codes that, when scanned, open a map application showing a specific location. This is perfect for businesses, events, tourist attractions, or any situation where you want to help people find a physical location easily.

## Location QR Code Formats

There are several ways to create location QR codes:

### 1. Using Geo URI Format

The Geo URI format is widely supported and uses the following structure:

<CodeWithHighlights wrap code="geo:**latitude**,**longitude**,**altitude**" />

The altitude parameter is optional and can be omitted. For example:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**geo:37.7749,-122.4194" />

<img loading="lazy" src="https://quickchart.io/qr?text=geo:37.7749,-122.4194" />

This QR code will open the default map app on the user's device pointing to the coordinates of San Francisco.

### 2. Using Google Maps URLs

You can also use direct Google Maps URLs to create more detailed location QR codes:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://maps.google.com/?q=**address or coordinates**" />

For example, with a specific address:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://maps.google.com/?q=1600+Amphitheatre+Parkway,+Mountain+View,+CA" />

<img loading="lazy" src="https://quickchart.io/qr?text=https://maps.google.com/?q=1600+Amphitheatre+Parkway,+Mountain+View,+CA" />

Or with coordinates:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://maps.google.com/?q=37.7749,-122.4194" />

### 3. Using Apple Maps URLs

For iOS devices, you can use Apple Maps links:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://maps.apple.com/?ll=**latitude**,**longitude**&q=**label**" />

For example:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://maps.apple.com/?ll=37.7749,-122.4194&q=San%20Francisco" />

## Creating Location QR Codes in Spreadsheets

You can generate location QR codes in bulk using spreadsheets. Here's an example formula for Google Maps URLs:

```
="https://quickchart.io/qr?text=" & ENCODEURL("https://maps.google.com/?q=" & A2 & "," & B2 & "&z=17")
```

Where:
- Column A contains the latitude
- Column B contains the longitude
- The `&z=17` parameter sets the zoom level (optional)

For addresses rather than coordinates:

```
="https://quickchart.io/qr?text=" & ENCODEURL("https://maps.google.com/?q=" & A2)
```

Where:
- Column A contains the full address

For more details on using spreadsheets, see our guide on [generating QR codes in Excel and Google Sheets](/documentation/generate-qr-codes-excel-google-sheets/).

## Advanced Map Parameters

### Google Maps Parameters

Google Maps URLs support several parameters:

- `q=` - Search query or address (can be coordinates or text)
- `z=` - Zoom level (0-21, higher is more zoomed in)
- `t=` - Map type (`m` for standard, `k` for satellite, `h` for hybrid)
- `layer=` - Additional layer (`t` for traffic, `c` for bicycling, `r` for transit)

Example with traffic layer:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://maps.google.com/?q=Times+Square,+New+York&layer=t" />

### Apple Maps Parameters

Apple Maps URLs support several parameters:

- `ll=` - Latitude and longitude
- `q=` - Label for the pin
- `z=` - Zoom level
- `t=` - Map type (`m` for standard, `k` for satellite, `h` for hybrid)
- `dirflg=` - Transportation type (`d` for driving, `w` for walking, `r` for transit)

## Adding Directions

You can create QR codes that not only show a location but also provide directions:

### Google Maps Directions

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://www.google.com/maps/dir/?api=1&destination=**destination**&travelmode=**mode**" />

Where mode can be `driving`, `walking`, `bicycling`, or `transit`. For example:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://www.google.com/maps/dir/?api=1&destination=Empire+State+Building,+New+York&travelmode=walking" />

<img loading="lazy" src="https://quickchart.io/qr?text=https://www.google.com/maps/dir/?api=1&destination=Empire+State+Building,+New+York&travelmode=walking" />

## Customization Options

You can customize your location QR codes using any of the [standard QR code parameters](/documentation/qr-codes/#qr-code-parameters). Here's an example with custom styling:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**geo:37.7749,-122.4194&**dark=**4285f4&**caption=**Find Us&**captionFontSize=**15" />

<img loading="lazy" src="https://quickchart.io/qr?text=geo:37.7749,-122.4194&dark=4285f4&caption=Find Us&captionFontSize=15" />

## Best Practices

1. **Use the right format** - For universal compatibility, the `geo:` URI format works well. For more detailed maps, use Google Maps URLs.
2. **Include a label or description** - When using map service URLs, include a clear label so users know what location they're looking at.
3. **Test on different devices** - Different phones may open different map apps by default, so test your QR codes on both Android and iOS devices.
4. **Consider QR code density** - Long URLs create more complex QR codes that may be harder to scan. Consider using a URL shortener if your map URL is very long.

## Use Cases

- **Business listings** - Add QR codes to your website, business cards, or marketing materials
- **Event locations** - Include a location QR code on event invitations or tickets
- **Tourist attractions** - Display QR codes at key points of interest or on brochures
- **Real estate listings** - Add QR codes that show property locations
- **Emergency meeting points** - Use QR codes to help people navigate to assembly points

## Need help?

For questions about generating location QR codes, visit our [community forum](https://community.quickchart.io/).

To learn more about QR code customization options, check out the [QR code API documentation](/documentation/qr-codes/).

<Author />