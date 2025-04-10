# **Официальный учебник по PowerShine 2.0**  
*(Полное руководство с синтаксисом .pshn)*  

---

## **Содержание**  
1. [Введение в PowerShine](#1-введение-в-powershine)  
2. [Установка](#2-установка)  
3. [Синтаксис и структура](#3-синтаксис-и-структура)  
4. [Типы данных](#4-типы-данных)  
5. [Супер-функции](#5-супер-функции)  
6. [Классы и объекты](#6-классы-и-объекты)  
7. [Работа с данными](#7-работа-с-данными)  
8. [Модули](#8-модули)  
9. [Обработка ошибок](#9-обработка-ошибок)  
10. [Многопоточность](#10-многопоточность)  
11. [Компиляция](#11-компиляция)  
12. [Примеры](#12-примеры)  

---

## **1. Введение в PowerShine**  
**PowerShine** — современный язык с:  
- **Высокоуровневым синтаксисом** (подобно Python)  
- **Нативной производительностью** (через LLVM)  
- **Уникальными фичами**:  
  - Реактивные переменные  
  - Встроенные веб-хуки  
  - Безопасная работа с памятью  

```pshn
power [demo] then  
    Print-n["Привет, PowerShine 2.0!"]  
end_power
```

---

## **2. Установка**  
### **2.1. Инсталляция**  
```bash
jpik install powershine --stable
```  
### **2.2. Проверка**  
```bash
pshn --version
> PowerShine 2.0.3 (LLVM 15)
```

---

## **3. Синтаксис и структура**  
### **3.1. Основные блоки**  
```pshn
power [program_id] then  
    @ Код программы  
    Run.power [exit_code]  
end_power  
```

### **3.2. Комментарии**  
```pshn
@ Однострочный  
` Многострочный  
  комментарий `  
```

---

## **4. Типы данных**  
### **4.1. Базовые типы**  
| Тип       | Пример          | Описание            |  
|-----------|----------------|---------------------|  
| `int`     | `42`           | Целое число         |  
| `float`   | `3.14`         | Число с плавающей точкой |  
| `str`     | `"текст"`      | Строка (UTF-8)      |  
| `bool`    | `yes` / `no`   | Логический тип      |  

### **4.2. Специальные типы**  
```pshn
json_data: dict = {"key": "value"}  
opt_data: maybe[str] = some["data"] | none  
```

---

## **5. Супер-функции**  
*(Аналог функций в других языках)*  
### **5.1. Базовый синтаксис**  
```pshn
super greet[name: str] -> str then  
    return "Привет, #{name}!"  
end_super  
```

### **5.2. Лямбды**  
```pshn
square = [x] => x * x  
```

---

## **6. Классы и объекты**  
### **6.1. Классы**  
```pshn
object User[name: str] then  
    field name = name  
    
    super introduce[] then  
        Print-n["Меня зовут #{name}"]  
    end_super  
end_object  
```

### **6.2. Наследование**  
```pshn
object Admin[name, role] : User[name] then  
    field role = role  
end_object  
```

---

## **7. Работа с данными**  
### **7.1. Массивы**  
```pshn
nums = [1, 2, 3]  
nums << 4  @ Добавление элемента  
```

### **7.2. Словари**  
```pshn
user = {"name": "Alice", "age": 25}  
Print-n[user["name"]]  
```

---

## **8. Модули**  
### **8.1. Импорт**  
```pshn
Ps.import[math]  
Ps.import[http.{Server, Client}]  
```

### **8.2. Создание модуля**  
```pshn
@ file: utils.pshn  
object StringUtils then  
    super reverse[s: str] -> str then ... end_super  
end_object  
```

---

## **9. Обработка ошибок**  
```pshn
try then  
    risky_operation[]  
catch [e: Error] then  
    Print-e["Ошибка: #{e}"]  
end_try  
```

---

## **10. Многопоточность**  
```pshn
parallel then  
    task1[]  
    task2[]  
end_parallel  
```

---

## **11. Компиляция**  
### **11.1. В нативный код**  
```bash
pshn compile app.pshn -o app --optimize
```

### **11.2. В WASM**  
```bash
pshn compile --target=wasm app.pshn
```

---

## **12. Примеры**  
### **12.1. HTTP-сервер**  
```pshn
Ps.import[http]  

server = http.Server[]  
server.on["/", req => {"message": "OK"}]  
server.listen[8080]  
```

### **12.2. Парсинг JSON**  
```pshn
data = json.parse['{"name": "Alice"}']  
Print-n[data["name"]]  
```
---

**PowerShine** — это:  
🚀 Высокая производительность  
📚 Простота изучения  
🔧 Гибкость для любых задач# PowerShine