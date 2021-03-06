![alt text](https://raw.githubusercontent.com/ossgroupp/react-dialog/HEAD/media/logo.png "Speech bubble")

# @osspim/react-dialog

React component to display accessible dialogs. This is a [general purpose component to build awesome and accessible dialogs in react](https://ossgroup.com/developers/react-components/react-dialog). Built initially for use in the [OSSPIM headless commerce service](https://ossgroup.com).

Uses [styled-components](https://npmjs.org/package/styled-components) and [a11y-dialog](https://www.npmjs.com/package/a11y-dialog). Leverages the [native dialog HTML element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dialog) when possible

This module uses **Promises** and does *not* provide a polyfill. To easily
provide Promise polyfills for your users, try [polyfills.io](https://polyfill.io/v2/docs/)

## Demo
[Demo](https://react-dialog.milliseconds.io)

![alt text](https://raw.githubusercontent.com/ossgroupp/react-dialog/HEAD/media/react-dialog.gif "React dialog in action")

## Usage

```
yarn add @osspim/react-dialog styled-components
```

### In your app root

```
import { Wrapper } from '@osspim/react-dialog';

export default () => (
  <main>
    <YourApp />
  </main>
  <Wrapper />
);
```

### Use it

```
import { showDialog, showAlert, showConfirm, closeCurrent } from '@osspim/react-dialog';

await showDialog('Hey dude');
await showDialog({
  body: <strong>Hey dude</strong>
});

await showAlert('Wow');
const confirmResult = await showConfirm('Are you sure?');

const confirmResult = await showConfirm({
  body: <div>JSX rules</div>,
  buttons: {
    ok: p => <button {...p}>Allrighty</button>,
    cancel: p => <button {...p}>Nope</button>
  }
});

// Closes any open dialog
closeCurrent();
```

## Wrapper props
| Prop Name    | Default | Type | Description                                |
| ------------ | ------- | ---- | ------------------------------------------ |
| cleanTheme   | false   | bool | Use the clean theme instead of the default |
| ButtonOk     | false   | jsx  | Set a custom default Ok button             |
| ButtonCancel | false   | jsx  | Set a custom default Cancel button         |
| ButtonClose  | false   | jsx  | Set a custom default Close button          |
| Heading      | false   | jsx  | Set a custom default Heading               |

## Dialog functions
All of the show dialog functions (showDialog, showAlert, showConfirm) returns a promise when called. The promise is resolved when the dialog is closed. The return value of the
promise changes depending on which type of dialog it is

The functions accepts a single string argument. They also support a single object as argument with these common properties:

```
{
  title<string|jsx>: <h1>Hi there</h1>
  body<string|jsx>: 'you',
  showCloseButton<bool>: false (default is true),
  disableBackdropClick<bool>: false
}
```

showConfirm does however accept a few more:
```
...
buttons: {
  ok: props => <button {...props}>{props.children}</button>,
  cancel: "Nope nope!"
}
```
showConfirm resolves its promise with either "ok" or "cancel"
# react-dialog
