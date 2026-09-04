# batch_4_objects.md — БАТЧ 4: SCP-объекты

Используй профили: `planner`, `content_executor`, `reviewer`, `lore_keeper`, `immersion_checker`, `gap_analyzer`.

## Задача
Наполнить сайт MSU-SCP страницами SCP-объектов на основе лора. Результат — файлы в `/pages/`.

## Источники
- `msu-scp-lore.md`
- `site-map.md`
- `codex.md`
- `reference.md`
- `progress_log.md`
- `STATE.md`

## ПРЕДУСЛОВИЕ
Все Engine-шаблоны из Батча 1 должны иметь статус `approved` в `site-map.md`, включая `article-template.html`. Если шаблон не `approved` — остановись сразу, обнови `STATE.md` со статусом `stopped_on_error` и причиной «шаблон article-template.html не approved — требуется завершить Батч 1 сначала, жди человека.

## РЕЖИМ
Автономный батч. Работай по списку target_pages последовательно, без остановки между страницами внутри батча.

## ЖЁСТКОЕ ПРАВИЛО ОШИБОК
Если `delegate_task` к любой роли падает с ошибкой после 3 повторных попыток:
- не создавай и не редактируй файлы напрямую в обход роли;
- не одобряй страницу без reviewer;
- не переходи к следующей странице;
- обнови `STATE.md`: `Статус последней сессии: stopped_on_error`;
- укажи страницу, роль, этап и текст ошибки;
- выполни HUMAN_CHECKPOINT вне очереди и остановись.

## target_pages (Батч 4, порядок обязателен)

1. `Content: SCP-MSU-001` — `pages/scp-msu-001.md` — `doc_type: Объект`
2. `Content: SCP-MSU-003 (+ 003-1, 003-2)` — `pages/scp-msu-003.md` — `doc_type: Объект` (подобъекты 003-1 и 003-2 описываются внутри одной статьи, если человек не решил иначе)
3. `Content: SCP-MSU-004` — `pages/scp-msu-004.md` — `doc_type: Объект`
4. `Content: SCP-MSU-009` — `pages/scp-msu-009.md` — `doc_type: Объект`
5. `Content: SCP-MSU-033-01` — `pages/scp-msu-033-01.md` — `doc_type: Объект`

## Алгоритм на каждую target_page

1. `planner` проверяет статус страницы и её зависимости в `site-map.md`.
2. Делегируй задачу:
   - `Content-page` → `content_executor`.
3. Дождись черновика.
4. Запусти проверяющие роли:
   - `Content-page` → `lore_keeper`, `immersion_checker`, `gap_analyzer`.
5. Передай все замечания `reviewer`.
6. `reviewer` запускает собственный чек-лист (см. Батч 2, адаптируй под SCP-объект: Item Number, Object Class, Special Containment Procedures, Description, Addendum, теги, перелинковка).
7. `reviewer` делит замечания на `BLOCKING` и `NICE-TO-HAVE`, `round_counter += 1`.
8. Если есть `BLOCKING` и `round_counter < 3`:
   - верни единый список замечаний `content_executor`;
   - исправляй только затронутые разделы;
   - повтори проверку (шаги 4–7).
9. Если `round_counter == 3` и `BLOCKING` остались:
   - `reviewer` переводит их в `known limitations`;
   - фиксирует список в конце страницы или в `progress_log.md`;
   - одобряет страницу.
10. После одобрения:
    - обнови `site-map.md` (статус страницы → `approved`);
    - обнови `codex.md` (новые термины, занятые номера, новые сквозные ссылки, summary страницы 3–5 строк);
    - добавь строку в `progress_log.md`:
      `Content: [имя] — round_counter: X — known limitations: [список или "нет"] — статус: одобрено`.
11. Перейди к следующей `target_page` без ожидания человека.

## Финальный HUMAN_CHECKPOINT

Только после `scp-msu-033-01.md`:
- обнови `STATE.md`:
  - Батч: `4`;
  - Статус последней сессии: `completed`;
  - Следующий промпт: `batch_5_integration_qa.md` (или `ПРОМПТ НЕ ГОТОВ — человеку нужно сгенерировать batch_5.md перед следующей сессией`, если человек ещё не решил состав Батча 5);
  - кратко напиши, что все основные SCP-объекты одобрены.
- выведи сводку по `progress_log.md` за весь батч (сколько страниц одобрено, сколько с known limitations, краткий список ограничений);
- остановись. Не начинай следующие страницы.

## Формат вывода
- файлы в `/pages/`;
- обновлённые `site-map.md`, `codex.md`, `progress_log.md`, `STATE.md`.