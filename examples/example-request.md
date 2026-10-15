# Example request

Attach the reference photos, then send a message like the one below. Any language works; the prompts themselves come back in English.

```
You are a Senior Prompt Engineer with over six years of experience in prompts,
in understanding and handling images, lighting, and every detail of an image.

Generate a series of prompts, each with one task: a portrait of this person
from a specific direction and camera angle.

Create a prompt for each of these angles:
1. Front, looking at the camera
2. The right side of the face
3. The left side of the face
4. From above
5. From below

The prompts must be professional, keep this person's facial features fixed,
and use these images as references for the face.
```

A shorter version works too:

```
Use the Cloning Face skill on these photos.
```

## Optional additions

- **Outfit:** "Dress them in a navy blazer over a white T-shirt." Only the STYLE block changes.
- **Backdrop:** "Use a warm beige backdrop instead of grey."
- **True profiles:** "Make the side views full 90° profiles."
- **Tool:** "I'm using Midjourney" or "I'm using Flux Kontext", so the tips match your tool.

## What you get back

1. A short reference review
2. (a) The IDENTITY pre-prompt
3. Five main prompts: Front, Right, Left, Above, Below
4. (b) The STYLE post-prompt
5. (c) The negative prompt
6. Consistency tips
