# Firefox

## userChrome.css

~/.mozilla/firefox/<user>/chrome/userChrome.css

```css
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */
```

### Tree Style Tab

```css
tab:not([selected="true"]) {
    background-color: #B9B9BD !important;
    color: #000000 !important;
}
```  