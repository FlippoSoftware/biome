# @flippo-software/biome

Shared [Biome](https://biomejs.dev) configuration presets — one set of formatter/linter rules, extendable per project type.

## Install

```sh
pnpm add -D @flippo-software/biome @biomejs/biome
```

## Usage

Extend one or more presets from your project's `biome.jsonc`:

```jsonc
{
	"extends": ["@flippo-software/biome/base"]
}
```

Available presets:

| Preset | Use for |
| --- | --- |
| `base` | Any project — formatter (4-space indent, single quotes, no trailing commas), linter rules, and import sorting. |
| `react` | React components — enables `react` lint domain, JSX filename conventions, hook-dependency checks. |
| `storybook` | `*.stories.ts(x)` files — relaxes cognitive-complexity limits for story definitions. |
| `test` | Unit test files (`*.tests.ts(x)`, `*.mocks.ts(x)`, `*.testplane.*`) — relaxes complexity limits, allows inline regex in queries. |

Combine as needed:

```jsonc
{
	"extends": [
		"@flippo-software/biome/base",
		"@flippo-software/biome/react",
		"@flippo-software/biome/test"
	]
}
```

## Requirements

- `@biomejs/biome` `^2.5.11` (peer dependency)
- Node and pnpm versions pinned in [.nvmrc](.nvmrc) and `package.json`'s `packageManager` field

## Contributing

Commit messages must follow [Conventional Commits](https://www.conventionalcommits.org) (`feat:`, `fix:`, `chore:`, ...) — this drives automatic versioning and is enforced on every pull request.

Direct pushes to `main` are disabled — changes land through pull requests. Merging to `main` triggers [release-please](https://github.com/googleapis/release-please), which opens a versioned release PR based on your commits; merging that PR tags a release and publishes to npm automatically.

```sh
pnpm lint     # check lint rules
pnpm format   # apply formatting
pnpm check    # CI-mode check (lint + format, no writes)
```

## License

ISC
