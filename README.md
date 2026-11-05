# SNAKE FACTORY — HTML5 playtest

> **АКТИВНА ВЕРСІЯ: v1.3 — вільне плавне керування.** Експеримент v1.4 з рухом по клітинках відкладений після тестування. Його код збережено в гілці [`experiments/grid-v14`](../../tree/experiments/grid-v14). Головна гра на `main` знову має керування v1.3.

**Snake Factory** — мобільна аркада, що поєднує **Snake + Inventory Tetris (BUILD) + Merge + Auto Combat**.

Ця збірка — іграбельний тест інтеграції спрайтів Claude (`SNAKE_FACTORY_HANDOFF.zip`) із механіками Snake Factory v0.9.

## Запуск

Після ввімкнення GitHub Pages гра відкриватиметься за адресою:

**https://mickalaykorolyov-bit.github.io/snake-factory/**

Можна також завантажити `index.html` та відкрити локально в браузері.

### Керування

- **На телефоні:** рухай змійку пальцем.
- **На комп'ютері:** WASD або стрілки.
- **BOOST:** коротке прискорення.
- **BUILD:** пауза та майстерня для встановлення модулів у сітці 5×4.
- **MERGE:** однакові сусідні модулі об'єднуються.
- Стрілянина автоматична, коли на змійці встановлена відповідна зброя.

## Що завантажено

Файл `index.html` **містить усю гру й необхідні спрайти всередині** (data URI та вбудовані описи атласів). Додаткові каталоги не потрібні: це автономна версія для GitHub Pages.

У тесті підключено: голову змійки з анімацією, механічні модулі, павуків, важких ворогів, боса та базові тайли підлоги. Поки не реалізовано повний набір анімацій/ефектів та остаточний pixel-perfect рендер із арт-специфікації Claude.

**Важливо:** це не повний арт-пак у вигляді окремих редагованих PNG-файлів. Для наступного етапу розробки рекомендовано додати вихідні PNG/JSON у папку `assets/` та розділити HTML/CSS/JS.

## Увімкнення GitHub Pages

1. Відкрий репозиторій → **Settings → Pages**.
2. **Build and deployment → Deploy from a branch**.
3. Обери гілку **main**, папку **/(root)**.
4. Натисни **Save** та відкрий адресу вище після завершення публікації.

## GDevelop

Для цієї версії **GDevelop не потрібен**. Якщо вирішимо перенести гру в GDevelop, потрібно буде імпортувати окремі спрайти й перенести механіки у сцени/події.


## Оновлення v1.0 — Claude Visual Expansion

Новий візуальний шар доступний у кореневому `index.html` і на GitHub Pages. **Геймплей і баланс не змінювалися.**

- Анімовані кристали, жовті ящики модулів і аптечки.
- Спрайтові постріли, влучання та криваві сліди.
- Розширені фабричні тайли й промислові декорації на арені.
- Візуальні рівні модулів Merge (бронза / срібло / золото).
- Оновлені спрайти павуків і боса; оформлення HUD та BUILD.
- Окремі вихідні PNG + JSON у `assets/visual_v10/`.

Пакет Claude також має спрайти отрути, павутини й складних атак боса, але вони **не підключені як механіки** в цьому оновленні.

Для повернення до попередньої збірки збережено гілку `backup/claude-initial-art`.

## v1.1 — COIL KILL / Web Shooter / Body Weapons

**COIL KILL — основна механіка:** проведи змійку навколо ворогів і поверни голову до віддаленого сегмента свого тіла. Коли петля замикається, **усі павуки всередині миттєво гинуть**, включно з босом. Після петлі є коротка перезарядка, а перед повторним замиканням потрібно розвести голову й тіло.

- **THE AWAKENING:** довге тіло (від 14 сегментів); гармати, пилка та інші модулі фізично розміщені вздовж нього, атаки відбуваються з позиції відповідного сегмента.
- **THE INFESTATION:** павуки-павутинники стріляють анімованими клейкими снарядами по голові та сегментах. Уповільнення 40%, за повторного влучання до 55%, триває близько трьох секунд.
- **THE SKULL FACTORY:** довша змійка для більшої петлі, фінальний павук-череп теж може загинути від COIL KILL.

Базова швидкість знижена приблизно на 26% порівняно з попередньою версією. В BUILD з'явився **перегляд порядку фізичних сегментів від голови до хвоста**. Наявні модулі, Merge, 3 рівні × 3 хвилі та винагороди збережені.

На початковому екрані є кнопки **«ТЕСТ ПАВУТИНИ · L2»** і **«ТЕСТ БОСА · L3»**, щоб швидко перевірити нові механіки без проходження кампанії. Вони запускають окремі практичні сесії з тестовою конструкцією.

Окремі вихідні спрайти павутини: [assets/coil_v11](assets/coil_v11/). Перед оновленням створено резервну гілку [backup/visual-v10-before-coil](../../tree/backup/visual-v10-before-coil).


## v1.2 — MORPH LAB: four body transformations

