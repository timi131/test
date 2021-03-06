### Авторизация

POST: ``/api/v3/users/login``  

```json
params = {
username*
password*
 }
```
- response
```json
eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjo1NjcsImV4cCI6MTY1NDE1OTYzN30.9fh4Tj5rcKpjvEwgQznwrUfTprWYVCDgvI5AmN-QpDc
```


### Поиск пользователя по телефону

GET: ``/api/v4/callcenter/users/by_phone``  

```json
params = {
phone* // +79999999999
 }
```
- response
```json
{
  user: {},
  vehicles: []
}
```

### Поиск автомобиля по госномеру и 4 символам вина

GET: ``/api/v4/callcenter/vehicles/by_plate_and_vin``  

```json
params = {
plate*
vin*
 }
```

- response
```json
{
  "id": 12297,
  "vehicle_year_of_production": 2021,
  "vehicle_plate_no": "О178ЕР196",
  "vin": "Z8NFBNJ11ES126982",
  "new_car_deliver_at": "2021-04-21T00:00:00.000+03:00",
  "new_car_delivered_at": "2021-04-28T16:20:00.000+03:00",
  "condition_penalty": null,
  "return_km": null,
  "city_of_use_id": 81,
  "last_seen_km": null,
  "last_seen_date": null,
  "insurance": {
    "casco": {}
    },
    "osago": {}
    },
    "dc": {}
  },
  "road_assistance": {},
  "company_name": "Cherkizovo CK",
  "contacts": {
    "service_manager": {},
    "sales_manager": {},
    "tyres_manager": {},
    "fuel_manager": {},
    "secretay": {}
  },
  "definition_name": "Nissan Qashqai 2.0 144 AT-V AWD B SUV SE",
  "main_status_name": "Leased",
  "vehicle_brand_id": 9,
  "expected_return_at": "2024-04-27T16:20:00.000+03:00",
  "contract_number": "411-014",
  "vehicle_model_id": 71,
  "city_of_use_name": "Липецк"
}

```

### Автомобиль по id

GET: ``/api/v4/callcenter/vehicles/:id``  


### Возможные типы обращения

GET: ``/api/v4/callcenter/call_types``  
```json
params = {
client_type* // client partner potential buyer
 }
```

- response
```json
[
  {
    "id": 1,
    "name": "РАТ помощь на дороге (эвакуация, бензин)"
  },
...
]
```

### Список СТО

GET: ``/api/v4/callcenter/service_companies``  

```json
params = {
vehicle_brand_id*
city_id*
 }
```

- response
```json
[
  {
    "id": 1986,
    "company_name": "РОЛЬФ ООО (Рольф Химки)",
    "postal_address": "141400,Московская обл., Химкинский р-н, г. Химки, Ленинградское ш., вл. № 21\t"
  },
...
]
```

### Список городов

GET: ``/api/v3/cities``  


- response
```json
[
  {
    "id": 259,
    "name": "c. Ивановка "
  },
...
]
```

### Список брендов ам

GET: ``/api/v3/vehicle_brands``  



- response
```json
[
  {
    "id": 52,
    "name": "Bajaj"
  },
...
]
```

### Создание звонка

POST: ``/api/v4/callcenter/calls``  

```json
params = {
client_type* // client partner potential buyer
name*
email
phone*
position
company_name
desired_time // когда удобно звонить
city
note0* // comment
call_type_id* // страховая, РАТ, АП, приём обращения
vehicle_id
call_action_id* // предпринятое действие
 }
```

- response
```json
created call
```

### Создание заявки на сервис

POST: ``//api/v4/callcenter/vehicles/:vehicle_id/service_requests``  

```json
params = {
driver_name
driver_email*
driver_mobile
km
driver_location*
city_id*
driver_id*
expense_category_id
driver_sms
send_driver_email
send_driver_sms
desired_time*
note0
request_type
driver_service_company_id
date_at*
to_number

 }
```
- response
```json
created sr
```
