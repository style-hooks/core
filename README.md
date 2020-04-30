[![Bundlephobia](https://img.shields.io/bundlephobia/minzip/@style-hooks/core?style=for-the-badge)](https://bundlephobia.com/result?p=@style-hooks/core)
[![Code coverage](https://img.shields.io/codecov/c/gh/style-hooks/core?style=for-the-badge)](https://codecov.io/gh/style-hooks/core)
[![Build status](https://img.shields.io/travis/style-hooks/core?style=for-the-badge)](https://travis-ci.org/style-hooks/core)
[![License](https://img.shields.io/github/license/style-hooks/core?style=for-the-badge)](https://jaredlunde.mit-license.org/)

---

<p align=center>
  <br/>
  <img src='https://raw.githubusercontent.com/style-hooks/docs/master/assets/logo%402x.png' width='320'/>
</p>

<h2 align=center>A suite of utilities for adding responsive style props to your React components
using <a href='http://emotion.sh'>Emotion</a></h2>

<p align=center>
  Use <code>@style-hooks</code> to seamlessly add themes, CSS-in-JS styles,
  variants, breakpoint props, a <code>css</code> prop, and an <code>as</code> prop 
  to any React function component.
</p>
<p align=center>
  For a <code>styled-components</code>-like interface, check out <a href='https://github.com/style-hooks/styled'>@style-hooks/styled</a>. 
</p>

```jsx harmony
/** @jsx jsx */
import React from 'react'
import {css, jsx} from '@emotion/core'
import {createStyleHook, createElement, ThemeProvider} from '@style-hooks/core'
// Your very own style hook
const useBox = createStyleHook('box', {
  w: (value, theme, props) => css`
    width: ${value + theme.box.sizeUnit};
  `,
})
// Accompanying component w/ style props using
// your style hook
const Box = props => {
  props = useBox(props)
  // createElement here provides this component
  // an 'as' prop, you could also use emotion's
  // jsx()
  return createElement('div', props)
}
// The theme for your app
const theme = {box: {sizeUnit: 'px'}}
// Usage w/ theme
const App = () => (
  <ThemeProvider theme={theme}>
    {/* 
      Shows off the 'as' prop, 
      followed by 'breakpoint props',
      followed by the 'css' prop
    */}
    <Box
      as="main"
      w="200:phone 300:tablet"
      css={theme => css`
        @media ${theme.breakpoints.phone} {
          height: 200px;
          background-color: hotpink;
        }

        @media ${theme.breakpoints.tablet} {
          height: 300px;
          background-color: skyblue;
        }
      `}
    >
      Hello world from this {'<main>'}
    </Box>
  </ThemeProvider>
)
```

## Installation

#### `npm i @style-hooks/core @emotion/core`

#### `yarn add @style-hooks/core @emotion/core`

## Playground

Check out
[`@style-hooks` on CodeSandbox](https://codesandbox.io/s/style-hooks-examples-t20yi)

## [API Documentation](https://style-hooks.jaredlunde.com)

Complete documentation can be found
[here](https://style-hooks.jaredlunde.com)

- [**`Introduction`**](https://style-hooks.jaredlunde.com) Learn more
  about the basics of `style-hooks`
- [**`useStyles()`**](https://style-hooks.jaredlunde.com/api/useStyles)
  A hook for creating responsive CSS styles with responsive breakpoints
  from input props
- [**`createElement()`**](https://style-hooks.jaredlunde.com/api/createElement)
  A wrapper around `React.createElement` for adding an `as` prop and `css` prop to your
  component
- [**`<ThemeProvider>`**](https://style-hooks.jaredlunde.com/api/ThemeProvider)
  The theme context provider
- [**`<ThemeConsumer>`**](https://style-hooks.jaredlunde.com/api/ThemeConsumer)
  The theme context consumer
- [**`useTheme()`**](https://style-hooks.jaredlunde.com/api/useTheme) A hook
  for consuming the theme
- [**`<StylesConsumer>`**](https://style-hooks.jaredlunde.com/api/StylesConsumer)
  A context consumer for reading, replacing, and merging themes
- [**`useStylesContext()`**](https://style-hooks.jaredlunde.com/api/useStylesContext)
  A hook for reading, replacing, and merging themes
