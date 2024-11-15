# final_task
purchases = [
    {"item": "apple", "category": "fruit", "price": 1.2, "quantity": 10},
    {"item": "banana", "category": "fruit", "price": 0.5, "quantity": 5},
    {"item": "milk", "category": "dairy", "price": 1.5, "quantity": 2},
    {"item": "bread", "category": "bakery", "price": 2.0, "quantity": 3},
]
def total_revenue(purchases):
    price_1=[pr['price']*pr['quantity'] for pr in purchases]
    return sum(price_1)
    
def items_by_category(purchases):
    category_dict={}
    for categ in purchases:
        ctgry=categ["category"]
        itm = categ["item"]
        if ctgry not in category_dict:
            category_dict[ctgry]=[]
        category_dict[ctgry].append(itm)
    return category_dict

def expensive_purchases(purchases, min_price):
    mn_prc = [pr for pr in purchases if pr['price']>=min_price]
    return mn_prc

min_price=min([pr['price'] for pr in purchases])

def average_price_by_category(purchases):
    category_price={}

    for categ in purchases:
        ctgry=categ["category"]
        price = categ["price"]
        if ctgry not in category_price:
            category_price[ctgry]=[]
        category_price[ctgry].append(price)

    for ctgry, price in category_price.items():
        avg_price=sum(price)/len(price)
        category_price[ctgry]=avg_price

    return category_price

def most_frequent_category(purchases):
    max_quant = 0
    most_frequent_cat = ""
    for purchase in purchases:
        category = purchase["category"]
        quantity = purchase["quantity"]
        if quantity > max_quant:
            max_quant = quantity
            most_frequent_cat = category
    return most_frequent_cat

print("Общая выручка: ", total_revenue(purchases))
print("Товары по категориям: ", items_by_category(purchases))
print(f"Покупки дороже {min_price}: ", expensive_purchases(purchases, min_price))
print("Средняя цена по категориям: ", average_price_by_category(purchases))
print("Категория с наибольшим количеством проданных товаров: ", most_frequent_category(purchases))