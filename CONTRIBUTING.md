# Contributing to Surf Browser

Thanks for helping make Surf better. This repository holds the downloads, documentation and release notes for Surf. The source code is not public, so the ways to help are reporting bugs, suggesting features and improving the docs.

## Report a bug

Open an issue using the bug report form. Please search [existing issues](https://github.com/gajishere/surf-browser-releases/issues) first. A good report includes:

- The Surf version. Type `ver` in Surf to see it.
- Your Windows version (Windows 10 or 11, and the build if you know it).
- Which download you use: the portable zip, or the small exe that needs .NET 10.
- Numbered steps that reproduce the problem, what happened, and what you expected.
- Console output or a screenshot, if it helps.

For security problems, do not open a public issue. See [SECURITY.md](SECURITY.md).

## Suggest a feature

Open an issue using the feature request form. Describe the problem you are trying to solve, then show the command or behaviour you have in mind as console input, for example `C:\Web> ...`. Mention any alternatives you considered.

## Improve the docs

Pull requests are welcome for documentation: typos, clearer wording, missing commands, better examples. Keep each pull request small and focused, and fill in the pull request template.

## Code contributions

The source code is not public, so code pull requests are not possible. If you have an idea for a code change, open a feature request or bug report instead and describe it there.

## Verify a download

Each release includes a `SHA256SUMS.txt` file with one line per download. To check your download in PowerShell, from the folder that holds the file:

```powershell
Get-FileHash .\<file> -Algorithm SHA256
```

Replace `<file>` with the name of the file you downloaded. Compare the `Hash` value with the matching line in `SHA256SUMS.txt`. The comparison is not case-sensitive. If the values differ, delete the file and download it again from the [latest release](https://github.com/gajishere/surf-browser-releases/releases/latest).

## Conduct

By taking part you agree to follow the [Code of Conduct](CODE_OF_CONDUCT.md).
