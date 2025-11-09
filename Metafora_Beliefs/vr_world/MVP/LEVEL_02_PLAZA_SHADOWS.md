# 🌑 LEVEL 2: ПЛОЩАДЬ ТЕНЕЙ (Piazza delle Ombre)

> *"В каждой тени живёт часть тебя, которую ты боишься увидеть. Но только встретившись с ней лицом к лицу, ты обретёшь целостность."*

---

## 📖 ПРОЛОГ

**Контекст:**
Переход из Level 1. Fade from white. Постепенно проявляется более тёмное пространство. Контрастные тени. Холоднее. Напряжённее.

**Голос AI (более серьёзный тон):**
```
"Добро пожаловать в Площадь Теней... [пауза 3 сек]
Здесь живут твои страхи... [пауза 4 сек]
Не бойся... Тени — это тоже ты... [пауза 3 сек]
Просто посмотри на них..."
```

**Визуал:**
- Появление в центре площади
- Вокруг — движущиеся тени
- AI материализуется рядом

**Цель пролога:**
- Создать атмосферу безопасного страха
- Подготовить к работе с ограничивающими убеждениями
- Объяснить механику "живых теней"

**Продолжительность:** 2-3 минуты

---

## 🎬 ЭПИЛОГ

**Контекст:**
Пользователь проработал 2-3 убеждения. Тени стали полупрозрачными (осознанными).

**Голос AI:**
```
"Ты увидел свои тени... [пауза 3 сек]
И они больше не пугают тебя так сильно... [пауза 4 сек]
Это важный шаг... [пауза 2 сек]
Теперь давай посмотрим, откуда они пришли... [пауза 3 сек]
Портал в Аркаду Времени открыт..."
```

**Переход:**
- Портал #2 появляется в конце аркады
- Fade to sepia (цвет прошлого)
- Load Level 3

---

## 🎮 МЕХАНИКА УРОВНЯ

### Основные механики:

#### 1. ЖИВЫЕ ТЕНИ
- **Поведение:** Тени отделяются от объектов и движутся независимо
- **Триггер:** При приближении игрока (5м) тень "замечает" и поворачивается
- **Взаимодействие:**
  1. Наведение → тень пульсирует
  2. Клик → тень замирает, появляется текст убеждения из beliefs.csv
  3. AI начинает диалог об этом убеждении

#### 2. КНИГА ТЕНЕЙ
- **Расположение:** На постаменте в центре
- **Функция:** Показывает список всех ограничивающих убеждений
- **Интерактивность:**
  - Открыть книгу → страницы перелистываются
  - Каждая страница = одно убеждение
  - Клик на убеждение → соответствующая тень подсвечивается

#### 3. ЗЕРКАЛО-ПОРТАЛ
- **Функция:** Показывает "теневое я"
- **Механика:**
  - Посмотреть в зеркало → видишь темную версию себя
  - AI: "Что тебе не нравится в этом отражении?"
  - Долгий взгляд (10 сек) → инсайт-вопросы

#### 4. ОБЕЛИСКИ
- **Количество:** 5 штук
- **Функция:** Marker points для навигации
- **Символы:** При приближении светятся древние знаки
- **Интерактивность:** Касание → короткая мудрость о тенях

### Прогрессия:

```
1. Вход → Ориентация (1 мин)
   ↓
2. AI объясняет механику теней (1 мин)
   ↓
3. Первая тень — tutorial взаимодействия (2-3 мин)
   ↓
4. Свободное исследование — 2-3 тени (10-15 мин)
   ↓
5. Книга Теней — review проработанного (2 мин)
   ↓
6. Портал #2 открывается → Эпилог (1 мин)
   ↓
7. Переход на Level 3
```

---

## 🗺️ ASCII-КАРТА УРОВНЯ

