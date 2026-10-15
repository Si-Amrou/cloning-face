# Cloning Face

A Claude skill that turns reference photos of **any face** into a set of identity-locked image-generation prompts, so the same face stays consistent across five camera angles.

## What it produces

For every set of reference photos, the skill returns:

| Part | Purpose |
|------|---------|
| Reference review | Which photos to use, which to downweight, what to crop out |
| **(a) Pre-prompt: IDENTITY block** | Locks the face: shape, skin, hair, hairline, eyes, nose, lips, facial hair |
| **Five main prompts** | Front, Right side, Left side, From above, From below |
| **(b) Post-prompt: STYLE block** | Shared studio look: framing, backdrop, light, lens, realism |
| **(c) Negative prompt** | Blocks face drift, distortion and artefacts |
| Consistency tips | Seeds, reference weights, generation order |

Each final prompt is assembled like this:

```
[IDENTITY BLOCK] + [POSE & ANGLE + LIGHTING for one angle] + [STYLE BLOCK]
```

Only the middle part changes between the five images. That is what keeps the face stable.

## Repository structure

```
cloning-face/
├── .claude-plugin/
│   ├── plugin.json          # Plugin manifest
│   └── marketplace.json     # Lets Claude Code install the repo as a plugin
├── skills/
│   └── cloning-face/
│       └── SKILL.md         # The skill itself
├── examples/
│   └── example-request.md   # How to ask for a kit
├── .gitignore
├── LICENSE
└── README.md
```

## Installation

### Claude.ai (web, desktop, mobile)

1. Download or zip the `skills/cloning-face` folder.
2. Open **Settings → Capabilities → Skills** and upload the zip.
3. Start a new chat, attach face photos and ask for a Cloning Face kit.

### Claude Code

Add the repository as a plugin marketplace, then install the plugin:

```
/plugin marketplace add Si-Amrou/cloning-face
/plugin install cloning-face@cloning-face
```

Or copy the skill folder directly into your personal skills directory:

```bash
mkdir -p ~/.claude/skills
cp -r skills/cloning-face ~/.claude/skills/
```

## Usage

Attach 2–6 clear photos of the person's face and write something like:

> Use the Cloning Face skill on these photos.

The best references are frontal, evenly lit and taken from a normal distance. Close phone selfies and photos with other people in them still work, but the skill will tell you to downweight or crop them.

Paste the finished prompts into your image tool together with the reference photos. The skill works well with face-reference features such as InstantID, PuLID, IP-Adapter FaceID, Midjourney omni-reference, Flux Kontext, and Gemini or GPT image editing.

## Tips for best results

- Generate the **front view first**, then add it as an extra reference for the other four angles.
- Keep the **seed fixed** across all five images.
- If side views drift, reduce the rotation from 60° to about 45°.
- To change the outfit, edit only the clothing line in the STYLE block.

## Responsible use

Only use photos of yourself or of people who have given you permission. The skill describes visible features only; it does not identify people or describe sensitive traits, and it always produces clothed, professional portraits.

## License

[MIT](LICENSE)
