## User
| Type | Data Type | Description | Constraints |
|---|---|---|---|
| user_id | serial | unique identifier of user | Primary Key |
| user_name | varchar(255) | name of account | Not Null |
| user_password | varchar(255) | password of account | Not Null |
| user_email | varchar(255) | user's email | Not Null |

## Ride
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| ride_id | serial | unique identifier of ride | Primary Key |
| ride_name | varchar(255) | name of ride | Not Null |
| ride_deacription | varchar(255) | brif description of the ride | Not Null |
| image_url | text | url of the image | Not Null |
| time_per_round | time | time per round using minute | Not Null |
| max_per_round | int | max people can play the ride per round | Not Null |

## RidePrice
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| ride_price_id | serial | unique identifier of price | Primary Key |
| ride_id | integer | ride id of the ride that indicates this price | Foreign Key, Not Null |
| normal_price | decimal(6,2) | price of adult ticket without fast pass | Not Null, Check (price >= 0) |
| fast_pass_price | decimal(6,2) | price of adult ticket with fast pass | Not Null, Check (price >= 0) |
| type_id | int | type id of the ticket type that user's select | Foreign Key, Not Null | 

## TicketType
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| type_id | serial | unique identifier of type | Primary Key |
| type | enum ('Children', 'Adult', 'Senior') | type of ticket | Not Null |


## Cart
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| cart_id | serial | unique indentifier of cart | Primary Key |
| user_id | integer | user id of the user that add this cart | Foreign Key, Not Null | 

## CartItem 
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| cart_item_id | serial | unique identifier of cart item | Primary Key |
| cart_id | integer | cart id of cart user order | Foreign Key, Not Null |
| ride_price_id | integer | ride price id of the ticket price | Foreign Key, Not Null |
| quantity | integer | quantity of the ticket | Not Null, Check (quantity > 0) |
| has_fast_pass | boolean | check user's want fast pass or not | default false |
| visit_date | date | visit date that user's want to use ticket | Not Null |

## Booking
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| booking_id | serial | unique indentifier of booking | Primary Key |
| user_id | integer | user id of the user that booking | Foreign Key, Not Null |
| totol_price | decimal (8,2) | all price ticket that user's order | Not Null, Check (price >= 0) |
| booking_status | enum ('Cancel', 'Done') | booking status | Not Null |


## Ticket 
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| ticket_id | serial | unique identifier of ticket | Primary Key |
| booking_id | integer | booking id of the booking that create this ticket | Foreign Key, Not Null |
| ride_price | integer | show the ticket type of this ticket | Foreign Key, Not Null |
| quantity | integer | quantity of this ticket | Not Null, Check (quantity >= 1) |
| has_fast_pass | boolean | show user's has fast pass or not | default false |
| price_snapshot | decimal (6,2) | price of the ticket at user's order | Not Null, Check (price >= 0) |

## Discount 
| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| discount_id | serial | unique identifier of discount | Primary Key |
| min_value | int | booking total price can use discount | Not Null, Check (min_value >= 0) |
| percent_value | int | value of the % that discount | Not Null, Check (min_value >= 0)|

