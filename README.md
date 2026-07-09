# BlueBuild Template &nbsp; [![bluebuild build badge](https://github.com/blue-build/template/actions/workflows/build.yml/badge.svg)](https://github.com/blue-build/template/actions/workflows/build.yml)

<img width="402" height="426" alt="542900251-a3d3f06c-29eb-40a7-a096-213a3418af8e" src="https://github.com/user-attachments/assets/15eba342-0518-48e9-a1c4-738c0fe94f6e" />

Declarative, Atomic, immutable linux system. Built from atomic fedora, specifically Fedora silverblue, with customisations including the cachyOS kernel (v3 compatible cpus only) pre-installed. SCX schedular BPFland enabled by default. Niri, with Dank Material Shell, Contains MY software choices for all types of computing. (These cannot be uninstalled by the user). Dont use this- make your own with bluebuild, it is not too difficult.


<img width="1920" height="1080" alt="hurunagus-niri-dms" src="https://github.com/user-attachments/assets/caef46ac-db93-48e9-a62d-b0eb72aebd07" />


To rebase an existing atomic Fedora installation to the latest build:

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/blue-build/template:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/blue-build/template:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## ISO

If build on Fedora Atomic, you can generate an offline ISO with the instructions available [here](https://blue-build.org/how-to/generate-iso/#_top). These ISOs cannot unfortunately be distributed on GitHub for free due to large sizes, so for public projects something else has to be used for hosting.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/blue-build/template
```