```
═══════════════════════════════════════════════════════════════
                    LEVEL 2: ПЛОЩАДЬ ТЕНЕЙ
                         (40m x 60m)
═══════════════════════════════════════════════════════════════

    🌀 Вход (из Level 1)
         │
         ▼
┌────────────────────────────────────────────────────────┐
│ АРКАДА БЕСКОНЕЧНОСТИ (левая сторона)                   │
│ ▓▓  ▓▓  ▓▓  ▓▓  ▓▓  ▓▓  ▓▓  ▓▓ ...∞                  │
│ ║   ║   ║   ║   ║   ║   ║   ║                        │
│                                                        │
│     💀           ⚫ SPAWN         👤                   │
│  ОБЕЛИСК 1      POINT         ТЕНЬ #1                │
│                                                        │
│                                                        │
│  👤         ┌─────────────┐          👤               │
│ ТЕНЬ #2     │  КНИГА      │       ТЕНЬ #3            │
│             │  ТЕНЕЙ      │                           │
│             │  на пост.   │         💀                │
│             └─────────────┘      ОБЕЛИСК 2           │
│                                                        │
│        🔮 AI                                          │
│                                                        │
│  💀                                    👤             │
│ ОБЕЛИСК 3        👤                 ТЕНЬ #5          │
│                ТЕНЬ #4                                │
│                                                        │
│                                    💀                 │
│           ┌──────────┐         ОБЕЛИСК 4             │
│           │ ЗЕРКАЛО- │                                │
│           │ ПОРТАЛ   │         👤                     │
│           │  ╔════╗  │       ТЕНЬ #6                 │
│           │  ║ 👁  ║  │                                │
│           │  ╚════╝  │       💀                       │
│           └──────────┘    ОБЕЛИСК 5                  │
│                                                        │
│                                                        │
│                         🌀 ПОРТАЛ #2                  │
│                      (в Аркаду Времени)               │
│                    (открывается после                 │
│                     работ�� с тенями)                  │
└────────────────────────────────────────────────────────┘
                                         │
                         СТЕНА ОТРАЖЕНИЙ │
                         ════════════════╝
                         Тёмная поверхность
                         отражает теневые
                         двойники

ЛЕГЕНДА:
▓▓ — Колонны аркады (бесконечные)
👤 — Теневые фигуры (6-10 штук, интерактивные)
💀 — Обелиски с символами
🔮 — AI-наставник
╔═╗ — Зеркало-портал
🌀 — Порталы (вход/выход)
⚫ — Точка появления игрока

ЗОНЫ:
[A] Входная зона — адаптация к темноте
[B] Аркада Бесконечности — левая сторона
[C] Центральная зона — Книга Теней + AI
[D] Зона зеркала — глубинная работа
[E] Стена Отражений — правая сторона
[F] Выходная зона — портал #2

═══════════════════════════════════════════════════════════════
```

---

## 🎨 MIDJOURNEY ПРОМПТЫ

### Промпт 1: Общий вид Площади Теней
```
Dark metaphysical plaza in Giorgio de Chirico style, dramatic high
contrast shadows dominating the scene, rows of infinite colonnade
receding into darkness on the left, mysterious shadow figures detached
from their sources standing independently, obsidian obelisks with
glowing ancient symbols, dark grey and deep purple tones, ominous
yet safe atmosphere, central book on pedestal emanating soft glow,
harsh directional lighting creating impossible shadow geometry,
VR environment, unreal engine, moody cinematic --ar 16:9 --stylize 800 --v 6
```

### Промпт 2: Живая тень с текстом убеждения
```
A sentient shadow figure standing upright in a de Chirico metaphysical
space, shadow is detached from any object and moves independently,
semi-transparent dark silhouette with soft edges, glowing text in
Russian floating beside it reading "Я недостаточно хорош", ethereal
particles emanating from shadow, dark purple and black tones,
dramatic lighting, sense of confronting inner fears, VR game asset,
cinematic atmosphere --ar 9:16 --stylize 750 --v 6
```

### Промпт 3: Зеркало-портал с тёмным отражением
```
An ornate dark mirror portal in metaphysical plaza, showing distorted
shadowy reflection of viewer's silhouette, mirror frame is aged bronze
with cryptic engravings, reflection shows darker version of self with
glowing eyes, surrounded by swirling dark particles and purple mist,
de Chirico aesthetic, ominous but transformative energy, VR interactive
object, dramatic rim lighting --ar 9:16 --stylize 800 --v 6
```

---

## 🎥 ПРОМПТЫ ДЛЯ ВИДЕО

