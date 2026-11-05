# dsh-purge Safe Compatibility Edition

This is a maintained compatibility branch based on the upstream dsh-purge project.
It keeps the original license and attribution requirements. It is not an official
DeepSeek product and is not endorsed by DeepSeek.

## Compatibility baseline

- Target DSH: `0.2.1-rc.5` (the npm `latest` version checked on 2026-11-05).
- Node.js: `^22.19.0 || >=24.0.0`, matching the current DSH runtime requirement.
- Do not force-install this branch on DSH 0.2.2 alpha/RC builds or future versions
  until the manifest and runtime behavior have been reviewed against that build.
- DSH is a fast-moving public preview. A matching version declaration is not a
  substitute for an integration test on your own installation.

## Install on a separate profile first

Back up the profile before installing. Keep your existing profile untouched while
checking compatibility.

Web:

```sh
dsh plugin --profile web add https://codeload.github.com/a2570825402-code/dsh-purge/tar.gz/refs/heads/safe-edition
```

Desktop:

```sh
dsh plugin --profile desktop add https://codeload.github.com/a2570825402-code/dsh-purge/tar.gz/refs/heads/safe-edition
```

Restart the selected host and inspect its plugin status before applying any patch.
Web and Desktop are separate profiles and must be checked independently.

## Rollback

1. Stop the selected DSH host.
2. Restore the profile backup you made before installation, or remove this bundle
   with `dsh plugin --profile <web|desktop> remove dsh-purge`.
3. Restart DSH and verify the original profile is healthy.
4. If a patch was already applied, use the plugin's Revert action before removing
   the bundle whenever the host still starts normally.

Do not delete backup files until the rollback has been verified.

## Safety and limitations

- Use only on a DSH installation and local environment you own or are authorized
  to administer.
- This branch does not bypass DeepSeek server-side policy, moderation, account
  controls, or service monitoring. No account-safety or ban-avoidance guarantee
  is possible.
- The Safe Edition label here means a conservative compatibility target and
  documented rollback path. It does **not** mean every inherited upstream prompt,
  red-team preset, or drill feature has been independently rewritten or audited
  into a benign security scanner. Review and disable any feature you do not need.
- Do not use the red-team/drill functionality against public systems or systems
  without explicit authorization.

## Validation status

Repository metadata and source files were inspected and the compatibility
manifest/documentation were updated. This GitHub-only editing session cannot run
the DSH host, install dependencies, execute the build, or perform a live Web /
Desktop integration test. Treat this branch as requiring local verification
before applying patches to a daily-use profile.
