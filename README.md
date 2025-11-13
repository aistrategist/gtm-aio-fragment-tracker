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
- Text-highlight deep links (\`#:~:text=\`)

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
- Captures the highlight fragment (\`#:~:text=...\`)  
- Attaches \`aio_fragment\` signals to GA4 events  
- Overrides \`page_location\` so GA4 sees the full fragment  
- Optionally appends \`?aio=1\` as a persistent tracking identifier  
- Sends the event to GA4 using a dedicated \`aio_pageview\` event

No coding required.  
Just import → select GA4 config → publish.

---

## 📂 What’s Included in the Module

### Inside the GTM Container

| Component                    | Purpose                                                   |
|-----------------------------|-----------------------------------------------------------|
| \`cJS – Full URL With Hash\`  | Captures complete landing URL including AIO fragments     |
| \`cJS – AIO Fragment Flag\`   | 1/0 flag showing whether AIO/snippet click detected      |
| \`GA4 – AIO Pageview Helper\` | Sends AIO parameters into GA4                             |
| \`HTML – AIO URL Enhancer\`   | Adds \`?aio=1\` to maintain tracking across pages           |
| \`GA4 – Config (Placeholder)\`| Placeholder so import never breaks                        |
| \`AIO – All Pages\`           | Universal trigger                                         |

The container is exported as:

\`\`\`text
gtm/aio-watchtower-gtm-module-v1.json
\`\`\`

---

## 🛠 Installation (Quick Version)

📘 Full installation guide: [\`docs/installation-guide.md\`](docs/installation-guide.md)

1. Go to **GTM → Admin → Import Container**
2. Upload:

   \`\`\`text
   gtm/aio-watchtower-gtm-module-v1.json
   \`\`\`

3. Choose:
   - **Merge**
   - **Rename conflicting tags/variables**

4. Open tag: \`GA4 – AIO Pageview Helper\`
   - Select your site’s GA4 configuration tag
   - Save

5. Publish the container

6. In GA4 → **Admin → Custom Definitions**:
   - Create a new **event-scoped dimension**:
     - **Name:** \`aio_fragment\`
     - **Event parameter:** \`aio_fragment\`

7. Wait for GA4 to start populating the dimension (usually within a few hours).

---

## 🧪 Testing

📘 Detailed testing guide: [\`docs/testing-guide.md\`](docs/testing-guide.md)

To simulate an AIO click in GTM preview:

1. Open DevTools → Console
2. Run:

   \`\`\`js
   window.location = window.location.origin + window.location.pathname + '#:~:text=testing';
   \`\`\`

3. In the GTM debug panel, confirm:

   - \`GA4 – AIO Pageview Helper\` **fired**
   - \`HTML – AIO URL Enhancer\` **fired**
   - Variable \`cJS – AIO Fragment Flag\` = \`1\`
   - Variable \`cJS – Full URL With Hash\` includes \`#:~:text=\`

In GA4 Realtime, you’ll see the event carrying \`aio_fragment = 1\`.

---

## 📊 Example GA4 Output

See the \`/examples\` folder for:

- GTM preview example  
- GA4 \`aio_fragment\` custom dimension screenshot  
- GA4 exploration with AIO segment  

(*Add these screenshots manually after you generate them.*)

---

## ❓ FAQ

📘 [\`docs/faq.md\`](docs/faq.md)

Answers include:

- Does this capture all AIO traffic?  
- What happens if Google changes URL patterns?  
- Does this work with automotive platforms like Dealer Inspire / Dealer.com?  
- Does it impact SEO?  

---

## 📝 License

MIT — free to use, modify, deploy, or embed in client projects.

---

## 🤝 Contribute

Pull requests welcome, especially for:

- BigQuery AIO reporting templates  
- DataForSEO AIO validation add-ons  
- Automotive demo dashboards  
- Support for additional URL patterns and engines  

---

## ⭐ Star This Repo

If you find this helpful, consider starring the repo so others can discover it.
