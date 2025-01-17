# Макет {#layout}

Вы можете выбрать макет страницы, установив опцию `layout` в [метаданных](./frontmatter-config). Изначально есть 3 макета: `doc`, `page` и `home`. Если ничего не указано, то страница будет использовать макет `doc`.

```yaml
---
layout: doc
---
```

## Макет `doc` {#doc-layout}

Вариант `doc` — это макет по умолчанию, который стилизует всё содержимое Markdown в виде «документации». Он работает, оборачивая весь контент в CSS-класс `vp-doc` и применяя стили к вложенным элементам.

Почти все общие элементы, такие как `p` или `h2`, получают специальную стилизацию. Поэтому имейте в виду, что если вы добавите какой-либо пользовательский HTML внутри Markdown-контента, то он также будет подвержен влиянию этих стилей.

Кроме того, в нём предусмотрены специальные функции, перечисленные ниже. Эти функции включены только в данном макете.

- Ссылка «Редактировать»
- Ссылки предыдущая/следующая
- Оглавление
- Реклама [Carbon Ads](./default-theme-carbon-ads)

## Макет `page` {#page-layout}

Вариант `page` сгенерирует «пустую страницу». Markdown всё равно будет разобран, и все [расширения Markdown](../guide/markdown) будут работать так же, как и с макетом `doc`, но никаких стилей по умолчанию применено не будет.

Макет `page` позволит вам оформить всё самостоятельно, без влияния темы VitePress на разметку. Это удобно, когда вы хотите создать свою собственную страницу.

Обратите внимание, что даже при таком раскладе сайдбар всё равно будет отображаться, если у страницы есть соответствующая конфигурация сайдбара.

## Макет `home` {#home-layout}

Вариант `home` сгенерирует шаблонную «домашнюю страницу». В этом макете вы можете установить дополнительные параметры, такие как `hero` и `features`, для дальнейшей настройки контента. Посетите секцию [Тема по умолчанию: Домашняя страница](./default-theme-home-page) для получения более подробной информации.

## Без макета {#no-layout}

Если вам не нужен макет, вы можете указать `layout: false` в метаданных. Этот параметр полезен, если вам нужна полностью настраиваемая целевая страница (по умолчанию без сайдбара, панели навигации или футера).

## Свой макет {#custom-layout}

Вы также можете использовать собственный макет:

```md
---
layout: foo
---
```

Будет выполнен поиск компонента с именем `foo`, зарегистрированного в контексте. Например, вы можете зарегистрировать свой компонент глобально в `.vitepress/theme/index.ts`:

```ts
import DefaultTheme from 'vitepress/theme'
import Foo from './Foo.vue'

export default {
  extends: DefaultTheme,
  enhanceApp({ app }) {
    app.component('foo', Foo)
  }
}
```
