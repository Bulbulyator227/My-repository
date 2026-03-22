# Тест-кейсы для API


## 1. POST /api/1/item – Создание объявления

### 1. Создание объявления с валидными данными (позитивный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST-запрос с телом 
`{
  "sellerID": "123466",
  "name": "Велик",
  "price": "500",
  "statistics": {
    "likes": "1",
    "viewCount": "1",
    "contacts": "1"
  }
}`.
- **Ожидаемый результат**:
  1. Код ответа 200.
  2. Объявление создано
  3. Отображен ответ c body в формате:
`{
  "id": "<string>",
  "sellerId": "<integer>",
  "name": "<string>",
  "price": "<integer>",
  "statistics": {
    "likes": "<integer>",
    "viewCount": "<integer>",
    "contacts": "<integer>"
  },
  "createdAt": "<string>"
}`

### 2. Создание объявления с минимальными граничными значениями (позитивный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с данными в теле  у всех полей, например `sellerID = 1`
- **Ожидаемый результат**:
  1. Код ответа 200.
  2. Объявление создано
  3. Отображен ответ c body в формате:
`{
  "id": "<string>",
  "sellerId": "<integer>",
  "name": "<string>",
  "price": "<integer>",
  "statistics": {
    "likes": "<integer>",
    "viewCount": "<integer>",
    "contacts": "<integer>"
  },
  "createdAt": "<string>"
}`

### 3. Создание объявления с максимальными граничными значениями (позитивный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с данными максимальной длины в теле у всех полей, например `sellerID = 123456` **Ожидаемый результат**:
  1. Код 200.
  2. Отображен ответ c body в формате:
`{
  "id": "<string>",
  "sellerId": "<integer>",
  "name": "<string>",
  "price": "<integer>",
  "statistics": {
    "likes": "<integer>",
    "viewCount": "<integer>",
    "contacts": "<integer>"
  },
  "createdAt": "<string>"
}`

### 4. Создание объявления с ценой в виде числа (позитивный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с данными `price = 100`.
- **Ожидаемый результат**:
  1. Код ответа 200.
  2. Объявление создано
  3. Отображен ответ c body в формате:
`{
  "id": "<string>",
  "sellerId": "<integer>",
  "name": "<string>",
  "price": 100,
  "statistics": {
    "likes": "<integer>",
    "viewCount": "<integer>",
    "contacts": "<integer>"
  },
  "createdAt": "<string>"
}`


