# MIP-003 Input Schema – Full Reference

Complete type and validation reference for [MIP-003 Attachment 01](https://github.com/masumi-network/masumi-improvement-proposals/blob/main/MIPs/MIP-003/MIP-003-Attachement-01.md).

## Supported Input Types (Detailed)

| Type | Description | Common Validations | Data Fields |
|------|-------------|-------------------|-------------|
| **none** | Display-only text/information | None (ignored) | description |
| **text** | Single-line text input | min, max, format: nonempty | placeholder, description, default |
| **textarea** | Multi-line text input | min, max, format: nonempty | placeholder, description, default |
| **number** | Numeric input | min, max, format: integer | placeholder, description, default |
| **boolean** | True/false checkbox | optional | description, default |
| **email** | Email address input | format: email (auto), min, max | placeholder, description, default |
| **password** | Password input (hidden) | min, max | placeholder, description |
| **tel** | Telephone number | format: tel-pattern, min, max | placeholder, description, default |
| **url** | URL/website input | format: url (auto), min, max | placeholder, description, default |
| **date** | Date picker | min, max | description, default |
| **datetime-local** | Date and time picker | min, max | description, default |
| **time** | Time picker | min, max | description, default |
| **month** | Month/year picker | min, max | description, default |
| **week** | Week picker | min, max | description, default |
| **color** | Color picker | None | default, description |
| **range** | Slider control | min, max | min, max, step, default, description |
| **file** | File upload | accept, min, max | description, outputFormat |
| **hidden** | Hidden field | None | value (required) |
| **search** | Search input | min, max, format: nonempty | placeholder, description, default |
| **checkbox** | Single checkbox | optional | description, default |
| **radio** | Radio button group | min: 1, max: 1 | values (required), default, description |
| **option** | Multi/single select | min, max | values (required), description |

## Validation Types (Full Matrix)

| Validation | Description | Applicable Types | Default |
|------------|-------------|------------------|---------|
| `min` | Minimum length (text), value (number/range), date/time, or options. Inclusive. | text, password, tel, search, textarea, number, range, date, datetime-local, time, month, week, option, checkbox, radio | - |
| `max` | Maximum length, value, date/time, or options. Inclusive. | Same as min | - |
| `format` | Specific format | text, email, url, tel, search → url, email, nonempty, tel-pattern; number → integer | - |
| `accept` | HTML accept attribute for file types | file | - |
| `optional` | Field not required | all | false |

Multiple validations of the same type apply in sequence with logical AND (e.g. two `min` rules both must pass).

## Format Validation Values

- `nonempty` – Field must not be empty
- `integer` – Number must be integer
- `email` – Valid email format (often implicit for email type)
- `url` – Valid URL format (often implicit for url type)
- `tel_pattern` – Telephone pattern

## Data Field Rules by Type

- **option / radio**: `values` array required; must be unique
- **range**: `min`, `max`, `step` in data for display; can also use validations
- **file**: `outputFormat` required; only `url` supported
- **hidden**: `value` required in data

## JSON Schema Example (Full)

```json
{
  "id": "example-input",
  "type": "text",
  "name": "Example name",
  "data": {
    "values": ["Option 1", "Option 2"],
    "placeholder": "test 123",
    "description": "Example input"
  },
  "validations": [
    { "validation": "min", "value": "3" },
    { "validation": "max", "value": "20" },
    { "validation": "format", "value": "nonempty" },
    { "validation": "optional", "value": "true" }
  ]
}
```

## Type-Specific Examples

**none (display only):**
```json
{
  "type": "none",
  "name": "Instructions",
  "data": { "description": "Please fill out all required fields" }
}
```

**text with validations:**
```json
{
  "type": "text",
  "name": "Username",
  "data": { "placeholder": "Enter username", "description": "3-20 characters" },
  "validations": [
    { "validation": "min", "value": "3" },
    { "validation": "max", "value": "20" }
  ]
}
```

**number (integer, range):**
```json
{
  "type": "number",
  "name": "Age",
  "data": { "description": "Must be 18 or older" },
  "validations": [
    { "validation": "min", "value": "18" },
    { "validation": "max", "value": "120" },
    { "validation": "format", "value": "integer" }
  ]
}
```

**range (slider):**
```json
{
  "type": "range",
  "name": "Priority Level",
  "data": {
    "min": "1",
    "max": "10",
    "step": "1",
    "default": "5",
    "description": "1 (low) to 10 (high)"
  }
}
```

**file (single upload, URL output):**
```json
{
  "id": "file-upload",
  "type": "file",
  "name": "Document Upload",
  "data": {
    "description": "PDF or Word documents only (max 4.5MB)",
    "outputFormat": "url"
  },
  "validations": [
    { "validation": "accept", "value": "image/*,.pdf,.doc,.docx" },
    { "validation": "min", "value": "1" },
    { "validation": "max", "value": "1" }
  ]
}
```

**hidden:**
```json
{
  "type": "hidden",
  "name": "Session ID",
  "data": { "value": "abc123xyz" }
}
```

**option (multi-select with min/max):**
```json
{
  "type": "option",
  "name": "Countries",
  "data": {
    "values": ["United States", "United Kingdom", "Canada"],
    "description": "Select one or more countries"
  },
  "validations": [
    { "validation": "min", "value": "1" },
    { "validation": "max", "value": "3" }
  ]
}
```

## File Handling

File inputs support only `outputFormat: "url"`. The buyer uploads the file and the agent receives a URL string. `outputFormat: "base64"` is not supported.

## Security

- Treat all input as untrusted.
- Validate server-side; the schema guides frontend rendering only.
- Do not combine impossible validations (e.g. `format: email` with `max: 2`).
