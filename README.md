<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

Часть кода веб-сайта является открытым исходным кодом, добро пожаловать, чтобы помочь оптимизировать перевод.

## интерфейсный код

* [интерфейсный код](https://github.com/xxai-art/web)
* [Языковые пакеты для сайта в целом](https://github.com/xxai-art/web/tree/main/i18n)
* [Языковые пакеты для модулей входа](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Многоязычная документация веб-сайта](https://github.com/xxai-doc)

Интерфейсным языком программирования является [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , который добавляет некоторые функции, основанные на синтаксисе coffeescript, см [. ./coffee_plus.md](./coffee_plus.md) .

## Интернационализация веб-сайтов и документов

Опирайтесь на следующие 3 проекта

* [@w5/мдт](https://www.npmjs.com/package/@w5/mdt)

  Суффикс `.mdt` , вы можете использовать синтаксис, аналогичный `<+ ./coffee_plus/import.js>` , для ссылки на внешние файлы и генерировать уценку с суффиксом `.md` .

* [@w5/трмд](https://www.npmjs.com/package/@w5/trmd)

  Перевод Markdown не будет переводить коды и ссылки и будет кэшировать переведенные предложения. Если перевод изменен, но исходный текст не изменен, повторное выполнение не приведет к перезаписыванию модификации перевода.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Языковые файлы для перевода веб-сайтов, созданных с помощью `yaml` .
