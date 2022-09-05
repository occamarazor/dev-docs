# MERN dev setup

## Project init
```
yarn init
```
```
{
  "scripts": {
    "lint": "yarn eslint . --fix --max-warnings=0",
    "format": "yarn prettier . --write"
  },
  "lint-staged": {
    "**/*": "prettier --write --ignore-unknown"
  }
}

```

## Prettier & ESLint install
```
yarn add -D --exact prettier
yarn add -D eslint-config-prettier eslint-plugin-prettier eslint-plugin-jest
```

## Airbnb dependencies install
```
npx install-peerdeps --dev eslint-config-airbnb
```

## Git hooks install
```
yarn add -D husky lint-staged
npx husky install
npm set-script prepare "husky install"
npx husky add .husky/pre-commit "npx lint-staged"
```

## Prettier ignore
```
touch .prettierignore
```
```
node_modules
coverage
public
```

## Prettier config
```
touch .prettierrc.json
```
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

## ESLint ignore
```
touch .eslintignore
```
```
node_modules
coverage
public
```

## ESLint config
```
touch .eslintrc.json
```
```
{
  "env": {
    "es2021": true,
    "browser": true,
    "node": true,
    "jest/globals": true
  },
  "extends": ["airbnb", "prettier"],
  "plugins": ["jest", "prettier"],
  "parserOptions": {
    "ecmaVersion": "latest",
    "sourceType": "module",
    "ecmaFeatures": {
      "jsx": true
    }
  },
  "rules": {},
  "settings": {
    "import/resolver": {
      "node": {
        "moduleDirectory": ["node_modules", "src"]
      }
    }
  }
}
```