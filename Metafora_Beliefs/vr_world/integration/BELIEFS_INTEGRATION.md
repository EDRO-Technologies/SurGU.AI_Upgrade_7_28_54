# 🔗 ИНТЕГРАЦИЯ VR-МИРА С BELIEFS.CSV
## Система связи между виртуальным миром и базой данных убеждений

---

## 📋 ВАРИАНТЫ ИНТЕГРАЦИИ

### ВАРИАНТ 1: МИНИМАЛЬНАЯ ИНТЕГРАЦИЯ (MVP)
**Подходит для:** Быстрого запуска, прототипирования, тестирования концепции

#### Как работает:
1. **При входе в VR:**
   - Система читает beliefs.csv
   - Загружает последние 5-10 активных убеждений
   - Передаёт их AI-наставнику в контекст

2. **Во время сессии:**
   - AI использует данные для персонализации диалогов
   - Упоминает конкретные убеждения из базы
   - НЕ меняет beliefs.csv в реальном времени

3. **После выхода из VR:**
   - Система сохраняет краткий лог сессии
   - Записывает, какие убеждения обсуждались
   - Обновление beliefs.csv делается вручную коучем

#### Плюсы:
- ✅ Простая реализация
- ✅ Минимум технических рисков
- ✅ Можно запустить за 2-3 недели

#### Минусы:
- ❌ Нет реальной синхронизации
- ❌ Требует ручной работы после сессии
- ❌ Ограниченная персонализация

#### Технический стек:
```python
# Псевдокод
def start_vr_session(user_id):
    beliefs = load_beliefs_csv(user_id)
    active_beliefs = filter_by_status(beliefs, ["identified", "analyzing"])

    ai_context = {
        "user_beliefs": active_beliefs[:10],
        "personality_profile": load_personality(user_id)
    }

    launch_vr(ai_context)

def end_vr_session(session_data):
    save_session_log(session_data)
    # Ручное обновление beliefs.csv позже
```

---

### ВАРИАНТ 2: УМЕРЕННАЯ ИНТЕГРАЦИЯ (РЕКОМЕНДУЕТСЯ)
**Подходит для:** Полноценного продукта, баланса функциональности и сложности

#### Как работает:
1. **При входе в VR:**
   - Чтение beliefs.csv + personality_profile.md
   - Анализ текущего состояния убеждений
   - AI получает полный контекст пользователя

2. **Во время сессии:**
   - **Динамическая подсветка:**
     - В Площади Теней появляются тени с текстами из beliefs.csv (status="identified")
     - В Садах видны деревья ранее трансформированных убеждений
     - В Башне этажи соответствуют завершённым трансформациям

   - **AI адаптируется:**
     - Рекомендует локации на основе статуса убеждений
     - Задаёт вопросы, связанные с конкретными убеждениями

   - **Полуавтоматическое обновление:**
     - Когда пользователь "сажает дерево" → статус меняется на "transforming"
     - Когда завершает работу с тенью → статус "analyzed"
     - **НО:** критические изменения требуют подтверждения

3. **После выхода из VR:**
   - Система предлагает review изменений
   - Коуч/пользователь подтверждает обновления
   - beliefs.csv обновляется автоматически

#### Плюсы:
- ✅ Хороший баланс автоматизации и контроля
- ✅ Визуализация прогресса в реальном времени
- ✅ AI имеет полный контекст
- ✅ Безопасность (требуется подтверждение)

#### Минусы:
- ⚠️ Средняя сложность разработки (6-8 недель)
- ⚠️ Требует API между VR и beliefs.csv

#### Технический стек:
```python
# Backend API (FastAPI)
from fastapi import FastAPI
import pandas as pd

app = FastAPI()

@app.get("/api/beliefs/{user_id}")
def get_user_beliefs(user_id: str):
    df = pd.read_csv(f"data/{user_id}/beliefs.csv")
    return df.to_dict('records')

@app.post("/api/beliefs/{user_id}/update")
def update_belief(user_id: str, belief_id: str, new_status: str):
    # Temporary update (pending confirmation)
    return {"status": "pending_confirmation", "belief_id": belief_id}

@app.post("/api/session/end")
def confirm_session_changes(user_id: str, changes: list):
    # User/coach reviews and confirms
    # Then update beliefs.csv
    pass
```

