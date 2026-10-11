# ChatGPT Cleanup

**Also available on OpenUserJS: [filters](https://openuserjs.org/scripts/sukhoi191/ChatGPT_cleanup_filters) and [styles](https://openuserjs.org/scripts/sukhoi191/ChatGPT_cleanup_styles)**.

A pair of userscripts for cleaning up the ChatGPT web interface. One hides unwanted interface elements; the other gives the mobile website an Android-app-inspired layout.

The scripts work independently, so you can install either one or both.

## Features

### Cleanup filters

`chatgpt-cleanup-filters.user.js` hides selected UI elements, including:

- Emoji reaction indicators and their reserved spacing
- The memory “Dive deeper” section
- Suggested follow-ups in writing blocks
- Conversation follow-up suggestions and their extra spacing
- Duplicate or malformed follow-up blocks
- Feedback prompts
- Upsell banners

Filter groups can be enabled or disabled individually. The script uses CSS selectors and DOM observation to handle dynamically rendered content without removing React-owned elements.

### Mobile styles

`chatgpt-cleanup-styles.user.js` adjusts the ChatGPT website on screens narrower than **768 px** to resemble the Android app more closely. Changes include:

- Light- and dark-mode colors
- Rounded header buttons and a restyled Chat / Work switch
- A more compact, rounded message composer
- Adjusted voice, send, model and attachment controls
- Mobile viewport and bottom safe-area spacing
- Removal of the welcome headline on the home screen

The styling is limited to mobile-width viewports; it does not intentionally restyle the desktop layout.

## Installation

1. Install a userscript manager such as [Violentmonkey](https://violentmonkey.github.io/) or [Tampermonkey](https://www.tampermonkey.net/) in a compatible browser.
2. Install the scripts you want from this repo:
   - **[Cleanup filters](https://raw.githubusercontent.com/sukhoi191/chatgpt-cleanup/refs/heads/main/chatgpt-cleanup-filters.user.js)**
   - **[Mobile styles](https://raw.githubusercontent.com/sukhoi191/chatgpt-cleanup/refs/heads/main/chatgpt-cleanup-styles.user.js)**
   
   Or install them from OpenUserJS:
   - **[Cleanup filters](https://openuserjs.org/scripts/sukhoi191/ChatGPT_cleanup_filters)**
   - **[Mobile styles](https://openuserjs.org/scripts/sukhoi191/ChatGPT_cleanup_styles)**
3. Open or reload [ChatGPT](https://chatgpt.com/).

Both scripts run on `chatgpt.com` and its subdomains. They do not require privileged userscript API grants.

## Configuration

The filters script contains a `FILTER_CONFIG` object with switches for each group:

```js
const FILTER_CONFIG = {
  reactions: true,
  memoryDiveDeeper: true,
  writingBlockFollowUps: true,
  followUps: true,
  duplicateFollowUps: true,
  malformedFollowUps: true,
  feedbackPrompts: true,
  upsellBanners: true
};
```

Set a group to `false` to disable its rules, then save and reload ChatGPT. The duplicate and malformed follow-up fixes have separate switches.

The mobile styles script uses CSS custom properties such as `--android-page`, `--android-control`, and `--android-border` to control its appearance. Light- and dark-mode values are defined separately.

**Note:** The supplied `.user.js` files are generated artifacts. Their headers say to edit the source files and rebuild with `node build.mjs`. Those source files and build script are not included in the four files documented here. Editing an installed script directly may also be overwritten by a later update.

## Updates

Each script includes userscript metadata pointing to its own update and download URLs:

| Script | Update metadata | Script download |
| --- | --- | --- |
| Filters | `chatgpt-cleanup-filters.meta.js` | `chatgpt-cleanup-filters.user.js` |
| Styles | `chatgpt-cleanup-styles.meta.js` | `chatgpt-cleanup-styles.user.js` |

The userscript manager can check the lightweight `.meta.js` file and fetch the corresponding `.user.js` file when a new version is available. Automatic update behavior and timing depend on the manager's settings. Increment the relevant `@version` when publishing changes.

## Files

| File | Purpose |
| --- | --- |
| `chatgpt-cleanup-filters.user.js` | Installable cleanup filters userscript |
| `chatgpt-cleanup-filters.meta.js` | Update metadata for the filters script |
| `chatgpt-cleanup-styles.user.js` | Installable mobile styling userscript |
| `chatgpt-cleanup-styles.meta.js` | Update metadata for the styles script |

## Limitations

ChatGPT's web interface changes frequently. Selectors that depend on its HTML structure, class names, or attributes may stop working after an update. Some rules use modern CSS selectors such as `:has()`, so browser support matters. The mobile styles aim to approximate the Android app's appearance, not reproduce its native functionality.

This is an unofficial project and is not affiliated with or endorsed by OpenAI.

## License

MIT. Copyright © 2026 sukhoi191.
