# Nignite (the fox)

> A port of [ignite (the fox)](https://github.com/73/ignite) by [73](https://github.com/73) for niri

A Firefox launcher script for [niri](https://github.com/niri-wm/niri) that opens URLs in the current workspace.

## What it does

When you open a URL:
- If there's already a Firefox window on your current workspace → opens the URL in a new tab
- If there's no Firefox window → opens a new Firefox window on the current workspace

This prevents Firefox from randomly opening on another workspace.

## Requirements

- [niri](https://github.com/niri-wm/niri) Wayland compositor
- `jq` for JSON parsing
- Firefox

## Installation

### Nix (Home Manager)

```nix
xdg.desktopEntries.nignite = {
  name = "Nignite the fox";
  genericName = "Web Browser";
  comment = "Browse the World Wide Web and stay sane";
  exec = "nignite %u";
  terminal = false;
  type = "Application";
  categories = [ "Application" "Network" "WebBrowser" ];
  mimeType = [
    "x-scheme-handler/unknown" "x-scheme-handler/about" "text/html"
    "text/xml" "application/xhtml+xml" "application/xml" "application/rss+xml"
    "application/rdf+xml" "image/gif" "image/jpeg" "image/png"
    "x-scheme-handler/http" "x-scheme-handler/https" "x-scheme-handler/ftp"
    "x-scheme-handler/chrome" "video/webm" "application/x-xpinstall"
  ];
};

xdg.mimeApps.defaultApplications = {
  "text/html" = "nignite.desktop";
  "x-scheme-handler/http" = "nignite.desktop";
  "x-scheme-handler/https" = "nignite.desktop";
  "x-scheme-handler/about" = "nignite.desktop";
  "x-scheme-handler/unknown" = "nignite.desktop";
};
```

### Manual

1. Copy `nignite` to your PATH:
   ```bash
   cp nignite ~/.local/bin/
   chmod +x ~/.local/bin/nignite
   ```

2. Copy `nignite.desktop`:
   ```bash
   cp nignite.desktop ~/.local/share/applications/
   ```

3. Set as default browser:
   ```bash
   xdg-settings set default-web-browser nignite.desktop
   ```


