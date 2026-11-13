# contentful-poms-lookup

A Contentful UI Extension that adds the POMS Lookup to `Symbol` fields in the Contentful editor, so editors can pick a POMS item and store its MID. Teams that use it register it in their own Contentful space, so its README is written for them.

## Ways to hurt yourself

1. **Developing in a shared space.** Pointing the extension at your local server affects all users using the extension in that space. Use a separate space for development.

## Running locally

For developer convenience, you can host the extension locally instead of uploading it to Contentful. Start the local development server and update the extension via the Contentful Extension CLI:

```bash
yarn start
contentful-extension update --space-id MY_SPACE_ID --force --src "http://localhost:8080"
```

If you now open an entry that uses the extension in your browser, it uses the code from your local machine. You need to enable insecure content, since the Contentful editor is served through HTTPS but your extension is not. See how to do that in [Firefox](https://support.mozilla.org/en-US/kb/mixed-content-blocking-firefox) and [Chrome](https://support.google.com/chrome/answer/1342714).

## Done means green

There are no tests, linting or CI. A change is done when the extension, hosted locally as above in a development space, stores the MID you pick in the field.

## Deploying

Deploying `index.html` again, without running it locally:

```bash
contentful-extension update --space-id MY_SPACE_ID --force
```

## Documentation

Most changes need no documentation; agents can read the code.

- The README is for the teams that install the extension: keep its installation and usage steps current when you change them.
- A reason that belongs to one spot in the code goes in a short comment there.

## How it works

`extension.json` registers the extension as "POMS Lookup" for `Symbol` fields and uploads `index.html` as its source. That page loads the Contentful UI Extensions SDK and its stylesheet from unpkg, and shows the field's value in an input with a button. The button opens the POMS Lookup with `POMS_LOOKUP_PARAMS` in its URL. The page accepts a `message` only from the POMS Lookup origin, stores the MID of the first selected item in the input and the field, and closes the popup. Typing in the input also sets the field.

These Contentful references help:

- [Getting started with Contentful UI Extensions](https://github.com/contentful/extensions/tree/master/samples/rating-dropdown)
- [Contentful UI Extensions SDK](https://github.com/contentful/ui-extensions-sdk)
- [Contentful UI Extensions API Reference](https://github.com/contentful/ui-extensions-sdk/blob/master/docs/ui-extensions-sdk-frontend.md)
- [Contentful Extension CLI](https://github.com/contentful/contentful-extension-cli)
