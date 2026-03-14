## UserType
| Type | description |
|---|---|
| customer | customer of the system | 
| admin | manager of the system |

## User

| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| user_id | serial | unique identifier of user | Primary Key |
| fisrtname | varchar(255) | user's firstname | Not Null |
| surname | varchar(255) | user's surname | Not Null |
| phonenumber | varchar(255) | user's phonenumber | Not Null |
| user_type | UserType | role of the user | default: customer |

## Appointment

| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| appointment_id | serial | unique identifier of appointmen | Primary Key |
| broken_part | varchar(255) | the part of the car that is broken and need to be fixed | None |
| short_description | varchar(255) | brief description of the appointment | None |
| user_id | integer | user id of the user that created this appointment | Foreign Key, Not Null |
| car_id | integer | car id of the car that needs fixing | Foreign Key, Not Null |

## Car 

| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
| car_id | serial | unique of car | Primary Key |
| brand | varchar(255) | model of the car | Not Null |
| owner | integer | owner of the car | Not Null |
