# BookLeaf-Assignment-2.
# Author Royalty Dashboard & Automated Notification System

## Overview

This project is an author royalty dashboard and admin portal built with Bubble, integrated with n8n and Google Gemini for AI-assisted royalty summary generation.

## Tech Stack

- **Frontend and application:** Bubble
- **Workflow automation:** n8n
- **AI integration:** Google Gemini
- **Data storage:** Bubble database
- **Integration:** Webhook and HTTP requests

## Features

### Author Portal
- Author login and dashboard
- View books associated with the logged-in author
- View copies sold, total royalty earned, royalty paid, and pending royalty
- Royalty summary and book publication status

### Admin Portal
- Separate admin login
- View the author list
- Search authors by name and filter by city
- View dashboard statistics

### AI-assisted Royalty Summary
- An n8n webhook receives royalty summary data.
- Google Gemini generates a professional email draft using the supplied author and book information.
- The draft includes royalty figures, publication status, quarterly payout guidance, and the minimum payout threshold.

## Business Rules

- Author royalty is based on the provided royalty data, not calculated from the book's MRP.
- The royalty policy specifies an 80/20 split of net profit after applicable costs.
- Royalties follow a quarterly payment cycle, with payment within 45 days after quarter-end.
- The minimum payout threshold is ₹1,000; eligible unpaid amounts roll over according to the supplied policy.
- Production books are shown with their current status.

## Setup and Testing

1. Open the Bubble application: https://harshitabisht794.bubbleapps.io/version-test
2. Sign in using the separate test credentials provided to the reviewer.
3. Test the author dashboard using an author account.
4. Test the author list, name search, and city filter using an admin account.
5. Open the exported n8n workflow and send a POST request to the `royalty-summary` webhook with sample author and book data.
6. Inspect the successful execution output from the Google Gemini node to review the generated email draft.

Do not commit passwords, API keys, webhook secrets, or other credentials to this repository.

## Current Limitations

- Gemini email draft generation has been tested in n8n.
- Automatic delivery of the generated email has not been completed.
- The callback from n8n to Bubble for recording notification results was blocked by the current Bubble subscription's API restriction.
- Consequently, end-to-end notification logging and delivery should not be considered fully operational.
- The source dataset provides cumulative royalty values and the last payout date, not a complete transaction-level payout history. The application does not invent individual payout records.

## Future Improvements

- Enable the required Bubble API access and complete notification callback integration.
- Add a configured email provider for actual email delivery.
- Complete notification history and delivery-status tracking.
- Add stronger production authentication and webhook-secret validation.
- Expand automated testing for authorization, data isolation, and error handling.

## Project Status

The Bubble author and admin login flows and the n8n Gemini draft-generation step have been tested. The email delivery and Bubble notification callback remain incomplete, as described above.
