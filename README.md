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

### Making Changes

When making changes to protos:
1. Create a new branch for your changes
2. Edit proto files in `protos/` directory
3. **Validate locally** before committing:
   ```bash
   cd protos
   protoc --proto_path=. --descriptor_set_out=/dev/null *.proto
   ```
4. Commit and push to your branch
5. Create a pull request
6. **CI validation** will automatically check:
   - Proto syntax is valid
   - Files compile without errors
   - Basic style guidelines are followed
7. After merge, update submodule references in dependent projects

### Updating Dependent Projects

After changes are merged to `main`:
```bash
# In polymind or polyops repository
cd protos
git pull origin main
cd ..
git add protos
git commit -m "Update proto definitions"
git push
```

### Validation

This repository includes automated validation via GitHub Actions (`.github/workflows/validate.yml`):
- Runs on all pushes to `main` and pull requests
- Validates proto files compile with `protoc`
- Checks for basic style issues (syntax version, package declaration)

**Recommendation**: Enable branch protection on `main` to require validation checks to pass before merging.
