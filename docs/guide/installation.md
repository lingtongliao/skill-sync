# Installation

## For Humans

Copy and paste this prompt to your LLM agent (Claude Code, OpenCode, Codex CLI, AmpCode, Cursor, etc.):

```text
Install and configure skills-sync by following the instructions here:
https://raw.githubusercontent.com/lingtongliao/skills-sync/refs/heads/main/docs/guide/installation.md
```

### Alternative (manual, direct command)

Install only `skills-update-manager` into `~/.skills/skills-update-manager`:

```bash
python -c "import tempfile,zipfile,urllib.request,shutil,pathlib;u='https://github.com/lingtongliao/skills-sync/archive/refs/heads/main.zip';t=pathlib.Path(tempfile.mkdtemp());z=t/'repo.zip';urllib.request.urlretrieve(u,z);zipfile.ZipFile(z).extractall(t);src=next(t.glob('skills-sync-*/skills/skills-update-manager'));dst=pathlib.Path.home()/'.skills'/'skills-update-manager';dst.parent.mkdir(parents=True,exist_ok=True);shutil.rmtree(dst,ignore_errors=True);shutil.copytree(src,dst);print(f'Installed: {dst}')"
```

Verify:

```bash
python ~/.skills/skills-update-manager/scripts/manage_skills.py check --repo lingtongliao/skills-sync --ref main
```

## For LLM Agents

Use `curl` to fetch this file exactly:

```bash
curl -fsSL https://raw.githubusercontent.com/lingtongliao/skills-sync/refs/heads/main/docs/guide/installation.md
```

Then execute these steps:

1. Ensure Python 3.10+ is available.
2. Run the manual install command above.
3. Run the verify command above.
4. If the user wants runtime auto-discovery, copy the installed folder to runtime-specific locations (for example `~/.claude/skills`, `~/.opencode/skills`, `~/.codex/skills`).
