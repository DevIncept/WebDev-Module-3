# Component styling in ReactJS
The reason we style your React application is no different from that which we have in mind when styling other websites or web applications we have been working on. Styling in React applications describes how React components or elements are displayed on screen or any other media.

![image](https://miro.medium.com/max/3200/1*8slP0diGduUQy3qk9N7HsQ.png)

## RADIUM:

#### Features

-   Conceptually simple extension of normal inline styles
-   Browser state styles to support  `:hover`,  `:focus`, and  `:active`
-   Media queries
-   Automatic vendor prefixing
-   Keyframes animation helper
-   ES6 class and  `createClass`  support

![image](https://sahilthakur7blog.files.wordpress.com/2018/01/og-image.jpg?w=640)


## CSS Modules

CSS Modules are awesome. If you are not familiar with CSS Modules, it is a concept of using a module bundler such as webpack to load CSS scoped to a particular document. CSS module loader will generate a unique name for each CSS class at the time of loading the CSS document Interoperable CSS to be precise). To see CSS Modules in practice, webpack-demo.

![image](https://blog.pusher.com/wp-content/uploads/2018/02/css-modules-react-header.png)

In large projects coming up with unique class names can be hard. CSS Modules enable you to use the same class wherever you want. Since the compiler handles the CSS it changes all the class names with different unique names in order make them locally available for that component.

## LESS/SASS

Generally, we recommend that you don’t reuse the same CSS classes across different components. For example, instead of using a .Button CSS class in **AcceptButton** and **RejectButton** components, we recommend creating a **Button** component with its own .Button styles, that both **AcceptButton** and **RejectButton** can render (but not inherit).

However, there is no such solution for LESS, at the moment. So In this article we will focus on creating a solution for LESS. Actually, it’s better to call this a work-around instead, as it has some negative aspects, like having to import your LESS file (say “style.less”) like “style.css”.

To solve this problem, we will set up a LESS-CSS compiler to compile a LESS each time we make changes to the stylesheet and put the compiled CSS file into the exact same directory so that the user can use the compiled CSS file instead by just changing the extension from LESS to CSS while importing the stylesheet.

![image](https://miro.medium.com/max/600/1*NSAaImEJtqC00Gw4hXBpHA.png)

<br>
<br>
<br>

# React Component Styling codes

## RADIUM
#### Install:
```
yarn add radium
# or 
npm install --save radium
```

#### Usage:

```
<Button kind="primary">Radium Button</Button>
import Radium from 'radium';
import React from 'react';
import color from 'color';

class Button extends React.Component {
  static propTypes = {
    kind: PropTypes.oneOf(['primary', 'warning']).isRequired
  };

  render() {
    // Radium extends the style attribute to accept an array. It will merge
    // the styles in order. We use this feature here to apply the primary
    // or warning styles depending on the value of the `kind` prop. Since its
    // all just JavaScript, you can use whatever logic you want to decide which
    // styles are applied (props, state, context, etc).
    return (
      <button style={[styles.base, styles[this.props.kind]]}>
        {this.props.children}
      </button>
    );
  }
}

Button = Radium(Button);

// You can create your style objects dynamically or share them for
// every instance of the component.
var styles = {
  base: {
    color: '#fff',
```
    // Adding interactive state couldn't be easier! Add a special key to your
    // style object (:hover, :focus, :active, or @media) with the additional rules.
    ':hover': {
      background: color('#0074d9')
        .lighten(0.2)
        .hexString()
    }
  ```},

  primary: {
    background: '#0074D9'
  },

  warning: {
    background: '#FF4136'
  }
};
```

## CSS MODULES
```
// From 
import "./App.css"; 
// To 
import styles from "./App.module.css";
```
#### Usage:
```
import React from "react";

import styles from "./App.module.css";

function App() {
  return (
    <div className={styles.customClass}>
      Hello React!
    </div>
  );
}

export default App;
```

## SASS/LESS

```
import './styles.less';
```

#### Usage:

```
var HtmlWebpackPlugin = require('html-webpack-plugin');
const path = require('path');

module.exports = {
    mode: 'development',
    module: {
        rules: [
            {
                test: /\.jsx?$/,
                loader: 'babel-loader'
            },
            {
                test: /\.less$/,
                use: [
                    { loader: 'style-loader' },
                    { loader: 'css-loader' },
                    { loader: 'less-loader' }
                ]
            }
        ]
    },
    resolve: {
        extensions: ['.js', '.jsx'],
        alias: {
            '@': path.resolve(__dirname, 'src/'),
        }
    },
    plugins: [new HtmlWebpackPlugin({
        template: './src/index.html'
    })],
    devServer: {
        historyApiFallback: true
    },
    externals: {
        // global app config object
        config: JSON.stringify({
            apiUrl: 'http://localhost:4000'
        })
    }
}
```

```
import React from 'react';
import { render } from 'react-dom';

import { App } from './App';

import './styles.less';

render(
    <App />,
    document.getElementById('app')
);
```
