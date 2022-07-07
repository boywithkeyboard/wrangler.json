<div align='center'>
<h1>wrangler.json</h1>
<b>✨ Configure Wrangler in the format of your choice. ✨</b>
</br>
</br>
</div>

## Installation

```bash
npm i -D wrangler.json
```

## Usage (CLI)

Run the below command and **wrangler.json** will automatically search for your configuration file and generate a `wrangler.toml` for you.

```bash
wrangler.json
```

### Automatically Detectable Files

- `wrangler.json`
- `wrangler.js`
- `wrangler.mjs`
- `wrangler.cjs`
- `wrangler.ts`

### Options

- `--config` to use a custom config, e.g. `wrangler.json --config="./my.json"`

## Usage (API)

```javascript
import { join } from 'node:path'
import { generateConfig, parseConfig } from 'wrangler.json'

// get the config from a file
const config = await parseConfig(join(someDirectory, './custom.json'))

// alternatively, you can only specify the directory name
const config = await parseConfig(someDirectory)

// generate a wrangler.toml from a config
await generateConfig(config)
```

## Config Files

`json`

```jsonc
{
  "$schema": "https://raw.githubusercontent.com/azurydev/wrangler.json/dev/schema.json",
  // your config (w/ autocomplete)
}
```

`js/mjs/ts`

```javascript
import { defineConfig } from 'wrangler.json'

export default defineConfig({
 // your config (w/ autocomplete)
})
```

`js/cjs`

```javascript
const { defineConfig } = require('wrangler.json')

module.exports = defineConfig({
 // your config (w/ autocomplete)
})
```

## Config Syntax

- all options must be specified in `camelCase`
- `vars` option was renamed to `variables`
- `nodeComp` option was renamed to `nodeCompatibility`
- any environment-related options must be specified under `development` *(global, default)*, `staging`, or `production`