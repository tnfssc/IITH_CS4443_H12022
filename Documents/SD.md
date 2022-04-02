# Software Design (SD) for Hotel Reservation System (HRS)

## Interfaces

```py
class Room(BaseModel):
  _id: str
  room_number: int
  suite: str
  capacity: int
```

```py
class Customer(BaseModel):
  _id: str
  first_name: str
  last_name: str
  email: str
  phone: str
  address: str
  city: str
  state: str
  zip_code: str
  country: str
```

```py
class Reservation(BaseModel):
  _id: str
  customer_id: str
  room_id: str
  check_in: str
  check_out: str
  price: float
```

```py
class Manager(BaseModel):
  _id: str
  name: str
  email: str
  phone: str
```

### Customer API Service

> Login

```py
# Customer Login
# Handled by Firebase
```

> General

```py
@app['get', 'post', 'put', 'delete', 'patch']('/customer/{function_name}')
async handler(function_name, ...params):
  try:
    user = await firebase_admin.auth.verify_id_token(headers['Authorization'])
  except:
    return json({'error': 'Unauthorized'}, status=401)
  return api_services[function_name].handle(user, params)
```

### Manager API Service

> Login

```py
# Manager Login
# Handled by Firebase
```

> General

```py
@app['get', 'post', 'put', 'delete', 'patch']('/manager/{function_name}')
async handler(function_name, ...params):
  try:
    user = await firebase_admin.auth.verify_id_token(headers['Authorization'])
  except:
    return json({'error': 'Unauthorized'}, status=401)
  return await api_services[function_name].handle(user, params)
```

### Customers Service

> Enter/Edit Details

```py
@app.post('/details')
async handler(user: firebase_admin.auth.UserRecord, details: Partial[Customer] | None) -> Customer:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> Delete Account

```py
@app.delete('/details/{user_id}')
async handler(user: firebase_admin.auth.UserRecord, user_id: str) -> None:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

### Rooms Service

> View Room Details

```py
@app.get('/rooms/{room_id}')
async handler(user: firebase_admin.auth.UserRecord, room_id: str) -> Room:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> Add/Edit Room
  
```py
@app.post('/rooms')
async handler(user: firebase_admin.auth.UserRecord, params: Partial[Room]) -> Room:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> Delete Room

```py
@app.delete('/rooms/{room_id}')
async handler(user: firebase_admin.auth.UserRecord, room_id: str) -> None:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

### Reservations Service

> View Reservation Details

```py
@app.get('/reservations/{reservation_id}')
async handler(user: firebase_admin.auth.UserRecord, reservation_id: str) -> Reservation:
  try:
    data = await db.find_one({'_id': reservation_id})
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> Create Reservation

```py
@app.post('/reservations')
async handler(user: firebase_admin.auth.UserRecord, params: Partial[Reservation]) -> Reservation:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> Edit Reservation

```py
@app.put('/reservations/{reservation_id}')
async handler(user: firebase_admin.auth.UserRecord, params: Partial[Reservation]) -> Reservation:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> Cancel Reservation

```py
@app.delete('/reservations/{reservation_id}')
async handler(user: firebase_admin.auth.UserRecord, reservation_id: str) -> None:
  try:
    data = await db.delete_one({'_id': reservation_id})
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> Add cost

```py
@app.post('/reservations/{reservation_id}/cost')
async handler(user: firebase_admin.auth.UserRecord, reservation_id: str, cost: int) -> Reservation:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> View cost

```py
@app.get('/reservations/{reservation_id}/cost')
async handler(user: firebase_admin.auth.UserRecord, reservation_id: str) -> int:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> Available Rooms

```py
@app.get('/rooms/available')
async handler(user: firebase_admin.auth.UserRecord, params: Partial[Reservation]) -> List[Room]:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

> Room availability

```py
@app.get('/rooms/{room_id}/available')
async handler(user: firebase_admin.auth.UserRecord, params: Partial[Reservation]) -> bool:
  try:
    data = # Logic
  except:
    return json({'error': 'Internal Server Error'}, status=500)
  return json(data)
```

### Storage Services

> General

```py
@app.post('/')
async handler(query: str):
  try:
    data = await db.exec(query)
  except:
    return json({'error': 'Error'}, status=500)
  return json(data)
```
