---
layout: docs
title: Press Key
permalink: /documentation/test-api/actions/press-key.html
checked: true
---
# Press Key

Presses the specified keyboard keys.

```text
t.pressKey( keys )
```

Parameter | Type   | Description
--------- | ------ | --------------------------------------------------------
`keys`    | String | The sequence of keys and key combinations to be pressed.

The following table shows how to specify keys of different types, key sequences and combinations.

Key Type                   | Example
-------------------------- | ------
Alphanumeric keys          | `'a'`, `'A'`, `'1'`
Modifier keys              | `'shift'`, `'alt'`, `'ctrl'`, `'meta'`
Navigation and action keys | `'backspace'`, `'tab'`, `'enter'`, `'capslock'`, `'esc'`, `'space'`, `'pageup'`, `'pagedown'`, `'end'`, `'home'`, `'left'`, `'right'`, `'down'`, `'ins'`, `'delete'`
Key combinations           | `'shift+a'`, `'ctrl+d'`
Sequential key presses     | Any of the above in a space-separated string, e.g. `'a ctrl+b'`

In addition to key presses handled by webpage elements, the `t.pressKey` action also allows you to execute certain key presses processed by the browser.

* `'ctrl+a'`, `'backspace'`, `'delete'`, `'left'`, `'right'`, `'up'`, `'down'`, `'home'`, `'end'`, `'enter'`, `'tab'`, `'shift+tab'`, `'shift+left'`, `'shift+right'`, `'shift+up'`, `'shift+down'`, `'shift+home'`, `'shift+end'`

With the exception of the keys and combinations listed above, the `t.pressKey` action will not invoke integrated browser keystrokes.

For elements with the `contentEditable` attribute, the following key presses are supported.

* `'ctrl+a'`,
* `'backspace'`, `'delete'`, `'left'` and `'right'` (only if text within the element is selected).

The following example shows how to use the `t.pressKey` action.

```js
import { expect } from 'chai';
import { Selector } from 'testcafe';

const nameInput = Selector('#developer-name');

fixture `My fixture`
    .page `http://www.example.com/`;

test('Key Presses', async t => {
    await t
        .typeText(nameInput, 'Peter Parker')
        .pressKey('home right . delete delete delete delete');

    expect(await nameInput.value).to.equal('P. Parker');
});
```
