# Installation Guide — AIO Fragment Tracker

This guide walks you through installing the GTM module that tracks AI Overview, Featured Snippet, and People Also Ask (PAA) clicks using URL fragment detection.

---

## 1. Import the GTM Container

1. Open **Google Tag Manager**
2. Navigate to **Admin → Import Container**
3. Select:

gtm/aio-watchtower-gtm-module-v1.json

yaml
Copy code

4. Choose:
   - **Merge**
   - **Rename conflicting tags/variables**
5. Click **Confirm**

---

## 2. Link to Your GA4 Configuration Tag

1. Find the tag:

GA4 – AIO Pageview Helper

yaml
Copy code

2. Open it  
3. In **Configuration Tag**, select your site’s GA4 config tag  
4. Save

---

## 3. Publish the Container

Click **Submit → Publish**.

You now have AIO/snippet detection logic deployed.

---

## 4. Create GA4 Custom Dimension

In GA4:

1. Go to **Admin → Custom Definitions**
2. Click **Create custom dimension**
3. Fill in:

- **Dimension name:** `aio_fragment`  
- **Scope:** Event  
- **Event parameter:** `aio_fragment`

Save.

---

## 5. Wait for Processing

GA4 will populate the dimension for all future pageviews that include AIO/snippet/PAA fragment traffic.

You are now fully tracking AIO traffic.
