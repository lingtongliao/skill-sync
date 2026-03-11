# skills-sync

`skills-sync` is a cross-assistant skill sync toolkit that helps you:
- check whether local skills are latest,
- summarize differences with latest GitHub version,
- update local skills safely with backup and rollback.

It can be used as a standalone CLI in any workflow, and also includes a Claude plugin wrapper.

## Repository Structure

```text
.claude-plugin/plugin.json  # optional Claude wrapper metadata
skills/skills-update-manager/
  SKILL.md
  scripts/manage_skills.py
  references/
  examples/
scripts/generate_manifest.py
catalog/skills-manifest.json
tests/
```

## Compatibility

- Claude Code
- Codex workflows
- OpenCode workflows
- Any custom toolchain using file-based skill directories

## Install for Local Development

1. Clone repository.
2. Run the CLI directly or integrate with your preferred assistant runtime.
3. Trigger with prompts/invocations like:
   - "检查我的skills是不是最新版本"
   - "对比本地skill和GitHub最新差异"
   - "更新我的skills到最新版本"

## User CLI Examples

Check all skills:

```bash
python "skills/skills-update-manager/scripts/manage_skills.py" check \
  --repo lingtongliao/skills-sync \
  --ref main
```

Show diff of a specific skill:

```bash
python "skills/skills-update-manager/scripts/manage_skills.py" diff \
  --repo lingtongliao/skills-sync \
  --ref main \
  --skill skills-update-manager \
  --show-patch
```

Apply update:

```bash
python "skills/skills-update-manager/scripts/manage_skills.py" update \
  --repo lingtongliao/skills-sync \
  --ref main \
  --apply
```

## Maintainer Commands

Generate manifest:

```bash
python scripts/generate_manifest.py --repo lingtongliao/skills-sync --ref main
```

Run tests:

```bash
python -m unittest discover -s tests
```

## Release Notes

Recommended release flow:
1. bump versions in `plugin.json` and changed `SKILL.md` files;
2. regenerate `catalog/skills-manifest.json`;
3. run tests;
4. create git tag `vX.Y.Z`;
5. publish GitHub Release.
