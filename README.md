# eht-privacy

Public-facing pages for the **E-HT Weight Loss** app, plus the Android
download. The app's source lives in a separate private repo.

The repo name predates the download page and is now a little narrow.
**Do not rename it.** A project Pages site is served from
`<user>.github.io/<repo>/`, so the repo name is part of the URL, and
that URL is hardcoded in the app (`app/settings.tsx`) and therefore
baked into every build already installed on someone's phone. It is
also the privacy-policy URL in the Play listing and in the Health
Connect declaration. Renaming would 404 all of those for anyone who
has not updated. If the name ever has to change, put a custom domain
on the Pages site first so the URL stops depending on it.

## Hosted at

- Landing: <https://father-sherman.github.io/eht-privacy/>
- Privacy: <https://father-sherman.github.io/eht-privacy/privacy/>
- Download: <https://father-sherman.github.io/eht-privacy/downloads/>

## Editing

Edit `privacy.md`, `index.md` or `downloads.md` and push to `main`.
GitHub Pages rebuilds in about a minute.

`_config.yml` has an `include:` allowlist. A new page that is not
listed there is simply not served, with no error.

The "Last updated" date in `privacy.md` should be bumped any time the
policy changes in a way users would care about.

`privacy.md` is the **canonical** copy. The app repo keeps a mirror at
`docs/privacy.md` for reference, and a test there fails if the two
drift, but this is the one users read.

## Releases

Each release carries one asset, `eht-weight-loss.apk`, deliberately
**unversioned** so that
`releases/latest/download/eht-weight-loss.apk` keeps resolving. A
versioned filename would 404 the moment the next release landed.

The APK is built with `EXPO_PUBLIC_GEMINI_API_KEY` empty, so no
developer API key ships in it. A key baked into a public APK is
readable by anyone who unzips the file. See the release runbook in the
app repo (`.play/RELEASE.md`, step 4b) for the build command and the
verification, which uses a positive control so a broken scan cannot
read as success.
