---
title: How to Create Email QR Codes
sidebar_label: Email QR Codes
tags: ['qr codes']
---

import Author from '@site/documentation/components/Author';
import CodeWithHighlights from '@site/documentation/components/CodeWithHighlights';
import Admonition from '@theme/Admonition';

# Creating Email QR Codes

Generate QR codes that, when scanned, open the user's email client with a pre-filled email address, subject, and message body. This is useful for contact forms, feedback collection, and making it easy for people to reach you without having to manually type your email address.

## Email QR Code Format

Email QR codes use the `mailto:` URI scheme with the following format:

<CodeWithHighlights wrap code="mailto:**email_address**?subject=**email_subject**&body=**email_body**" />

Where:
- **email_address**: The recipient's email address
- **subject**: (Optional) The pre-filled email subject
- **body**: (Optional) The pre-filled email message body

For example, a basic email QR code with just the address:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**mailto:contact@example.com" />

<img loading="lazy" src="https://quickchart.io/qr?text=mailto:contact@example.com" />

And a more complex example with subject and body:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**mailto:contact@example.com?subject=Website%20Inquiry&body=Hello%2C%0A%0AI%20have%20a%20question%20about%20your%20services.%0A%0ARegards%2C" />

<img loading="lazy" src="https://quickchart.io/qr?text=mailto:contact@example.com?subject=Website%20Inquiry&body=Hello%2C%0A%0AI%20have%20a%20question%20about%20your%20services.%0A%0ARegards%2C" />

## Creating Email QR Codes in Spreadsheets

You can generate email QR codes in bulk using spreadsheets. Here's an example formula:

```
="https://quickchart.io/qr?text=" & ENCODEURL("mailto:" & A2 & "?subject=" & B2 & "&body=" & C2)
```

Where:
- Column A contains the email address
- Column B contains the subject line
- Column C contains the email body

For more details on using spreadsheets, see our guide on [generating QR codes in Excel and Google Sheets](/documentation/generate-qr-codes-excel-google-sheets/).

## Multiple Recipients

You can include multiple recipients by separating email addresses with commas:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**mailto:person1@example.com,person2@example.com?subject=Meeting%20Request" />

## Including CC and BCC

You can include CC and BCC recipients by adding additional parameters:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**mailto:main@example.com?cc=cc@example.com&bcc=bcc@example.com&subject=Team%20Update" />

## Formatting the Email Body

For line breaks in the email body, use `%0A` (the URL-encoded form of a newline character):

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**mailto:contact@example.com?subject=Feedback&body=Hello%2C%0A%0AHere%20is%20my%20feedback%3A%0A%0A%0AThank%20you." />

This creates a body with:
```
Hello,

Here is my feedback:


Thank you.
```

## Customization Options

You can customize your email QR codes using any of the [standard QR code parameters](/documentation/qr-codes/#qr-code-parameters). Here's an example with custom styling:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**mailto:contact@example.com&**dark=**4285f4&**caption=**Email Us&**captionFontSize=**15" />

<img loading="lazy" src="https://quickchart.io/qr?text=mailto:contact@example.com&dark=4285f4&caption=Email Us&captionFontSize=15" />

## Best Practices

1. **Keep it simple** - While you can pre-fill subjects and body text, shorter content makes for easier-to-scan QR codes.
2. **URL encode special characters** - Make sure to URL encode the entire mailto string, especially when including special characters or spaces.
3. **Test your QR codes** - Always scan your QR codes with different devices to ensure they work correctly.
4. **Consider privacy** - Be mindful that including both CC and BCC recipients in a QR code means that anyone who scans the code will see all the email addresses.

## Use Cases

- **Business cards** - Add a QR code that opens an email directly to your business email
- **Customer feedback** - Create QR codes with pre-filled subject lines like "Feedback about your experience"
- **Event RSVPs** - Generate QR codes that create email responses with pre-filled RSVP information
- **Support requests** - Create QR codes that pre-fill technical details to make support requests more efficient

## Need help?

For questions about generating email QR codes, visit our [community forum](https://community.quickchart.io/).

To learn more about QR code customization options, check out the [QR code API documentation](/documentation/qr-codes/).

<Author />