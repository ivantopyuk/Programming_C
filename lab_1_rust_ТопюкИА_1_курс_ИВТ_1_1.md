# Rust - Лабораторная работа №1
## Задача 1
### Постановка задачи
Напишите программу, которая запрашивает у пользователя имя и выводит на экран приветственное сообщение с использованием этого имени.
### Математическая модель
--
### Список идентификаторов
| Имя  | Тип    | Описание                                                    |
| ---- | ------ | ----------------------------------------------------------- |
| user_name | string | Строка, которая хранит имя, введённое пользователем с клавиатуры. |
### Код программы
```Rust
use std::io;

fn main() {
    println!("Введите ваше имя: ");

    let mut name = String::new();

    io::stdin()
        .read_line(&mut name)
        .expect("Не удалось прочитать строку");

    let name = name.trim();

    print!("Привет, {}!", name);
}

```
### Результаты выполненной работы
![image.png](https://i.postimg.cc/zGrJmrJp/laba-1-rust-1.png)
## Задача 2
### Постановка задачи
Создайте переменную типа целое беззнаковое число и выведите ее значение на экран. Явно укажите тип переменной. Затем измените значение переменной и снова выведите его.
### Математическая модель
--
### Список идентификаторов
| Имя | Тип | Описание              |
| --- | --- | --------------------- |
| num   | u32 | Переменная для хранения целочисленного значения, которое может быть изменено в процессе выполнения программы. |
### Код программы
```Rust
fn main() {
    let mut x: u32 = 50;
    println!("Первоначальное значение x: {}", x);
    x = 23;
    println!("Новое значение x: {}", x);
}
```
### Результаты выполненной работы
![image.png](https://i.postimg.cc/GhYcS21H/laba-1-rust-2.png)
## Задача 3
### Постановка задачи
Напишите функцию, которая принимает строку и возвращает ее длину (количество символов). Затем вызовите эту функцию с различными строками.
### Математическая модель
--
### Список идентификаторов
| Имя                       | Тип   | Описание                                                            |
| ------------------------- | ----- | ------------------------------------------------------------------- |
| s                         | &str  | Параметр функции для вычисления длины переданной строки.                                      |
| test_string1, test_string2, test_string3   | &str  | Переменные, в которых хранятся строки, чью длину мы проверяем. |
| result1, result2, result3 | usize | Локальные переменные в main, хранят результаты вызова string_length |

### Код программы
```Rust
fn string_length(s: &str) -> usize {
    s.chars().count()
}

fn main() {
    let s1: &str = "Hello";
    let s2: &str = "Привет, мир!";
    let s3: &str = "";

    let result1: usize = string_length(s1);
    println!("Длина строки \"{}\": {}", s1, result1);

    let result2: usize = string_length(s2);
    println!("Длина строки \"{}\": {}", s2, result2);

    let result3: usize = string_length(s3);
    println!("Длина пустой строки: {}", result3);
}

```
### Результаты выполненной работы
![image.png](https://i.postimg.cc/3xF3YcNh/laba-1-rust-3.png)
## Задача 4
### Постановка задачи
Задайте структуру Car с полями brand, model и year, и создайте несколько экземпляров этой структуры. Выведите информацию о каждой машине на экран.
### Математическая модель
--
### Список идентификаторов
| Имя              | Тип    | Описание                                                                  |
| ---------------- | ------ | ------------------------------------------------------------------------- |
| Car              | struct | Имя структуры, описывающей автомобиль.                                    |
| brand            | String | Поле структуры Car, хранящее название бренда автомобиля.                  |
| model            | String | Поле структуры Car, хранящее модель автомобиля.                           |
| year             | u32    | Поле структуры Car, хранящее год выпуска автомобиля.                      |
| car_1, car_2, car_3 | Car    | Переменные, представляющие экземпляры структуры, содержащие информацию об автомобиле. |

### Код программы
```Rust
struct Car {
    brand: String,
    model: String,
    year: u32,
}

fn main() {
    let car1 = Car {
        brand: "Lada".to_string(),
        model: "Vesta".to_string(),
        year: 2022,
    };
    let car2 = Car {
        brand: "Kia".to_string(),
        model: "Rio".to_string(),
        year: 2020,
    };
    let car3 = Car {
        brand: "Hyundai".to_string(),
        model: "Solaris".to_string(),
        year: 2019,
    };

    println!("Car 1: {} {} ({})", car1.brand, car1.model, car1.year);
    println!("Car 2: {} {} ({})", car2.brand, car2.model, car2.year);
    println!("Car 3: {} {} ({})", car3.brand, car3.model, car3.year);
}
```
### Результаты выполненной работы
![image.png](https://i.postimg.cc/rpyMmNRr/laba-1-rust-4.png)
## Задача 5
### Постановка задачи
Напишите программу, которая запрашивает у пользователя число 𝑁 и выводит на экран 𝑁-ное число Фибоначчи. Используйте рекурсию для решения этой задачи.
### Математическая модель
--
### Список идентификаторов

| Имя    | Тип                     | Описание                                                             |
| ------ | ----------------------- | -------------------------------------------------------------------- |
| n      | u32                     | Переменная, задающая номер числа Фибоначчи, введённая пользователем. |
| fib_number | u64                     | Переменная, в которой хранится результат вычисления n-го числа Фибоначчи. |
| input  | String                  | Переменная для хранения ввода пользователя в виде строки..                  |


### Код программы
```Rust
use std::io;

fn f(n: u32) -> u64 {
    match n {
        0 => 0,
        1 => 1,
        _ => f(n - 1) + f(n - 2),
    }
}

fn main() {
    println!("Введите число n:");

    let mut input = String::new(); 
    io::stdin().read_line(&mut input).expect("Ошибка ввода"); 
    let n: u32 = input.trim().parse().expect("Введите целое число");

    let result = f(n); 
    println!("{}-е число Фибоначчи: {}", n, result);
}
```
### Результаты выполненной работы
![image.png](https://i.postimg.cc/7LBDTJSQ/laba-1-rust-5.png)
## Задача 6
### Постановка задачи
Реализуйте перечисление DayOfWeek для дней недели. Напишите функцию, которая принимает день недели и возвращает следующий день. Обработайте случаи перехода на следующий день недели, если текущий день– воскресенье.
### Математическая модель
--
### Список идентификаторов
| Имя       | Тип                  | Описание                                                                                 |
| --------- | -------------------- | ---------------------------------------------------------------------------------------- |
| DayOfWeek | enum                 | Перечисление, описывающее дни недели                                                     |
| day       | DayOfWeek (параметр) | Входной параметр функции next_day - текущий день недели                                  |
| today     | DayOfWeek            | Локальная переменная в main, хранящая сегодняшний день                                   |
| next_day | DayOfWeek            | Переменная для хранения следующего дня недели, вычисленного на основе текущего дня. |

### Код программы
```Rust
#[derive(Debug)] 
enum DayOfWeek {
    Понедельник,
    Вторник,
    Среда,
    Четверг,
    Пятница,
    Суббота,
    Воскресенье,
}

fn next_day(day: DayOfWeek) -> DayOfWeek {
    match day {
        DayOfWeek::Понедельник => DayOfWeek::Вторник,
        DayOfWeek::Вторник => DayOfWeek::Среда,
        DayOfWeek::Среда => DayOfWeek::Четверг,
        DayOfWeek::Четверг => DayOfWeek::Пятница,
        DayOfWeek::Пятница => DayOfWeek::Суббота,
        DayOfWeek::Суббота => DayOfWeek::Воскресенье,
        DayOfWeek::Воскресенье => DayOfWeek::Понедельник,
    }
}

fn main() {
    let today = DayOfWeek::Воскресенье;
    println!("Сегодня: {:?}", today);
    
    let tomorrow = next_day(today);
    println!("Завтра будет: {:?}", tomorrow);
}
```
### Результаты выполненной работы
![image.png](https://i.postimg.cc/MHrJvCRM/laba-RUSTUPD.png)
## Задача 7
### Постановка задачи
Создайте структуру Product с полями name, price и category, а также перечисление (enum) Category для категорий товаров. Напишите метод для вывода информации о продукте и ассоциированную функцию для подсчета общей суммы товаров в заданной категории из массива продуктов.
### Математическая модель
--
### Список идентификаторов

| Имя           | Тип                     | Описание                                                                |
|---------------|-------------------------|-------------------------------------------------------------------------|
| Category      | enum                    | Перечисление категорий товаров (Electronics, Clothing, Food, Books)     |
| Product       | struct                  | Структура, описывающая товар                                            |
| name          | String                  | Название продукта                                                       |
| price         | f64                     | Цена продукта в рублях                                                  |
| category      | Category                | Категория продукта                                                      |
| products      | Vec<Product             | Вектор (массив) продуктов для анализа                                   |
| print_info()  | метод                   | Выводит информацию о продукте (название, цена, категория)               |
| total_price() | ассоц. функция          | Считает сумму цен товаров указанной категории                           |
| category_name | `&str                   | Локальная переменная в print_info(), хранящая название категории        |
| total         | f64                     | Результат вычисления общей стоимости в total_price()                    |
| electronics   | f64                     | Общая стоимость товаров категории Electronics                           |
| clothing      | f64                     | Общая стоимость товаров категории Clothing                              |
| food          | f64                     | Общая стоимость товаров категории Food                                  |
| books         | f64                     | Общая стоимость товаров категории Books                                 |

### Код программы
```Rust
#[derive(Debug, PartialEq, Clone, Copy)]
enum Category {
    Electronics,
    Clothing,
    Food,
    Books,
}

struct Product {
    name: String,
    price: f64,
    category: Category,
}

impl Product {
    fn print_info(&self) {
        let category_name = match self.category {
            Category::Electronics => "Электроника",
            Category::Clothing => "Одежда",
            Category::Food => "Еда",
            Category::Books => "Книги",
        };
        
        println!(
            "Товар: {}\nЦена: {:.2} руб.\nКатегория: {}\n{}",
            self.name, self.price, category_name,
            "-".repeat(30)
        );
    }
    
    fn total_price(products: &[Product], category: Category) -> f64 {
        products.iter()
            .filter(|p| p.category == category)
            .map(|p| p.price)
            .sum()
    }
}

fn main() {
    let products = vec![
        Product {
            name: "Ноутбук Lenovo".to_string(),
            price: 89990.0,
            category: Category::Electronics,
        },
        Product {
            name: "Футболка Nike".to_string(),
            price: 3499.0,
            category: Category::Clothing,
        },
        Product {
            name: "Яблоки (1 кг)".to_string(),
            price: 129.90,
            category: Category::Food,
        },
        Product {
            name: "Молоко (1 л)".to_string(),
            price: 89.90,
            category: Category::Food,
        },
        Product {
            name: "Rust для начинающих".to_string(),
            price: 2499.0,
            category: Category::Books,
        },
        Product {
            name: "Смартфон Samsung".to_string(),
            price: 65990.0,
            category: Category::Electronics,
        },
        Product {
            name: "Алгоритмы. Руководство".to_string(),
            price: 3599.0,
            category: Category::Books,
        },
    ];
    
    for product in &products {
        product.print_info();
    }
    
    let categories = [
        Category::Electronics,
        Category::Clothing,
        Category::Food,
        Category::Books,
    ];
    
    for category in categories {
        let total = Product::total_price(&products, category);
        let category_name = match category {
            Category::Electronics => "Электроника",
            Category::Clothing => "Одежда",
            Category::Food => "Еда",
            Category::Books => "Книги",
        };
        println!("Общая стоимость {}: {:.2} руб.", category_name, total);
    }
}
```
### Результаты выполненной работы
![image.png](https://i.postimg.cc/Kzw20XqP/laba-1-rust-7.png)
## Задача 8
### Постановка задачи
Создайте структуру Employee с полями name, position, salary, а также перечисление Position для должностей сотрудников. Напишите функцию, которая принимает вектор сотрудников и возвращает вектор сотрудников заданной должности.
### Математическая модель
--
### Список идентификаторов

| Имя       | Тип                      | Описание                                                   |
| --------- | ------------------------ | ---------------------------------------------------------- |
| Position  | enum                     | Перечисление возможных должностей                          |
| Employee  | struct                   | Структура, описывающая сотрудника                          |
| name      | String (поле Employee)   | Имя сотрудника                                             |
| position  | Position (поле Employee) | Должность сотрудника                                       |
| salary    | f64 (поле Employee)      | Оклад сотрудника                                           |
| employees | &[Employee]              | Массив сотрудников, по которому выполняется фильтрация по должности.           |
| target    | Position                 | Целевая должность для фильтрации                           |
| e         | &Employee                | Ссылка на текущего сотрудника при фильтрации               |
| employees_list     | Vec<Employee>            | Список сотрудников, которые могут быть отфильтрованы по должности. |
| devs      | Vec<Employee>            | Массив сотрудников, которые имеют должность разработчика. |

### Код программы
```Rust
#[derive(Debug, PartialEq, Clone)] 
enum Position {
    SeniorDeveloper,
    JuniorDeveloper,
    UXSpecialist,
    QAEngineer,
}

#[derive(Debug, Clone)]
struct Employee {
    name: String,
    position: Position,
    salary: f64,
}

fn filter_by_position(employees: &[Employee], target: Position) -> Vec<Employee> {
    employees
        .iter()
        .filter(|e| e.position == target)
        .cloned()
        .collect()
}

fn main() {
    let staff = vec![
        Employee { name: "Alex".into(), position: Position::SeniorDeveloper, salary: 95000.0 },
        Employee { name: "Maria".into(), position: Position::JuniorDeveloper, salary: 60000.0 },
        Employee { name: "John".into(), position: Position::UXSpecialist, salary: 85000.0 },
        Employee { name: "Emma".into(), position: Position::QAEngineer, salary: 75000.0 },
        Employee { name: "David".into(), position: Position::JuniorDeveloper, salary: 62000.0 },
    ];

    let juniors = filter_by_position(&staff, Position::JuniorDeveloper);
    
    println!("Junior Developers:");
    for emp in juniors {
        println!("{} (${})", emp.name, emp.salary as i64);
    }
}

```
### Результаты выполненной работы
![image.png](https://i.postimg.cc/zXnrFcnh/laba-1-rust-8.png)
## Информация о студенте
Топюк И. А., 1 курс, ИВТ-1.1
