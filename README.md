reverse-index
==========

A module or generating a reverse index from a collection of objects

## Installation

```bash
npm install reverse-index
```

## Usage

```javascript
builder = require('reverse-index');

//
// What properties deserve the most weight
//

WEIGHTED_PROPS = [ 'text', 'year' ];

//
// Using an array as the collection
//

collection = {
  "star_wars":  { "text": "a long time ago in a galaxy far, far away...", "year": "1977" },
  "spaceballs": { "text": "once upon a time warp... in a galaxy very, very, very, very, far away...", "year": "1987" }
}

builder.build({
  properties: WEIGHTED_PROPS,
  collection: collection
});

//=>

{
  '1977': { star_wars: 1 },
  '1987': { spaceballs: 1 },
  'long': { star_wars: 2 },
  'time': { star_wars: 2, spaceballs: 2 },
  'ago': { star_wars: 2 },
  'galaxy': { star_wars: 2, spaceballs: 2 },
  'far': { star_wars: 2, spaceballs: 2 },
  'away': { star_wars: 2, spaceballs: 2 },
  'long time': { star_wars: 2 },
  'time ago': { star_wars: 2 },
  'galaxy far': { star_wars: 2 },
  'far far': { star_wars: 2 },
  'far away': { star_wars: 2, spaceballs: 2 },
  'long time ago': { star_wars: 2 },
  'galaxy far far': { star_wars: 2 },
  'far far away': { star_wars: 2 },
  'upon': { spaceballs: 2 },
  'warp': { spaceballs: 2 },
  'time warp': { spaceballs: 2 }
}

//
// Using an object as the collection
//

collection = [
  { "name": "star_wars",  "text": "a long time ago in a galaxy far, far away...", "year": "1977" },
  { "name": "spaceballs", "text": "once upon a time warp... in a galaxy very, very, very, very, far away...", "year": 1987 }
]

builder.build({
  properties: WEIGHTED_PROPS,
  collection: collection
});

//=>

{
  '1977': { '0': 1 },
  '1987': { '1': 1 },
  'long': { '0': 2 },
  'time': { '0': 2, '1': 2 },
  'ago': { '0': 2 },
  'galaxy': { '0': 2, '1': 2 },
  'far': { '0': 2, '1': 2 },
  'away': { '0': 2, '1': 2 },
  'long time': { '0': 2 },
  'time ago': { '0': 2 },
  'galaxy far': { '0': 2 },
  'far far': { '0': 2 },
  'far away': { '0': 2, '1': 2 },
  'long time ago': { '0': 2 },
  'galaxy far far': { '0': 2 },
  'far far away': { '0': 2 },
  'upon': { '1': 2 },
  'warp': { '1': 2 },
  'time warp': { '1': 2 }
}
```

## Contributing

  * Fork the project.
  * Make your feature addition or bug fix.
  * Add tests for it. This is important so I don't break it in a future version unintentionally.
  * Commit, do not mess with version (if you want to have your own version, that is fine but bump version in a commit by itself I can ignore when I pull)
  * Send me a pull request. Bonus points for topic branches.
