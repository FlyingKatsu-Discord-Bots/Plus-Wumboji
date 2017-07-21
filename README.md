# Plus-Wumboji

An add-on for [Discord-Bot-Module](https://github.com/FlyingKatsu-Discord-Bots/Discord-Bot-Module). Sends enlarged emoji to your server.

Supports custom emoji as well as emoji identifiers from [EmojiOne(#4a166f9)](https://github.com/emojione/emojione/commit/4a166f9334809b5044ecf493f7decf47d50e0a8a) with images from [Twemoji 2.3](http://twemoji.maxcdn.com/2/test/preview.html).

## Usage

Use `node custom/emoji/extract-shortname.js filename.json` to generate a `filename.json` containing an object whose keys are unicode emoji, each with a shortname (such as `:grinning:` or `:rofl:`) and a URL of the corresponding EmojiOne or Twemoji PNG files.

To make the keys be shortnames instead of emoji symbols, use: 

> `node custom/emoji/extract-shortname.js filename-short.json true`

Most keys should use the correct unicode code points, but not all are guaranteed to match Discord at this time.  For example, `:family_mwgb:` correctly includes zero-width-joiners that combine all four people 👨👩👧👦 into a single emoji 👨‍👩‍👧‍👦, but `:man_zombie:` does not yet have a corresponding Discord emoji.

This file converts a code point like `0x1F4A9` into the actual Unicode emoji 💩, and also converts `:emoji_skin_tone5:` or `:emoji_dark_skin_tone:` into a Discord-readable `:emoji::skin-tone-5:`

```json
{
  "💩": {
    "name": "pile of poo",
    "shortname": ":poo:",
    "identifier": "💩",
    "url": {
      "twemoji": "https://twemoji.maxcdn.com/2/72x72/1f4a9.png",
      "emojione": "https://cdn.jsdelivr.net/emojione/assets/3.1/png/32/1f4a9.png"
    }
  },
  "👮": {
    "name": "police officer",
    "shortname": ":cop:",
    "identifier": "👮",
    "url": {
      "twemoji": "https://twemoji.maxcdn.com/2/72x72/1f46e.png",
      "emojione": "https://cdn.jsdelivr.net/emojione/assets/3.1/png/32/1f46e.png"
    }
  },
  "👮🏿": {
    "name": "police officer: dark skin tone",
    "shortname": ":cop::skin-tone-5:",
    "identifier": "👮🏿",
    "url": {
      "twemoji": "https://twemoji.maxcdn.com/2/72x72/1f46e-1f3ff.png",
      "emojione": "https://cdn.jsdelivr.net/emojione/assets/3.1/png/32/1f46e-1f3ff.png"
    }
  }
}
```


## External Attribution

In order to identify and auto-enlarge non-custom emoji in Discord, data was taken from the following projects:

### EmojiOne

Copyright 2017 EmojiOne 
- Emoji icons provided free by EmojiOne via jsDelivr
- custom/emoji/emoji_strategy.json ([EmojiOne commit 4a166f9](https://github.com/emojione/emojione/commit/4a166f9334809b5044ecf493f7decf47d50e0a8a))
- https://github.com/emojione/emojione

### Twemoji

Copyright 2017 Twitter, Inc et al
- Twemoji icons provided free by Twitter via MaxCDN
- https://github.com/twitter/twemoji
  
## License
Copyright 2017 FlyingKatsu and other contributors

Code licensed under the MIT License: http://opensource.org/licenses/MIT
