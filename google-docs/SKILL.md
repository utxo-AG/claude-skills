# Google Docs MCP Server

## Setup (One-time)

**Before using this MCP server, you MUST complete OAuth setup:**

### 1. Google Cloud Configuration
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create or select a project
3. Enable these APIs:
   - Google Docs API
   - Google Sheets API
   - Google Drive API
4. Configure OAuth consent screen:
   - User type: External (or Internal for Workspace)
   - Add scopes: `documents`, `spreadsheets`, `drive.file`
5. Create OAuth credentials:
   - Application type: Desktop app
   - Download JSON file
   - Save as `credentials.json` in `/Users/patricktobler/google-docs-mcp/`

### 2. Authorization
```bash
cd /Users/patricktobler/google-docs-mcp
node ./dist/server.js
```
- Browser opens for authorization
- Grant permissions
- Paste authorization code in terminal
- `token.json` is created automatically

### 3. Restart Claude Code
After setup, restart Claude Code for the MCP server to load.

---

## Available Tools

### Document Operations
| Tool | Description |
|------|-------------|
| `read_document` | Read document content (plain text, JSON, or markdown) |
| `append_text` | Add text to end of document |
| `insert_text` | Insert text at specific position |
| `delete_text` | Remove text from document |
| `format_text` | Apply formatting (bold, italic, colors) |
| `format_paragraph` | Set alignment, spacing, indentation |
| `insert_table` | Create tables |
| `insert_page_break` | Add page breaks |
| `insert_image` | Add images by URL |

### Spreadsheet Operations
| Tool | Description |
|------|-------------|
| `read_spreadsheet` | Read data using A1 notation |
| `write_spreadsheet` | Write data to cells |
| `append_rows` | Add rows to sheet |
| `clear_range` | Clear cell contents |
| `create_spreadsheet` | Create new spreadsheet |
| `add_sheet` | Add new sheet to spreadsheet |

### Drive Operations
| Tool | Description |
|------|-------------|
| `search_drive` | Search for files/folders |
| `list_documents` | List docs in folder |
| `create_folder` | Create new folder |
| `move_file` | Move file to folder |
| `copy_file` | Duplicate file |
| `rename_file` | Change file name |
| `delete_file` | Remove file |

### Comment Operations
| Tool | Description |
|------|-------------|
| `list_comments` | Get document comments |
| `add_comment` | Add new comment |
| `reply_to_comment` | Reply to existing comment |
| `delete_comment` | Remove comment |

---

## Usage Examples

### Read a Document
```
Use the read_document tool with the document ID from the URL:
https://docs.google.com/document/d/{DOCUMENT_ID}/edit

Extract the ID and call read_document with format "markdown" or "text"
```

### Write to Spreadsheet
```
Use write_spreadsheet with:
- spreadsheetId: from URL
- range: "Sheet1!A1:B10"
- values: [[row1], [row2], ...]
```

### Search Drive
```
Use search_drive with:
- query: filename or content search
- Returns list of matching files with IDs
```

---

## When to Use

- Reading/writing Google Docs content
- Updating spreadsheets programmatically
- Managing files in Google Drive
- Working with document comments
- Creating documents from templates

## Notes

- Document IDs are in the URL between `/d/` and `/edit`
- Spreadsheet ranges use A1 notation (e.g., "A1:C10")
- Multi-tab documents use tab IDs
- Images must be publicly accessible URLs
- Store `credentials.json` and `token.json` securely

## Troubleshooting

**"credentials.json not found"**
- Complete Google Cloud setup (step 1)
- Save credentials file to `/Users/patricktobler/google-docs-mcp/`

**"token.json not found"**
- Run authorization (step 2)
- Re-run if token expired

**MCP server not loading**
- Restart Claude Code
- Check `~/.claude.json` has google-docs entry
