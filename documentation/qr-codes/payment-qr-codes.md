---
title: How to Create Payment QR Codes
sidebar_label: Payment QR Codes
tags: ['qr codes']
---

import Author from '@site/documentation/components/Author';
import CodeWithHighlights from '@site/documentation/components/CodeWithHighlights';
import Admonition from '@theme/Admonition';

# Creating Payment QR Codes

Generate QR codes that enable contactless payments when scanned. Payment QR codes are useful for businesses, freelancers, and individuals who want to make it easy for others to send them money without having to manually enter payment details.

## Payment QR Code Types

There are several formats for payment QR codes depending on the payment service you're using:

### 1. PayPal QR Codes

PayPal payment links use the following format:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://paypal.me/**username**/**amount**" />

For example:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://paypal.me/yourname/15" />

<img loading="lazy" src="https://quickchart.io/qr?text=https://paypal.me/yourname/15" />

This QR code will open PayPal with a pre-filled payment amount of $15 to the account "yourname".

### 2. Venmo QR Codes

Venmo payment links use the following format:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://venmo.com/**username**" />

For example:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://venmo.com/yourname" />

### 3. Cash App QR Codes

Cash App payment links use the following format:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://cash.app/$**username**/**amount**" />

For example:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://cash.app/$yourname/20" />

### 4. Cryptocurrency QR Codes

For cryptocurrency payments, you can create QR codes containing wallet addresses:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**bitcoin:**wallet_address**?amount=**amount**" />

For example (using a placeholder wallet address):

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**bitcoin:3FZbgi29cpjq2GjdwV8eyHuJJnkLtktZc5?amount=0.001" />

<img loading="lazy" src="https://quickchart.io/qr?text=bitcoin:3FZbgi29cpjq2GjdwV8eyHuJJnkLtktZc5?amount=0.001" />

Similar formats exist for other cryptocurrencies:
- Ethereum: `ethereum:0x...`
- Litecoin: `litecoin:L...`

## Creating Payment QR Codes in Spreadsheets

You can generate payment QR codes in bulk using spreadsheets. Here's an example formula for PayPal links:

```
="https://quickchart.io/qr?text=" & ENCODEURL("https://paypal.me/" & A2 & "/" & B2)
```

Where:
- Column A contains the PayPal username
- Column B contains the payment amount

For more details on using spreadsheets, see our guide on [generating QR codes in Excel and Google Sheets](/documentation/generate-qr-codes-excel-google-sheets/).

## Advanced Payment Parameters

### PayPal Parameters

You can add additional parameters to PayPal links:

- `/amount` - Specify the payment amount
- `?currency=EUR` - Change the currency (default is USD)

Example with EUR currency:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://paypal.me/yourname/15?currency=EUR" />

### Cryptocurrency Parameters

Bitcoin URI scheme supports several parameters:

- `amount` - The amount to send
- `label` - A label for the recipient address
- `message` - A message to attach to the transaction

Example with label and message:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**bitcoin:3FZbgi29cpjq2GjdwV8eyHuJJnkLtktZc5?amount=0.001&label=Donation&message=Thank%20you%20for%20your%20support!" />

## EMV QR Code Standard

For merchant payments, the EMV® QR Code specification (used by systems like Mastercard and Visa) provides a standardized format:

<Admonition type="info">
  EMV QR codes contain structured payment data following the EMV Co specifications. These are commonly used in retail settings and banking apps around the world.
</Admonition>

Creating EMV QR codes requires following specific data formatting requirements that vary by region and payment system. Consider using dedicated payment platforms that can generate these specialized QR codes for you.

## Customization Options

You can customize your payment QR codes using any of the [standard QR code parameters](/documentation/qr-codes/#qr-code-parameters). Here's an example with custom styling:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**https://paypal.me/yourname/25&**dark=**4285f4&**caption=**Pay with PayPal&**captionFontSize=**15" />

<img loading="lazy" src="https://quickchart.io/qr?text=https://paypal.me/yourname/25&dark=4285f4&caption=Pay with PayPal&captionFontSize=15" />

## Security Considerations

<Admonition type="caution">
  Payment QR codes provide direct access to payment methods. Always handle them securely and be aware that anyone who scans them will be able to send payments to the encoded account.
</Admonition>

## Best Practices

1. **Include clear instructions** - Add text near the QR code explaining what it's for and how much will be charged.
2. **Consider fixed vs. variable amounts** - For donations or variable payments, you might omit the amount parameter.
3. **Test before deployment** - Always scan your QR codes with different devices to ensure they work correctly.
4. **Regular verification** - Periodically scan your own QR codes to ensure they still work as expected.
5. **Security** - For cryptocurrency addresses, be especially careful to verify the address is correct.

## Use Cases

- **Donations** - Non-profits can display QR codes for quick donations
- **Tip jars** - Businesses can offer contactless tipping
- **Invoices** - Freelancers can add payment QR codes to invoices
- **Event tickets** - Include payment options for upgrades or merchandise
- **Street performers** - Display payment QR codes for people who don't carry cash
- **Restaurant bills** - Add payment QR codes to receipts for easy splitting and payment

## Need help?

For questions about generating payment QR codes, visit our [community forum](https://community.quickchart.io/).

To learn more about QR code customization options, check out the [QR code API documentation](/documentation/qr-codes/).

<Author />