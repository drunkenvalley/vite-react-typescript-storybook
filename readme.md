# Vite + React + Typescript + Storybook

A minimal example preset for combining React, Typescript and Storybook using Vite.

## Getting started

### Requirements

1. **Node.js v14 LTS** or above
2. **npm v6** or above <small>(included with Node)</small>

### Installation

1. Set up your own git repository;
    a. Fork this repository and clone it to local,
    b. Or download this repository, before pushing it to your own repository.
2. Open the folder in Terminal of choice and run `npm install` or `npm ci`.
3. Verify React is working with `npm run dev` and opening the page in your browser. Default url is <http://127.0.0.1:5173>.
4. Verify Storybook is working with `npm run storybook`, opening the page in your browser. Default url is <http://localhost:6006>.

## Features

### Vite

Vite is an incredibly fast build tool to replace Webpack. It is built on Rollup, itself blazing fast. It itself comes with a slew of features out of the box, such as SASS/SCSS, JSX, etc. See the [Official Vite webpage](https://vitejs.dev/) for more documentation.

#### Aliases

This repository is setup with `@` as an alias for the `src` folder. For example, instead of writing `import Button from "../../Button"` you would instead write `import Button from '@/path/to/Button'`. Storybook has also been configured to resolve the alias when building.

To add your own alias look to the `tsconfig.json`'s `path`, and `vite.config.ts`'s `resolve.alias` options.

**Example:**

`// tsconfig.json`

```json
"baseUrl": "./",
"paths": {
    "@/*": ["src/*"]
},
```

`// vite.config.ts`

```typescript
resolve: {
  alias: {
    "@": resolve(__dirname, "src")
  }
}
```

### React

Hopefully React needs no introduction; it is one of the biggest Javascript frameworks. See the [Official React webpage](https://reactjs.org/) for more documentation.

#### JSX

Among its most recognizable features we have JSX, which allows you to mix an HTML-like syntax inside of your Javascript. Just name your Javascript file `.jsx` or `.tsx` and you're off to the races.

**Example:**

`// Button.tsx`

```tsx
export default function Button ({ children }) {
  return (
    <button className="bg-dark text-light" onClick={(e) => e.preventDefault()}>
      {children}
    </button>
  )}
```

### Typescript

Adding Typescript to your project lets you opt into better typing. This gives you better autocompletion for objects through interfaces, et al. See the [official Typescript webpage](https://www.typescriptlang.org/) for more documentation.

**Example:**

`// Component.tsx`

```tsx
import { ReactNode, MouseEvent } from 'react'

interface Props {
  children: ReactNode,
  className?: string,
  onClick?: (e: MouseEvent) => void
}

export default function Component ({ children, ...attrs }: Props) {
  // VSCode will understand that attrs contains property 'className' and 'onClick',
  // though they might be because of the '?' in the interface.
  return (
    <button {...attrs}>
      {children}
    </button>
  )
}
```

### Storybook

A great toolkit for building your UI components in isolation before the site itself is complete, Storybook helps empower your build process. It also makes it easier to test and validate the components outside its intended context. See the [official Storybook webpage](https://storybook.js.org/) for more documentation.
