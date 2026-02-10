# Railway Deployment

## When to Use
- User asks to deploy something
- Checking deployment status/logs
- Managing environment variables

## Workflow

### 1. Check Status
```
mcp__Railway__check-railway-status
```

### 2. List Projects (if needed)
```
mcp__Railway__list-projects
```

### 3. Deploy
```
mcp__Railway__deploy
  - workspacePath: path to project
  - service: optional, specific service
  - environment: optional, target environment
```

### 4. Verify Deployment
After deploy completes:
1. Get logs to check for errors
```
mcp__Railway__get-logs
  - workspacePath: path
  - logType: "deploy"
```

2. Generate/get domain
```
mcp__Railway__generate-domain
  - workspacePath: path
```

3. Use Browserbase to screenshot the live URL and verify

## Common Tasks

### Set Environment Variables
```
mcp__Railway__set-variables
  - workspacePath: path
  - variables: ["KEY=value", "KEY2=value2"]
```

### Check Build Logs (if deploy failed)
```
mcp__Railway__get-logs
  - workspacePath: path
  - logType: "build"
```

### Create New Environment
```
mcp__Railway__create-environment
  - workspacePath: path
  - environmentName: "staging" or "production"
```

## Post-Deploy Checklist
1. Check deploy logs for errors
2. Get/generate domain URL
3. Screenshot live site with Browserbase
4. Report success/failure to user
