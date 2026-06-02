# Feature Examples

These examples show the kind of stakeholder-ready output the `explain-feature` skill should produce.

## 1. Laravel feature

Input:

```text
Audience: Product Manager
Complexity: Detailed
Feature: Laravel order export job that lets admins export filtered order data as a CSV file. The export runs in the background and emails the file when ready.
```

Output:

### 1. What is this feature?

Admins can now export filtered order data into a CSV file without waiting on the page. The system prepares the file in the background and sends an email when the export is ready.

### 2. Why do we need it?

Large exports can take time. This avoids slow admin screens and gives the operations team a more reliable way to get reporting data.

### 3. What problem does it solve?

Before this, admins might have to wait for a large export to finish in the browser. If it took too long, the page could time out or feel broken.

### 4. How does it work?

The admin chooses filters, requests an export, and can keep working. The system puts the export into a background waiting line and processes it separately.

Analogy: Think of it like ordering a prepared report from an assistant instead of standing at the printer until every page is ready.

### 5. What changes for the user?

Admins get a smoother export experience and receive the file by email when it is ready.

### 6. What remains unchanged?

The order data, filtering rules, and admin permissions remain the same.

### 7. Risks and edge cases

Very large exports may still take longer. Email delivery must work correctly, and only authorized admins should receive export files.

### 8. Real-world example

An operations manager filters orders from the last quarter and requests an export. They continue reviewing orders and later receive a CSV link by email.

### 9. Non-technical summary

This improves admin reporting by making large exports more reliable and less disruptive.

### Technical glossary

- CSV: A spreadsheet-friendly file format.
- Queue: A waiting line for background work that does not need to happen immediately.

## 2. Angular feature

Input:

```text
Audience: QA
Complexity: Detailed
Feature: Angular dashboard filters now update the URL so users can share or refresh a filtered view.
```

Output:

The feature allows dashboard filters to stay visible in the browser URL. Users can refresh the page or share a link and keep the same filtered dashboard view.

QA should verify that filters persist after refresh, copied links open with the same filters, invalid filter values are handled safely, and existing dashboard data still loads normally.

## 3. React feature

Input:

```text
Audience: Client
Complexity: Basic
Feature: React profile page now shows a completion checklist.
```

Output:

The profile page now helps users understand what information is missing from their account. Instead of guessing, they see a simple checklist showing which profile steps are complete and which still need attention.

This makes onboarding clearer and can reduce support questions from users who are unsure why their profile is not complete.

## 4. API endpoint

Input:

```text
Audience: Product Manager
Complexity: Detailed
Feature: New API endpoint returns delivery estimates for a cart before checkout.
```

Output:

The application can now ask for delivery estimates before a customer reaches checkout. This helps show shipping expectations earlier in the buying journey.

The user benefit is clearer decision-making: customers can see whether delivery timing works for them before they invest time completing checkout.

Technical glossary:

- API: A structured way for one system or app to talk to another.

## 5. Authentication flow

Input:

```text
Audience: Executive
Complexity: Executive Summary
Feature: Passwordless login with one-time email links.
```

Output:

Passwordless login lets users sign in through a secure link sent to their email instead of typing a password. This can reduce password reset friction and improve the login experience.

The main risk is email dependency: if email delivery is delayed or blocked, users may have trouble signing in.

Technical glossary:

- Authentication: The process of confirming that a person is allowed to access an account.

## 6. Cookie consent feature

Input:

```text
Audience: Marketing
Complexity: Detailed
Feature: Cookie consent banner with separate required, analytics, and marketing preferences.
```

Output:

The site now gives visitors more control over cookie preferences. Required cookies stay enabled because the site needs them to function, while analytics and marketing cookies can be accepted or rejected separately.

Marketing can describe this as improved visitor choice and clearer consent handling. Avoid claiming that this alone guarantees legal compliance unless legal review confirms it.

Technical glossary:

- Analytics cookies: Cookies that help the team understand how visitors use the site.
- Marketing cookies: Cookies used to personalize or measure advertising.

