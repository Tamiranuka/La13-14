class Product:
    def __init__(self, name, product_type, unit_of_measure, price):
        self.name = name
        self.product_type = product_type
        self.unit_of_measure = unit_of_measure
        self.price = price

    def input_product(self):
        self.name = input("Бүтээгдэхүүний нэрийг оруулна уу: ")
        self.product_type = input("Бүтээгдэхүүний төрлийг оруулна уу: ")
        self.unit_of_measure = input("Хэмжих нэгжийг оруулна уу: ")
        self.price = float(input("Үнэ оруулна уу: "))

    def print_product(self):
        print("Бүтээгдэхүүний нэр: ", self.name)
        print("Бүтээгдэхүүний төрөл: ", self.product_type)
        print("Хэмжих нэгж: ", self.unit_of_measure)
        print("Үнэ: ", self.price)

with open("input.txt", "r") as file:
    lines = file.readlines()

products = []
for line in lines:
    data = line.strip().split(',')
    product = Product(*data)
    products.append(product)


for i, product in enumerate(products, start=1):
    print(f"Бүтээгдэхүүн {i}:")
    product.print_product()
    print()

with open("output.txt", "w") as file:
    for product in products:
        file.write(f"Бүтээгдэхүүн: {product.name}, Төрөл: {product.product_type}, Unit: {product.unit_of_measure}, Price: {product.price}\n")
