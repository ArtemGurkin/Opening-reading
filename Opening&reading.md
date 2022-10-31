# Task 1

cook_book = {}

with open('file.txt', 'rt') as file:
    for l in file:
        dish_name = l.strip()
        dish = []
        ingr_num = file.readline()
        for i in range(int(ingr_num)):
            portions = file.readline()
            ingridient, amount, measurement = portions.strip().split(' | ')
            dish.append({'ingredient_name': ingridient, 'amount': amount, 'measurement': measurement})
            cook_book[dish_name] = dish
        blank_line = file.readline()

print(cook_book)

# Task 2

shop_list = {}
def get_shops_list_by_dishes(dishes, person_count):
    for dish in dishes:
        if dish in cook_book and dish in dishes:
            shop_list_details = {}
            for i in cook_book[dish][0:]:
                if i['ingredient_name'] in shop_list_details:
                    shop_list_details = {i['ingredient_name']: {'measurement': i['measurement'], 'amount': i['amount']}}
                else:
                    person = int(i['amount']) * person_count
                    shop_list_details = {i['ingredient_name']: {'measurement': i['measurement'], 'amount': person}}
                    shop_list.update(shop_list_details)
    return shop_list

print(get_shops_list_by_dishes(['Омлет', "Запеченный картофель"], 3))

# Task 3

f1 = open('1.txt')
f2 = open('2.txt')
f3 = open('3.txt')

r_1 = f1.readlines()
r_2 = f2.readlines()
r_3 = f3.readlines()

f1 = open('1.txt')
f2 = open('2.txt')
f3 = open('3.txt')

result_1 = len(f1.readlines())
result_2 = len(f2.readlines())
result_3 = len(f3.readlines())

list = {1: (result_1), 2: (result_2), 3: (result_3)}
sorted_val = sorted(list.values())
sorted_list = {}
sorted_list['1'] = f'{result_1}\n{("".join(r_1))}'
sorted_list['2'] = f'{result_2}\n{("".join(r_2))}'
sorted_list['3'] = f'{result_3}\n{("".join(r_3))}'

for key, value in sorted_list.items():
    with open('Final.txt', 'a') as document:
        document.write(f'{key}.txt\n{value}\n')