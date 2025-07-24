# Inline Buildpack Example

This example demonstrates how to use an inline buildpack to debug environment variables and inspect the `$CNB_PLATFORM_DIR/env/` directory during the build process.

## What the Inline Buildpack Does

The inline buildpack defined in `project.toml` will:

1. **Echo all current environment variables** - Shows all environment variables available during the build process, sorted alphabetically
2. **List contents of `$CNB_PLATFORM_DIR/env/`** - Shows the directory structure and contents of any files in the platform environment directory
3. **Display file contents** - If any files exist in the platform env directory, it will show their contents

## Files

- `project.toml` - Contains the inline buildpack definition

## References

- [Inline Buildpack Documentation](https://buildpacks.io/docs/for-app-developers/how-to/build-inputs/use-inline-buildpacks/)
- [Cloud Native Buildpacks](https://buildpacks.io/)
