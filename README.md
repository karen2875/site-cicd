# site-cicd

![Deploy static site](https://github.com/karen2875/site-cicd/actions/workflows/deploy.yml/badge.svg)

Индивидуальный проект к лабораторной работе по CI/CD: **проверка HTML и CSS (линтинг) перед деплоем** на GitHub Pages.

Сайт: https://karen2875.github.io/site-cicd/

## Как устроен пайплайн

Workflow `.github/workflows/deploy.yml` состоит из двух заданий:

1. `lint` — устанавливает Node.js, проверяет HTML через HTMLHint (правила в `.htmlhintrc`) и CSS через Stylelint (правила в `.stylelintrc.json`).
2. `deploy` — публикует сайт на GitHub Pages. Объявлено с `needs: lint`, поэтому запускается только после успешной проверки.

Запуск происходит при каждом push в ветку main, а также вручную (кнопка Run workflow во вкладке Actions).

## Файлы проекта

- `index.html`, `style.css` — страница сайта и её оформление;
- `.htmlhintrc`, `.stylelintrc.json` — правила проверки;
- `.github/workflows/deploy.yml` — workflow.

## Как проверить, что защита работает

1. В `index.html` удалите закрывающий тег `</h1>` и сделайте коммит в main.
2. Во вкладке Actions задание `lint` завершится красным крестиком на шаге Lint HTML, а `deploy` будет пропущено: сайт не обновится, бейдж станет красным.
3. Верните тег и сделайте новый коммит: оба задания станут зелёными, сайт обновится.
