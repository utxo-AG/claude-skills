---
name: mip-003-input-schema
description: Defines the Masumi MIP-003 input validation schema format for agent job inputs. Use when creating, rendering, or validating agent input schemas, job input forms, input types, validation rules, or when working with Masumi protocol inputs.
---

# MIP-003 Input Validation Schema

Standard format for agent input types per [MIP-003 Attachment 01](https://github.com/masumi-network/masumi-improvement-proposals/blob/main/MIPs/MIP-003/MIP-003-Attachement-01.md). Types align with HTML input types (except button).

## Core Fields

| Field | Required | Description |
|-------|----------|-------------|
| `id` | Yes | Unique identifier; links input to data. Must be unique within the form. |
| `type` | Yes | Input type; determines rendering and validation. |
| `name` | Yes | Display label for the user. |
| `data` | No | Type-specific config (placeholder, description, values, default, etc.). |
| `validations` | No | Validation rules. |

**Default:** All fields are required unless `validation: "optional"` is set.

## Quick Reference: Input Types

| Type | Use Case | Key Data Fields |
|------|----------|-----------------|
| `none` | Display-only text | `description` |
| `text` | Single-line text | placeholder, description, default |
| `textarea` | Multi-line text | placeholder, description, default |
| `number` | Numeric input | placeholder, description, default |
| `boolean` / `checkbox` | True/false | description, default |
| `email` | Email address | placeholder, description, default |
| `password` | Hidden password | placeholder, description |
| `tel` | Phone number | placeholder, description, default |
| `url` | URL/website | placeholder, description, default |
| `date` | Date picker | description, default |
| `datetime-local` | Date + time | description, default |
| `time` | Time picker | description, default |
| `month` | Month/year | description, default |
| `week` | Week picker | description, default |
| `color` | Color picker | default, description |
| `range` | Slider | min, max, step, default, description |
| `file` | File upload | description, **outputFormat** (required) |
| `hidden` | Hidden field | **value** (required) |
| `search` | Search input | placeholder, description, default |
| `radio` | Radio group | **values** (required), default, description |
| `option` | Single/multi select | **values** (required), description |

## Validations

| Validation | Applies To | Description |
|------------|------------|-------------|
| `min` | text, number, range, date/time, option, etc. | Min length, value, date, or options. Inclusive. |
| `max` | Same as min | Max length, value, date, or options. Inclusive. |
| `format` | text, email, url, tel, number | `email`, `url`, `nonempty`, `integer`, `tel_pattern` |
| `accept` | file | HTML accept spec (e.g. `image/*,.pdf,.doc,.docx`) |
| `optional` | all | Field is not required (default: required) |

Validations are combined with logical AND. Avoid contradictory rules (e.g. `format: email` with `max: 2`).

## Minimal Examples

**Text with length:**
```json
{
  "id": "username",
  "type": "text",
  "name": "Username",
  "data": { "placeholder": "Enter username", "description": "3-20 characters" },
  "validations": [
    { "validation": "min", "value": "3" },
    { "validation": "max", "value": "20" }
  ]
}
```

**Select (radio):**
```json
{
  "id": "payment",
  "type": "radio",
  "name": "Payment Method",
  "data": {
    "values": ["Credit Card", "PayPal", "Bank Transfer"],
    "default": "Credit Card"
  }
}
```

**File upload (outputFormat required):**
```json
{
  "id": "document",
  "type": "file",
  "name": "Document Upload",
  "data": { "description": "PDF only (max 4.5MB)", "outputFormat": "url" },
  "validations": [
    { "validation": "accept", "value": "image/*,.pdf,.doc,.docx" },
    { "validation": "min", "value": "1" },
    { "validation": "max", "value": "1" }
  ]
}
```

**Optional boolean:**
```json
{
  "id": "newsletter",
  "type": "boolean",
  "name": "Subscribe to Newsletter",
  "data": { "default": false },
  "validations": [{ "validation": "optional", "value": "true" }]
}
```

## Important Notes

1. **File `outputFormat`**: Only `url` is supported; agent receives file as URL string.
2. **option/radio**: Require non-empty `values` array; values must be unique.
3. **range**: Put min/max in `data` for display; use `validations` for constraints.
4. **hidden**: Requires `data.value`.
5. **Untrusted data**: Always validate received input server-side; schema guides UI only.

## Reference

- [MIP-003 Attachment 01](https://github.com/masumi-network/masumi-improvement-proposals/blob/main/MIPs/MIP-003/MIP-003-Attachement-01.md) – Official spec
- For complete type table, validation matrix, and all examples, see [reference.md](reference.md).
