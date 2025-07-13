 **Social Media Blocker v0.1** Chrome extension repository. It includes:

* Overview
* Installation steps
* Usage
* Contribution guide (including how to customize it to block any site)

---

````markdown
# 🚫 Social Media Blockr v0.1

A lightweight and open-source Chrome extension to block access to distracting social media sites — specifically **Facebook** and **X.com (Twitter)** by default.

This tool is perfect for staying focused, studying, working, or creating a distraction-free browser experience.

---

## ✅ Features

- Blocks `facebook.com` and `x.com`
- Built with Chrome’s native `declarativeNetRequest` API (efficient & secure)
- No tracking, no external requests, 100% local
- Easily customizable to block any websites
- Clean and simple codebase

---

## 🚀 Installation

To install the extension manually in Chrome:

1. **Download or clone this repo**:
   ```bash
   git clone https://github.com/your-username/social-media-blockr.git
````

2. Open Chrome and go to:

   ```
   chrome://extensions/
   ```

3. Enable **Developer mode** (top right corner).

4. Click **"Load unpacked"** and select the cloned folder (`social-media-blockr`).

5. The extension will load and immediately block access to:

   * `https://facebook.com`
   * `https://x.com`

---

## 📁 File Structure

```
social-media-blockr/
├── manifest.json      # Extension config
└── background.js      # Rules to block specific sites
```

---

## 🛠️ How to Customize (Block Other Sites)

To block any other site (e.g. TikTok, Reddit, Instagram), follow these steps:

### 1. Edit `manifest.json`

Update the `"host_permissions"` array to include the new sites:

```json
"host_permissions": [
  "*://*.facebook.com/*",
  "*://*.x.com/*",
  "*://*.reddit.com/*",         // example
  "*://*.tiktok.com/*"          // example
]
```

### 2. Edit `background.js`

Add a new blocking rule for each site you want to block:

```js
chrome.declarativeNetRequest.updateDynamicRules({
  addRules: [
    {
      id: 1,
      priority: 1,
      action: { type: "block" },
      condition: {
        urlFilter: "facebook.com",
        resourceTypes: ["main_frame"]
      }
    },
    {
      id: 2,
      priority: 1,
      action: { type: "block" },
      condition: {
        urlFilter: "x.com",
        resourceTypes: ["main_frame"]
      }
    },
    {
      id: 3,
      priority: 1,
      action: { type: "block" },
      condition: {
        urlFilter: "reddit.com",         // new block
        resourceTypes: ["main_frame"]
      }
    },
    {
      id: 4,
      priority: 1,
      action: { type: "block" },
      condition: {
        urlFilter: "tiktok.com",         // new block
        resourceTypes: ["main_frame"]
      }
    }
  ],
  removeRuleIds: [1, 2, 3, 4]
});
```

**Note**: Make sure each rule has a unique `id`.

---

## 🙋‍♂️ Contributing

Contributions are welcome! You can:

* Add UI controls (e.g. enable/disable toggle)
* Add support for scheduling (block only during work hours)
* Improve customization from a settings panel

To contribute:

1. Fork this repo
2. Create a new branch
3. Make your changes
4. Open a pull request with a clear explanation

---

## 🔐 Privacy

This extension runs 100% locally in your browser.
It does **not track**, **store**, or **transmit** any user data.

---

## 📜 License

MIT License — free to use, modify, and share.

---