### Видео 1: Вход на Площадь Теней (8 сек)
```
Camera motion: Fade from white to darkness, slow dolly forward
Scene: Midjourney image of dark plaza
Movement: Camera emerges from portal, shadows start to move and
separate from columns, player POV looking around nervously
Speed: Slow (0.7x)
Effects: Vignette closing in, particle dust, shadows animating
Audio: Low drone, distant whispers
Purpose: Establish foreboding atmosphere
```

### Видео 2: Тень оживает и показывает текст (10 сек)
```
Camera motion: Fixed, focused on shadow figure
Scene: Midjourney shadow with belief text
Movement: Shadow slowly turns toward camera, text materializes
letter by letter beside it, shadow pulsates with breathing rhythm
Speed: Normal (1x)
Effects: Text glow, particle trails from shadow, subtle distortion
Audio: Whisper crescendo, typewriter effect for text
Purpose: Demonstrate core mechanic
```

### Видео 3: Зеркало показывает тёмное отражение (12 сек)
```
Camera motion: Slow push in toward mirror, slight orbit
Scene: Midjourney mirror image
Movement: Reflection becomes clearer, dark version of player
appears with glowing eyes, mirror ripples like water
Speed: Slow build to medium (0.8x → 1.0x)
Effects: Reflection distortion, purple mist swirl, eye glow pulse
Audio: Eerie hum, heartbeat bass, mirror resonance
Purpose: Teaser for deep shadow work
```

---

## 📦 СПИСОК АССЕТОВ

### 3D МОДЕЛИ

```
1. Колонны аркады (левая сторона)
   - Полигоны: 1,500 каждая × 15 = 22,500
   - Текстура: 1024x1024 (темнее, чем в Level 1)
   - LOD: 3 уровня

2. Обелиски (5 штук)
   - Полигоны: 3,000 каждый = 15,000
   - Текстура: 1024x1024 с glow map
   - Символы: Animated shader (pulsing)

3. Книга Теней
   - Полигоны: 3,000
   - Текстура: 2048x2048 (aged leather)
   - Анимация: Page turning (10 frames)
   - Интерактивность: Page flip sound + haptic

4. Зеркало-портал
   - Полигоны: 4,000
   - Текстура: 1024x1024 (frame) + realtime reflection
   - Shader: Distortion + dark tint
   - VFX: Purple mist particles

5. Теневые фигуры (6-10 штук)
   - Полигоны: 2,000 каждая = 12,000-20,000
   - Shader: Transparent black + soft edges
   - Анимация: Idle sway, turn toward player
   - Интерактивность: Text display trigger

6. Постамент для книги
   - Полигоны: 1,500
   - Текстура: 1024x1024 (dark stone)

7. Стена Отражений
   - Полигоны: 5,000
   - Текстура: 1024x2048 (dark reflective surface)
   - Shader: Glossy black + distorted reflections
```

### ТЕКСТУРЫ

```
8. Skybox (ночное небо)
   - Разрешение: 2048x2048
   - Цвет: Deep purple → black gradient
   - Звёзды: Subtle, не яркие

9. Lightmap (драматичное освещение)
   - Разрешение: 2048x2048
   - Тени: Очень контрастные, длинные
   - Ambient: Dark purple

10. Glow maps
    - Обелиски: 512x512 (символы светятся)
    - Книга: 512x512 (страницы светятся)
    - Тени: Procedural glow
```

### АУДИО

```
11. Ambient track
    - Drone: 30Hz bass, unsettling
    - Whispers: Multi-layered, unintelligible
    - Duration: 5 minutes loop
    - Format: OGG 96kbps mono

12. AI голос — фразы для Level 2
    - Количество: 20 фраз
    - Тон: Более серьёзный, глубокий
    - Reverb: Cathedral + low-pass filter

13. SFX:
    - Shadow whoosh (движение тени): 3 вариации
    - Book page turn: 5 вариаций
    - Obelisk hum: Seamless loop
    - Mirror resonance: 1 sound
    - Text appear: Typewriter effect
    - Format: OGG 96kbps
```

### VFX

```
14. Shadow particles
    - Количество: 200-500 на тень
    - Shader: Additive black (да, это возможно)
    - Movement: Slow upward drift

15. Obelisk symbol glow
    - Particle system: 100 частиц
    - Color: Purple → white pulse
    - Duration: 2 sec cycle

16. Mirror distortion
    - Post-process effect
    - Radial blur + chromatic aberration
    - Triggered on gaze

17. Portal #2 effect
    - Similar to Level 1, but sepia-tinted
    - 1000 частиц
```

