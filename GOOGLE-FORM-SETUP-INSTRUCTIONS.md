# Google Form Setup for Workshop Bookings

## Step 1: Create Google Form

1. Go to https://forms.google.com
2. Click "+ Blank" to create new form
3. Title: "Vibe Coding Workshop Bookings"

## Step 2: Add These Fields (in order)

1. **Workshop** (Dropdown)
   - AI Assistants (Beginner)
   - Vibe Coding for PMs (Beginner)
   - Vibe Coding: Pro (Advanced)
   - Product Teams Workshop
   - Design + Code (Beginner)
   - Design Systems (Advanced)
   - AI Design Sprint

2. **Number of Participants** (Short answer, Number)

3. **Format** (Dropdown)
   - Remote (Zoom)
   - In-Person (Tel Aviv)

4. **Name** (Short answer, Required)

5. **Email** (Short answer, Email validation, Required)

6. **Company** (Short answer, Optional)

7. **Message** (Paragraph)

## Step 3: Link to Spreadsheet

1. In form, click "Responses" tab
2. Click green spreadsheet icon
3. Select "Create a new spreadsheet"
4. Name it: "Workshop Bookings"

## Step 4: Get Form IDs

1. Click "Send" button
2. Click "<>" (embed icon)
3. Copy the iframe src URL
4. It looks like: `https://docs.google.com/forms/d/e/FORM_ID/viewform`
5. Save the FORM_ID

## Step 5: Get Field Entry IDs

1. Open form in preview mode
2. Right-click any field → Inspect
3. Find `entry.XXXXXXXXXX` for each field
4. Note down all entry IDs:
   - Workshop: entry.________
   - Participants: entry.________
   - Format: entry.________
   - Name: entry.________
   - Email: entry.________
   - Company: entry.________
   - Message: entry.________

## Step 6: Update workshops.html

Replace this line (around line 865):
```javascript
const googleFormUrl = 'https://docs.google.com/forms/d/e/1FAIpQLSd_REPLACE_WITH_YOUR_FORM_ID/formResponse';
```

With your actual form ID:
```javascript
const googleFormUrl = 'https://docs.google.com/forms/d/e/YOUR_ACTUAL_FORM_ID/formResponse';
```

And replace entry IDs (lines 867-873):
```javascript
'entry.YOUR_WORKSHOP_ID': workshop,
'entry.YOUR_PARTICIPANTS_ID': participants,
'entry.YOUR_FORMAT_ID': format,
'entry.YOUR_NAME_ID': name,
'entry.YOUR_EMAIL_ID': email,
'entry.YOUR_COMPANY_ID': company,
'entry.YOUR_MESSAGE_ID': message
```

## Step 7: Test

1. Fill out your form on the website
2. Check if data appears in your Google Sheet
3. If not, verify entry IDs are correct

## Current Pricing Logic (Already Implemented)

- Base: ₪14,200 for 20 people
- Each person more: +₪200
- Each person less: -₪200
- In-person: +₪5,000

Examples:
- 15 people remote: ₪13,200
- 20 people remote: ₪14,200
- 25 people remote: ₪15,200
- 20 people in-person: ₪19,200

## What's Already Done

✅ Sophisticated slider widget (1-50 people)
✅ Real-time price calculation
✅ Removed blue circle image
✅ Removed "Product Manager @ ZoomInfo"
✅ Form connected to Google Forms
✅ Fallback to LinkedIn if form fails

## What You Need to Do

1. Create the Google Form (5 minutes)
2. Get the Form ID and Entry IDs (10 minutes)
3. Update workshops.html with your IDs (2 minutes)
4. Test the form (1 minute)
5. Commit and push

Total time: ~18 minutes to have fully working booking system!