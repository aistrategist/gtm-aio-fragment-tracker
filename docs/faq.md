# FAQ — AIO Watchtower GTM Module

---

### ❓ Does this track *all* AI Overview traffic?

No.

This module tracks **fragment-based** AIO, featured snippet, and PAA clicks — cases where Google appends a highlight fragment such as:

#:~:text=some-highlighted-text

yaml
Copy code

This gives you **high-signal sampling**, not 100% of AIO traffic.

---

### ❓ What if Google changes how fragment URLs work?

If Google introduces new fragment patterns, update:

- `cJS – AIO Fragment Flag`
- The optional Enhancer tag (if needed)

Your GA4 structure remains valid.

---

### ❓ Will this work on platforms like Dealer Inspire, Dealer.com, CDK, Motive, etc.?

Yes.  
It runs through GTM and is platform-agnostic.

---

### ❓ Can the fragment disappear before the user sees it?

Yes — some JS frameworks strip the fragment on load.  
But GTM reads `document.location.href` **before** the strip in most cases.

---

### ❓ Does the enhancer (`?aio=1`) affect SEO?

No:

- Uses `history.replaceState`  
- Does not reload  
- Does not affect canonical  
- Not indexed by Google  

It is purely a client-side UX adjustment.

---

### ❓ Can I use this across multiple sites or clients?

Yes — it is a portable module designed for:

- Agencies
- Dealer groups
- Multi-domain SaaS setups
- Analysts running cross-site studies

Just import → link to GA4 → publish.
