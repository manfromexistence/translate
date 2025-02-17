# Translate
free translate

## Features

- Auto language detection
- Spelling correction
- Language correction
- Fast and reliable – it uses the same servers that [translate.google.com](https://translate.google.com) uses

## Install
```
npm install --save manfromexistence-translate
```

## Usage

Perfect support object:

``` js
const translate = require('manfromexistence-translate')
const tranObj = {
  a: 1,
  b: '1',
  c: "How are you?\nI'm nice.",
  d: [true, 'true', 'hi', { a: 'hello', b: ['world']}],
}

translate(tranObj, {to: 'zh-cn', except:['a']}).then(res => {
    console.log(res)
}).catch(err => {
    console.error(err)
})

// => { a: 1, b: '1', c: "你好吗？\n我很好。", d: [true, 'true', '嗨', { a: 'hello', b: ['世界']}] }
```

From automatic language detection to English:

``` js
const translate = require('manfromexistence-translate')

translate('I speak Chinese', {to: 'zh-cn'}).then(res => {
    console.log(res)
}).catch(err => {
    console.error(err)
})
```

From English to Dutch with a typo:

``` js
translate('I speak Chinese!', {from: 'en', to: 'zh-cn'}).then(res => {
    console.log(res)
}).catch(err => {
    console.error(err)
})
```


translate for array or object:
``` js
translate({a: 'I speak Chinese!', b: ['hello', 'world']}, {from: 'en', to: 'zh-cn'}).then(res => {
    console.log(res)
}).catch(err => {
    console.error(err)
})
```

## API

### translate(text, options)

#### text
Type: `string`, `object`, `array`
The text to be translated

#### options
Type: `object`

##### from
Type: `string` Default: `auto`
The `text` language. Must be `auto` or one of the codes/names (not case sensitive) contained in [languages.js](https://github.com/manfromexistence/translate/blob/master/languages.js)

##### to
Type: `string` Default: `en`
The language in which the text should be translated. Must be one of the codes/names (not case sensitive) contained in [languages.js](https://github.com/manfromexistence/translate/blob/master/languages.js).

##### except
Type: `array` Default:`[]`
Attributes in excluded objects do not participate in translation

### Returns an `object`:

- `text` *(string, object, array)* – The translated text.

``` js
translate(['I speak Chinese\nHello world', 'hello'], {from: 'en', to: 'nl'}).then(res => {
    console.log(res);
    //=> ["我说中文\n你好世界","你好"]
}).catch(err => {
    console.error(err);
});
```

## License

MIT © [manfromexistence](ajju40959@gmail.com)
