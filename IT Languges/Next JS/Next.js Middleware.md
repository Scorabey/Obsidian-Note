> middleware.ts — це файл, який керує запросами сервера, до того як вони дйдуть до користувача.
> Він повинен лежати в корні проекта, біля app/

#### Простий приклад

```typescript
import { NextResponse } from 'next/server'
import type { NextRequest } from 'next/server'

export function middleware(request: NextRequest) {
  return NextResponse.redirect(new URL('/home', request.url))
}

export const config = {
  matcher: '/about/:path*',
}
```

## Matcher — контролює вказані шляхи
#### Простий синтаксис, для контролю одного маршруту

```typescript
export const config = {
	matcher: '/about/:path*'
}
```

#### Синтаксис для контролю декількох маршрутів

```typescript
export const config = {
	matcher: [
	'/about/:path*', 
	'/support/:path*',
	'/home/:path*'
	]
}
```

