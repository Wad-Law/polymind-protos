# Polymind Protos

Shared Protocol Buffer definitions for the Polymind ecosystem.

## Usage

This repository is intended to be used as a Git submodule in:
- **polymind** - Main trading bot (gRPC server)
- **polyops** - Operations CLI (gRPC client)

## Structure

```
protos/
  └── control.proto  # ControlService API definitions
```

## Integration

### Adding as submodule:
```bash
git submodule add <repo-url> protos
```

### Cloning projects with submodules:
```bash
git clone --recurse-submodules <project-url>
```

### Updating submodule:
```bash
git submodule update --remote protos
```

## Development

When making changes to protos:
1. Make changes in this repository
2. Commit and push to remote
3. Update submodule reference in dependent projects:
   ```bash
   cd protos
   git pull origin main
   cd ..
   git add protos
   git commit -m "Update proto definitions"
   ```
