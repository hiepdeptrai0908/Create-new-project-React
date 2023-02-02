## Các bước tạo dự án với create-react-app :wink:

## Step 1: Khởi tạo dự án

```sh
npx create-react-app name-project
```

## Step 2: Đẩy dự án lên github

Tạo <code style="color:green;font-weight:700">ssh key</code> mới với câu lệnh:

```sh
ssh-keygen -t ed25519 -C "hiepdeptrai0908@gmail.com"
```

:arrow_right: sau đó mở file có đường dẫn `/Users/hiepdeptrai0908/.ssh/***.pub` thêm vào ssh key trong settings github

Link github: `https://github.com/hiepdeptrai0908/react_shopee`

## Step 3: Cài đặt customize-cra (Tuỳ chỉnh Create-React-App)

:arrow_right: Để có thể ghi đè cấu hình của webpack

1. :wrench: Install:

<code style="color:green;font-weight:700">customize-cra</code> hoạt động dựa trên nền <code style="color:green;font-weight:700">react-app-rewired</code>

```sh
npm install customize-cra react-app-rewired --D
```

2. :white_check_mark: Tạo file <code style="color:green;font-weight:700">config-overrides.js</code> tại thư mục root ( Ngang cấp với file src )

```js
module.exports = function override(config, env) {
    //do stuff with the webpack config...
    return config
}
```

3. Thay thế <code style="color:green; font-weight: bold">react-scripts</code> thành <code style="color:green; font-weight: bold">react-app-rewired</code> trong file <code style="color:green; font-weight: bold">package.json</code>

```json
"scripts": {
    "start": "react-app-rewired start",
    "build": "react-app-rewired build",
    "test": "react-app-rewired test",
    "eject": "react-scripts eject"
}
```

4. Chạy thử `npm start` xem có hoạt động bình thường hay không

## Step 4: Cài đặt babel-plugin-module-resolver

:arrow_right: Cấu hình lại đường dẫn gọn gàng hơn

```js
// Mặc định:
import MyUtilFn from '../../../../utils/MyUtilFn'
// Mong muốn:
import MyUtilFn from 'utils/MyUtilFn'
```

1. :wrench: Install the plugin

```sh
npm install --save-dev babel-plugin-module-resolver
```

Hoặc

```sh
yarn add --dev babel-plugin-module-resolver
```

2. Tạo file <code style="color:green; font-weight: bold">.babelrc</code> tại thư mục root để cấu hình đường dẫn.

```json
{
    "plugins": [
        [
            "module-resolver",
            {
                "alias": {
                    "~": "./src"
                }
            }
        ]
    ]
}
```

3. Tạo file <code style="color:green; font-weight: bold">jsconfig.json</code> tại thư mục root để cấu hình ánh xạ đường dẫn.

```json
{
    "compilerOptions": {
        "baseUrl": ".",
        "paths": {
            "~/*": ["src/*"]
        }
    }
}
```

4. Nạp cấu hình <code style="color:green; font-weight: bold">babel</code> vào webpack ở file <code style="color:green; font-weight: bold">config-overrides.js</code>

```js
const { override, useBabelRc } = require('customize-cra')

module.exports = override(useBabelRc())
```

```js
// Kết quả
import Header from '~/components/Header'
```

## Step 5: Cài đặt và cấu hình Prettier tự động format code

1. Tạo file <code style="color:green; font-weight: bold">.prettierrc</code> tại thư mục root

```json
{
    "arrowParens": "always",
    "bracketSameLine": false,
    "bracketSpacing": true,
    "embeddedLanguageFormatting": "auto",
    "htmlWhitespaceSensitivity": "css",
    "insertPragma": false,
    "jsxSingleQuote": false,
    "printWidth": 120,
    "proseWrap": "preserve",
    "quoteProps": "as-needed",
    "requirePragma": false,
    "semi": false,
    "singleQuote": true,
    "tabWidth": 4,
    "trailingComma": "all",
    "useTabs": false,
    "vueIndentScriptAndStyle": false
}
```

Góp ý thêm là nếu bạn nào chưa làm được thì có thể là do chưa chỉnh lại default của typescript.

-   Chuột phải vào màn hình chọn `Format Document With...` -> `Configure Default Formatter` -> `Prettier` - `code formatter`

-   Nếu ctrl S mà code vẫn chưa tự format thì vào `File` -> `Preferences` -> `Settings`. Tìm kiếm từ khoá `format`, tick vào ô `Format a file on save...` của mục Editor: `Format on save`.

## Step 6: Style CSS

1. Trường hợp sử dụng Tailwind CSS :laughing:

```sh
npm install -D tailwindcss
npx tailwindcss init
```

```js
// tailwind.config.js
module.exports = {
    content: ['./src/**/*.{html,js}'],
    theme: {
        extend: {},
    },
    plugins: [],
}
```

Import tailwindcss vào file CSS cấp cao nhất

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

2. Trường hợp sử dụng sass module
    [x] sass
    [x] classnames

```sh
npm install -D sass classnames
```

-   Sau đó chạy lại <code style="color:green; font-weight: bold">npm start</code> để nạp lại plugin của sass

3. Reset CSS sử dụng thư viện <code style="color:green; font-weight: bold">normalize.css</code>

```sh
npm install --save normalize.css
```

Import <code style="color:green; font-weight: bold">normalize.css</code> vào trong file css root

```css
@import 'normalize.css';

:root {
}

* {
    box-sizing: border-box;
}

html {
    font-size: 62.5%;
}

body {
    font-family: Roboto, Sans-serif;
    font-size: 1.6rem;
    line-height: 1.5;
    text-rendering: optimizespeed;
}
```

## Step 7: Cấu hình Router/Layout cho dự án

1. Cài đặt <code style="color:green; font-weight: bold">react-router-dom</code>

```sh
npm install react-router-dom
```

2. Đưa cấu hình Routes ra ngoài
3. Xây dựng cơ chế tải Layout

## Step 8:

## Step 9:

## Step 10:
