---
title: "useRouter"
date: 2024-06-08T06:00:20+06:00
menu:
  sidebar:
    name: useRouter
    identifier: useRouter
    parent: next
    weight: 3
---

useRouter 钩子允许你以编程方式更改 客户端组件 内的路由。

*推荐：除非你有使用 useRouter 的特定要求，否则请使用 <Link> 组件 进行导航。*
```javascript
'use client'

import { useRouter } from 'next/navigation'

export default function Page() {
  const router = useRouter()

  return (
    <button type="button" onClick={() => router.push('/dashboard')}>
      Dashboard
    </button>
  )
}
```
**从 next/router 迁移**
使用 App Router 时，应从 next/navigation 而不是 next/router 导入 useRouter 钩子

- pathname 字符串已被删除并替换为 usePathname()

- query 对象已被删除并被 useSearchParams() 取代

- router.events 已被替换。
