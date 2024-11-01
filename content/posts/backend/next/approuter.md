---
title: "App router"
date: 2024-06-08T06:00:20+06:00
menu:
  sidebar:
    name: App-router
    identifier: app router
    parent: next
    weight: 2
---

  在使用 Next.js 13 引入的 `app` 目录时，项目结构和文件组织方式与传统的 `pages` 目录有所不同。这是因为 `app` 目录采用了全新的布局和数据获取方法，以支持 React Server Components 和更灵活的路由配置。

### `app` 目录的特点

1. **文件结构**：`app` 目录使用文件夹而不是文件来定义路由。每个路由都由一个文件夹表示，文件夹内可以包含 `page.tsx`、`layout.tsx`、`loading.tsx` 等文件来定义页面、布局和加载状态等。

2. **动态路由**：`app` 目录仍然支持动态路由，但语法略有不同。你需要使用 `[param]` 语法创建动态路由文件夹。

例如：

```
src/
└── app/
    └── post/
        └── [id]/
            └── page.tsx
```

对应的页面代码可能是：

```tsx
// src/app/post/[id]/page.tsx

import { useRouter } from 'next/router';

const PostPage = () => {
  const router = useRouter();
  const { id } = router.query;

  return <div>Post ID: {id}</div>;
};

export default PostPage;
```

3. **布局文件**：`layout.tsx` 文件用于定义页面的公共布局，它可以包含在 `app` 目录或子目录中。例如：

```tsx
// src/app/layout.tsx

export default function RootLayout({ children }) {
  return (
    <html>
      <body>{children}</body>
    </html>
  );
}
```

4. **数据获取**：`app` 目录中的页面组件可以使用异步组件和数据获取方法，例如 `getStaticProps` 和 `getServerSideProps`。

### 过渡和兼容

如果你从使用 `pages` 目录的传统结构过渡到使用 `app` 目录的新结构，需要注意以下几点：

- **路径更改**：确保文件路径和目录结构符合 `app` 目录的新规范。
- **数据获取方法调整**：检查并调整数据获取方法，确保与新目录结构兼容。
- **更新依赖**：确保你的 Next.js 和相关依赖项更新到最新版本，以支持 `app` 目录功能。

### 示例项目结构

这是一个包含动态路由的示例项目结构：

```
src/
└── app/
    ├── layout.tsx
    ├── page.tsx
    └── post/
        └── [id]/
            └── page.tsx
```

### 示例页面代码

#### `src/app/page.tsx`

```tsx
// src/app/page.tsx

export default function HomePage() {
  return <div>Welcome to the Home Page</div>;
}
```

#### `src/app/post/[id]/page.tsx`

```tsx
// src/app/post/[id]/page.tsx

import { useRouter } from 'next/router';

const PostPage = () => {
  const router = useRouter();
  const { id } = router.query;

  return <div>Post ID: {id}</div>;
};

export default PostPage;
```

使用 `app` 目录可以带来更灵活的路由和布局管理方式，同时支持新的 React Server Components 特性。如果你遇到问题或不确定某些实现细节，可以参考 Next.js 官方文档中的 `app` 目录指南，获取更多详细信息和示例。