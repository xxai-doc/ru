<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Рекомендуется сначала установить nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , а затем `direnv allow` после входа в каталог ( [файл .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) будет выполняться автоматически после входа в каталог).

Значение: китайский перевод на японский, корейский, английский, английский перевод на все остальные языки. Если вы хотите поддерживать только китайский и английский языки, вы можете просто написать `zh: en` .

Значение: китайский перевод на японский, корейский, английский, английский перевод на все остальные языки. Если вы хотите поддерживать только китайский и английский языки, вы можете просто написать `zh: en` .

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

### Инструкции по автоматизации перевода документов

См. репозиторий кода [xxai-art/doc](https://github.com/xxai-art/doc)

Рекомендуется сначала установить nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , а затем `direnv allow` после входа в каталог ( [файл .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) будет выполняться автоматически после входа в каталог).

Чтобы избежать перевода большой кодовой базы на сотни языков, я создал отдельную кодовую базу для каждого языка и создал организацию для хранения кодовой базы.

Установка переменной среды `GITHUB_ACCESS_TOKEN` и последующий запуск [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) автоматически создаст репозиторий кода.

Конечно, вы также можете поместить его в кодовую базу.

Справочник по скрипту перевода [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Код скрипта интерпретируется следующим образом:

[bunx](https://bun.sh/docs/cli/bunx) — это замена npx, которая работает быстрее. Конечно, если у вас не установлен bun, вместо него можно использовать `npx` .

`bunx mdt zh` отображает `.mdt` в каталоге zh как `.md` , см. 2 связанных файла ниже

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` — это основной код для перевода (если у вас установлен только `nodejs` , но не установлены `bun` и `direnv` , вы также можете запустить `npx i18n` для перевода).

Он будет анализировать [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , конфигурация `i18n.yml` в этом документе выглядит следующим образом:

```
en:
zh: ja ko en
```

Значение: китайский перевод на японский, корейский, английский, английский перевод на все остальные языки. Если вы хотите поддерживать только китайский и английский языки, вы можете просто написать `zh: en` .

Последним является [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , который извлекает содержимое между основным заголовком и первым подзаголовком файла `README.md` каждого языка для создания записи `README.md` . Код очень простой, можете посмотреть сами.

Google API используется для бесплатного перевода. Если вы не можете получить доступ к Google, настройте и установите прокси-сервер, например:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Сценарий перевода создаст переведенный кеш в каталоге `.i18n` , проверьте его с помощью `git status` и добавьте в репозиторий кода, чтобы избежать повторных переводов.

Пожалуйста, запускайте `bunx i18n` каждый раз, когда вы изменяете перевод, чтобы обновить кеш.

Если исходный текст и перевод будут изменены одновременно, кеш будет перепутан, поэтому, если вы хотите изменить, вы можете изменить только один, а затем запустить `bunx i18n` для обновления кеша.