```csharp
// Unity VR Client
public class BeliefsAPI : MonoBehaviour {
    private string apiUrl = "http://localhost:8000/api";

    public async Task<List<Belief>> LoadBeliefs(string userId) {
        string url = $"{apiUrl}/beliefs/{userId}";
        var response = await UnityWebRequest.Get(url).SendWebRequest();
        return JsonConvert.DeserializeObject<List<Belief>>(response.downloadHandler.text);
    }

    public void OnTreePlanted(Belief belief) {
        // Temporary status change in VR
        belief.status = "transforming";
        pendingChanges.Add(belief);
    }
}
```

---

### ВАРИАНТ 3: ПОЛНАЯ ИНТЕГРАЦИЯ (ADVANCED)
**Подходит для:** Долгосрочного продукта, максимальной автоматизации

#### Как работает:
1. **Реал-тайм синхронизация:**
   - VR-мир постоянно подключён к базе данных
   - Изменения применяются мгновенно (с валидацией AI)
   - Если AI уверен на 90%+, обновление автоматическое

2. **Умная визуализация:**
   - Мир "живёт" даже без пользователя:
     - Деревья растут между сессиями (на основе времени)
     - Башня добавляет этажи автоматически
     - Новые тени появляются при добавлении убеждений извне

3. **AI-ведомые изменения:**
   - AI анализирует диалог и определяет:
     - Когда убеждение идентифицировано
     - Когда пользователь готов к трансформации
     - Когда убеждение интегрировано
   - Предлагает обновления статуса в реальном времени

4. **Мультиплатформенность:**
   - Изменения из VR синхронизируются с веб-версией
   - Коуч может видеть прогресс в реальном времени
   - Возможна совместная сессия (коуч + клиент в VR)

#### Плюсы:
- ✅ Максимальная автоматизация
- ✅ Мир становится "живым"
- ✅ Возможности для коллаборации
- ✅ Полная аналитика

#### Минусы:
- ❌ Высокая сложность (3-4 месяца разработки)
- ❌ Риски с безопасностью данных
- ❌ Требует продвинутого AI
- ❌ Дороже в поддержке

#### Технический стек:
```python
# Backend (FastAPI + WebSocket + PostgreSQL)
from fastapi import FastAPI, WebSocket
import asyncio

app = FastAPI()

@app.websocket("/ws/vr/{user_id}")
async def vr_websocket(websocket: WebSocket, user_id: str):
    await websocket.accept()

    # Subscribe to belief changes
    async for message in websocket:
        event = parse_vr_event(message)

        if event.type == "shadow_touched":
            # AI analyzes interaction
            ai_confidence = analyze_belief_identification(event.dialogue)

            if ai_confidence > 0.9:
                # Auto-update
                update_belief_status(event.belief_id, "identified")
            else:
                # Request confirmation
                await websocket.send_json({
                    "action": "confirm_status_change",
                    "belief_id": event.belief_id,
                    "confidence": ai_confidence
                })
```

---

## 🗄️ СТРУКТУРА BELIEFS.CSV

### Текущая структура (предполагаемая):
```csv
id,belief_text,category,status,created_date,last_updated
1,"Я недостаточно хорош",limiting,identified,2025-10-15,2025-10-15
2,"Я заслуживаю успеха",supporting,transforming,2025-10-16,2025-10-18
```

