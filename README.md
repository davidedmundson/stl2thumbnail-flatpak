# stl2thumbnail Flatpak

Flatpak packaging of [krepa098/stl2thumbnail](https://github.com/krepa098/stl2thumbnail), an STL 3D model file thumbnailer.

## Build

```sh
# One-time: pin the glm tarball hash in the manifest
curl -sL https://github.com/g-truc/glm/archive/refs/tags/1.0.3.tar.gz | sha256sum
# Paste the result into the `sha256:` line for the glm module.

# Build and install at user scope
flatpak run org.flatpak.Builder --user --install --force-clean build-dir io.github.lipeaaraujo.stl2thumbnail.yml
```

## Smoke test

```sh
flatpak run --command=stl2thumbnail io.github.lipeaaraujo.stl2thumbnail --width=256 --height=256 --if=/path/to/sample.stl --of=/tmp/out.png xdg-open /tmp/out.png
```

## Export a shareable bundle

```sh
flatpak run org.flatpak.Builder --repo=repo --force-clean build-dir io.github.lipeaaraujo.stl2thumbnail.yml
flatpak build-bundle repo stl2thumbnail.flatpak io.github.lipeaaraujo.stl2thumbnail
```

The resulting `stl2thumbnail.flatpak` file can be shared and installed with `flatpak install ./stl2thumbnail.flatpak`.

## License

Packaging files (manifest, metainfo, README): MIT.
Upstream stl2thumbnail source: GPL-3.0-or-later.
