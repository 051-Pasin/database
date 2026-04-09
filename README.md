## User
| Type | Data Type | Description | Constraints |
|---|---|---|---|
| user_id | serial | unique identifier of user | Primary Key |
| user_name | varchar(255) | name of account | Not Null |
| user_pswd | varchar(255) | password of account | Not Null |
| user_email | varchar(255) | user's email | Not Null |

## Ride

| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| ride_id | serial | unique identifier of ride | Primary Key |
| ride_name | varchar(255) | name of ride | Not Null |
| ride_deacription | varchar(255) | brif description of the ride | Not Null |
| image_url | text | url of the image | Not Null |

## RidePrice

| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| ride_price_id | serial | unique identifier of price | Primary Key |
| ride_id | integer | ride id of the ride that indicates this price | Foreign Key, Not Null |
| ticket_type | enum ('Children', 'Adult', 'Senior') | type of the ticket that specified by age | Not Null|
| normal_price | decimal(6,2) | price of adult ticket without fast pass | Not Null, Check (price >= 0)
| fast_pass_price | decimal(6,2) | price of adult ticket with fast pass | Not Null, Check (price >= 0)

## Cart
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| cart_id | serial | unique indentifier of cart | Primary Key |
| user_id | integer | user id of the user that add this cart | Foreign Key, Not Null | 

## CartItem 
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| cart_item_id | serial | unique identifier of cart item | Primary Key |
| cart_id | integer |  | Foreign Key, Not Null |
| ride_price_id | integer |  | Foreign Key, Not Null |
| quantity | integer |  | Not Null, Check (quantity >= 1) |
| has_fast_pass | boolean |  | Not Null |
| visit_date | date |  | Not Null |

## Booking
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| booking_id | serial | unique indentifier of booking | Primary Key |
| user_id | integer |  | Foreign Key, Not Null |
| totol_price | decimal (8,2) |  | Not Null, Check (price >= 0) |
| booking_status | enum ('Cancel', 'Pending', 'Done') |  | Not Null |

## Ticket 
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| ticket_id | serial |  | Primary Key |
| booking_id | integer |  | Foreign Key, Not Null |
| ride_price | integer |  | Foreign Key, Not Null |
| quantity | integer |  | Not Null, Check (quantity >= 1) |
| has_fast_pass | boolean |  | Not Null |
| price_snapshot | decimal (6,2) |  | Not Null, Check (price >= 0) |

