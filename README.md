# jag-k Flatpak Repository

This repository hosts the signed Flatpak remote for applications published by
jag-k. It is deployment storage rather than an application source repository.
GitHub Pages serves it from `https://flatpak.jag-k.dev/`; the DNS `flatpak`
CNAME points to `jag-k.github.io`.

## Add the remote

```sh
flatpak remote-add --user --if-not-exists jag-k \
  https://flatpak.jag-k.dev/jag-k.flatpakrepo
```

List available applications:

```sh
flatpak remote-ls jag-k
```

Install Clipboard Transformer:

```sh
flatpak install --user jag-k dev.jag_k.clipboard_transformer
```

The application-specific ref can add the remote and install the application in
one step:

```sh
flatpak install --user \
  https://flatpak.jag-k.dev/clipboard-transformer.flatpakref
```

## Repository layout

- `repo/` is the signed OSTree repository consumed by Flatpak.
- `jag-k.flatpakrepo` describes the shared `jag-k` remote.
- `*.flatpakref` files install individual applications from that remote.
- `index.html` is the small GitHub Pages landing page.

The release workflows in the individual application repositories own generated
repository contents. Do not edit `repo/`, `.flatpakrepo`, or `.flatpakref`
files manually.

GitHub Pages must publish from the root of the `main` branch.