---

## 🛠️ ТЗ ДЛЯ LEVEL DESIGNER

### ЗАДАЧА
Создать **Level 2: Площадь Тене��** — пространство для безопасной встречи со страхами и ограничивающими убеждениями.

### ЦЕЛИ УРОВНЯ

#### Обучающие:
- ✅ Научить работе с интерактивными тенями
- ✅ Познакомить с Книгой Теней (UI для beliefs.csv)
- ✅ Показать механику осознания убеждений

#### Эмоциональные:
- ✅ Создать атмосферу "безопасного страха"
- ✅ Помочь экстернализировать внутренние страхи (тени = внешние объекты)
- ✅ Дать ощущение контроля над тенями (можно заморозить, осознать)

#### Психологические:
- ✅ Работа с 2-3 ограничивающими убеждениями из beliefs.csv
- ✅ Практика сократического диалога с AI
- ✅ Первый шаг трансформации: identified → analyzed

### REFERENCE

**Визуал:**
- Giorgio de Chirico — "The Enigma of a Day" (1914)
- Film Noir lighting (high contrast shadows)
- "Limbo" game (shadow aesthetics)

**Психология:**
- Carl Jung — Shadow Work
- Acceptance and Commitment Therapy (ACT) — cognitive defusion

### ОСВЕЩЕНИЕ

- **Один жёсткий источник:** Создаёт контрастные тени
- **Цвет:** Cold white with purple tint
- **Тени:** 90% чёрные, 10% deep purple (для драмы)
- **Ambient:** Very dark (#1A1A2E)

### SOUND DESIGN

```
Ambient layers:
├─ Base drone: 30Hz, -18dB
├─ Whisper layer: Panned left-right, -24dB
├─ Wind: Intermittent, -30dB
└─ Reverb: Large Cathedral, 4sec decay

Interactive sounds:
├─ Shadow interaction: -12dB, 3D positioned
├─ Book pages: -15dB, stereo
├─ AI voice: -6dB, 3D from AI position
└─ Portal hum: -20dB → -10dB (distance-based)
```

### PERFORMANCE

- **Полигоны:** ~97,000 (в бюджете)
- **Draw calls:** < 120
- **Тени:** Baked (тени от теней = real-time, но cheap)
- **FPS:** 90 stable на Quest 3

### ИНТЕГРАЦИЯ С BELIEFS.CSV

```python
# При входе в уровень
limiting_beliefs = load_beliefs(status="identified", category="limiting")

# Создать тени
for belief in limiting_beliefs[:10]:  # Максимум 10 теней
    spawn_shadow(
        text=belief.text,
        position=random_position(),
        id=belief.id
    )

# При взаимодействии
def on_shadow_clicked(shadow):
    # Заморозить тень
    shadow.freeze()

    # Показать текст
    display_belief_text(shadow.belief_id)

    # AI диалог
    ai_start_dialogue(shadow.belief_id)

    # После диалога
    update_belief_status(shadow.belief_id, "analyzed")
    shadow.make_transparent(0.5)  # Полупрозрачная = осознанная
```

### ТЕСТИРОВАНИЕ

```
ЭМОЦИОНАЛЬНЫЙ ТЕСТ:
☐ Уровень вызывает лёгкое напряжение, но не страх
☐ Тени кажутся "живыми", но не агрессивными
☐ После работы с тенью — ощущение облегчения
☐ Не вызывает motion sickness

ГЕЙМПЛЕЙ:
☐ Тени реагируют на приближение плавно
☐ Текст убеждения читабелен (размер, контраст)
☐ AI диалог логично связан с убеждением
☐ Книга Теней открывается корректно

ПРОИЗВОДИТЕЛЬНОСТЬ:
☐ 90 FPS на Quest 3
☐ Тени не создают FPS drops
☐ Освещение не слишком тёмное (читабельность)
```

---

**Level Designer:** [Ваше имя]
**Дата:** 19.10.2025
**Версия:** 1.0 MVP
**Статус:** Ready for Production