The update uses the existing mechanics and Claude pixel art. Core movement, 3 levels, BUILD, Merge, web spiders, and instant **COIL KILL** remain.

**Power runes:** collect any two in either order. Unmatched runes reset the first half of the recipe.

| Pair / action | Power | Effect |
|---|---|---|
| ◆ energy crystal + ● gold coin | **FIREWORK SNAKE** | For **4 seconds**, every body segment shoots toward nearby spiders (or radially when no target) |
| ◆ energy crystal + ✧ purple amulet | **SCATTER & REBUILD** | Body detaches into autonomous shooting drones for **3.4 seconds**, then returns; COIL KILL unavailable while detached |
| ● gold coin + ✧ purple amulet | **LIZARD TAIL** | Last **5** segments detach into a decoy, attracting spiders; explode after **3 seconds**, then regrow |
| ✧ purple amulet + ✧ purple amulet | **CUT THE LINE** | Tail whip damages and knocks back enemies along the trailing body |
| Bite a **small spider mouth-first** | **FIREWORK SNAKE** | Instant firework, with **12-second** bite recharge |
| Press **BOOST** while making a sharp turn | **CUT THE LINE** | One whip per BOOST activation |

The older pale/white collectible crystal remains **metal (+2)**. The **cyan energy crystal** is a different item for morph recipes.

**Test result:** all nine waves, both level rewards, final boss, BUILD, COIL, normal bite and four powers were tested in a browser environment with no JavaScript errors. This is a playtest build; mobile feel and balancing remain to be refined.

**Recovery:** branch `backup/v11-before-morph-lab` retains the v1.1 build.

The live page is a self-contained HTML5 game: no separate asset server is necessary. The sprite atlases remain in `assets/` for future game development.

## v1.3 — BODY GROWTH & SEVERABLE SEGMENTS

**The primary objective is to grow your mechanical snake.** Your body is a tactical resource, and enemies can break it.

- **Start small and slow:** 6 physical body segments; movement begins at 54 units/s (previously 80), with small later-level progression and ENGINE module speed upgrades.
- **Collect green chassis blocks:** enemy kills can drop a green body segment; picking one up adds +1 segment. You also get a guaranteed +1 segment for standard wave completion and +2 as a level reward, up to **24** segments.
- **COIL KILL unlocks at 12 segments:** before that, loops cannot kill enemies. Dropping below 12 after damage locks COIL until regrowth. The HUD shows current length/12.
- **Enemies that sever segments:** from the end of Level 1 and then levels 2–3, heavy spiders, broodmothers, bosses and newly added **red-clawed CUTTER spiders** can bite a physical body segment. A successful bite shortens the snake by one. Segment losses have a cooldown to prevent an instant cascade.
- **Weapons can detach:** if the targeted segment carries a module, the installed module drops as a recoverable pickup with its current kind and upgrade level preserved. Pick it up and reinstall in **BUILD**. If the field inventory is full, the dropped module stays on the floor.
- **Actual weapon capacity depends on length:** you cannot install more modules than you have physical body slots (Merge still works normally). This gives tangible value to growth, while smaller builds remain maneuverable.
- **Long bodies empower existing transformations:** every extra segment adds a FIREWORK firing position and an independent SCATTER drone, while giving wider tactical coils and stronger spatial presence. LIZARD TAIL unlocks at 9 segments.
- **Safety:** start protection still applies in tutorial waves, and the minimum body is four segments. Existing BUILD, Merge, web slow, COIL, morph powers, three levels and bosses remain.

The previous version is preserved at branch `backup/v12-before-body-growth`. The playable game remains a self-contained `index.html`; green chassis icons are presently drawn directly to the pixel-art canvas.

## v1.4 — GRID MOVEMENT (experimental control mode)

Experimental build (not active on `main`): snake movement is **cell-by-cell**, like classic Snake, instead of free-angle steering.

- Playable board: **16 columns × 24 rows**, cell centers spaced **24 internal pixels** apart, with a matching visible grid.
- Four cardinal headings only (up, right, down, left). Direction changes happen instantly at the next tile boundary.
- **Mobile:** swipe on the arena or use the visible four-button D-pad. **Desktop:** arrow keys / WASD.
- As in classic Snake, a direct **180° reverse is disallowed**; use two 90° turns. You can queue up to two turns.
- **Walls:** stop the snake until a valid turn is chosen; wall contact does not cost HP.
- **BOOST, web slow, and ENGINE upgrades** affect the number of grid steps per second, not off-grid velocity.
- **Level 2 conveyors:** accelerate movement in their direction or slow it against the flow; they no longer displace the player between cells.
- The existing **COIL KILL** system uses the now-right-angled snake path, unlocked at 12 body segments.
- All other combat and workshop systems (3 levels, BUILD, Merge, Firework, Scatter, Lizard Tail, Cut the Line, segment severing) remain in place.

This is an experiment to compare play feel with v1.3. The previous free-motion build is preserved on branch `backup/v13-before-grid-movement`.
