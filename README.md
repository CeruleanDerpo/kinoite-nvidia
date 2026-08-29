# kinoite-nvidia &nbsp; [![bluebuild build badge](https://github.com/ceruleanderpo/kinoite-nvidia/actions/workflows/build.yml/badge.svg)](https://github.com/ceruleanderpo/kinoite-nvidia/actions/workflows/build.yml)

A maintained set of images for `rpm-ostree`/`bootc`-based systems
This repo builds the following images:
+ [`kinoite-nvidia`](#kinoite-nvidia)
+ [`kinoite-nvidia-gaming`](#kinoite-nvidia-gaming)
+ [`kinoite-nvidia-niri`](#kinoite-nvidia-niri)

## `kinoite-nvidia`
An up-to-date kinoite image with Nvidia support out of the box to prevent the hassles most kinoite users who have an Nvidia card have to face

### Installation
To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  bootc switch ghcr.io/ceruleanderpo/kinoite-nvidia:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  bootc switch --enforce-container-sigpolicy ghcr.io/ceruleanderpo/kinoite-nvidia:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## `kinoite-nvidia-gaming`
A version of [`kinoite-nvidia`](#kinoite-nvidia), with the Steam package included, recommended if you use a controller


### Installation
To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  bootc switch ghcr.io/ceruleanderpo/kinoite-nvidia-gaming:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  bootc switch --enforce-container-sigpolicy ghcr.io/ceruleanderpo/kinoite-nvidia-gaming:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## `kinoite-nvidia-niri`
A Kinoite image that includes the Nvidia drivers, the [Niri](https://niri-wm.github.io/niri/index.html) window manager and some tools for customization and shells, along with KDE Plasma as a fallback
It tries to integrate Plasma's services instead of GNOME's to prevent duplicated functionality

> [!note]
> The image doesn't come with the systemd services for the tools such as plasma-polkit-agent yet, so they will have to be configured manually

### Installation
To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  bootc switch ghcr.io/ceruleanderpo/kinoite-nvidia-niri:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  bootc switch --enforce-container-sigpolicy ghcr.io/ceruleanderpo/kinoite-nvidia-niri:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

<!-- ## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/how-to/generate-iso/#_top). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting. -->

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

+ `kinoite-nvidia`:
  ```bash
  cosign verify --key cosign.pub ghcr.io/ceruleanderpo/kinoite-nvidia
  ```
+ `kinoite-nvidia-gaming`:
  ```bash
  cosign verify --key cosign.pub ghcr.io/ceruleanderpo/kinoite-nvidia-gaming
  ```
+ `kinoite-nvidia-niri`:
  ```bash
  cosign verify --key cosign.pub ghcr.io/ceruleanderpo/kinoite-nvidia-niri
  ```
