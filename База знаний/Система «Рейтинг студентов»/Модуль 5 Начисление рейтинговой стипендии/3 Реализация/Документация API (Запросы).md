## Загрузка файлов с заявками

```
POST	/listLoad/all
```

На вход файлы csv со следующими названиями:

-   Студенты, получающие государственную академическую стипендию - ГАС
-   Студенты на каникулах - Каникулы
-   Студенты со свободным графиком - Свободный график
-   Культурно-творческая деятельность - КТД
-   Научно-исследовательская деятельность - НИД
-   Общественная деятельность - ОД
-   Научно-исследовательская деятельность - НИД
-   Спортивная деятельность - СД
-   Учебная деятельность - УД

JSON ответ:

```
[ 
            {title: "ГАС.csv", status: "OK"},
            {title: "Каникулы.csv", status: "OK"},
            {title: "КТД.csv", status: "OK"},
            {title: "НИД.csv", status: "OK"},
            {title: "ОД.csv", status: "OK"},
            {title: "Свободный график.csv", status: "OK"},
            {title: "СД.csv", status: "OK"},
            {title: "УД.csv", status: "OK"},
]
```

## Получение количества мест по направлениям для настроек

```
GET	/ratingCount
```

Возвращает список направлений с количеством мест

JSON ответ:

```
[
            {
                        "id":1,
                        "count":70,
                        "course":{"title":"НИД"},
                        "datetable":{"id":1,"date":[{"value":"2022-07-01","inclusive":true},{"value":"2023-01-31","inclusive":false}]}
            },
            {
                        "id":2,
                        "count":65,
                        "course":{"title":"УД"},
                        "datetable":{"id":1,"date":[{"value":"2022-07-01","inclusive":true},{"value":"2023-01-31","inclusive":false}]}
            },
            {
                        "id":3,
                        "count":60,
                        "course":{"title":"СД"},
                        "datetable":{"id":1,"date":[{"value":"2022-07-01","inclusive":true},{"value":"2023-01-31","inclusive":false}]}
            },
            {
                        "id":5,
                        "count":60,
                        "course":{"title":"ОД"},
                        "datetable":{"id":1,"date":[{"value":"2022-07-01","inclusive":true},{"value":"2023-01-31","inclusive":false}]}
            },
            {
                        "id":4,
                        "count":60,
                        "course":{"title":"КТД"},
                        "datetable":{"id":1,"date":[{"value":"2022-07-01","inclusive":true},{"value":"2023-01-31","inclusive":false}]}
            }
]
```

## [](https://github.com/KutenkovV/Student-Raiting/blob/master/server/README.md#-%D0%B8%D0%B7%D0%BC%D0%B5%D0%BD%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BA%D0%BE%D0%BB%D0%B8%D1%87%D0%B5%D1%81%D1%82%D0%B2%D0%B0-%D0%BC%D0%B5%D1%81%D1%82-%D0%BF%D0%BE-%D0%BD%D0%B0%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F%D0%BC-)Изменение количества мест по направлениям

```
PUT	/ratingCount
```

Изменяет количество мест

Ответ:

```
ОК
```

## [](https://github.com/KutenkovV/Student-Raiting/blob/master/server/README.md#-%D0%BF%D0%BE%D0%BB%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D1%81%D0%BF%D0%B8%D1%81%D0%BA%D0%B0-%D1%81%D1%82%D1%83%D0%B4%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%D1%81-%D0%B8%D1%85-%D0%B7%D0%B0%D1%8F%D0%B2%D0%BA%D0%B0%D0%BC%D0%B8-)Получение списка студентов с их заявками

```
GET	/listLoad/ud
GET	/listLoad/od
GET	/listLoad/sd	
GET	/listLoad/nid	
GET	/listLoad/ktd
```

Возвращает студентов с заявками, отсортированных по наличию, ГАС и баллам, с указанием будет ли рейтинговая,если применены настройки. Если списки не были загружены, начался новый период рейтинга, а фронт запрашивает их, то возвращается пустота.

JSON ответ:

```
[
            {
                        "id":5848,
                        "rowNumber":"5",
                        "destination":false,
                        "cause":null,
                        "student":{
                                    "studnumber":2423455,
                                    "fullname":"Опарина Татьяна Александровна",
                                    "educationgroup":"ЭУм-20-1",
                                    "institute":"ИЭ","sad":"Да",
                                    "vacation":"Нет","free":"Нет"
                        },
                        "rating":{
                                    "points":366,
                                    "ratingcourse":{
                                                "id":1,
                                                "levelid":"2",
                                                "courseid":"1",
                                                "courselevel":{"level":1}
                                    }
                        },
                        "datetable":{
                                    "id":1,
                                    "date":[{
                                                "value":"2022-07-01",
                                                "inclusive":true
                                    },{
                                                "value":"2023-01-31",
                                                "inclusive":false}
                                    ]}
            },
            ...
]

```

