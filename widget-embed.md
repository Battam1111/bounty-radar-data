# Embeddable Radar Widget

Embed a live, auto-updating list of recent ZK bounties on any site.

## Minimal embed (default = top 8, all ecosystems)
```html
<iframe src="https://battam1111.github.io/bounty-radar-data/widget.html"
        width="100%" height="500" frameborder="0"></iframe>
```

## Per-ecosystem
```html
<!-- Noir-only -->
<iframe src="https://battam1111.github.io/bounty-radar-data/widget.html?ecosystem=noir"
        width="100%" height="500" frameborder="0"></iframe>

<!-- Aleo, 5 items, light theme -->
<iframe src="https://battam1111.github.io/bounty-radar-data/widget.html?ecosystem=aleo&limit=5&theme=light"
        width="100%" height="400" frameborder="0"></iframe>
```

## Query parameters
- `ecosystem` — `aleo` | `noir` | `midnight` | `aztec` | `risc0` | `cairo` (leave empty for all)
- `limit` — 1..50, default 8
- `theme` — `auto` (default) | `light` | `dark`

## Auto-height (optional)
Add to your parent page so the iframe resizes to fit content:
```html
<iframe id="bounty-widget" src="..." width="100%" frameborder="0"></iframe>
<script>
window.addEventListener('message', e => {
  if (e.data?.type === 'bounty-radar-resize') {
    document.getElementById('bounty-widget').style.height = e.data.height + 'px';
  }
});
</script>
```

## License
CC0 — copy, embed, modify freely. No tracking, no cookies, no analytics on the widget itself.
