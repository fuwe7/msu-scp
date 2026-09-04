# site-map.md — реестр страниц сайта MSU-SCP

Статусы: not_started / in_progress / review / approved

## Engine-pages (шаблоны, вёрстка, навигация) — БАТЧ 1, делать первым
| Страница | Файл | Статус | Раунды ревью |
|---|---|---|---|
| Главная (с блоком вступительной Tale вместо "Статья дня") | index.html | approved | 1 |
| Header (общий) | templates/header.html | approved | 1 |
| Footer (общий) | templates/footer.html | approved | 1 |
| Шаблон SCP-объекта | templates/article-template.html | approved | 1 |
| Шаблон досье локации (ЛП-XX) | templates/dossier-location-template.html | approved | 1 |
| Шаблон теоретического документа | templates/theory-doc-template.html | approved | 1 |
| Шаблон архива инцидента | templates/incident-report-template.html | approved | 1 |
| Шаблон Tale | templates/tale-template.html | approved | 1 |
| Шаблон досье персонала | templates/dossier-personnel-template.html | approved | 1 |
| Hub-статей (объекты) | templates/hub-template.html | approved | 1 |
| Hub-tales | templates/tales-hub.html | approved | 1 |
 Страница "О Фонде" — ТОЛЬКО скелет/шаблон | templates/about-template.html | approved | 1 |

## Content-pages (наполнение из лора) — БАТЧ 2+, только после approved нужных шаблонов
| Страница | ID | doc_type | Файл | Статус | Приоритет |
|---|---|---|---|---|---|
| Вступительный Tale (студент находит ПОРОГ-17) | - | Tale | pages/tale-intro.md | approved | 1 — первая content-страница |
| Экстренное распоряжение ПОРОГ-17 | - | Архив/распоряжение | pages/porog-17.md | not_started | 2 |
| Досье локации "Цирк" | ЛП-17 | Досье локации | pages/lp-17-tsirk.md | approved | 2 |
| Происхождение Парадоксов | ТЛП-02 | Теория | pages/tlp-02.md | approved | 3 |
| "Столкновение" | АН-2017-14 | Инцидент | pages/an-2017-14.md | approved | 3 |
| SCP-MSU-003 (+ 003-1, 003-2) | SCP-MSU-003 | Объект | pages/scp-msu-003.md | approved | 4 |
| SCP-MSU-001 | SCP-MSU-001 | Объект | pages/scp-msu-001.md | approved | 4 |
| SCP-MSU-004 | SCP-MSU-004 | Объект | pages/scp-msu-004.md | approved | 4 |
| SCP-MSU-009 | SCP-MSU-009 | Объект | pages/scp-msu-009.md | approved | 4 |
| SCP-MSU-033-01 | SCP-MSU-033-01 | Объект | pages/scp-msu-033-01.md | approved | 4 |
| Досье локации "Офис" (ЛП-33) | ЛП-33 | Досье локации | pages/lp-33-ofis.md | approved | 5 |
| Досье локации ЛП-74 | ЛП-74 | Досье локации | pages/lp-74.md | approved | 5 |
| Страница "О Фонде" (текст) | - | org-info | pages/about.md | approved | 2 (батч 2) |
## Правило зависимостей
Content-page нельзя брать в работу, пока не approved соответствующий Engine-шаблон её doc_type (см. content_executor_v2.soul.md, ветки A-F).
