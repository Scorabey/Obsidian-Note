## Типи із `next/`

### `Metadata` і ``ResolvingMetadata``

> `Metadata` — тип дя статичного експорту метаданних. `ResolvingMetadata` — Тип другого аргументу `generateMetadata`, через нього можна получити метаданні батьківського сегменту і росширити їх

```TSX
import type { Metadata, ResolvingMetadata } from 'next'

export async function generateMetadata(
  { params }: Props,
  parent: ResolvingMetadata
): Promise<Metadata> {
  const prevImages = (await parent).openGraph?.images || []
  return {
    title: 'Страница',
    openGraph: { images: ['/og.jpg', ...prevImages] }
  }
}
```

### NextConfig

> Тип для `next.config.ts` — дає автодоповнення всіх опцій в конфігу

```TSX
import type { NextConfig } from 'next'
const config: NextConfig = { typedRoutes: true }
export default config
```

### Route

> Використовується для типізованих ссилок. Літеральних строк в href валідується автоматично

```TSX
import type { Route } from 'next'
router.push(('/blog/' + slug) as Route)
```

### Типи із `next/server`

###### `NextRequest`

> Розширює Web `Request` API додатковими методами: зручна праця з куками через `.cookies.get()/.set()`, доступ до распарсеному URL через `.nextUrl`

```TSX
import type { NextRequest } from 'next/server'

export function middleware(req: NextRequest) {
  const token = req.cookies.get('token')
  const path = req.nextUrl.pathname
}
```

###### NextResponse

> Розширює Web Response. Загальні статичні методи

```TS
NextResponse.next()           // пропустить запрос
NextResponse.redirect(url)    // редирект
NextResponse.rewrite(url)     // переписать URL без редиректа
NextResponse.json(data)       // JSON-ответ
```

### Типи із `'next/navigation'`

> Хуки для Client Components — повертає типізованні значення

```TS
useRouter()        // AppRouterInstance
usePathname()      // string
useSearchParams()  // ReadonlyURLSearchParams
useParams()        // Record<string, string | string[]>
```
