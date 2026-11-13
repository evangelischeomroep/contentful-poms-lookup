<img src="./.github/banner.svg" alt="contentful-poms-lookup" width="100%">

<p align="center">A POMS Lookup button for MID fields in the Contentful editor.</p>

Contentful UI Extension to add the POMS Lookup to the Contentful editor.

## What it does

- **Fills a field from POMS.** Editors click a button below a text field, pick an item in the POMS Lookup window, and its MID lands in the field.
- **Takes a typed MID too.** Editors can also type or paste a MID straight into the field.

## Installation

We're using Yarn in this repo, but npm will work as well.

1. Clone the repository.
2. Adapt the `POMS_LOOKUP_PARAMS` in `index.html` to your purposes.
3. Install the [Contentful Extension CLI](https://github.com/contentful/contentful-extension-cli) globally: `yarn global add contentful-extension-cli`.
4. Register/upload the extension with the Contentful API to make the Contentful editor aware of its existence:

```bash
export CONTENTFUL_MANAGEMENT_ACCESS_TOKEN=abcdefg
contentful-extension create --space-id MY_SPACE_ID
```

You need an access token for this. Instructions are in [Contentful's documentation](https://www.contentful.com/developers/docs/references/authentication/#getting-an-oauth-token).

## Using the extension in the Contentful editor

After you uploaded the extension via the Contentful Extension CLI, you need to reload the Contentful editor. Then, in your space, choose any Content Type with a `Symbol` field or create a new one. Open the “Settings” dialog for a field and switch to the Appearance tab. An extension with the name “POMS Lookup” should be visible at the end of the list. Select the extension from the list and save the Content Type. Finally you can open an entry for that Content Type and see the extension rendered.

Clicking on the "Zoek in POMS" button will open the POMS Lookup window. There you can search an item, select it and click the "Kies 1 geselecteerd item" button to close the POMS Lookup window again. The MID of the selected item should now be entered in the input field.

## Contributing

Working on this repo? [AGENTS.md](./AGENTS.md) has the setup, conventions and checks.
