# [Deploy](https://company-cards-test-assignment.netlify.app/)

## Техническое задание
Ссылка с ресурсами и макетом - http://bonusmoney.info/dev_test/FrontendTask.zip

Требуется реализовать экран начальный экран с логотипом компании, который показывается на 3 секунды. Далее открывается экран со списком карт компаний, используя шрифт и иконки, предложенные в директории res. Для ознакомления с деталями реализации см. файл Макет.
Карты компаний должны подгружаться порционно с сервера. Подгрузка с сервера осуществляется с параметрами offset - текущее суммарное количество загруженных карт и limit - запрашиваемое количество карт. 
На картах компаний должны присутствовать 3 кнопки:

- Подробнее;
- Показать (см. файл eye в res/img*);
- Удалить (см. файл trash в res/img*).

При нажатии на них требуется вывести попап (см. файл popup.png), попап должен быть с кнопкой действия, которая закрывает его, а также тексом: «нажата кнопка такая-то, ид компании: companyId», параметр companyId приходит с сервера.

При первичном запуске должен показываться начальный экран на 3 секунды (splash_sample.jpg). Далее показывается экран с прелоудером (см. файл first_load_sample.jpg). Далее, если карт нет - должен показываться текст, сообщающий об этом (см. файл first_load_sample.jpg). В случае если они есть, при дальнейшей подгрузке данных внизу должен показываться прелоудер (см. файл next_load_sample.jpg), а при обновлении страницы сверху должен показываться индикатор обновления (см. файл refresh_sample.jpg). 

При прорисовке карточек компании, нужно учитывать, что у каждой компании динамически проставляются цвета, то есть у одной карточки компании может быть фон карты фиолетовый, а у другой желтый, также и с цветами элементов на карте (см. в Макете раздел Dynamic colors). 

Запросы к серверу находятся в файле AndroidDevTask.postman_collection. Запросы авторизируются заголовком TOKEN, со значением 123. Для тестировки имеется 3 запросa:
- Ideal – не выдает ошибок при подгрузке;
- Long – с задержкой ответа для тестирования прелоудера;
- Error – выдает ошибки. 

Запрос getAllCards же с определенной вероятностью моделирует ожидание и ошибки. Для финальной версии требуется подключить только его. 

При подключении необходимо корректно обрабатывать различные ошибки: 
- Код ответа 401 – требуется вывести попап с текстом «ошибка авторизации»;
- Код ответа 400 – требуется вывести попап с текстом message – из ответа с сервера;
- Код ответа 500 – требуется вывести попап с текстом «все упало».

Если при запросе происходит ошибка, то нужно вывести попап (см. файл popup.png), который содержит текст ошибки(описано выше) и кнопку действия(закрывания), также в этом попапе можно перед текстом использовать иконку (см. файл exclamation в res/img*).  

Техническая составляющая
- Нужно использовать html, css, js, react.
- Опционально использовать mobx или redux.
- Опционально использовать сборщик vite.

## System requirements
- node v20.6.1
  
## Installation
```
npm install
```
  
## Running the app
```
npm run dev
```

