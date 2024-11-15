# markdown-prerender

A React library for rendering dynamic components within markdown content.

## Installation

```bash
npm install @crimson206/markdown-prerender
# or
yarn add @crimson206/markdown-prerender
```

## Features

- Dynamic component injection in markdown
- Support for both JSON and TypeScript syntax blocks
- Server-side rendering compatible
- React component hydration
- Type-safe API

## Basic Usage

```tsx
import { processDynamicComponents, useDynamicComponents } from '@crimson206/markdown-prerender';
import ReactMarkdown from 'react-markdown';
import rehypeRaw from 'rehype-raw';

const YourComponent = () => {
  const dynamicRenderResult = processDynamicComponents(
    markdownContent,
    [
      {id: 'myComponent', Component: MyDynamicComponent},
      {id: 'anotherComponent', Component: AnotherComponent}
    ]
  );

  useDynamicComponents(dynamicRenderResult.componentPairs);

  return (
    <ReactMarkdown rehypePlugins={[rehypeRaw]}>
      {dynamicRenderResult.transformedContent}
    </ReactMarkdown>
  );
};
```

## Markdown Syntax

### JSON Block

'''json
```json
{
    "type": "dynamicRenderer",
    "id": "myComponent",
    "props": {
        "title": "Example",
        "count": 5
    }
}
```
'''

### TypeScript Block
'''ts
```ts

const spec = {
    type: "dynamicRenderer",
    id: "myComponent",
    props: {
        title: "Example",
        count: 5
    }
}
```
'''

## API Reference

### processDynamicComponents

Processes markdown content and prepares dynamic components for rendering.

```typescript
function processDynamicComponents(
  options: {
    initialContent: string;
    componentDefinitions: ComponentDefinition[];
  }
): DynamicRenderResult;
```

### useDynamicComponents

A React hook that hydrates dynamic components in the DOM.

```typescript
function useDynamicComponents(components: ComponentPair[]): void;
```

### Types

```typescript
interface ComponentDefinition {
  id: string;
  Component: React.FC<any>;
}

interface DynamicRenderResult {
  transformedContent: string;
  componentPairs: ComponentPair[];
}

interface ComponentPair {
  id: string;
  useComponent: () => JSX.Element;
}
```

## Requirements

- React 18.3.0 or higher
- react-markdown
- rehype-raw

## License

MIT

## For Development Reference

We provide a flattened module structure for easier understanding and AI assistance during development. You can download it here: [flatten_module.zip](https://github.com/crimson206/talkative-prerender/releases/download/v0.1.0/flatten_module.zip)

### Using the Flattened Module with AI

1. Download and extract `flatten_module.zip`
2. When seeking AI assistance:
   - Share the relevant files from the flattened module
   - Ask specific questions about implementation details
   - Use it as a reference for understanding the library's structure

[Rest of Features and API documentation remains the same...]
