# vue-command

A fully working Vue.js terminal emulator. See the [demo](https://ndabap.github.io/vue-command/).

## Features

- Parse arguments with [yargs-parser](https://www.npmjs.com/package/yargs-parser)
- Search history
- White/Dark theme support
- Autocomplete
- Lowest supported width is 300 pixels

## Installation

```bash
$ npm i vue-command --save
```

## Properties

| Property              | Type      | Default        | Required | Description                                                                                                                     |
|-----------------------|-----------|----------------|----------|---------------------------------------------------------------------------------------------------------------------------------|
| `commands`            | `Object`  | `{}`           | Yes      | Key-value pairs where key is command and value is function with [yargs arguments](https://github.com/yargs/yargs-parser#readme) |
| `hideBar`             | `Boolean` | `false`        | No       | Hides the bar                                                                                                                   |
| `hidePrompt`          | `Boolean` | `false`        | No       | Hides the prompt                                                                                                                |
| `prompt`              | `String`  | `~neil@moon:#` | No       | Sets the prompt                                                                                                                 |
| `placeholderText`     | `String`  | `Type help`    | No       | Sets the placeholder                                                                                                            |
| `placeholderTimeout`  | `Number`  | `4000`         | No       | Sets the placeholder timeout                                                                                                    |
| `showHelp`            | `Boolean` | `false`        | No       | Shows the placeholder                                                                                                           |
| `title`               | `String`  | `neil@moon: ~` | No       | Sets the title                                                                                                                  |
| `whiteTheme`          | `Boolean` | `false`        | No       | Enables the white theme                                                                                                         |
| `yargsOptions`        | `Object`  | `{}`           | No       | Sets the [yargs options](https://github.com/yargs/yargs-parser#readme)                                                          |

## Usage

```vue
<template>
  <vue-command
    :yargs-options="{ alias: { color: ['colour'] } }"
    :commands="commands"
  />
</template>

<script>
import VueCommand from 'vue-command'
import 'vue-command/dist/vue-command.css'

export default {
  components: {
    VueCommand
  },

  data: () => ({
    commands: {
      // yargs arguments
      pokedex: ({ color, _ }) => {
        if (color && _[1] === 'pikachu') return 'yellow'

        return `Usage: pokedex pokemon [option]<br><br>

        Example: pokedex pikachu --color
        `
      }
    }
  })
}
</script>

<style lang="scss">
  .vue-command {
    .term {
      -webkit-border-radius: 8px;
      -moz-border-radius: 8px;
      border-radius: 8px;
    }

    .term-std {
      min-height: 300px;
      max-height: 300px;
      overflow-y: scroll;
    }
  }
</style>
```

## Author

[Julian Claus](https://www.julian-claus.de) and contributors.

## License

MIT
