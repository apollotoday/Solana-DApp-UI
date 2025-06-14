# Contributing to SolUI

Thank you for your interest in contributing to SolUI! We appreciate your support and look forward to your contributions. This guide will help you understand the directory structure and provide detailed instructions on how to add a new component to SolUI.

## Getting Started

### Fork and Clone the Repository


1. **Clone your forked repository to your local machine**

   ```bash
   git clone https://github.com/<YOUR_USERNAME>/sol-ui.git
   ```

2. **Navigate to the project directory**

   ```bash
   cd sol-ui
   ```

3. **Create a new branch for your changes**

   ```bash
   git checkout -b my-new-branch
   ```

4. **Install dependencies**

   ```bash
   pnpm i
   ```

5. **Create a `.env.local` file**

   ```bash
   touch .env.local && echo "NEXT_PUBLIC_APP_URL=http://localhost:3000" > .env.local
   ```

7. **Run the project**
   ```bash
   pnpm dev
   ```

## Adding a New Component

To add a new component to SolUI, you will need to modify several files. Follow these steps:

### 1. Create Component

Create the main component in `registry/components/solui/example-component.tsx`

```typescript
import React from 'react'

export default function ExampleComponent() {
  return (
    <div>
      OPOS.
    </div>
  )
}
```

### 2. Create Component Demo

Provide a basic example to showcase your component in `registry/components/example/example-component-demo.tsx`

```typescript
import ExampleComponent from '@/registry/components/solui/example-component'

export default function ExampleComponentDemo() {
  return (
    <div className="relative justify-center">
    <ExampleComponent />
  </div>
  )
}
```

### 3. Update Sidebar

Add your component to the sidebar in `config/docs.ts`

```typescript
{
    title: "Example Component",
    href: `/docs/components/example-component`,
    items: [],
    label: "New",
}
```

### 4. Create docs

Create an MDX file for documenting your component in `content/docs/components/example-component.mdx`

````md
---
title: Example Component
date: 2025-02-12
description: Example component for Sol UI
author: apollum
published: true
---

<ComponentPreview name="example-component-demo" />

## Installation

<Tabs defaultValue="cli">

<TabsList>
  <TabsTrigger value="cli">CLI</TabsTrigger>
  <TabsTrigger value="manual">Manual</TabsTrigger>
</TabsList>
<TabsContent value="cli">

```bash
npx solui-cli add example-component
```

</TabsContent>

<TabsContent value="manual">

<Steps>

<Step>Copy and paste the following code into your project.</Step>

<ComponentSource name="example-component" />

<Step>Update the import paths to match your project setup.</Step>

</Steps>

</TabsContent>

</Tabs>

<ComponentSource name="example-component" />

</Steps>

## Props

| Prop  | Type   | Description                | Default |
| ----- | ------ | -------------------------- | ------- |
| color | String | The color of the component | "blue"  |
````

### 5. Update Registry

Export your component and example in the registry in `registry/index.tsx`

```typescript
const ui: Registry = {
  "example-component": {
    name: "example-component",
    type: "components:ui",
    files: ["registry/components/solui/example-component.tsx"],
  },
};

const example: Registry = {
  "example-component-demo": {
    name: "example-component",
    type: "components:example",
    files: ["registry/components/example/example-component-demo.tsx"],
    component: React.lazy(
      () => import("@/registry/components/example/example-component-demo"),
    ),
  },
};
```
### 6. Pull Request

Provide a clear and concise title for your PR.

### PR Fixes:
- 1
- 2

Fix #[Issue Number if there]

### Checklist before requesting a review:
- [ ] I have performed a self-review of my code.
- [ ] I assure there is no similar/duplicate pull request regarding the same issue.

### Attach Screenshots or Videos (if applicable)

## Ask for Help

For any help or questions, please open a new GitHub issue.
