# Privacy Policy

**Effective date**: May 4, 2026  
**Last updated**: May 8, 2026

## Who we are

**DataLens** is a Chrome extension project. This policy uses “we”, “our”, or “us” to refer to the maintainers of DataLens. We do **not** operate a cloud backend that receives your inspected web page content for storage or profiling.

**Contact (support and privacy questions)**  

- Public issues: [github.com/jingshaq/DataLens/issues](https://github.com/jingshaq/DataLens/issues)  
- Community discussions: [github.com/jingshaq/DataLens/discussions](https://github.com/jingshaq/DataLens/discussions)

**Security reports (do not use public issues for sensitive reports)**  

- Email: [jingshaq+datalens-security@gmail.com](mailto:jingshaq+datalens-security@gmail.com)

Source code may be distributed separately from the community repository above; see any packaging notes shipped with your copy of the extension.

## Overview

This Privacy Policy explains how the DataLens Chrome extension handles information when you use it.

## Information collection

DataLens operates primarily **locally** on your device.

### Data processed locally

- **Web page content**: XML, JSON, and YAML (or related text) from pages you choose to inspect  
- **User settings**: Preferences stored in `chrome.storage.local`  
- **Editing history**: Undo/redo for inline edits, held temporarily in memory during use

### AI model processing (optional)

- An optional local model (e.g. Flan-T5) runs **on your device** in an offscreen document  
- **Inference does not send your inspected page content to AI APIs we operate**  
- **Distributed builds (including typical Chrome Web Store packages)** ship model weights and ONNX Runtime WASM **inside the extension**. At runtime they load from `chrome-extension://…` URLs—**no fetch of model files from Hugging Face, jsDelivr, or similar CDNs** during normal use  
- **Fallback:** If a build is installed **without** those bundled files (unusual), the underlying library may attempt to **download public model artifacts over HTTPS** from hosts such as Hugging Face (`huggingface.co`, `hf.co`) or jsDelivr (`cdn.jsdelivr.net`). That traffic would still be **downloads of published weights**, not uploads of your page content. Maintainers obtain bundled files using project scripts that may fetch from Hugging Face **at build time** on a developer machine—this is **not** end-user runtime behavior for standard packages  

## Third-party services

- **Normal user path:** Model inference uses **assets bundled with the extension**; no ongoing reliance on third-party model CDNs for inference  
- **Fallback / non-standard builds:** Public model hosts may be contacted **only if** bundled assets are missing, as described above. Those operators have their own privacy policies for their services; DataLens does **not** send them your inspected page content as part of model loading  

## Data sharing

**We do not operate a service that collects your inspected web content or sells personal data for advertising.**

- No analytics from us  
- No telemetry from us  
- No user tracking by us  
- **Content you inspect is not uploaded to servers we control**

For **standard packaged builds**, outbound HTTPS from the extension related to local AI is **not** used to download model weights (they are already in the package). Other extension behavior may still use the network only where necessary for non-AI features you use; local AI itself stays on-device as described above.

## Native messaging (optional)

If you install and register an MCP native messaging host:

- Communication is between the extension and **software you run on your device**  
- Whether data leaves your machine depends on **that native application**; configure it carefully  
- You can keep this feature disabled if you do not use a host

## Permissions explanation

| Permission                         | Purpose                                                          |
| ---------------------------------- | ---------------------------------------------------------------- |
| `storage`                          | Save your settings locally                                       |
| `nativeMessaging`                  | Optional MCP bridge to local tools                               |
| `clipboardWrite` / `clipboardRead` | Copy/paste in the inspection UI                                  |
| `offscreen`                        | Run local AI without blocking the UI thread                      |
| `activeTab` / `tabs`               | Tie inspection to the tab you are working in                     |
| `scripting`                        | Inject bundled scripts when needed for detection and UI mounting |
| `sidePanel`                        | Show the inspection side panel                                   |
| `contextMenus`                     | Optional context menu entries (e.g. inspect with DataLens)       |

## Host permissions

The extension declares **`host_permissions`: `<all_urls>`** so it can run where you might inspect structured data.

- **Page inspection**: Lets content scripts and related logic access DOM text you interact with **for local parsing and visualization**. We **do not** upload that content to our servers  
- **Why not narrower hosts alone:** Restricting patterns would block inspecting arbitrary sites users browse  
- **Local AI and the network:** Store-style builds load bundled models from the extension origin; **`<all_urls>` is not used as proof that models are downloaded from the web** in that configuration. Only the **fallback** path (missing bundled assets) may cause HTTPS fetches to public model hosts, as explained under *AI model processing*

## Data retention

- **Settings**: Until you uninstall the extension or clear extension storage  
- **Session data**: Cleared when you close the relevant tab/session  
- **Bundled model assets**: Shipped inside the extension package; removed when you uninstall  
- **Any runtime caches** the browser or libraries create for models: cleared when you uninstall or clear extension/site data as applicable

## Children’s privacy

DataLens is not directed at children under 13, and we do not knowingly collect personal information from children. If you believe a child has submitted personal data through our support channels, contact us using the addresses above.

## Your rights (including EEA/UK users)

Because core processing is **local** and we **do not** operate an account system for the extension:

- You can stop processing by disabling features or uninstalling the extension  
- You can clear stored settings via Chrome’s extension data controls  
- Depending on your region, you may have rights to access, rectify, or delete personal data **we hold if you contact us** (for example, via email or issue content you voluntarily submit). For complaints, you may contact your local data protection authority

This section is a general summary and does not limit mandatory rights under applicable law.

## Changes to this policy

We may update this policy from time to time. We will revise the **Last updated** date at the top when we do. Material changes may also be reflected in the Chrome Web Store listing or in-extension notices where appropriate.

## Contact

For privacy questions: use [GitHub Issues](https://github.com/jingshaq/DataLens/issues) or the security email above for sensitive matters.
