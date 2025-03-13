+++
date = 2024-03-12T06:34:54-08:00
draft = false
title = 'Hide the Close Button (or Any Similar UI Element) in Zen Browser'
weight = 10
+++

After Zen Browser updated to version 1.9b, a small close button appears when hovering over a tab (in the Collapsed Toolbar Layout).

I want to remove it, but I couldn't find any option to do so.

## Hide the Close Button

1. In Zen Browser, Type about:support in the address bar and press Enter.
2. Look for the ``Profile Directory`` section.
3. Create a file named ``userChrome.css`` in your ''Profile Directory/chrome'' (Create the ``chome`` folder if it doesn’t exist)
4. Add the following CSS to ``userChrome.css``  
```css
.tab-close-button.close-icon {
    display: none !important;
}
```

5. Restart the browser.

## Find the Element You Want to Hide/Modify

1. Open the ``about:config`` page, search for ``devtools.debugger.remote-enabled``
2. Toggle the setting to true by double-clicking on it
3. Press Ctrl + Shift + Alt + I to open the Developer Tools.
4. If a popup window asks for permission, allow the connection.
5. Navigate to the **Inspector** tab.
6. Use the button next to the Inspector tab to select an element.
7. Find the element’s class name in the Inspector panel.


## References

- [Live Editing Zen Theme - Zen Browser Docs](https://docs.zen-browser.app/guides/live-editing)
