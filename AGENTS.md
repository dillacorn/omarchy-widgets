# Fork development notes

This fork tracks `SimonSchubert/omarchy-widgets`. Keep upstream content intact. Do not include this fork-only file in upstream pull requests.

## Omagara (`faces/dillacorn/omagara/`)

- Keep experiments on separate branches; update an open PR only after testing and approval.
- From a checkout containing Omagara, run `java -jar tools/owl.jar review . faces/dillacorn/omagara/face.owl` before pushing. Also verify the upstream PR's `review` check: CI uses the upstream base branch's checker.
- The OWL reviewer can flag `cmd(condition ? null : command)` as unquoted even when command arguments use `sh()`. For an intentionally harmless idle command, use a quoted `"true"` branch instead of `null`; keep `sh()` for **every** dynamic shell value. This is a review workaround, not a general replacement for disabled sources.
- `cmd("true")` still executes when the source runs. Do not describe it as avoiding all shell startup or polling. Keep settings-changing actions guarded and backed up.
- On Android, `owl-check` only accepts installed `*.owl` files directly under `~/.config/omalauncher/widgets/`. Validate the installed file with backup/rollback; compilation does not prove runtime behavior.
- Confirm the exact changed files and PR head, then require a green upstream review before asking for merge.