## [](https://github.com/KutenkovV/Student-Raiting/blob/master/server/README.md#-%D0%BF%D0%BE%D0%BB%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D1%81%D0%BF%D0%B8%D1%81%D0%BA%D0%B0-%D1%81%D1%82%D1%83%D0%B4%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%D0%BA%D0%BE%D1%82%D0%BE%D1%80%D1%8B%D0%B5-%D0%BF%D0%BE%D0%B4%D0%B0%D0%BB%D0%B8-%D0%BD%D0%B0-%D0%BD%D0%B5%D1%81%D0%BA%D0%BE%D0%BB%D1%8C%D0%BA%D0%BE-%D0%BD%D0%B0%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B9-)Получение списка студентов которые подали на несколько направлений

```
GET	/studentRatingManyCourses
```

Возвращает список студентов, которые подали на несколько направлений

JSON ответ:

```
[
        {
                "id": "153",
                "studnumber": 2410513,
                "fullname": "Судомойкин Всеволод Львович",
                "educationgroup": "ЭВМб-19-1",
                "institute": "ИИТиАД",
                "nid": {
                        "point": 0,
                        "destination": false
                },
                "od": {
                        "point": 0,
                        "destination": false
                },
                "sd": {
                        "point": 0,
                        "destination": false
                },
                "ktd": {
                        "point": 175,
                        "destination": true
                },
                "ud": {
                        "point": 48,
                        "destination": true
                }
        },
        ...
]
```

## [](https://github.com/KutenkovV/Student-Raiting/blob/master/server/README.md#-%D0%BE%D0%BF%D1%80%D0%B5%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%B8%D0%B5-%D0%BD%D0%B0%D0%BF%D1%80%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F-)Определение направления

```
PUT	/studentRatingManyCourses
```

Определяет направление по которому студент будет получать стипендию, если он подал заявки в несколько направлений

Ответ:

```
{}
```

## [](https://github.com/KutenkovV/Student-Raiting/blob/master/server/README.md#-%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0-%D0%B3%D0%BE%D1%82%D0%BE%D0%B2%D0%BD%D0%BE%D1%81%D1%82%D0%B8-%D1%84%D0%B8%D0%BD%D0%B0%D0%BB%D1%8C%D0%BD%D0%BE%D0%B3%D0%BE-%D1%81%D0%BF%D0%B8%D1%81%D0%BA%D0%B0-)Проверка готовности финального списка

```
GET	/getTheFinalFileIsReady
```

Возвращает true или false

Ответ:

```
true/false
```

## [](https://github.com/KutenkovV/Student-Raiting/blob/master/server/README.md#-%D0%BF%D0%BE%D0%BB%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D1%81%D0%B2%D0%BE%D0%B4%D0%BA%D0%B8-)Получение сводки

```
GET	/report
```

Возвращает сводку

JSON ответ:

```
[
        {
                "title": "Научно-исследовательская деятельность",
                "totalSubmitted": "110",
                "count": "71",
                "borderPoint": "15",
                "numberReceived": "86"
        },
        {
                "title": "Учебная деятельность",
                "totalSubmitted": "124",
                "count": "65",
                "borderPoint": "25",
                "numberReceived": "98"
        },
        {
                "title": "Спортивная деятельность",
                "totalSubmitted": "84",
                "count": "60",
                "borderPoint": "20",
                "numberReceived": "72"
        },
        {
                "title": "Общественная деятельность",
                "totalSubmitted": "123",
                "count": "60",
                "borderPoint": "72",
                "numberReceived": "77"
        },
        {
                "title": "Культурно-творческая деятельность",
                "totalSubmitted": "79",
                "count": "60",
                "borderPoint": "43",
                "numberReceived": "68"
        }
]
```

## [](https://github.com/KutenkovV/Student-Raiting/blob/master/server/README.md#-%D0%BF%D0%BE%D0%BB%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B8%D1%82%D0%BE%D0%B3%D0%BE%D0%B2%D0%BE%D0%B3%D0%BE-%D1%81%D0%BF%D0%B8%D1%81%D0%BA%D0%B0-)Получение итогового списка

```
GET	/finalList
```

Возвращает итоговый список

JSON ответ:

```
[ 
            {title: "ГАС.csv", status: "OK"},
            {title: "Каникулы.csv", status: "OK"},
            {title: "КТД.csv", status: "OK"},
            {title: "НИД.csv", status: "OK"},
            {title: "ОД.csv", status: "OK"},
            {title: "Свободный график.csv", status: "OK"},
            {title: "СД.csv", status: "OK"},
            {title: "УД.csv", status: "OK"},
]
```

## [](https://github.com/KutenkovV/Student-Raiting/blob/master/server/README.md#-%D0%BF%D0%BE%D0%BB%D1%83%D1%87%D0%B5%D0%BD%D0%B8%D0%B5-%D0%B8%D1%82%D0%BE%D0%B3%D0%BE%D0%B2%D0%BE%D0%B3%D0%BE-%D1%84%D0%B0%D0%B9%D0%BB%D0%B0-)Получение итогового файла

```
GET	/finalListFile
```

Скачивает итоговый файл

Ответ:

```
Файл Рейтинг.xlsx
```