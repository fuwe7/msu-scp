# Аудит навигации и поиска (До исправлений)

## Проблемные ссылки

pages/scp-msu-001.html
→ « Предыдущий
→ ../index.html
→ ведет на index.html, хотя должна на отдельную страницу
→ Корректный href: None (нет предыдущего)

pages/scp-msu-001.html
→ Следующий »
→ ../index.html
→ ведет на index.html, хотя должна на отдельную страницу
→ Корректный href: scp-msu-003.html

pages/scp-msu-003.html
→ « Предыдущий
→ /pages/scp-msu-001.html
→ абсолютный путь от корня (начинается с /)
→ Корректный href: scp-msu-001.html

pages/scp-msu-003.html
→ Следующий »
→ /pages/scp-msu-004.html
→ абсолютный путь от корня (начинается с /)
→ Корректный href: scp-msu-004.html

pages/scp-msu-004.html
→ « Предыдущий
→ /pages/scp-msu-003.html
→ абсолютный путь от корня (начинается с /)
→ Корректный href: scp-msu-003.html

pages/scp-msu-004.html
→ Следующий »
→ /pages/scp-msu-009.html
→ абсолютный путь от корня (начинается с /)
→ Корректный href: scp-msu-009.html

pages/scp-msu-009.html
→ « Предыдущий
→ /pages/scp-msu-004.html
→ абсолютный путь от корня (начинается с /)
→ Корректный href: scp-msu-004.html

pages/scp-msu-009.html
→ Следующий »
→ /pages/scp-msu-033-01.html
→ абсолютный путь от корня (начинается с /)
→ Корректный href: scp-msu-033-01.html

pages/scp-msu-033-01.html
→ « Предыдущий
→ /pages/scp-msu-009.html
→ абсолютный путь от корня (начинается с /)
→ Корректный href: scp-msu-009.html

pages/scp-msu-033-01.html
→ Следующий »
→ ../index.html
→ ведет на index.html, хотя должна на отдельную страницу
→ Корректный href: None (нет следующего)

## Строка поиска

Контейнер строки поиска `<div class="search-bar">...</div>` и `<input placeholder="Поиск по базе данных..." type="text">` присутствует в <header> каждого `.html` файла.
