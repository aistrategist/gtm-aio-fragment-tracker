# Testing Guide — AIO Watchtower GTM Module

This guide explains how to validate your AIO tracking module using GTM Preview Mode.

---

## 1. Enter GTM Preview Mode

1. In GTM, click **Preview**
2. Enter your site URL
3. Click **Connect**

A new tab will open containing your site and the GTM debug sidebar.

---

## 2. Simulate AIO/Featured Snippet Click

Open **DevTools → Console** and run:

### Simulation with full reload:

```js
window.location = window.location.origin + window.location.pathname + '#:~:text=testing';
Simulation with soft navigation:
js
Copy code
history.replaceState(null, '', '#:~:text=testing');
dataLayer.push({ event: 'gtm.js' });
3. Validate in GTM Debugger
In GTM Preview:

Tags Fired:
GA4 – AIO Pageview Helper

HTML – AIO URL Enhancer (optional)

Variables:
Variable	Expected Result
cJS – AIO Fragment Flag	1
cJS – Full URL With Hash	contains #:~:text=testing

4. Validate in GA4 Realtime
Go to Reports → Realtime in GA4.

Locate your active session and confirm:

Event name: aio_pageview

Event param: aio_fragment = 1

Once validated, your site is fully tracking AIO/snippet/PAA fragment traffic.

yaml
Copy code