### Рекомендуемая расширенная структура для VR:
```csv
id,belief_text,category,status,created_date,last_updated,vr_location,vr_visualized_as,growth_stage,transformation_progress
1,"Я недостаточно хорош",limiting,identified,2025-10-15,2025-10-15,plaza_shadows,shadow_01,null,0
2,"Я заслуживаю успеха",supporting,transforming,2025-10-16,2025-10-18,gardens,tree_03,young_plant,45
3,"Мои ошибки — опыт",supporting,integrated,2025-10-10,2025-10-18,tower,floor_2,flowering,100
```

#### Новые поля:
- **vr_location:** Где убеждение визуализируется (plaza_shadows, gardens, tower, etc.)
- **vr_visualized_as:** ID визуального объекта в VR (shadow_01, tree_03, floor_2)
- **growth_stage:** Для Садов Метаморфоз (seed, sprout, young_plant, tree, flowering)
- **transformation_progress:** 0-100% (для визуализации роста)

---

## 🎮 ПРИМЕРЫ ИНТЕГРАЦИИ ПО ЛОКАЦИЯМ

### 1. ПЛОЩАДЬ ТЕНЕЙ → beliefs.csv

#### При входе в локацию:
```python
# Загрузить убеждения со статусом "limiting" или "identified"
limiting_beliefs = df[df['status'].isin(['limiting', 'identified'])]

# Создать тени в VR
for belief in limiting_beliefs:
    spawn_shadow(
        position=random_position(),
        text=belief['belief_text'],
        belief_id=belief['id']
    )
```

#### При взаимодействии с тенью:
```python
# Пользователь касается тени
def on_shadow_touched(shadow):
    belief = get_belief(shadow.belief_id)

    # AI начинает диалог
    ai_dialogue(belief.text)

    # После диалога → обновление статуса
    if user_confirmed_awareness():
        update_belief(belief.id, status="analyzed")
        shadow.become_transparent()  # Визуальная обратная связь
```

---

### 2. САДЫ МЕТАМОРФОЗ → beliefs.csv

#### При входе в локацию:
```python
# Загрузить убеждения со статусами "transforming" и "integrated"
transforming = df[df['status'] == 'transforming']
integrated = df[df['status'] == 'integrated']

# Создать деревья
for belief in transforming:
    plant_tree(
        stage=belief['growth_stage'],
        label=belief['belief_text'],
        progress=belief['transformation_progress']
    )

for belief in integrated:
    plant_tree(
        stage="flowering",
        label=belief['belief_text'],
        progress=100
    )
```

#### При посадке нового дерева:
```python
def on_tree_planted(belief_text):
    # Создать новое убеждение
    new_belief = {
        'id': generate_id(),
        'belief_text': belief_text,
        'category': 'supporting',
        'status': 'transforming',
        'vr_location': 'gardens',
        'growth_stage': 'seed',
        'transformation_progress': 0
    }

    add_belief_to_csv(new_belief)
    spawn_seed_in_vr(new_belief)
```

#### Рост дерева между сессиями:
```python
# Cron job (запускается каждый день)
def update_tree_growth():
    transforming_beliefs = df[df['status'] == 'transforming']

    for belief in transforming_beliefs:
        days_since_planted = (today - belief['created_date']).days

        # Обновление стадии роста
        if days_since_planted >= 14:
            belief['growth_stage'] = 'flowering'
            belief['transformation_progress'] = 100
            belief['status'] = 'integrated'
        elif days_since_planted >= 7:
            belief['growth_stage'] = 'tree'
            belief['transformation_progress'] = 70
        elif days_since_planted >= 3:
            belief['growth_stage'] = 'young_plant'
            belief['transformation_progress'] = 40
        elif days_since_planted >= 1:
            belief['growth_stage'] = 'sprout'
            belief['transformation_progress'] = 15

        update_belief_in_csv(belief)
```

---

### 3. БАШНЯ ПЕРСПЕКТИВЫ → beliefs.csv

#### При входе в башню:
```python
# Загрузить все трансформированные убеждения
integrated_beliefs = df[df['status'] == 'integrated']

# Построить этажи
tower_height = len(integrated_beliefs)

for i, belief in enumerate(integrated_beliefs, start=1):
    create_floor(
        floor_number=i,
        belief_text=belief['belief_text'],
        transformation_date=belief['last_updated'],
        color=get_color_by_category(belief['category'])
    )
```

