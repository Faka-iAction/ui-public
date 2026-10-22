# UI design system

The design system shared by every FAKA iAction front end: the web app, the website, the
mobile app and, for brand colour only, the admin.

Repository: `Faka-iAction/ui-public` (FAKA iAction platform, UI component).

## Contents

- [DESIGN_SYSTEM.md](DESIGN_SYSTEM.md): colour tokens for light and dark, type, shape and
  spacing, components, the app frame and navigation, and the accessibility rules.

## How it is used

- **Web app and website:** one stylesheet built on these tokens. No framework, and every page
  works without JavaScript.
- **Mobile app (Flutter):** the same tokens in the app theme.
- **Admin:** the [Tabler](https://tabler.io) theme (MIT), with the FAKA iAction primary colour.

## Visibility

This repository is **public**. Everything in it is visible to anyone. It holds only sanitised
content: no secrets, credentials, production infrastructure details, risk thresholds or
commercial terms.

## Architecture

This component follows the FAKA iAction master architecture. FAKA iAction is the platform;
FAKA iRequest is one vertical on it.

## Licence

All rights reserved, with a limited permission for educational use. See
[LICENSE.md](LICENSE.md). The licence is a draft pending legal review. The webfonts named
below (Figtree, Bricolage Grotesque) are under the SIL Open Font License; Tabler is MIT.
