### Задание. NotFoundException
Вы развиваете приложение с менеджером товаров, который мы рассматривали на лекции, и решили сделать так, чтобы при попытке удаления несуществующего объекта из репозитория генерировалось ваше исключение, а не ArrayIndexOfBoundsException.

Обратите внимание: это правильный подход, поскольку таким образом вы сообщаете через генерацию исключения, что это исключение, вписывающееся в вашу логику, а не ошибка программиста.

Что нужно сделать:

Возьмите проект с менеджером, репозиторием и товарами, мы его писали в рамках ДЗ про наследование.
Создайте класс исключения NotFoundException, отнаследовавшись от RuntimeException, и реализуйте как минимум конструктор с параметром-сообщением. Он будет просто вызывать суперконструктор предка, см. подсказку.
В методе удаления removeById сначала проверяйте, есть ли элемент. Для этого прямо из метода removeById вызывайте метод findById: если результат null, тогда выкидывайте исключение NotFoundException.
Напишите два автотеста на репозиторий: первый должен проверять успешность удаления существующего элемента, второй — генерации NotFoundException при попытке удаления несуществующего элемента.
Подсказка
Для реализации этой логики вам понадобится добавить метод findById, предназначенный для поиска товара в репозитории по его ID. Так, он должен принимать параметр ID искомого товара, пробегаться по всем товарам репозитория и сверять их ID с искомым, в случае совпадения делать return этого товара. Если же, пробежав все товары репозитория, ни один подходящий найден не был, то есть цикл закончился без вызова return внутри него, то следует сделать return null. Общая схема этого метода будет такой:

public Product findById(???) {
  for (???) {
    if (???) {
      return product;
    }
  }
  return null;
}
Убедитесь, что ваши автотесты проходят. Напоминаем, что проект должен быть на базе Maven, с подключёнными зависимостями и необходимыми плагинами.

Итого: у вас должен быть репозиторий на GitHub, в котором расположен ваш Java-код и автотесты к нему.

Мы рекомендуем вам указывать в сообщении исключения: при удалении по какому конкретно ID было сгенерировано ваше исключение. Простейший способ, как это можно сделать: "Element with id: " + id + " not found".
