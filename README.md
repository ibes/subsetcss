# subsetcss

Linting your CSS to limit yourself to a defined subset of values.

CSS can get unweildy sometimes, as new features are added and new people join the team. It's hard to be consistent,
and that's why utility/functional CSS libraries like Tailwind are growing in popularity. SubsetCSS helps aleviate this problem by enforcing your CSS to a predefined amount of values, keeping everyone on the same page as a project evolves.

Note: in development

![Example Output](./example.png "Example")

## Install

```sh
yarn add -D subsetcss stylelint
```

## Setup

Add a `.stylelintrc` file with the following config:

```json
{
  "plugins": [
    "subsetcss"
  ],
  "rules": {
    "subsetcss/config": "./.subsetcss.js"
  }
}
```

Create a `.subsetcss.js` file with content like:

```js
module.exports = {
  'subsets': {
    'font-size': [
      '.75rem',     // 12px
      '.875rem',    // 14px
      '1rem',       // 16px
      '1.125rem',   // 18px
      '1.25rem',    // 20px
      '21.5rem',    // 24px
      '31.875rem',  // 30px
      '42.25rem',   // 36px
      '53rem',      // 48px
    ],
    'border-width': [
      '0',
      '1px',
      '2px',
      '3px'
    ],
    'border-color': [
      'transparent',
      '#22292f',
      '#3d4852',
      '#606f7b',
      '#8795a1',
      '#b8c2cc'
    ],
    'border-style': ['solid'],
    '@media': {
      'params': {
        'max-width': ['400px', '768px'],
      },
      'subsets': {
         'font-size': [
          '1rem',       // 16px
          '1.125rem',   // 18px
          '1.25rem',    // 20px
          '21.5rem',    // 24px
          '31.875rem'   // 30px
        ]
      }
    }
  }
};
```

## Run

You can run with `yarn stylelint "src/styles/*.css"`. Feel free to add to your npm scripts
or setup with any intermediate tools.


## Contributing

See the [Contributing](./CONTRIBUTING.md) guide.
