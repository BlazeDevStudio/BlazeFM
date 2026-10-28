# BlazeFM repository migration manifest

**Date:** 2026-10-28  
**Project:** BlazeFM v1.3.3 Android file manager  
**Status:** SOURCE_STAGED; CI and device acceptance require separate verification.  

## Provenance

- **Original repository:** [BlazingSystems/BlazingSystems-Labs](https://github.com/BlazingSystems/BlazingSystems-Labs)
- **Original path:** `android/blazefm/`
- **Exact source commit:** `5d8e4f1d95b6bfc551996634df9c6f7b86af56b4` (Labs `main` at migration inspection).
- **Destination repository:** [BlazingSystems/BlazeFM](https://github.com/BlazingSystems/BlazeFM)
- **Destination branch:** `migration/blazefm-v133-source-20261028`
- **Destination untouched original main:** `83f76793ef149ed4b17483a89f3e9f3a3ac4f494`.
- **Exact-source staging commit:** `598fd904917d8be5ca9f54f551d37329fa41efe3`.
- **Source binary/third-party attribution:** original `THIRD_PARTY.md` copied verbatim; audit licensing and distribution obligations separately before public release.

## Source integrity result

The full 109-file `android/blazefm/` source subtree was imported at repository root. Recursive Git tree comparison verified **109/109 identical Git blob SHAs and file modes**; zero missing, altered or extra files, and both recursive listings were non-truncated. The destination is a content-copy migration; the original commit graph and attribution remain accessible only through the linked Labs repository and exact source commit.

## CI migration

- Original Labs workflow: [`.github/workflows/blazefm-android.yml`](https://github.com/BlazingSystems/BlazingSystems-Labs/blob/5d8e4f1d95b6bfc551996634df9c6f7b86af56b4/.github/workflows/blazefm-android.yml).
- The original workflow publishes preview releases and a fallback artifact branch on Labs main. **Those publishing steps are deliberately NOT transplanted** into the destination CI.
- Destination `.github/workflows/blazefm-ci.yml` uses root-aware path filters, JDK 17, Android SDK 35, Gradle 8.9 and Android Gradle Plugin 8.7.3, assembles debug and unsigned release APKs, runs Android lint, produces SHA-256 manifests and uploads non-published CI artifacts.
- CI workflow has read-only repository permission and cancels obsolete repeat PR runs. It does not sign production releases, flash devices, create tags, publish prereleases or touch the original Labs workflow.
- Re-evaluate live workflow and artifact results at the actual PR head before changing status to VERIFIED.

## Remaining acceptance

1. Build and lint in new destination at exact commit SHA, inspect all failed jobs and compare code/artifact identity.
2. Device tests across relevant Android versions, especially older/512-MB-class phones, all-files access, root, SAF, remote FTP/SMB/SFTP and duplicate-cleanup failure modes.
3. Security and policy review for broad file/package permissions and third-party license obligations.
4. Release signing must use a controlled private source and explicit authorization. No source/PR deletion or forced history rewrite.
5. Keep original Labs source and production/upload workflows intact until replacement coverage and ownership are accepted.

**No production readiness or APK installability is implied by repository organization.**
