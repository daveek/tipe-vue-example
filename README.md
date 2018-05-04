# Getting Started with Tipe using Vue

## Configuration for vue/webpack/tipe-loader
Tipe works seamlessly with Vue

[Webpack](https://webpack.js.org)

[tipe-loader](https://github.com/tipeio/tipe-loader)

## Installation

```bash
  npm install -dev webpack tipe-loader
```
// Or
```bash
  yarn add --dev webpack tipe-loader
```
## Setup
Find your API Key and Org Secret key on Tipe Dashboard under API Keys.

![API Keys UI](https://cdn.tipe.io/tipe/docs/API-keys-info.png)

## Configuration
Setup your `webpack.config.js` file.

Replace `YOUR_API_KEY_HERE` and `YOUR_ORG_KEY_HERE` with the keys you found on the Tipe Dashboard.

```js
const webpack = require('webpack');
const path = require('path');

module.exports = {
  entry: './src/main.js',
  output: {
    path: path.resolve(__dirname, './dist'),
    publicPath: '/dist/',
    filename: 'build.js'
  },
  module: {
    rules: [
      // ... babel-loader
      },
      {
        test: /\.tipe$/,
        use: [
          {
            loader: 'tipe-loader',
            options: {
              apiKey: 'YOUR_API_KEY_HERE',
              orgKey: 'YOUR_ORG_KEY_HERE'
            }
          }
        ]
      }
    ]
  }
};
```
NOTE:

`tipe-loader` must be below your `babel-loader` in your `webpack.config` file.

## Package.json
In your package.json add a `build` command like so:
```json
{
  "scripts": {
    "build": "webpack"
  },
}
```

## Tipe File
Create your `.tipe` file and follow the GraphQL schema.
Find your Document ID:

You can find the Document ID in the API tab when viewing your Document and press `[Run GraphQL]`

* replace `YourDoc` with any alias you like
* replace `YOUR_DOCUMENT_ID` with the id of your document
* replace `YourDocumentTemplate` with the Name of your Document's Template

If you need help querying the right data, check the `Example Code` found after clicking `[Run GraphQL]`.

```graphQL
query Tipe {
  YourDoc: YourDocumentTemplate(id: "YOUR_DOCUMENT_ID") {
    title
    subtitle
    section1
    section2
    section3
    _meta {
      id
      name
      updatedAt
      createdAt
      published
    }
  }
}
```
## Adding Tipe to your `.vue` file.

Your data is ready syncronously at run time. Since our data is fetched during build-time we have it immediately and can include our `Landing` default data when our component is created.

Add your `.tipe` file to your `.vue` file like so:

```html
  </div>
</template>

<script>
import { Landing } from './example.tipe';

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      landing: Landing
    }
  }
}
</script>

<style>
```

Run your current build like so:

```bash
  npm run build
```
```bash
  yarn build
```
