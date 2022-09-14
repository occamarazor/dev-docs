# MERN dev setup

## Project init
```
yarn init
```

## ESLint install
```
npm init @eslint/config
```

## Node configs install
```
yarn add -D eslint-config-node eslint-plugin-node eslint-plugin-jsdoc
```

## Jest configs install
```
yarn add -D eslint-plugin-jest
```

## Airbnb configs install
```
npx install-peerdeps --dev eslint-config-airbnb
```

## Prettier configs install
```
yarn add -D --exact prettier
yarn add -D eslint-config-prettier eslint-plugin-prettier
```

## Git hooks install
```
yarn add -D lint-staged
npx husky-init && yarn
npx husky add .husky/pre-commit "yarn lint-staged"
```

## Package.json update
```
{
  "scripts": {
    "prepare": "husky install",
    "lint": "eslint . --fix",
    "format": "prettier . --write"
  },
  "lint-staged": {
    "*.js": "eslint --fix --max-warnings=0",
    "*.(json|css|md)": [
      "prettier --write --ignore-unknown"
    ]
  }
}
```

## Prettier FE ignore
```
node_modules
coverage
public
```

## Prettier BE ignore
```
node_modules
coverage
```

## Prettier config
```
{
"printWidth": 100,
"tabWidth": 2,
"useTabs": false,
"semi": true,
"singleQuote": true,
"bracketSpacing": true,
"trailingComma": "all",
"jsxSingleQuote": true
}
```

## ESLint FE ignore
```
node_modules
coverage
public
```

## ESLint FE config
```
{
  "env": {
    "es2021": true,
    "browser": true,
    "jest/globals": true
  },
  "extends": ["plugin:react/recommended", "airbnb", "airbnb/hooks", "plugin:prettier/recommended"],
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "plugins": ["react", "jest"],
  "rules": {
    "react/react-in-jsx-scope": "off",
    "react/jsx-filename-extension": "off",
    "react/function-component-definition": "off"
  }
}
```

## ESLint BE ignore
```
node_modules
coverage
```

## ESLint BE config
```
{
  "env": {
    "es2021": true,
    "node": true,
    "jest/globals": true
  },
  "extends": [
    "eslint:recommended",
    "plugin:node/recommended",
    "airbnb-base",
    "plugin:prettier/recommended"
  ],
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module"
  },
  "plugins": ["node", "jest", "jsdoc"],
  "rules": {
    "import/extensions": [
      "error",
      {
        "js": "ignorePackages"
      }
    ]
  }
}
```