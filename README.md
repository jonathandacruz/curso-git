# 


# curso-git-udemy

---
 
## Avisos paroquiais!

A trilha de aprendizado a seguir está disponível para o desenvolvimento das aulas na plataforma udemy para o curso de como controlar a versão do seu projeto utilizando Git e Github.

Fique por dentro 

[Curso com desconto!](https://www.udemy.com/course/git-controle-de-versao/?referralCode=FD1BFEB99BF453504B3F)

[Canal do Discord - Vamos papear!](https://discord.gg/zd5U7s4Y)

## Trilha

- [Instalação](#Instalação)
  - [Instalando no Mac](#git-no-mac)
  - [With Bootstrap](#with-bootstrap)
  - [With Material Design](#with-material-design)
  - [As Single Select](#as-single-select)
- [Install](#install)
  - [As NPM package](#as-npm-package)
  - [Using a CDN](#using-a-cdn)
  - [Peer Dependencies](#peer-dependencies)
- [Usage](#usage)
- [Props](#props)
  - [className](#classname)
  - [clearSearchOnChange](#clearsearchonchange)
  - [onChange](#onchange)
  - [onNodeToggle](#onnodetoggle)
  - [onAction](#onaction)
  - [onFocus](#onfocus)
  - [onBlur](#onblur)
  - [data](#data)
  - [texts](#texts)
  - [keepTreeOnSearch](#keeptreeonsearch)
  - [keepChildrenOnSearch](#keepchildrenonsearch)
  - [keepOpenOnSelect](#keepopenonselect)
  - [mode](#mode)
    - [multiSelect](#multiselect)
    - [hierarchical](#hierarchical)
    - [simpleSelect](#simpleselect)
    - [radioSelect](#radioselect)
  - [showPartiallySelected](#showpartiallyselected)
  - [showDropdown](#showdropdown)
    - [initial](#initial)
    - [always](#always)
  - [form states (disabled|readOnly)](#form-states-disabled-readonly)
  - [id](#id)
  - [searchPredicate](#searchpredicate)
  - [inlineSearchInput](#inlinesearchinput)
  - [tabIndex](#tabIndex)
  - [disablePoppingOnBackspace](#disablePoppingOnBackspace)
- [Styling and Customization](#styling-and-customization)
  - [Using default styles](#default-styles)
  - [Customizing with Bootstrap, Material Design styles](#customizing-styles)
- [Keyboard navigation](#keyboard-navigation)
- [Performance](#performance)
  - [Search optimizations](#search-optimizations)
  - [Search debouncing](#search-debouncing)
  - [Virtualized rendering](#virtualized-rendering)
  - [Reducing costly DOM manipulations](#reducing-costly-dom-manipulations)
- [FAQ](#faq)
- [Doing more with HOCs](/docs/HOC.md)
- [Development](#development)
- [License](#license)
- [Contributors](#contributors)

 

Online demo: https://dowjones.github.io/react-dropdown-tree-select/#/story/with-bootstrap-styles

##### With Material Design

Online demo: https://dowjones.github.io/react-dropdown-tree-select/#/story/with-material-design-styles

##### As Single Select

Online demo: https://dowjones.github.io/react-dropdown-tree-select/#/story/simple-select

## Instalação

### As NPM package

```js
npm i react-dropdown-tree-select

// or if using yarn
yarn add react-dropdown-tree-select
```

### Using a CDN

You can import the standalone UMD build from a CDN such as:

```html
<script src="https://unpkg.com/react-dropdown-tree-select/dist/react-dropdown-tree-select.js"></script>
<link href="https://unpkg.com/react-dropdown-tree-select/dist/styles.css" rel="stylesheet" />
```

**Note:** Above example will always fetch the latest version. To fetch a specific version, use `https://unpkg.com/react-dropdown-tree-select@<version>/dist/...`
Visit [unpkg.com](https://unpkg.com/#/) to see other options.

### Peer Dependencies

In order to avoid version conflicts in your project, you must specify and install [react](https://www.npmjs.com/package/react), [react-dom](https://www.npmjs.com/package/react-dom) as [peer dependencies](https://nodejs.org/en/blog/npm/peer-dependencies/). Note that NPM(version 4-6) doesn't install peer dependencies automatically. Instead it will show you a warning message with instructions on how to install them. If using Npm 7.X.X version, peer dependencies will be installed automatically.

If you're using the UMD builds, you'd also need to install the peer dependencies in your application:

```html
<script src="https://unpkg.com/react/dist/react.js"></script>
<script src="https://unpkg.com/react-dom/dist/react-dom.js"></script>
```

## Usage

```jsx
import React from 'react'
import ReactDOM from 'react-dom'

import DropdownTreeSelect from 'react-dropdown-tree-select'
import 'react-dropdown-tree-select/dist/styles.css'

const data = {
  label: 'search me',
  value: 'searchme',
  children: [
    {
      label: 'search me too',
      value: 'searchmetoo',
      children: [
        {
          label: 'No one can get me',
          value: 'anonymous',
        },
      ],
    },
  ],
}

const onChange = (currentNode, selectedNodes) => {
  console.log('onChange::', currentNode, selectedNodes)
}
const onAction = (node, action) => {
  console.log('onAction::', action, node)
}
const onNodeToggle = currentNode => {
  console.log('onNodeToggle::', currentNode)
}

ReactDOM.render(
  <DropdownTreeSelect data={data} onChange={onChange} onAction={onAction} onNodeToggle={onNodeToggle} />,
  document.body
) // in real world, you'd want to render to an element, instead of body.
```

## Props

### className

Type: `string`

Additional classname for container. The container renders with a default classname of `react-dropdown-tree-select`.

### clearSearchOnChange

Type: `bool`

Clear the input search if a node has been selected/unselected.

### onChange

Type: `function`

Fires when a node change event occurs. Currently the following actions trigger a node change:

- Checkbox click which checks/unchecks the item
- Closing of pill (which unchecks the corresponding checkbox item)

Calls the handler with the current node object and all selected nodes (if any). Example:

```jsx
function onChange(currentNode, selectedNodes) {
  // currentNode: { label, value, children, expanded, checked, className, ...extraProps }
  // selectedNodes: [{ label, value, children, expanded, checked, className, ...extraProps }]
}

return <DropdownTreeSelect data={data} onChange={onChange} />
```

### onNodeToggle

Type: `function`

Fires when a node is expanded or collapsed.

Calls the handler with the current node object. Example:

```jsx
function onNodeToggle(currentNode) {
  // currentNode: { label, value, children, expanded, checked, className, ...extraProps }
}

return <DropdownTreeSelect data={data} onNodeToggle={onNodeToggle} />
```

### onAction

Type: `function`

Fires when a action is triggered. Example:

```jsx
function onAction(node, action) {
  console.log('onAction::', action, node)
}

return <DropdownTreeSelect data={data} onAction={onAction} />
```

### onFocus

Type: `function`

Fires when input box receives focus or the dropdown arrow is clicked. This is helpful for setting `dirty` or `touched` flags with forms.

### onBlur

Type: `function`

Fires when input box loses focus or the dropdown arrow is clicked again (and the dropdown collapses). This is helpful for setting `dirty` or `touched` flags with forms.

### data

Type: `Object` or `Array`

Data for rendering the tree select items. The object requires the following structure:

```js
{
  label,          // required: Checkbox label
  value,          // required: Checkbox value
  children,       // optional: Array of child objects
  checked,        // optional: Initial state of checkbox. if true, checkbox is selected and corresponding pill is rendered.
  disabled,       // optional: Selectable state of checkbox. if true, the checkbox is disabled and the node is not selectable.
  expanded,       // optional: If true, the node is expanded (children of children nodes are not expanded by default unless children nodes also have expanded: true).
  className,      // optional: Additional css class for the node. This is helpful to style the nodes your way
  tagClassName,   // optional: Css class for the corresponding tag. Use this to add custom style the pill corresponding to the node.
  actions,        // optional: An array of extra action on the node (such as displaying an info icon or any custom icons/elements)
  dataset,        // optional: Allows data-* attributes to be set on the node and tag elements
  isDefaultValue, // optional: Indicate if a node is a default value. When true, the dropdown will automatically select the node(s) when there is no other selected node. Can be used on more than one node.
  tagLabel,       // optional: tag label in case you need it to differ from the checkbox label
  ...             // optional: Any extra properties that you'd like to receive during `onChange` event
}
```

The `action` object requires the following structure:

```js
{
  className, // required: CSS class for the node. e.g. `fa fa-info`
  title,     // optional: HTML tooltip text
  text,      // optional: Any text to be displayed. This is helpful to pass ligatures if you're using ligature fonts
  ...        // optional: Any extra properties that you'd like to receive during `onChange` event
}
```

An array renders a tree with multiple root level items whereas an object renders a tree with a single root element (e.g. a `Select All` root node).

### texts

Texts to override various labels, place holders & messages used in the component. You can also use this to provide translated messages.

The `texts` object requires the following structure:

```js
{
  placeholder,              // optional: The text to display as placeholder on the search box. Defaults to `Choose...`
  inlineSearchPlaceholder,  // optional: The text to display as placeholder on the inline search box. Only applicable with the `inlineSearchInput` setting. Defaults to `Search...`
  noMatches,                // optional: The text to display when the search does not find results in the content list. Defaults to `No matches found`
  label,                    // optional: Adds `aria-labelledby` to search input when input starts with `#`, adds `aria-label` to search input when label has value (not containing '#')
  labelRemove,              // optional: The text to display for `aria-label` on tag delete buttons which is combined with `aria-labelledby` pointing to the node label. Defaults to `Remove`
}
```

### keepTreeOnSearch

Type: `bool`

Displays search results as a tree instead of flattened results

### keepChildrenOnSearch

Type: `bool`

Displays children of found nodes to allow searching for a parent node on then selecting any child node of the found node. Defaults to `false`

_NOTE_ this works only in combination with `keepTreeOnSearch`

### keepOpenOnSelect

Type: `bool` (default: 'false')

Keeps single selects open after selection. Defaults to `false`

_NOTE_ this works only in combination with `simpleSelect` or `radioSelect`

### mode

Type: `string` (default: `multiSelect`)

Defines how the dropdown is rendered / behaves

#### multiSelect

A multi selectable dropdown which supports tree data with parent-child relationships. This is the default mode.

#### hierarchical

A multi selectable dropdown which supports tree data **without** parent-child relationships. In this mode, selecting a node has no ripple effects on its descendants or ancestors. Subsequently, `showPartiallySelected` becomes a moot flag and has no effect as well.

⚠️ Note that `hierarchical=true` negates/overrides `showPartiallySelected`.

#### simpleSelect

Turns the dropdown into a simple, single select dropdown. If you pass tree data, only immediate children are picked, grandchildren nodes are ignored.

⚠️ If multiple nodes in data are selected - by setting either `checked` or `isDefaultValue`, only the first visited node stays selected.

#### radioSelect

Turns the dropdown into radio select dropdown.

Like `simpleSelect`, you can only select one value; but keeps the tree/children structure.

⚠️ If multiple nodes in data are selected - by setting either `checked` or `isDefaultValue`, only the first visited node stays selected.

### showPartiallySelected

Type: `bool` (default: `false`)

If set to true, shows checkboxes in a partial state when one, but not all of their children are selected. Allows styling of partially selected nodes as well, by using [:indeterminate](https://developer.mozilla.org/en-US/docs/Web/CSS/:indeterminate) pseudo class. Simply add desired styles to `.node.partial .checkbox-item:indeterminate { ... }` in your CSS.

### showDropdown

Type: `string`

Let's you choose the rendered state of the dropdown.

#### initial

`showDropdown: initial` shows the dropdown when rendered. This can be used to render the component with the dropdown open as its initial state.

#### always

`showDropdown: always` shows the dropdown when rendered, and keeps it visible at all times. Toggling dropdown is disabled.

### form states (disabled|readOnly)

Type: `bool` (default: `false`)

`disabled=true` disables the dropdown completely. This is useful during form submit events.
`readOnly=true` makes the dropdown read only, which means that the user can still interact with it but cannot change any of its values. This can be useful for display only forms.

### id

Type: `string`

Specific id for container. The container renders with a default id of `rdtsN` where N is the count of the current component rendered.

Use to ensure a own unique id when a simple counter is not sufficient, e.g in a partial server render (SSR)

### searchPredicate

Type: `function`

Optional search predicate to override the default case insensitive contains match on node labels. Example:

```jsx
function searchPredicate(node, searchTerm) {
  return node.customData && node.customData.toLower().indexOf(searchTerm) >= 0
}

return <DropdownTreeSelect data={data} searchPredicate={searchPredicate} />
```

### inlineSearchInput

Type: `bool` (default: `false`)

`inlineSearchInput=true` makes the search input renders **inside** the dropdown-content. This can be useful when your UX looks something like [this comment](https://github.com/dowjones/react-dropdown-tree-select/issues/308#issue-526467109).

### tabIndex

Type: `number` (default: `0`)

`tabIndex=0` attribute indicates that its element can be focused, and where it participates in sequential keyboard navigation.

### disablePoppingOnBackspace

Type: `bool` (default: `false`)

`disablePoppingOnBackspace=true` attribute indicates that when a user triggers a 'backspace' keyDown in the empty search bar, the tree will not deselect nodes.

## Styling and Customization

### Default styles

The component brings minimal styles for bare-bones functional rendering. It is kept purposefully minimal so that user can style/customize it completely to suit their needs.

#### Using WebPack

If you're using a bundler like WebPack, make sure you configure WebPack to import the default styles. To do so, simply add this rule to your WebPack config:

```js
// allow WebPack to import/bundle styles from node_modules for this component
module: {
  rules: [
    {
      test: /\.css$/,
      use: ExtractTextPlugin.extract({
        fallback: 'style-loader',
        use: [
          {
            loader: 'css-loader',
          },
        ],
      }),
      include: /node_modules[/\\]react-dropdown-tree-select/,
    },
  ]
}
```
 
