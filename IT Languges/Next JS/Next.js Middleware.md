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

## Cookies

> Cookies — грають роль невеликого сховища, де можна зберігати налаштування теми ли локалізації користувача

### Методи

- **Delete** — Видалити по name
- **Has** — Перевірити наявність
- **Get** — Получити по name
- **GetAll** — Получити всі наявні кукі в користувача
- **Set** — Встанновити нові кукі

### Приклад коду

```typescript
export function middleware(request: NextRequest) {
    let newUser = NextResponse.next()
    newUser.cookies.set('locale', 'ua', {
        path: '/',
        maxAge: 60 * 60 * 24 * 365,
        httpOnly: false
    })
  
    return newUser
}
```
