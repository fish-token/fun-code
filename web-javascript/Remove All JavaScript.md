# What Does it Do?

These snippets of JS remove all JavaScript from the page, both visually and functionally. Some stuff removed by this snippet include:

- All `<script>` tags (head and body)
- All timeouts and intervals
- All event listeners
- All non-native properties
- (Optional) DOM visual state

**Clarifications:**

- This JS contains code that will only works in the `Developer Console`, so make sure to only put it in there
- You are removing JS, which may cause unintended effects and perhaps break things
- These snippets of JavaScript shouldn't cause any performance issues

## What's The Setup Process?

Just follow the steps below!

- Open your browser's `Developer Tools` panel by doing one of the following:
  - Right-Click any webpage and click `Inspect` or `Inspect Element`
  - Pressing `Shift + Ctrl + C` (or `Shift + Cmd + C` on mac)
  - Clicking the three dots in the top right corner of your browser (to the right of your profile picture), then click `More Tools`, and finally `Developer Tools`
- Navigate to the `Console` tab
- Copy and paste the snippets (listed under the **Code** section)
- Press your `Enter` key and watch the magic unfold

## Code

The necessary code (core functionality):

```javascript
const highestId = window.setTimeout(() => {}, 0);
const allElements = [window, document, ...document.querySelectorAll('*')];
const nativeProps = new Set(['window', 'document', 'location', 'history', 'chrome', 'console', 'navigator', 'top', 'frames', 'self']);
document.querySelectorAll('script').forEach(s => s.remove());
for (let i = 0; i <= highestId; i++) {
    window.clearTimeout(i);
    window.clearInterval(i);
}
allElements.forEach(el => {
    const listeners = getEventListeners(el); 
    for (const type in listeners) {
        listeners[type].forEach(l => {
            el.removeEventListener(type, l.listener, l.useCapture);
        });
    }
});
Object.keys(window).forEach(key => {
    if (!nativeProps.has(key)) {
        try {
            delete window[key];
        } catch(e) {
            window[key] = null;
        }
    }
});
// Optional #1 Paste (over this comment)
// Optional #2 Paste (over this comment)
console.log('Cleanup complete! Snippet created by Fish Token. (GitHub: http://github.com/Fish-token or GitLab: https://gitlab.com/fish-token-clan)');
```

Optional #1 (faster but not as precise HTML cleanup):

```javascript
document.body.innerHTML = document.body.innerHTML;
```

Optional #2 (clean visual clutter):

```javascript
document.body.innerHTML = '';
```

## What's The Removal Process?

Just simply refresh the webpage!
