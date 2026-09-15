# radix-validators

Public assets for the Radix validators operated by [@jerseyjon](https://github.com/jerseyjon).

This repository exists so that the `icon_url` and `info_url` recorded in each
validator's on-ledger metadata point at somewhere durable and version-controlled.
The previous icon lived on a site that was redeployed, the path moved, and the
URL silently began returning 404 — which is exactly the failure a git-backed
host avoids.

## Setup (one time)

1. Create a **public** repo named `radix-validators` on GitHub.
2. Upload the contents of this folder to the repository root.
3. **Settings → Pages → Build and deployment**: source `Deploy from a branch`,
   branch `main`, folder `/ (root)`. Save.
4. Wait a minute, then confirm both URLs return 200:

```
https://jerseyjon.github.io/radix-validators/
https://jerseyjon.github.io/radix-validators/radix-charts-v2.png
```

Those two URLs are what the transaction manifests write on-ledger, so they must
resolve before the metadata is worth updating.

## Files

| file | purpose |
|---|---|
| `index.html` | the `info_url` landing page |
| `radix-charts-v2.png` | 512×512 icon, the `icon_url` target |
| `radix-charts-v2-128.png` | 128×128 copy, if a smaller asset is ever wanted |

## Why the icon looks the way it does

It renders at roughly 32–40 px tall in validator lists, so it carries no fine
detail, has its own solid background (list backgrounds vary between light and
dark), and its three bars step in **luminance as well as hue** so the ascending
read survives greyscale and the common forms of colour blindness.

## Don't move these files

The paths are written into on-ledger metadata. Changing a filename means another
signed transaction to update it. If a file must be replaced, keep the same name.