### 5. Создание объявления без поля `statistics` (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с незаполненными полями `statistics` (только `sellerID`, `name`, `price`).
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 6. Создание объявления с отрицательным `sellerID` (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с данными `sellerID = -100`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 7. Создание объявления с отрицательной ценой (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с данными `price = -50`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 8. Создание объявления с пустым `name` (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с данными `name = ""`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 9. Создание объявления без обязательного поля `sellerID` (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос без данных `sellerID`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 10. Создание объявления без обязательного поля `name` (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос без данных `name`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 11. Создание объявления без обязательного поля `price` (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос без данных `price`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 12. Создание объявления с `sellerID` в виде строки (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с данными `sellerID = "123abc"`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 13. Создание объявления с `price` в виде строки (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с данными `price = "сто"`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`
### 14. Создание объявления с неверным `Content-Type` (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с валидными данными и заголовком `Content-Type: text/plain`
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 15. Создание объявления с невалидным JSON (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с валидными данными в теле без закрывающей скобки `{"sellerID": 123, "name": "Тест", "price": 100` 
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`
### 16. Создание объявления с дополнительным нестандартным полем (негативный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Отправить POST запрос с дополнительными полями `"extra": "data"` в теле.
- **Ожидаемый результат**:
  1. Код 400.
  2. Объявление не создано
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 17. Создание нескольких объявлений с одинаковым `sellerID` (позитивный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Создать 3 объявления с одним `sellerID`.
- **Ожидаемый результат**:
  1. Код ответа 200.
  2. Объявление создано
  3. Отображен ответ c body в формате:
`{
  "id": "<string>",
  "sellerId": "<integer>",
  "name": "<string>",
  "price": "<integer>",
  "statistics": {
    "likes": "<integer>",
    "viewCount": "<integer>",
    "contacts": "<integer>"
  },
  "createdAt": "<string>"
}`

### 18. Повторное создание точно такого же объявления (позитивный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json"; 
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Создать два объявления с идентичными данными в полях `sellerID`, `name`, `price`.
- **Ожидаемый результат**:
  1. Код ответа 200.
  2. Объявление создано
  3. Отображен ответ c body в формате:
`{
  "id": "<string>",
  "sellerId": "<integer>",
  "name": "<string>",
  "price": "<integer>",
  "statistics": {
    "likes": "<integer>",
    "viewCount": "<integer>",
    "contacts": "<integer>"
  },
  "createdAt": "<string>"
}`

---

## 2. GET /api/1/item/{id} – Получение объявления по UUID

### 19. Получение существующего объявления (позитивный)
- **Предусловие**: 
	1. Создано объявление с известным `id`.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/item/{id}` с заголовком `Accept: application/json`.
- **Ожидаемый результат**:
  1. Код 200.
  2. Полученный данные
  3. Отображен ответ c body в формате:
`{
    "id": "<string>",
    "sellerId": "<integer>",
    "name": "<string>",
    "price": "<integer>",
    "statistics": {
      "likes": "<integer>",
      "viewCount": "<integer>",
      "contacts": "<integer>"
    },
    "createdAt": "<string>"
  }`

### 20. Получение по несуществующему UUID (негативный)
- **Предусловие**: 
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/item/00000000-0000-0000-0000-000000000000`.
- **Ожидаемый результат**:
  1. Код 404.
  2. Данные не получены
  3. Отображен ответ c body в формате:
`{
  "result": "laborum",
  "status": "cillum enim eiusmod"
}`

### 21. Получение по невалидному формату (негативный)
- **Предусловие**: 
	1. Создано объявление  с известным `id`.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/item/123`
- **Ожидаемый результат**:
  1. Код 400.
  2. Дынные не получены 
  3. Отображен ответ cодержащий в body в формате:
`"ID айтема не UUID: <XXX>"`

### 22. Получение после удаления (негативный)
- **Предусловие**: 
	1. Создано объявление, затем удалено через DELETE /api/2/item/{id}.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/item/{id}`
- **Ожидаемый результат**:
  1. Код 404.
  2. Данные не получены
  3. Отображен ответ c body в формате:
`{
  "result": "laborum",
  "status": "cillum enim eiusmod"
}`

### 23. Получение без заголовка Accept (негативный)
- **Предусловие**: 
	1. Создано объявление с известным `id`.
- **Шаги**:
  1. Выполнить GET `/api/1/item/{id}` без заголовка `Accept`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Данные не получены
  3. Отображен ответ c body в формате:
`{
  "result": {
    "messages": {
      "culpa_b92": "<string>",
      "enim_24f": "<string>",
      "mollit_aa": "<string>"
    },
    "message": "<string>"
  },
  "status": "<string>"
}`

### 24. Идемпотентность (позитивный)
- **Предусловие**: 
	1. Создано объявление (POST) с известным `id`.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/item/{id}` дважды подряд.
- **Ожидаемый результат**:
  1. Код 200.
  2. Полученный данные
  3. Отображены идентичные ответы c body в формате:
`{
    "id": "<string>",
    "sellerId": "<integer>",
    "name": "<string>",
    "price": "<integer>",
    "statistics": {
      "likes": "<integer>",
      "viewCount": "<integer>",
      "contacts": "<integer>"
    },
    "createdAt": "<string>"
  }`


---
## 3. GET /api/1/statistic/{id} – Получение статистики по объявлению

### 25. Получение статистики существующего объявления (позитивный)
- **Предусловие**: 
	1. Создано объявление с известным `id`.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/statistic/{id}` с заголовком `Accept: application/json`.
- **Ожидаемый результат**:
  1. Код ответа 200.
  2. Объявление создано
  3. Отображен ответ c body в формате:
`{
   "likes": "<integer>",
   "viewCount": "<integer>",
   "contacts": "<integer>"
 }`


### 26. Получение статистики для нового объявления (позитивный)
- **Предусловие**: 
	1. Создано объявление с известным `id`.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/statistic/{id}`.
- **Ожидаемый результат**:
  1. Код ответа 200.
  2. Объявление создано
  3. Отображен ответ c body в формате:
`{
   "likes": "<integer>",
   "viewCount": "<integer>",
   "contacts": "<integer>"
 }`

### 27. Получение статистики по несуществующему UUID (негативный)
- **Предусловие**: 
	1. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/statistic/00000000-0000-0000-0000-000000000000`.
- **Ожидаемый результат**:
`{
  "result": "laborum",
  "status": "cillum enim eiusmod"
}`


### 28. Получение статистики по невалидному формату (негативный)
- **Предусловие**: 
	1. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/statistic/abc`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Сообщение об ошибке, например "ID айтема не UUID: <XXX>".

### 29. Получение статистики после удаления (негативный)
- **Предусловие**: 
	1. Создано объявление, затем удалено через DELETE /api/2/item/{id}.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/statistic/{id}`.
- **Ожидаемый результат**:
1. Код 400.
2. Данные не получены
3.Отображен ответ c body в формате:
`{
  "result": "laborum",
  "status": "cillum enim eiusmod"
}`


---

## 4. GET /api/1/{sellerId}/item – Получение всех объявлений продавца

### 30. Получение объявлений продавца с несколькими объявлениями (позитивный)
- **Предусловие**: 
	1. Создано 2 объявления с `sellerId = 123`.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/123/item` с заголовком `Accept: application/json`.
- **Ожидаемый результат**:
  1. Код 200.
  2. В ответе массив из 2 элементов, у каждого `sellerId = 123`.

### 31. Получение объявлений продавца без объявлений (позитивный)
- **Предусловие**: 
	1. Продавец с `sellerId = 1000000` не имеет объявлений.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/999999/item`.
- **Ожидаемый результат**:
  1. Код 200.
  2. Пустой массив

### 32. Получение с невалидным sellerId (не число) (негативный)
- **Предусловие**: 
	1. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/abc/item`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Сообщение об ошибке.

### 33. Получение с очень большим sellerId (позитивный)
- **Предусловие**: 
	1. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/999999999999/item`.
- **Ожидаемый результат**:
  1. Код 200.
  2. Пустой массив

### 34. Проверка, что возвращаются только объявления указанного продавца (позитивный)
- **Предусловие**: 
	1. Создано по 2 объявления для продавцов 111 и 222.
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить GET `/api/1/111/item`.
  2. Выполнить GET `/api/1/222/item`.
- **Ожидаемый результат**:
  1. Код 200.
  2. Первый ответ содержит в теле только объявления sellerId=111, второй – только sellerId=222.

---

## 5. DELETE /api/2/item/{id} – Удаление объявления

### 35. Удаление существующего объявления (позитивный)
- **Предусловие**: 
	1. Создано объявление с известным `id`.
	2. Accept:"application/json";
- **Шаги**:
  1. DELETE `/api/2/item/{id}` с заголовком `Accept: application/json`.
- **Ожидаемый результат**:
  1. Код 200 .

### 36. Повторное удаление того же объявления (негативный)
- **Предусловие**: 
	1. Объявление уже удалено (после теста 35).
	2. Accept:"application/json";
- **Шаги**:
  1. Выполнить DELETE ещё раз.
- **Ожидаемый результат**:
  1. Код 404.
  2. Тело ответа содержит информацию в формате 
`{
  "result": "laborum",
  "status": "cillum enim eiusmod"
}`

### 37. Удаление по несуществующему UUID (негативный)
- **Предусловие**: 
	1. Accept:"application/json";
- **Шаги**:
  1. DELETE `/api/2/item/00000000-0000-0000-0000-000000000000`.
- **Ожидаемый результат**:
  1. Код 404.
  2. Тело ответа содержит информацию в формате 
`{
  "result": "laborum",
  "status": "cillum enim eiusmod"
}`

### 38. Удаление по невалидному формату (негативный)
- **Предусловие**: 
	1. Accept:"application/json";
- **Шаги**:
  1. DELETE `/api/2/item/123`.
- **Ожидаемый результат**:
  1. Код 400.
  2. Сообщение об ошибке содержит текст "ID айтема не UUID".

### 39. Идемпотентность (позитивный)
- **Предусловие**: 
	1. Объявление удалено.
	2. Accept:"application/json";
- **Шаги**:
  1. После удаления повторить DELETE.
- **Ожидаемый результат**:
  1. Код 404.
  2. Тело ответа содержит информацию в формате 
`{
  "result": "laborum",
  "status": "cillum enim eiusmod"
}`

---

## 6. GET /api/2/statistic/{id} – Получение статистики (версия 2)

### 40. Получение статистики существующего объявления (позитивный)
- **Предусловие**: 
	1. Создано объявление с известным `id`.
	2. Accept:"application/json";
- **Шаги**:
  1. GET `/api/2/statistic/{id}` с заголовком `Accept: application/json`.
- **Ожидаемый результат**:
  1. Код 200.
  2. Отображен массив объектов

### 41. Получение статистики для несуществующего UUID (негативный)
- **Предусловие**: 
	1. Accept:"application/json";
- **Шаги**:
  1. GET `/api/2/statistic/00000000-0000-0000-0000-000000000000`.
- **Ожидаемый результат**:
  1. Код 404.
  2. Тело ответа содержит информацию в формате 
`{
  "result": "laborum",
  "status": "cillum enim eiusmod"
}`


### 42. Получение статистики для удалённого объявления (негативный)
- **Предусловие**: 
	1. Создано объявление, затем удалено через DELETE /api/2/item/{id}.
	2. Accept:"application/json";
- **Шаги**:
  1. GET `/api/2/statistic/{id}`.
- **Ожидаемый результат**:
  1. Код 404.
  2. Тело ответа содержит информацию в формате 
`{
  "result": "laborum",
  "status": "cillum enim eiusmod"
}`

---

## 7. Кросс-версионные и нефункциональные проверки

### 43. Согласованность статистики v1 и v2 (позитивный)
- **Предусловие**: 
	1. Создано объявление с известным `id`.
	2. Accept:"application/json";
- **Шаги**:
  1. GET `/api/1/statistic/{id}`.
  2. GET `/api/2/statistic/{id}`.
- **Ожидаемый результат**:
  1. Код 200 в обоих запросах.
  2. Тела ответов полностью идентичны.

### 44. Проверка времени ответа (Позитивный)
- **Предусловие**: 
	1. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Для каждого эндпоинта выполнить 10 запросов, измерить время.
- **Ожидаемый результат**:
  1. 95% запросов выполняются менее чем за 2 секунды.

### 45. Проверка формата UUID (позитивный)
- **Предусловие**: 
	1. Создано объявление с известным `id`.
	2. Accept:"application/json";
- **Шаги**:
  1. Извлечь `id` из ответа POST, проверить по регулярному выражению.
- **Ожидаемый результат**:
  1. `id` соответствует формату UUID v4 (8-4-4-4-12).

### 46. Проверка заголовка Accept (негативный)
- **Предусловие**: 
	1. Создано объявление с известным `id`.
- **Шаги**:
  1. Выполнить GET `/api/1/item/{id}` с заголовком `Accept: text/plain`.
- **Ожидаемый результат**:
  1. Код 406 
### 47. Валидация схемы ответа (позитивный)
- **Предусловие**: 
	1. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Для каждого эндпоинта проверить структуру JSON (наличие обязательных полей, типы).
- **Ожидаемый результат**:
  1. Ответ соответствует схеме, описанной в Postman-коллекции.

### 48. Удаление и повторное создание с тем же sellerId (позитивный)
- **Предусловие**: 
	1. Создано объявление, затем удалено через DELETE /api/2/item/{id}.
	2. Headers request: Content-typу:"application/json", Accept:"application/json";
	3. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. Создать новое объявление с тем же `sellerID`, что и удалённое.
- **Ожидаемый результат**:
  1. Код 200.
  2. Новое объявление создаётся успешно, `id` отличается.

### 49. Создание объявления с ценой, равной максимальному int (позитивный)
- **Предусловие**: 
	1. Headers request: Content-typу:"application/json", Accept:"application/json";
	2. base_url: `https://qa-internship.avito.com`
- **Шаги**:
  1. `price = 2147483647`.
- **Ожидаемый результат**:
  1. Код 200
