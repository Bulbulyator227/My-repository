### 1. При отправке запроса POST для /api/1/item тело ответа в случае успеха не соответствует примеру из "Success response"

**Краткое описание:**
При отправке запроса POST для /api/1/item тело ответа в случае успеха содержит значение `{"status": "Сохранили объявление - 04028fe6-8a47-43df-8f17-4ee7d984a0e9"}`


**Шаги воспроизведения:**
1. Открыть "Postman"
1. Нажать на раздел "Collections"
1. открыть коллекцию "qa-intership Copy 2"
1. Перейти по пути "api/1/items/{id}/Сохранить объявление"
1. Перейти на вкладку "Body" ввести значение 
`{"sellerID": 123456, "name": "Велик", "price": 500, "statistics": {"likes": 1, "viewCount": 1, "contacts": 1}}`
1. Нажать кнопку "Send"

**Фактический результат**
В body ответа отображено значение `{"status": "Сохранили объявление - 04028fe6-8a47-43df-8f17-4ee7d984a0e9"}`

**Ожидаемый результат**
В body ответа отображено значение в формате {"id": "<string>", "sellerId": "<integer>", "name": "<string>", "price": "<integer>", "statistics": {"likes": "<integer>", "viewCount": "<integer>", "contacts": "<integer>"}, "createdAt": "<string>"}

**Серьезность**: высокая

**Окружение**: Windows 11 Pro 25H2, Сборка ОС 26200.8037, Postman: 11.89.0

---

### 2. При отправке запроса POST для /api/1/item тело ответа в случае успеха не соответствует примеру из "Bad request"


**Краткое описание:**
При отправке запроса POST для /api/1/item тело без объекта `statistics` ответа в случае неуспеха содержит значение `{"result": {"message": "поле likes обязательно", "messages": {}}, "status": "400"}`

**Шаги воспроизведения:**
1. Открыть "Postman"
1. Нажать на раздел "Collections"
1. открыть коллекцию "qa-intership Copy 2"
1. Перейти по пути "api/1/items/{id}/Сохранить объявление"
1. Перейти на вкладку "Body" ввести значение 
`{"sellerID": 123456, "name": "Велик", "price": 500}`
1. Нажать кнопку "Send"

**Фактический результат**
В body ответа отображено значение `{"result": {"message": "поле likes обязательно", "messages": {}}, "status": "400"}`

**Ожидаемый результат**
В body ответа отображено значение `{"result": {"messages": {"culpa_b92": "<string>", "enim_24f": "<string>", "mollit_aa": "<string>"}, "message": "<string>"}, "status": "<string>"}`

**Серьезность**: высокая

**Окружение**: Windows 11 Pro 25H2, Сборка ОС 26200.8037, Postman: 11.89.0

---

### 3. При отправке запроса GET для /api/1/item и /api/2/item в случае успеха содержит значение в формате `[ { "createdAt": "<string>", "id": "<string>", "name": "<string>", "price": "<integer>", "sellerId": "<integer>", "statistics": { "contacts": "<integer>", "likes": "<integer>", "viewCount": "<integer>" } } ]`


**Краткое описание:**
При отправке запроса GET для /api/1/item в случае успеха содержит значение отличное от example в формате `{ "createdAt": "<string>", "id": "<string>", "name": "<string>", "price": "<integer>", "sellerId": "<integer>", "statistics": { "contacts": "<integer>", "likes": "<integer>", "viewCount": "<integer>" } }`


**Шаги воспроизведения:**
1. Открыть "Postman"
1. Нажать на раздел "Collections"
1. открыть коллекцию "qa-intership Copy 2"
1. Перейти по пути  "api/1/items/{id}/Получить объявление по идентификатору"
1. Добавить на вкладке "Params" существующий ID
1. Нажать кнопку "Send"

**Фактический результат**
В body ответа отображено значение в формате `[ { "createdAt": "<string>", "id": "<string>", "name": "<string>", "price": "<integer>", "sellerId": "<integer>", "statistics": { "contacts": "<integer>", "likes": "<integer>", "viewCount": "<integer>" } } ]`


**Ожидаемый результат**
В body ответа отображено значение в формате `{ "id": "<string>", "sellerId": "<integer>", "name": "<string>", "price": "<integer>", "statistics": { "likes": "<integer>", "viewCount": "<integer>", "contacts": "<integer>" }, "createdAt": "<string>" },`

**Серьезность**: низкая

**Окружение**: Windows 11 Pro 25H2, Сборка ОС 26200.8037, Postman: 11.89.0


---

### 4. При отправке запроса GET без заголовка Accept:application/json для /api/1/item отображен успех


**Краткое описание:**
При отправке запроса GET без заголовка Accept:application/json для /api/1/item отображен успех

**Шаги воспроизведения:**
1. Открыть "Postman"
1. Нажать на раздел "Collections"
1. открыть коллекцию "qa-intership Copy 2"
1. Перейти по пути  "api/1/items/{id}/Получить объявление по идентификатору"
1. Удалить на вкладке "Params" заголовок "Accept"
1. Нажать кнопку "Send"

**Фактический результат**
В body ответа отображен статус запроса 200

**Ожидаемый результат**
В body ответа отображен статус запроса 400

**Серьезность**: высокая

---

### 5. В коллекции для `GET /api/2/statistic/:id` присутствует пример ответа с кодом 100 (Continue)

**Краткое описание:**  
В коллекции для `GET /api/2/statistic/:id` присутствует пример ответа с кодом 100 (Continue)

**Шаги воспроизведения:**
1. Открыть "Postman"
1. Нажать на раздел "Collections"
1. открыть коллекцию "qa-intership Copy 2"
1. Перейти по пути  "/api/2/statistic/{id}/GET"

**Фактический результат**
Отображен example "Continue"

**Ожидаемый результат**
не отображен example "Continue"

**Серьезность**: низкая

**Окружение**: Windows 11 Pro 25H2, Сборка ОС 26200.8037, Postman: 11.89.0

