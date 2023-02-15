# Использование скриптового языка PYTHON
## Задание 1.  
Напишите два скрипта, каждый из которых принимает один параметр и: 
1. Прибавляет к параметру единицу как строку; 
2. Прибавляет к параметру единицу как число;

### Решение

#!/usr/bin/python3

import sys

print(f'{str(sys.argv[1])}1')
print(int(sys.argv[1]) + 1)

## Задание 2.
Напишите скрипт, который выводит содержимое каталога и подсчитывает в нём количество файлов.

### Решение

#!/usr/bin/python3

import os

dirs = next(os.walk('/'))[1]
total = 0

for dir in dirs:
    print(dir)
    total += 1

print('All files: ',total)

## Задание 3.
Напишите скрипт, который принимает один параметр и определяет, какой объект передан этим параметром (файл, каталог или не существующий).

### Решение

#1/usr/bin/python3

import sys
import os

if os.path.isdir(sys.argv[1]):
    print(f'{sys.argv[1]} - directory')
elif os.path.isfile(sys.argv[1]):
    print(f'{sys.argv[1]} - file')
else:
    print(f'{sys.argv[1]} - not exist')

## Задание 4.
Легенда
Пользователи в нашей компании начали пересылать друг другу некие "секретные" сообщения. Т.к. доступа к средствам криптографии у них нет, для "шифрования" они используют преобразование строк в формат Base64.
Задача
Написать скрипт для Bash, который:
1. Принимает на входе два аргумента. Первый - режим преобразования, второй - строка;
2. Если первый параметр равен crypt - преобразует второй параметр в строку Base64;
3. Если первый параметр равен decrypt - преобразует второй параметр в текст;
4. Если первый параметр равен любой другой строке - выйти из скрипта с ненулевым кодом возврата и сообщить об этом пользователю;
5. Если количество параметров скрипта не равно двум - выйти из скрипта с ненулевым кодом возврата выдать сообщение пользователю и завершить работу.

### Решение

#!/usr/bin/python3

import sys
from base64 import b64encode
from base64 import b64decode

count = len(sys.argv)
text = sys.argv[2]
if(count <= 3 and str(sys.argv[1]) == 'crypt'):
    text_bytes = text.encode('ascii')
    text_bytes = b64encode(text_bytes)
    text_bytes = text_bytes.decode('ascii')
    print(text_bytes)
elif(count <= 3 and str(sys.argv[1]) == 'decrypt'):
    text_bytes = text.encode('ascii')
    text_bytes = b64decode(text_bytes)
    text_bytes = text_bytes.decode('ascii')
    print(text_bytes)
elif(str(sys.argv[1]) != 'crypt' and str(sys.argv[1]) != 'decrypt'):
    print('Invalid action requested')
else:
    print('too many arguments')
