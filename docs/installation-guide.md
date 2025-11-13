1️⃣ README.md

Create/open README.md and paste everything below:

# 🎯 AIO Fragment Tracker

![Status](https://img.shields.io/badge/status-beta-yellow)
![GTM](https://img.shields.io/badge/GTM-module-blue)
![GA4](https://img.shields.io/badge/GA4-supported-brightgreen)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

### A drop-in Google Tag Manager module that tracks AI Overview (AIO), Featured Snippet, and People Also Ask (PAA) clicks using URL fragment detection for GA4.

This module works across:

- AI Overviews (Google Generative Search / SGE)
- Featured snippets
- People Also Ask expansions
- Text-highlight deep links (`#:~:text=`)

Perfect for:

- SEO analysts  
- Agencies  
- Automotive groups  
- Multi-site analytics setups  
- Anyone measuring AIO impact in GA4  

---

## 🚀 What This Module Does

This GTM module automatically:

- Detects when a user comes from an AIO/snippet/PAA feature  
- Captures the highlight fragment (`#:~:text=...`)  
- Attaches `aio_fragment` signals to GA4 events  
- Overrides `page_location` so GA4 sees the full fragment  
- Optionally appends `?aio=1` as a persistent tracking identifier  
- Sends the event to GA4 using a dedicated `aio_pageview` event

No coding required.  
Just import → select GA4 config → publish.

---

## 📂 What’s Included in the Module

### Inside the GTM Container

| Component                      | Purpose                                                   |
|-------------------------------|-----------------------------------------------------------|
| `cJS – Full URL With Hash`    | Captures complete landing URL including AIO fragments     |
| `cJS – AIO Fragment Flag`     | 1/0 flag showing whether AIO/snippet click detected      |
| `GA4 – AIO Pageview Helper`   | Sends AIO parameters into GA4                             |
| `HTML – AIO URL Enhancer`     | Adds `?aio=1` to maintain tracking across pages           |
| `GA4 – Config (Placeholder)`  | Placeholder so import never breaks                        |
| `AIO – All Pages`             | Universal trigger                                         |

The container is exported as:

~~~text
gtm/aio-watchtower-gtm-module-v1.json

🛠 Installation (Quick Version)

📘 Full installation guide: docs/installation-guide.md

Go to GTM → Admin → Import Container

Upload:

gtm/aio-watchtower-gtm-module-v1.json


Choose:

Merge

Rename conflicting tags/variables

Open tag: GA4 – AIO Pageview Helper

Select your site’s GA4 configuration tag

Save

Publish the container

In GA4 → Admin → Custom Definitions:

Create a new event-scoped dimension:

Name: aio_fragment

Event parameter: aio_fragment

Wait for GA4 to start populating the dimension (usually within a few hours).

🧪 Testing

📘 Detailed testing guide: docs/testing-guide.md

To simulate an AIO click in GTM preview:

Open DevTools → Console

Run:

window.location = window.location.origin + window.location.pathname + '#:~:text=testing';


In the GTM debug panel, confirm:

GA4 – AIO Pageview Helper fired

HTML – AIO URL Enhancer fired

Variable cJS – AIO Fragment Flag = 1

Variable cJS – Full URL With Hash includes #:~:text=

In GA4 Realtime, you’ll see the event carrying aio_fragment = 1.

📊 Example GA4 Output

Use the /examples folder for:

GTM preview example

GA4 aio_fragment custom dimension screenshot

GA4 exploration with AIO segment

(Add these screenshots manually after you generate them.)

❓ FAQ

📘 docs/faq.md

Answers include:

Does this capture all AIO traffic?

What happens if Google changes URL patterns?

Does this work with automotive platforms like Dealer Inspire / Dealer.com?

Does it impact SEO?

📝 License

MIT — free to use, modify, deploy, or embed in client projects.

🤝 Contribute

Pull requests welcome, especially for:

BigQuery AIO reporting templates

DataForSEO AIO validation add-ons

Automotive demo dashboards

Support for additional URL patterns and engines

⭐ Star This Repo

If you find this helpful, consider starring the repo so others can discover it.


---

## 2️⃣ `docs/installation-guide.md`

Create `docs/installation-guide.md` and paste:

~~~markdown
# Installation Guide — AIO Watchtower GTM Module

This guide walks you through installing the GTM module that tracks AI Overview, Featured Snippet, and PAA clicks using fragment detection.

---

## 1. Import the Container

1. Open **Google Tag Manager**
2. Go to **Admin → Import Container**
3. Select:

   ~~~text
   gtm/aio-watchtower-gtm-module-v1.json


Choose:

Merge

Rename conflicting tags/variables

Click Confirm

2. Link to Your GA4 Configuration Tag

In GTM, find the tag:

GA4 – AIO Pageview Helper


Open it

In the Configuration Tag dropdown, choose your site’s GA4 configuration tag

Save

3. Publish the Container

Click:

Submit → Publish

Your site now has AIO/snippet detection logic deployed.

4. Create GA4 Custom Dimension

In GA4:

Go to Admin → Custom Definitions

Click Create custom dimension

Fill in:

Dimension name: aio_fragment

Scope: Event

Event parameter: aio_fragment

Save.

5. Wait for GA4 to Populate

GA4 will begin storing AIO signals (where aio_fragment = 1) usually within a few hours of traffic hitting the site.

You are now tracking AIO traffic across the entire site.


---

## 3️⃣ `docs/testing-guide.md`

Create `docs/testing-guide.md` and paste:

~~~markdown
# Testing Guide — AIO Watchtower GTM Module

This guide shows how to simulate an AI Overview / featured snippet click inside GTM Preview Mode and validate that the module is working.

---

## 1. Enter GTM Preview Mode

1. In GTM, click **Preview**
2. Enter your site URL (homepage is fine)
3. Click **Connect**

A new tab will open with your site and the GTM debug overlay.

---

## 2. Simulate AIO Click Using Console

Open **DevTools → Console** and run one of the following:

### Option A — Full reload (most realistic)

~~~js
window.location = window.location.origin + window.location.pathname + '#:~:text=testing';


This simulates a user arriving with a text fragment, like from an AI Overview or snippet.

Option B — Soft update (no full reload)
history.replaceState(null, '', '#:~:text=testing');
dataLayer.push({ event: 'gtm.js' });


This forces GTM to re-evaluate the page with the fragment in place.

3. Validate in GTM Preview

In the GTM debug panel, under Tags:

Under Tags Fired on this page, you should see:

GA4 – AIO Pageview Helper

HTML – AIO URL Enhancer (if included)

Click Variables and confirm:

Variable	Expected value
cJS – AIO Fragment Flag	1
cJS – Full URL With Hash	Contains #:~:text=testing

If cJS – AIO Fragment Flag is 1, the module is correctly detecting fragment-based hits.

4. Validate in GA4 (Realtime)

In GA4:

Go to Reports → Realtime

Find your active user session

Click into the event details

You should see:

Event name: aio_pageview

Event parameter: aio_fragment = 1

Once confirmed, you are successfully tracking AIO/snippet/PAA traffic.


---

## 4️⃣ `docs/faq.md`

Create `docs/faq.md` and paste:

~~~markdown
# FAQ — AIO Watchtower GTM Module

---

### Does this track *all* AI Overview traffic?

No.

This module tracks **fragment-based** AIO/snippet/PAA clicks — that is, when Google (or another surface) sends users to your site with a URL containing a text fragment such as:

~~~text
#:~:text=some%20highlighted%20snippet


Not all AI Overview or snippet links use this format, so this should be considered a strong sample, not a complete universe of AIO traffic.

What happens if Google changes how AIO links work?

If Google changes how it structures URLs (e.g., different hash patterns or query parameters), you can update:

The detection logic in cJS – AIO Fragment Flag

The GTM tags in this module

The rest of the system (GA4 custom dimension, reporting flows) can stay the same.

Does this work for automotive sites (Dealer Inspire / Dealer.com / Motive / CDK)?

Yes — the module is platform-agnostic.

It runs in the browser via GTM and only depends on:

The presence of a fragment-style URL

The ability to read document.location.href

Some platforms may hide the fragment in the visible address bar, but GTM variables can still read the full URL in most cases.

Do fragments always appear in the URL bar?

Not always.

Some sites or frameworks update the URL after initial load, which can visually strip or hide the fragment.

However, this module reads the URL immediately and uses GTM’s event model, which often captures the fragment even if it disappears from the visible address bar later.

Is the AIO URL Enhancer required?

No, but it is recommended.

The enhancer:

Adds ?aio=1 to the URL for detected fragment-based hits

Uses history.replaceState, so it does not cause a reload

Makes it easier to segment AIO traffic via URL-based filters if needed

If you prefer not to alter the URL at all, you can omit or disable the enhancer tag and rely solely on aio_fragment in GA4.

Does this affect SEO or canonical URLs?

No.

The module:

Runs entirely client-side

Uses history.replaceState to adjust URL display without reload

Does not modify canonical tags, server responses, or indexable content

Search engines crawling the site do not execute GTM in the same way as users, so this has no practical SEO impact.

Can I use this across multiple sites / clients?

Yes.

The GTM container is designed to be:

Imported into any GTM web container

Wired to any GA4 configuration tag

Used across multiple domains and platforms

For agencies or multi-brand groups, you can:

Import the module to each client’s GTM container

Wire the helper tag to that client’s GA4 config

Reuse the same GA4 exploration templates and dashboards.