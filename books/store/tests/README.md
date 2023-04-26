## Тест api
1. Создается файл test_api.py (вывод на печать только url и response)
```
    from django.urls import reverse
from rest_framework import status
from rest_framework.test import APITestCase
from store.models import Book
from store.serializers import BooksSerializer

class BooksApiTestCase(APITestCase):
    def test_get(self):
        url = reverse('book-list')
        print(url)
        response = self.client.get(url)
        print(response.data)
        print(response)
 ```   
- 1.1	В нем создается class BooksApiTestCase(APITestCase): наследующий свойства класса APITestCase импортированного из пакета rest_framework.test
- 1.2	В class BooksApiTestCase(APITestCase): (далее все в этом классе) создается метод def test_get(self): необходимый для тестирования апи запросов к серверу проекта books.
- 1.3	В функции (методе) def test_get(self): (далее все в этом методе) создается переменная url, которой присваивается значение возвращаемое функцией reverse из пакета django.urls.base, аргумент функции reverse преобразовывается в url адрес и нужен для получения списка.
- 1.4	Создается функция печати переменной url.
- 1.5	Создается переменная response, которой присваивается значение, возвращаемое через аргумент self экземпляром client (осуществляет запрос к серверу) и методом (функцией) def get, класса APITestCase, с переданным ей аргументом url.
- 1.6	Создается функция печати переменной response.
2.	При запуске файла test_api.py функция reverse создает url адрес ***(не могу детально описать механизм – это вопрос)***  /book/ и присваивает это значение переменной url, значение выводиться на печать. Далее переменная url передается в качестве аргумента в функцию get, экземпляра client, который посылает запрос (по адресу /book/ ?) и возвращает значение Response status_code=200, "application/json", оно присваивается переменной response и выводиться на печать.
## Вопросы
Весь пункт 2 не очень понятен\
Почему запрос создается не через request?  
Client обратился по адресу /book/ получил status_code=200 
и что это фактически значит? Что есть такой адрес?\
Что значит application/json ?\
Это вообще тест? Почему нет сравнения результатов?