# Documentation

## Mindmap
Here is our documentation for mindmap
[Miro Link](https://miro.com/app/board/uXjVNwdDq-A=/?share_link_id=179473580058)

## ERD Plan
#### Gateway Service

```mermaid
erDiagram
    USER ||--|{ USER_AUTH : authenticated
    USER ||--|{ LEVELS : has
    USER {
        int level_id
        str phone_number
        str email
        str first_name
        str last_name
    }
    USER_AUTH {
        int user_id
        datetime last_login
        text pin
        text token
        bool is_blocked
    }
    LEVELS {
        int id
        str name
    }
    


```

#### Store Service

```mermaid
erDiagram
    STORES ||--|{ CUSTOMERS : has-optional
    STORES ||--|{ COURIERS : has
    STORES ||--|{ CATEGORIES : has
    STORES ||--|{ PRODUCTS : has
    CATEGORIES ||--|{ PRODUCTS : contains
    PRODUCTS ||--|{ PRODUCT_IMAGES : has
    PRODUCTS ||--|{ PRODUCT_PRICE_LOGS : has
    PRODUCTS ||--|| VARIANTS : has
    PRODUCTS ||--|| PRODUCT_RATE_LOGS :has
    STORES {
        int user_id
        str name
        tinyint status
        tinyint availability
    }
    CATEGORIES {
        str name
        str url
        str status(boolean)
        str category_parent_id
        str store_id
    }
    PRODUCTS{
        str name
        str sku
        int category_id
        text description
        int total_order
        dec rate
        int store_id
        int store_inventory_id
        bool is_active
        bool is_po
        str po_time
        int minimum_quantity
        str is_verified
    }
    PRODUCT_IMAGES{
        int product_id
        str url
    }
    PRODUCT_RATE_LOGS{
        int product_id
        int customer_id
        int rate
    }
    CUSTOMERS{
        str phone_number
        str name
        int store_id
    }
    PRODUCT_PRICE_LOGS{
        int product_id
        dec price_before
        dec current_price
        int created_by
    }
    VARIANTS{
        int product_id
        str name
        dec price
        str tag
        dec discount
    }
    COURIERS{
        str phone_number
        str name
        int store_id
    }


```

#### Inventory Service

```mermaid
erDiagram
    INVENTORIES ||--|{ INVENTORY_LOGS : has
    INVENTORIES ||--|{ PURCHASE_ORDERS : has
    PURCHASE_ORDERS ||--|{ PURCHASE_ORDER_ITEMS : has
    PURCHASE_ORDERS ||--|{ SUPPLIERS : has
    INVENTORIES{
        int product_id
        int remaining_quantity
        int store_id
        int city_id
    }
    INVENTORY_LOGS{
        int inventory_id
        int quantity_before
        int current_quantity
        int ref_id
        int created_by
        text note
    }
    PURCHASE_ORDERS{
        int store_id
        dec sub_total
        dec grand_total
        int supplier_id
        text evidence

    }
    PURCHASE_ORDER_ITEMS{
        int product_id
        int quantity
    }
    SUPPLIERS{
        int phone_number
        str name
    }


```

#### Order Service

```mermaid
erDiagram
    ORDERS ||--|| PAYMENTS : has
    ORDERS ||--|| ORDER_ITEMS : has
    ORDERS ||--|| DELIVERIES : has
    DELIVERIES ||--|| DELIVERY_LOGS : has
    DELIVERIES ||--|| CUSTOMER_ADDRESSES : has
    
    CUSTOMER_ADDRESSES{
        int customer_id
        str address_name
        text pointed_map
        str recipient_name
        text detail
    }
    ORDERS{
        int total_items
        dec sub_total
        dec grand_total
        int user_id
        int total_discount
        int promo_id
        str status
    }
    ORDER_ITEMS{
        int product_id
        int product_variant_id
        str product_name
        str product_unit_name
        dec price
        int quantity
        dec discount
        int rating
        int store_id
    }
    PAYMENTS{
        int transaction_id
        str method_type
        str method_detail
        dec amount
        text attachment
        tinyint status
        text note
    }
    DELIVERIES{
        int order_id
        int courier_id
        int customer_address_id
    }
    DELIVERY_LOGS{
        int order_delivery_id
        str status
        text notes
        text img
    }
```
