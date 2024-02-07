# Documentation

## Mindmap
Here is our documentation for mindmap
[Miro Link](https://miro.com/app/board/uXjVNwdDq-A=/?share_link_id=179473580058)

## ERD Plan
```mermaid
erDiagram
    USER ||--|{ USER_AUTH : authenticated
    USER ||--|{ LEVEL : has
    USER ||--|{ STORE : has
    CATEGORIES ||--|{ PRODUCTS : contains
    STORE ||--|{ CUSTOMERS : has
    STORE ||--|{ ORDERS : has
    STORE ||--|{ CATEGORIES : has
    STORE ||--|{ ORDERS : has
    STORE ||--|{ INVENTORIES : has
    INVENTORIES ||--|{ INVENTORY_LOG : has
    PRODUCTS ||--|{ PRODUCT_IMAGES : has
    PRODUCTS ||--|{ PRODUCT_QTY_LOGS : has
    PRODUCTS ||--|| VARIANTS : PRODUCT_VARIANT
    ORDERS ||--|| PAYMENTS : has
    ORDERS ||--|| DELIVERY : has
    DELIVERY ||--|| DELIVERY_PROGRESS : has
    USER {
        int level_id
        string phone_number
        string email
        string first_name
        string last_name
    }
    USER_AUTH {
        int user_id
        datetime last_login
        text pin
        text token
        bool is_blocked
    }
    LEVEL {
        int id
        string name
    }
    STORE {
        int user_id
        string name
        tinyint status
        tinyint availability
    }
    CATEGORIES {
        string name
        string url
        string status(boolean)
        string category_parent_id
        string store_id
    }
    PRODUCTS{
        string name
        string sku
        string category_id
        string description
        string total_order
        string total_rating
        string store_id
        string store_inventory_id
        string is_active
        string is_po
        string po_time
        string quantity
        string is_verified
    }
    PRODUCT_IMAGES{
        int product_id
        string url
    }

```
