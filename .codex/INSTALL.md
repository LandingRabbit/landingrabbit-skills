# Installing LandingRabbit Skills for Codex

Enable LandingRabbit Skills in Codex via native skill discovery. Just clone and symlink.

## Prerequisites

- Git

## Installation

1. **Clone the `landingrabbit-skills` repository:**

   ```bash
   git clone https://github.com/landingrabbit/landingrabbit-skills.git ~/.codex/landingrabbit-skills
   ```

2. **Create the skills symlink:**

   ```bash
   mkdir -p ~/.agents/skills
   ln -s ~/.codex/landingrabbit-skills/skills ~/.agents/skills/landingrabbit-skills
   ```

   **Windows (PowerShell):**

   ```powershell
   New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.agents\skills"
   cmd /c mklink /J "$env:USERPROFILE\.agents\skills\landingrabbit-skills" "$env:USERPROFILE\.codex\landingrabbit-skills\skills"
   ```

3. **Restart Codex** (quit and relaunch the CLI) to discover the skills.

## Verify

```bash
ls -la ~/.agents/skills/landingrabbit-skills
```

You should see a symlink (or junction on Windows) pointing to your LandingRabbit Skills directory.

## Updating

```bash
cd ~/.codex/landingrabbit-skills && git pull
```

Skills update instantly through the symlink.

## Uninstalling

```bash
rm ~/.agents/skills/landingrabbit-skills
```

Optionally delete the clone: `rm -rf ~/.codex/landingrabbit-skills`.
