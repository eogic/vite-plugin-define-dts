# vite-plugin-define-dts

根据 Vite 配置中的 `define` 选项自动生成对应的类型定义。

Automatically generate corresponding type definitions based on define `option` in the Vite configuration.

## 📦 安装 & Install

```shell
# npm
npm i vite-plugin-define-dts -D

# yarn
yarn add vite-plugin-define-dts -D

# pnpm
pnpm add vite-plugin-define-dts -D
```

## 🦄 基础用法 & Basic Usage

在 `vite.config.js` / `vite.config.ts` 中添加 VitePluginDefineDts 插件并进行配置：

Add VitePluginDefineDts plugin to `vite.config.js` / `vite.config.ts` and configure it:

```ts
// vite.config.js / vite.config.ts
import { VitePluginDefineDts } from 'vite-plugin-define-dts'

export default {
  plugins: [VitePluginDefineDts()]
}
```

在 `tsconfig.json` 文件中增加 `compilerOptions.types` 配置。

Add `compilerOptions.types` configuration to the `tsconfig.json` file.

```json
{
  "compilerOptions": {
    "types": ["define.d.ts"]
  }
}
```

## 🎃 参数 & Parameters

- path

  - 生成 `.d.ts` 文件的文件路径。默认为 `define.d.ts` 。
  - The file path for generating the `.d.ts` file. Defaults to `define.d.ts`.
- filter

  - 筛选出哪些全局常量需要被写入到 `.d.ts` 中。
  - Identify which global constants need to be written to `.d.ts` file.
  - 可以是一个正则表达式，一个函数或一个带有 `key` 和 `value` 属性的函数对象。
  - It can be a regular expression, a function, or an object with `key` and `value` properties.
- comment

  - 需要被写入到 `.d.ts` 文件顶部的注释。
  - Comments that need to be written at the top of the `.d.ts` file.
  - 可以是一个字符串或字符串数组。
  - It can be a string or an array of strings.

## 🎨 例子 & Example

```javascript
import {VitePluginDefineDts} from 'vite-plugin-define-dts'

export default {
    define: {
        __VITE_APP_VERSION__: JSON.stringify('0.0.1')
    },
    plugins: [
        VitePluginDefineDts({
            path: path.resolve(import.meta.dirname, 'types', 'define.d.ts'),
            filter: {
                key: /__VITE_/i,
                value: () => true
            },
            comment: 'DO NOT MODIY THIS FILE'
        })
    ]
}
```

## 🍬 作者 & Author

[eogic](https://github.com/eogic)

## 🎀 许可证 & License

[MIT licenses](https://opensource.org/licenses/MIT)


---

如果您喜欢这个插件，请给 [vite-plugin-define-dts](https://github.com/eogic/vite-plugin-define-dts) 一个星标，谢谢！

If you like this plugin, please give  [vite-plugin-define-dts](https://github.com/eogic/vite-plugin-define-dts)  a star, thanks!
