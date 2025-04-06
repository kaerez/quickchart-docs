---
title: How to Create Calendar Event QR Codes
sidebar_label: Calendar Event QR Codes
tags: ['qr codes']
---

import Author from '@site/documentation/components/Author';
import CodeWithHighlights from '@site/documentation/components/CodeWithHighlights';
import Admonition from '@theme/Admonition';

# Creating Calendar Event QR Codes

Generate QR codes that, when scanned, add events directly to a user's calendar. This is useful for event promotions, conference schedules, webinar invitations, and any situation where you want to make it easy for people to add your event to their calendar.

## Calendar Event QR Code Format

Calendar event QR codes use the iCalendar (iCal) format which follows a specific structure:

<CodeWithHighlights wrap code="BEGIN:VCALENDAR
VERSION:2.0
BEGIN:VEVENT
SUMMARY:**Event Title**
DTSTART:**Start Date and Time**
DTEND:**End Date and Time**
LOCATION:**Event Location**
DESCRIPTION:**Event Description**
END:VEVENT
END:VCALENDAR" />

The dates need to be in the format: `YYYYMMDDTHHMMSSZ` where:
- `YYYY` is the year
- `MM` is the month (01-12)
- `DD` is the day (01-31)
- `T` is a literal character separating the date from time
- `HH` is the hour in 24-hour format (00-23)
- `MM` is the minutes (00-59)
- `SS` is the seconds (00-59)
- `Z` indicates that the time is in UTC time zone

For example:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**BEGIN%3AVCALENDAR%0AVERSION%3A2.0%0ABEGIN%3AVEVENT%0ASUMMARY%3AAnnual%20Conference%0ADTSTART%3A20240520T090000Z%0ADTEND%3A20240520T170000Z%0ALOCATION%3A123%20Main%20St%2C%20Conference%20Center%0ADESCRIPTION%3AAnnual%20company%20conference%20with%20keynote%20speakers%20and%20networking%20events.%0AEND%3AVEVENT%0AEND%3AVCALENDAR" />

<img loading="lazy" src="https://quickchart.io/qr?text=BEGIN%3AVCALENDAR%0AVERSION%3A2.0%0ABEGIN%3AVEVENT%0ASUMMARY%3AAnnual%20Conference%0ADTSTART%3A20240520T090000Z%0ADTEND%3A20240520T170000Z%0ALOCATION%3A123%20Main%20St%2C%20Conference%20Center%0ADESCRIPTION%3AAnnual%20company%20conference%20with%20keynote%20speakers%20and%20networking%20events.%0AEND%3AVEVENT%0AEND%3AVCALENDAR" />

## Creating Calendar Event QR Codes in Spreadsheets

You can generate calendar event QR codes in bulk using spreadsheets. Here's an example formula that creates a QR code URL:

```
="https://quickchart.io/qr?text=" & ENCODEURL("BEGIN:VCALENDAR" & CHAR(10) & 
"VERSION:2.0" & CHAR(10) & 
"BEGIN:VEVENT" & CHAR(10) & 
"SUMMARY:" & A2 & CHAR(10) & 
"DTSTART:" & B2 & CHAR(10) & 
"DTEND:" & C2 & CHAR(10) & 
"LOCATION:" & D2 & CHAR(10) & 
"DESCRIPTION:" & E2 & CHAR(10) & 
"END:VEVENT" & CHAR(10) & 
"END:VCALENDAR")
```

Where:
- Column A contains the event title
- Column B contains the start date and time in the format `YYYYMMDDTHHMMSSZ`
- Column C contains the end date and time in the format `YYYYMMDDTHHMMSSZ`
- Column D contains the location
- Column E contains the description

For more details on using spreadsheets, see our guide on [generating QR codes in Excel and Google Sheets](/documentation/generate-qr-codes-excel-google-sheets/).

## Advanced Calendar Properties

You can add more properties to your calendar events:

### Adding Organizer Information

```
ORGANIZER;CN=Event Organizer:mailto:organizer@example.com
```

### Adding Reminder/Alarm

```
BEGIN:VALARM
TRIGGER:-PT1H
ACTION:DISPLAY
DESCRIPTION:Reminder
END:VALARM
```
This creates a reminder 1 hour before the event.

### Adding Event URL

```
URL:https://example.com/event-details
```

### Recurring Events

For a weekly recurring event:

```
RRULE:FREQ=WEEKLY;COUNT=10
```

This creates an event that repeats weekly for 10 occurrences.

## Customization Options

You can customize your calendar event QR codes using any of the [standard QR code parameters](/documentation/qr-codes/#qr-code-parameters). Here's an example with custom styling:

<CodeWithHighlights wrap code="https://quickchart.io/qr?**text=**BEGIN%3AVCALENDAR...&**dark=**4285f4&**caption=**Add to Calendar&**captionFontSize=**15" />

## Full Example

Here's a complete example for a conference event:

<CodeWithHighlights wrap code="BEGIN:VCALENDAR
VERSION:2.0
BEGIN:VEVENT
SUMMARY:Tech Conference 2024
DTSTART:20240610T090000Z
DTEND:20240612T170000Z
LOCATION:San Francisco Convention Center
DESCRIPTION:Annual technology conference featuring workshops, keynotes, and networking opportunities. Don't forget to bring your laptop!
ORGANIZER;CN=Tech Conference Team:mailto:info@techconference.example
URL:https://techconference.example
BEGIN:VALARM
TRIGGER:-P1D
ACTION:DISPLAY
DESCRIPTION:Conference starts tomorrow!
END:VALARM
END:VEVENT
END:VCALENDAR" />

To convert this to a QR code URL, URL-encode the entire content and append it to:

```
https://quickchart.io/qr?text=
```

## Tips

1. **Test your QR codes** - Always scan your QR codes with different devices to ensure they work correctly.
2. **Keep event details concise** - The more text in the QR code, the more complex it becomes, which might affect scannability.
3. **Consider time zones** - The 'Z' suffix indicates UTC time. Make sure to convert your local time to UTC or specify a time zone.
4. **URL encode special characters** - Make sure to URL encode the entire calendar event string.

## Need help?

For questions about generating calendar event QR codes, visit our [community forum](https://community.quickchart.io/).

To learn more about QR code customization options, check out the [QR code API documentation](/documentation/qr-codes/).

<Author />