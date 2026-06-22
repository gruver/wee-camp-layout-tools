# Layouts

Put exported layout JSON files in this folder when you want stable links on a
hosted static site.

Add each published layout to `index.json` so the app can show it in the
Starting Layout dropdown. Static hosts such as GitHub Pages cannot list folder
contents automatically, so the manifest is the source of truth for selectable
layouts.

Example:

```text
https://example.github.io/wee_camp_layout_tools/?layout=layouts/draft-1.json
```

The app also supports self-contained hash links made with `Copy Layout Link`,
but committed JSON files are better for larger layouts and review history.

Viewers can load a starting layout, make local edits in their browser, then use
`Export JSON` to send back an editable modified version.
