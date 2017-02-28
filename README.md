# Contentful POMS Lookup

Contentful UI Extension to add the POMS Lookup to the Contentful editor.

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

## Development

For developer convenience, it is possible to host the extension locally instead of uploading it to Contentful. This is useful if you're making changes. Please note that this will affect all users using the extension in your space. But you already created a separate space for development, didn't you?

Start the local development server and update the extension via the Contentful Extension CLI:

```bash
yarn start
contentful-extension update --space-id MY_SPACE_ID --force --src "http://localhost:8080"
```

If you now open an entry that uses the extension in your browser it will use the code from your local machine. You need to enable insecure content since the Contentful editor is served through HTTPS but your extension is not. See here how to do it in [Firefox][https://support.mozilla.org/en-US/kb/mixed-content-blocking-firefox] and [Chrome][https://support.google.com/chrome/answer/1342714].

Deploying `index.html` again, without having to run it locally, is as easy as:

```bash
contentful-extension update --space-id MY_SPACE_ID --force
```

## Useful resources

- [Getting started with Contentful UI Extensions](https://github.com/contentful/extensions/tree/master/samples/rating-dropdown)
- [Contentful UI Extensions SDK](https://github.com/contentful/ui-extensions-sdk)
- [Contentful UI Extensions API Reference](https://github.com/contentful/ui-extensions-sdk/blob/master/docs/ui-extensions-sdk-frontend.md)
- [Contentful Extension CLI](https://github.com/contentful/contentful-extension-cli)