---

### 4. ВОКЗАЛ ВЫБОРА → beliefs.csv

#### При входе на вокзал:
```python
# Загрузить убеждение, которое сейчас анализируется
current_belief = df[df['status'] == 'analyzing'].iloc[0]

# Сгенерировать альтернативные убеждения (AI)
alternatives = ai_generate_alternatives(current_belief['belief_text'])

# Показать на табло платформ
for i, alt in enumerate(alternatives, start=1):
    display_on_platform(
        platform_number=i,
        belief_text=alt,
        departure_status="NOW" if alt.confidence > 0.8 else "SOON"
    )
```

#### При выборе платформы:
```python
def on_platform_chosen(platform_number, new_belief_text):
    # Пользователь выбрал новое убеждение
    old_belief_id = get_current_analyzing_belief()

    # Обновить статус старого
    update_belief(old_belief_id, status="replaced")

    # Создать новое
    new_belief = {
        'id': generate_id(),
        'belief_text': new_belief_text,
        'category': 'supporting',
        'status': 'chosen',
        'vr_location': 'station',
        'created_date': today
    }

    add_belief_to_csv(new_belief)

    # Визуальный эффект: поезд прибывает
    train_arrival_animation(platform_number)
```

---

## 📊 DASHBOARD ДЛЯ КОУЧА

### Веб-интерфейс для мониторинга:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Метафора VR - Dashboard</title>
</head>
<body>
    <h1>Прогресс клиента: Иван Иванов</h1>

    <div class="stats">
        <div class="stat-card">
            <h3>Трансформировано убеждений</h3>
            <p class="big-number">7</p>
        </div>

        <div class="stat-card">
            <h3>Время в VR</h3>
            <p class="big-number">12ч 30м</p>
        </div>

        <div class="stat-card">
            <h3>Текущая локация</h3>
            <p>Сады Метаморфоз</p>
        </div>
    </div>

    <div class="beliefs-table">
        <h2>Активные убеждения</h2>
        <table>
            <tr>
                <th>Убеждение</th>
                <th>Статус</th>
                <th>VR-локация</th>
                <th>Прогресс</th>
            </tr>
            <tr>
                <td>Я заслуживаю успеха</td>
                <td>transforming</td>
                <td>Сады (дерево #3)</td>
                <td>
                    <div class="progress-bar">
                        <div class="progress" style="width: 45%"></div>
                    </div>
                    45%
                </td>
            </tr>
        </table>
    </div>

    <div class="vr-world-preview">
        <h2>Мир клиента</h2>
        <img src="/api/world-snapshot/user123" alt="VR World">
        <p>Последнее обновление: 2 минуты назад</p>
    </div>
</body>
</html>
```

---

## 🔒 БЕЗОПАСНОСТЬ И ПРИВАТНОСТЬ

### Принципы:
1. **Шифрование:** Все данные beliefs.csv шифруются (AES-256)
2. **Локальное хранение:** По умолчанию данные на устройстве пользователя
3. **Опциональная синхронизация:** Облако только с явного согласия
4. **Анонимизация:** AI не имеет доступа к личным данным (имя, email, etc.)
5. **Право на удаление:** Пользователь может удалить все данные одной кнопкой

---

## 📝 РЕКОМЕНДАЦИЯ

**Для MVP выбирайте ВАРИАНТ 2 (Умеренная интеграция)**

Почему:
- ✅ Даёт визуализацию прогресса (главная ценность VR)
- ✅ Сохраняет контроль (требуется подтверждение)
- ✅ Реализуемо за 6-8 недель
- ✅ Можно масштабировать до Варианта 3 позже

---

**Следующие шаги:**
1. Определиться с вариантом интеграции
2. Создать прототип API
3. Разработать систему синхронизации
4. Тестирование на 5-10 пользователях
