# fal.ai - Generative AI Models

## API Key
```
FAL_KEY=6731aef8-c046-43af-9899-6cabd41ed6bf:1628627f84ea59ff61dee82211e7b397
```

Set this in environment before using fal_client:
```python
import os
os.environ["FAL_KEY"] = "6731aef8-c046-43af-9899-6cabd41ed6bf:1628627f84ea59ff61dee82211e7b397"
import fal_client
```

## What is fal.ai
- 600+ production-ready generative media models
- Single unified API for image, video, voice, and audio generation
- Fastest inference for diffusion models
- Pay-per-use pricing

## When to Use
- Generating images from text prompts
- Image-to-image transformations
- Video generation
- Audio/voice generation
- Any generative AI media task

## Key Models (Text-to-Image)
| Model | ID | Price |
|-------|-----|-------|
| FLUX.1 dev | `fal-ai/flux/dev` | $0.025/megapixel |
| FLUX Pro Ultra | `fal-ai/flux-pro/v1.1-ultra` | $0.06/image |
| Fast SDXL | `fal-ai/fast-sdxl` | $0.001/compute sec |
| Recraft V3 | `fal-ai/recraft/v3/text-to-image` | $0.04/image |

## Quick Usage

### Python
```python
import os
os.environ["FAL_KEY"] = "6731aef8-c046-43af-9899-6cabd41ed6bf:1628627f84ea59ff61dee82211e7b397"
import fal_client

handler = fal_client.submit(
    "fal-ai/flux/dev",
    arguments={"prompt": "a cute cat"}
)
result = handler.get()
image_url = result["images"][0]["url"]
```

### List Available Models
```python
import httpx

response = httpx.get(
    "https://api.fal.ai/v1/models",
    params={"category": "text-to-image", "status": "active"},
    headers={"Authorization": "Key 6731aef8-c046-43af-9899-6cabd41ed6bf:1628627f84ea59ff61dee82211e7b397"}
)
models = response.json()["models"]
```

### Get Pricing
```python
response = httpx.get(
    "https://api.fal.ai/v1/models/pricing",
    params={"endpoint_id": "fal-ai/flux/dev"},
    headers={"Authorization": "Key 6731aef8-c046-43af-9899-6cabd41ed6bf:1628627f84ea59ff61dee82211e7b397"}
)
price = response.json()["prices"][0]
# {"endpoint_id": "...", "unit_price": 0.025, "unit": "megapixels"}
```

## API Endpoints

### Models List
```
GET https://api.fal.ai/v1/models
?category=text-to-image
&status=active
&limit=100
```

### Pricing
```
GET https://api.fal.ai/v1/models/pricing
?endpoint_id=fal-ai/flux/dev
```

### Generate (Queue API)
```
POST https://queue.fal.run/{model_id}
Authorization: Key {FAL_KEY}
Body: {"prompt": "..."}
```

## Response Format
```python
{
    "images": [
        {
            "url": "https://v3b.fal.media/files/...",
            "width": 1024,
            "height": 1024,
            "content_type": "image/png"
        }
    ],
    "seed": 12345,
    "timings": {"inference": 2.5}
}
```

## Notes
- Images hosted on `v3b.fal.media` are temporary
- Upload to permanent storage (DO Spaces) for long-term use
- Some "text-to-image" models require input images (e.g., `/lora/edit`)
- ~143 text-to-image models currently available

## Links
- Docs: https://docs.fal.ai
- Models: https://fal.ai/models
- MCP Server: https://docs.fal.ai/mcp
