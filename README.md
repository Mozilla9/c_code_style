### Code style for C projects

### 1 Именование файлов/папок в проекте
- имена файлов в проекте дожны быть на английском, в нижнем регистре. Разделитель между словами символ подчеркивания `_`

- имена папок также на английском, в нижнем регистре. Разделитель между словами символ тире `-`

```
src\
src\coap-proto
    - coap_proto.c        /* c source file */
    - coap_proto.h        /* c header file */

src\modem-driver
    - modem_routines.c    /* c source file */
    - modem_routines.h    /* c header file */
```

### 2 Заголовки

- в начало каждого файла помещается заголовок с названием/авторством/датой-создания/копирайтом. Современные *IDE* позволяют настроить шаблоны для автоматического добавления заголовков.

- Для `Eclipse`, `'Window'->'Preferences'->'C/C++'->'Code Style'->'Code Templates'`

```
/*
 * Copyright (c) ${year} ${company}. All Rights Reserved.
 * ${company} proprietary and confidential.
 * Use is subject to license terms.
 *
 * @Project: ${project_name}
 * @File:    ${file_name}
 *
 * @Author:  ${user}
 * @Created: ${date}
 *
 */
```

### 3 Типы данных

- Используем типы из страндартной библиотеки С. Подключаем через:

```
#include <stdint.h>
#include <stdbool.h>

/**
 * uint8_t
 * uint16_t
 * uint32_t
 * ...
 * bool
 */

```

### 4 Именование переменных и функций

1) Имена переменных и функций в нижнем регистре, слова разделяются через символ подчеркивания  **_**

```
uint32_t mmu_value;

void * pointer_on_void;

void send_data_to_modem(uint8_t *buf, const uint16_t data_len);
```

2) Имена новых типов на основе структур в нижнем регистре и начинаются с двух символов подчеркивания

```
typedef struct __my_new_type {
    uint32_t type;
    uint32_t handle;

} __my_new_type;

```

3) Имена констант, дефайнов, типов данных на основе функций

- имена в верхнем регистре

```
#define BUFFER_SIZE                 64

static const uint32_t BUFFER_SIZE = 100;

typedef void (*TERMINAL_CALLBACK)(void * arg);

```

4) Локальные переменные

- локальные переменные всегда должны быть определены в начале тела функции.
- присвоение значений идет после определения.

```
void send_data_to_modem(uint8_t *buf, const uint16_t data_len)
{
    uint32_t var1;
    uint32_t var2;
    
    /* assigement */
    var1 = 0;
    var2 = 100;
    
    /* code */
    
}

```

5) Глобальные переменные и функции

- все переменные и функции, которые видимы вне файла, должны начинаться с имени модуля, относящегося к ним. Так проще знать, где искать определения для функций и переменных.

```
extern char * dcp_router;
void dcp_global_func(char * buf);

```

6) Статические функции

- именование свободное, начинать с имени модуля не обязательно

```

static void some_static_func(char * buf);

```

### 5 Форматирование кода

1) Отступы, пробелы табуляции

- для отступов используем только пробелы (табуляции не используем)

- стандартный отступ равен 4 пробела

2) Определение функций

- открывающая скобка с новой строки

```
static uint32_t my_func(uint8_t * param1, uint32_t param2)
{
    /* code is here */
}
```

3) Определение указателей

```

uint32_t * pointer;   /* допустимо */
uint32_t *pointer;    /* допустимо */

uint32_t* pointer;    /* не допустимо */


```

4) Управляющие конструкции (**for**/**while**/**if**)

- после ключевого слова пробел
- открывающая фигурная скобка на той же строке

```
/* цикл for */
for (...) {

}

/* условие if */
if (...) {

} else if () {

} else {

}

/* цикл do-while */
do {

} while (...);


/* цикл while */
while (...) {

}

```

5) Комментарии

```

/* Одиночная строка комментария выглядит примерно как эта строка. */

/**
 * Многострочный коменнтарий должен быть оформлен как показано тут. Комментарии должны
 * предпочительно быть полными предложениями, заполненными так, чтобы быть похожими на
 * реальные параграфы.
 */

```


### Ссылки на другие стандарты

[http://www.maultech.com/chrislott/resources/cstyle/indhill-cstyle.pdf](http://www.maultech.com/chrislott/resources/cstyle/indhill-cstyle.pdf)

[https://www.gnu.org/prep/standards/standards.html#Formatting](https://www.gnu.org/prep/standards/standards.html#Formatting)

[https://users.ece.cmu.edu/~eno/coding/CCodingStandard.html#pnames](https://users.ece.cmu.edu/~eno/coding/CCodingStandard.html#pnames)
