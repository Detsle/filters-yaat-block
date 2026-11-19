# filters-yaat-block

Публичная база косметических CSS-фильтров для расширения **Я@ Block**.

Репозиторий содержит только декларативные CSS-правила, сгруппированные по категориям. Код расширения, JavaScript-движок, обработчики DOM и пользовательские настройки здесь не публикуются.

## Формат

- `filters-manifest.json` — версия базы, перечень категорий, пути, размеры и SHA-256 каждого файла.
- `filters/*.css` — отдельный полный CSS-файл для каждой категории.
- Версия фильтров независима от версии расширения. Текущая версия базы: **1.0.1** (первая публикация — **1.0.0**).

## Источники доставки

Расширение получает манифест и файлы последовательно из трёх адресов. При ошибке или несовпадении SHA-256 оно переходит к следующему источнику:

1. `https://raw.githubusercontent.com/Detsle/filters-yaat-block/main/`
2. `https://fastly.jsdelivr.net/gh/Detsle/filters-yaat-block@main/`
3. `https://cdn.jsdelivr.net/gh/Detsle/filters-yaat-block@main/`

Сами файлы запрашиваются по путям из `filters-manifest.json`. Отдельный промежуточный сервер или зеркало не используется.

## Обновление и безопасность

- Расширение проверяет обновления автоматически раз в сутки и по ручному запросу пользователя.
- Каждый CSS-файл проверяется по SHA-256 и размеру, указанным в манифесте.
- Новая база применяется только после успешной загрузки и проверки **всех** категорий.
- При ошибке остаётся предыдущая локальная база; если её ещё нет, используется встроенная база расширения.
- Загруженные файлы — только CSS. Удалённый JavaScript не исполняется.
- URL внешних ресурсов (`url()`), `@import`, `expression()` и JavaScript-выражения в фильтрах не допускаются.

## Категории

| Категория | Файл |
|---|---|
| `dzenSuggest` | [`filters/dzen-suggest.css`](filters/dzen-suggest.css) |
| `dzen` | [`filters/dzen.css`](filters/dzen.css) |
| `mail` | [`filters/mailru.css`](filters/mailru.css) |
| `yandexMail` | [`filters/yandex-mail.css`](filters/yandex-mail.css) |
| `yandexSearch` | [`filters/yandex-search.css`](filters/yandex-search.css) |
| `yandexWeather` | [`filters/yandex-weather.css`](filters/yandex-weather.css) |
| `yandexMetro` | [`filters/yandex-metro.css`](filters/yandex-metro.css) |
| `yandexMarket` | [`filters/yandex-market.css`](filters/yandex-market.css) |
| `yandexMaps` | [`filters/yandex-maps.css`](filters/yandex-maps.css) |
| `yandexEda` | [`filters/yandex-eda.css`](filters/yandex-eda.css) |
| `yandexAfisha` | [`filters/yandex-afisha.css`](filters/yandex-afisha.css) |
| `yandexTelemost` | [`filters/yandex-telemost.css`](filters/yandex-telemost.css) |
| `yandexRealty` | [`filters/yandex-realty.css`](filters/yandex-realty.css) |
| `kinopoisk` | [`filters/kinopoisk.css`](filters/kinopoisk.css) |

## Происхождение и лицензирование

Часть правил является авторскими селекторами по DOM-снимкам, предоставленным пользователем. Также присутствует адаптированная выборка сторонних правил. Сведения об источниках и атрибуции приведены в `FILTER-SOURCES.txt` и `THIRD-PARTY-NOTICES.txt`. Для правил Яндекс.Маркета, адаптированных из AdGuardFilters (GPL-3.0-only), в репозитории сохранён `LICENSE-GPL-3.0.txt`.

База является курируемой выборкой для Я@ Block, а не полной копией RU AdList, EasyList или AdGuardFilters.
