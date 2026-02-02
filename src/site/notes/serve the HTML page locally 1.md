---
{"dg-publish":true,"permalink":"/serve-the-html-page-locally-1/"}
---


### VS Code Live Server ✅

1. Reasons for Recommendation
  - **Live Hot Reload**: Automatically refreshes the browser after code changes, significantly improving development efficiency
  - **Zero-Command Operation**: No terminal commands needed; simply right-click the file to run it
  - **Smart Path Resolution**: Automatically handles file path issues (avoiding the limitations of the `file://` protocol)
  - **Customizable Port**: The default port (default 5500) can be modified in VS Code settings

We are discussing two different tools: live-server (the backend service used by the VS Code Live Server extension) and http-server (a simple global npm package).

1. **http-server**:
   - A zero-configuration, pure static [[HTTP server\|HTTP server]]
   - Provides only basic services: receives requests → returns files
   - **No live reload functionality** (manual browser refresh required after modifying files)

1. **live-server**:
   - Adds the following on top of http-server's basic functionality:
     ▶ File watching (watch) → detects changes in workspace files
     ▶ WebSocket long connection → establishes two-way communication between the browser and the server
     ▶ Automatic script injection → automatically inserts a piece of JS code into the returned HTML (used to receive reload instructions)
   - Core advantage: modifying files → automatically refreshes the browser

### Key Technical Points Verification:
- **Automatic Script Injection**:  
  - Viewing the HTML source returned by Live Server, you will find that a script similar to the following has been added at the bottom (used to establish a WebSocket connection): ...
- **CSS Hot Update Principle / CSS Refresh Mechanism**:  
  - Locate all `<link rel="stylesheet">` tags in the DOM, modify their `href` attribute (by adding timestamps or other random parameters), and force the browser to re-request the stylesheet.

1. WebSocket connection

```javascript
 const ws = new WebSocket('ws://localhost:PORT');
 ws.onmessage = (event) => {
 if (event.data === 'reload') window.location.reload();
 if (event.data === 'css') reloadStylesheets();
 };
```

2. CSS Hot Update

```javascript
function reloadStylesheets() {
 document.querySelectorAll('link[rel=stylesheet]').forEach(link => {
 const url = new URL(link.href);
 url.searchParams.set('forceReload', Date.now());
 link.href = url.href;
 });
}
```
