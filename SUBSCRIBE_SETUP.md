Mailchimp + RSS subscription setup

This guide walks you through creating a Mailchimp embedded signup form and an RSS-driven campaign so subscribers receive an email whenever you publish a new post.

Steps (high level)
1. Create a Mailchimp account and Audience (list).
2. Create an embedded signup form and copy the form `action` + hidden fields.
3. Paste that `action` and hidden fields into `_includes/subscribe.html` in this repo.
4. Create an RSS-driven (RSS-to-email) campaign in Mailchimp that points to `https://<your-domain>/feed.xml`.
5. Test by subscribing and publishing a post.

Detailed steps

1) Mailchimp account & Audience
- Sign up at https://mailchimp.com (there is a free tier for small audiences and basic forms; see Mailchimp's pricing page for current details).
- Create an Audience (also called a list). Configure required fields (usually just email).

2) Create an embedded form
- In Mailchimp, go to `Audience` → `Signup forms` → `Embedded forms`.
- Customize the form and copy the generated embed HTML.
- In the embed HTML you'll see a `<form action="https://...list-manage.com/subscribe/post?u=...&id=..." ...>` and one or more hidden input fields of the form `name="b_xxx_xxx"` (anti-bot field). Copy the full embed HTML.

3) Update the site include
- Open `_includes/subscribe.html` in the repo.
- Replace the placeholder `action="YOUR_MAILCHIMP_POST_URL_HERE"` with the Mailchimp form `action` URL (the full URL from the embed code).
- If the embed contains a hidden `b_...` input, add it to the form in `_includes/subscribe.html` so Mailchimp receives it.

Example: if Mailchimp gives you this embed snippet:

<form action="https://abcd1234.us1.list-manage.com/subscribe/post?u=aaaaaaaaa&id=bbbbbbbb" method="post" target="_blank" novalidate>
  <input type="email" value="" name="EMAIL" id="mce-EMAIL" placeholder="you@example.com" required>
  <input type="text" name="b_aaaaaaaaa_bbbbbbbb" tabindex="-1" value="">
  <button type="submit">Subscribe</button>
</form>

Then update `_includes/subscribe.html` so its `<form>` `action` matches the one above and add the hidden `input` with `name="b_..."` inside the form.

4) Create the RSS-driven campaign
- In Mailchimp go to `Campaigns` → `Create Campaign` → `Email` → `Automated` (or `Create` → `Email` → `Automated` → `Share blog updates`).
- Choose `RSS` or `RSS-to-email` campaign type.
- Provide your RSS feed URL: `https://<your-site-domain>/feed.xml` (jekyll-feed generates `/feed.xml`).
- Choose sending frequency: "Every time there's new content" or daily/weekly digest depending on your preference.
- Select the Audience you want to send to (the one you created).
- Design the email template and save.
- Start the automation. Mailchimp will check the feed at the chosen frequency and send emails when new items are found.

5) Test
- Subscribe using the form on your site (Mailchimp often requires double opt-in depending on settings).
- Publish a new post and confirm the RSS item appears in `https://<your-site-domain>/feed.xml`.
- Mailchimp should pick it up at the next check and send the email to subscribers.

Notes about cost and alternatives
- Mailchimp offers a free tier for basic signup forms and small audiences, but some advanced automations (RSS frequency options, higher send volume, or certain templates) may require a paid plan. Check Mailchimp's current pricing before relying on it.
- Alternatives that are developer-friendly and often cheaper (or free for small lists):
  - Buttondown (great for newsletters, supports RSS-to-email and is free for small lists).
  - MailerLite (offers free tier with automations for small lists).
  - ConvertKit (has free tier, but features vary).
  - Use a simple service like Zapier/Make to forward RSS items to an SMTP provider or to add subscribers to a transactional email provider.

Local preview (optional)
To preview changes locally and test the form appearance, run Jekyll locally:

```bash
# install bundler and dependencies (if not already installed)
bundle install

# serve locally
bundle exec jekyll serve --livereload
```

Then open http://127.0.0.1:4000 and test the form.

If you'd like, I can:
- Walk through the Mailchimp UI with you step-by-step.
- Paste the exact Mailchimp embed into `_includes/subscribe.html` if you paste the generated embed HTML here.
- Or implement a GitHub Actions + SendGrid alternative (fully automated, but requires adding API keys to repo secrets).

