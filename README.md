# Lumacut releases

This repository is the release channel for **Lumacut**, a video editor for Windows 10/11 (64-bit). It holds only
what installed copies need: the installer and the signed update information for each version. The source code is
not here.

## Install

Download `Lumacut-Setup-<version>.exe` from the [latest release](../../releases/latest) and run it. It installs
for the current user in a few seconds (no administrator rights), adds desktop and Start-menu shortcuts, and can be
removed from *Settings → Apps*. The installer isn't signed with a paid Microsoft certificate yet, so the first time
Windows may say "Windows protected your PC": choose *More info → Run anyway*.

## Updates

Lumacut updates itself: *Help (?) → Check for updates → Download → Install & Restart*, plus a quiet check once a
day. Installed copies read

    https://github.com/Yorgaki/lumacut-releases/releases/latest/download/latest.json

from the newest release. That file is signed with the Lumacut release key (Ed25519); Lumacut checks the signature
against the public key built into it, downloads the installer it names, and installs it only if its size and
SHA-512 match the signed values. A file that isn't signed with the release key, or an installer that doesn't
match, is refused. Projects and settings are kept across updates.

## Maintainers

Releases are made with `npm run release` in the Lumacut project, which builds, signs and uploads both files and
publishes the release only once both are in place. Don't upload or edit release files by hand: an unsigned or
changed `latest.json` is refused by every installed copy.
