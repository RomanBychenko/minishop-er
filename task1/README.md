# Завдання 1 — ER-модель інтернет-магазину

## Опис

Цей проєкт містить ER-модель простого інтернет-магазину.
У моделі показано покупців, товари, категорії та замовлення.

## ER-діаграма

```mermaid
erDiagram
    CUSTOMER ||--o{ PURCHASE_ORDER : "оформлює"
    CATEGORY ||--o{ PRODUCT : "містить"
    PURCHASE_ORDER ||--|{ ORDER_ITEM : "містить"
    PRODUCT ||--o{ ORDER_ITEM : "входить до"

    CUSTOMER {
        string customer_id PK
        string full_name
        string email
    }

    CATEGORY {
        string category_id PK
        string name
    }

    PRODUCT {
        string product_id PK
        string name
        decimal price
    }

    PURCHASE_ORDER {
        string order_id PK
        datetime created_at
        string status
    }

    ORDER_ITEM {
        string item_id PK
        int quantity
        decimal unit_price
    }
```

## Перевірка моделі

Модель перевірено на відповідність файлу spec.md.
Вона містить 5 сутностей та 4 зв'язки з кардинальностями.

Атрибут PRODUCT.price зберігає поточну ціну товару,
а ORDER_ITEM.unit_price — ціну на момент оформлення замовлення.

Результати перевірки описані у файлі verification.md.