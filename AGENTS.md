# Agent instructions

## Setting up Warmr (for coding agents)

The step-by-step setup prompt at https://warmr.so/setup/claude-setup.md is the single source for how to run each check and its fix. This section lists the order and the check names only. The page at https://warmr.so/setup-with-claude shows that prompt and copies it. The full docs index is at https://docs.warmr.so/llms.txt.

### Setup order

1. Mac prerequisites
2. iPhone prep
3. Install the Warmr Mac app and sign in
4. Install the Warmr runner on each phone and run its checks
5. Account ramp
6. First test post
7. Troubleshooting reference

### Checks

Each row names one check and who acts.

#### Mac (step 1)

| Check | Who acts |
|---|---|
| macOS version: 14 or later | Agent |
| Xcode installed and selected | Agent checks. The user runs the one `sudo` command in the agent rules below. |
| Mac kept awake: no system sleep, display sleep or disk sleep | Agent |
| Powered USB hub: required from 4 iPhones | User |
| Open-file limit: Warmr raises its own limit at launch. Act only on the `open_file_limit_low` finding from `warmrctl doctor`. | Agent |

#### iPhone (step 2)

| Check | Who acts |
|---|---|
| iOS 17 or later | Agent |
| Plugged in, with **Trust This Computer** tapped | User taps on the phone |
| Developer Mode on | User, on the phone |
| Developer Disk Image mounted | Agent |
| Signing with the user's own Apple team, free or paid account. The limits of each are in Step 2.0 of the prompt. | User sets the team in Xcode. Agent checks. |

#### Install (step 3)

| Check | Who acts |
|---|---|
| Sign in at https://app.warmr.so | User |
| Download and install the Warmr Mac app | User |
| Activate the license | User pastes the key into the app, never into chat |
| Wire up `warmrctl` with `bootstrap`, then check `setup status`. The full commands are in Steps 3.4 and 3.5 of the prompt. | Agent |

#### Per phone (step 4)

| Check | Who acts |
|---|---|
| iPhone visible | Agent |
| Signing identity | Agent |
| Developer Disk Image mounted | Agent |
| Runner reachable | Agent |
| Video stream | User confirms the live screen in the app |
| Touch | Agent checks UI Automation. The first ramp session proves the taps. |
| TikTok or Instagram installed | Agent checks. The user installs the app on the phone. |

#### First post (step 6)

| Check | Who acts |
|---|---|
| One clip, one account whose ramp finished, confirmed published exactly once | Agent, after the user names the clip and the account |

### Agent rules

- Never ask for or store passwords, Apple ID credentials, device passcodes or the license key in chat.
- Never run a command with `sudo` before you explain it. The only one is `sudo xcode-select -s /Applications/Xcode.app/Contents/Developer`, and the user runs it.
- Stop and ask the user whenever a step needs a physical action on the phone.
- Run the setup in a local Terminal on the Mac that runs Warmr. Never run it over SSH or from a cloud agent.

## Editing these docs

### About this project

- This is a documentation site built on [Mintlify](https://mintlify.com)
- Pages are MDX files with YAML frontmatter
- Configuration lives in `docs.json`
- Run `mint dev` to preview locally
- Run `mint broken-links` to check links

### Style preferences

- Use active voice and second person ("you")
- Keep sentences concise, with one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references

### MDX safety

This file compiles as MDX. Put every `<UDID>`-style placeholder, every angle bracket and every brace inside inline code or a code block. If you do not, the file fails to parse and `mint validate` prints a `parsing error` line for it. Look for that line: the command can still print success and exit 0.
