# Ọjà Registry

The official package registry for Ifá-Lang packages.

## Structure

```
index/
├── 1/           # 1-character package names
├── 2/           # 2-character package names  
├── 3/           # 3-character packages (first char subdirs)
│   └── a/
│       └── abc
└── og/          # 4+ character packages (first 2 chars)
    └── un/      # next 2 chars
        └── ogunda-utils
```

## Publishing a Package

1. Ensure your `oja.toml` has complete metadata:
```toml
[package]
name = "my-package"
version = "1.0.0"
description = "A useful package"
repository = "https://github.com/username/my-package"
license = "MIT"
```

2. Create a Git tag and push:
```bash
oja publish
```

3. Submit a PR to this repository with your package index file.

## Package Index Format

Each package has a JSON file at `index/{path}/{name}`:

```json
{
  "name": "my-package",
  "description": "A useful package",
  "repository": "https://github.com/username/my-package",
  "license": "MIT",
  "versions": [
    {
      "version": "1.0.0",
      "checksum": "sha256:...",
      "yanked": false
    }
  ]
}
```

## Installing Packages

```bash
# Add by name (uses registry)
oja add my-package

# Add specific version
oja add my-package@1.0.0

# Add by Git URL (bypasses registry)
oja add https://github.com/username/my-package
```

## Search

Visit [packages.json](./packages.json) for the full searchable index.

---

*Maintained by the Ifá-Lang community*
