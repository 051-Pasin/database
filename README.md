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
| image_url | varchar(255) | url of the image | Not Null |

## RidePrice

| Attribute | Data Type | Description | Constraints |
|---|---|---|---|
