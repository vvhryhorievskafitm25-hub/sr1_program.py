# sr1_program.py
"""
Самостійна робота №1: Розробка консольної програми на Python
з використанням базових конструкцій, структур даних, ітераторів та генераторів.
Виконано студенткою групи КБ-25: Григор'євська
"""

import math

# =====================================================================
# 1. Базові оператори, умовні конструкції та цикли (Математичні задачі)
# =====================================================================
def calculate_factorial(n: int) -> int:
    """Обчислення факторіала числа за допомогою циклу while з перевіркою умов."""
    if n < 0:
        raise ValueError("Факторіал від'ємного числа не визначено.")
    result = 1
    current = 1
    while current <= n:
        result *= current
        current += 1
    return result


def analyze_geometry():
    """Аналіз геометричної фігури (кола) з використанням умовних конструкцій."""
    print("--- 1. Геометричні розрахунки та умовні конструкції ---")
    radius = 7.5
    print(f"Радіус кола: {radius}")
    
    if radius <= 0:
        print("Помилка: радіус має бути додатним числом.")
    else:
        area = math.pi * (radius ** 2)
        perimeter = 2 * math.pi * radius
        print(f"  Площа кола: {area:.2f}")
        print(f"  Периметр (довжина) кола: {perimeter:.2f}")
        
        # Умовна розширена логіка
        if area > 100:
            print("  [Аналіз]: Велика геометрична фігура (площа > 100).")
        else:
            print("  [Аналіз]: Компактна геометрична фігура.")
    print()


# =====================================================================
# 2. Робота зі структурами даних (Списки, кортежі, словники)
# =====================================================================
def demonstrate_data_structures():
    print("--- 2. Демонстрація роботи зі структурами даних ---")
    
    # 1. Кортеж (незмінна структура для фіксованих параметрів конфігурації)
    system_config = ("КБ-25", "Григор'євська", 2026)
    print(f"Студентська конфігурація (tuple): Група - {system_config[0]}, Студент - {system_config[1]}, Рік - {system_config[2]}")
    
    # 2. Список (мутабельна послідовність числових значень)
    grades = [92, 85, 78, 95, 88, 90]
    print(f"Початковий список оцінок: {grades}")
    grades.append(97)  # додавання елемента
    grades.sort(reverse=True)  # сортування за спаданням
    print(f"Оновлені та відсортовані оцінки (list): {grades}")
    
    # 3. Словник (асоціативний масив для зберігання зведених даних)
    summary_report = {
        "student": system_config[1],
        "group": system_config[0],
        "max_grade": max(grades),
        "min_grade": min(grades),
        "average_grade": sum(grades) / len(grades)
    }
    
    print("Зведений звіт (dict):")
    for key, value in summary_report.items():
        if isinstance(value, float):
            print(f"  {key}: {value:.2f}")
        else:
            print(f"  {key}: {value}")
    print()


# =====================================================================
# 3. Ітератори та Генератори
# =====================================================================
class CountdownIterator:
    """Користувацький клас-ітератор для зворотного відліку."""
    def __init__(self, start: int):
        self.current = start

    def __iter__(self):
        return self

    def __next__(self):
        if self.current < 0:
            raise StopIteration
        val = self.current
        self.current -= 1
        return val


def fibonacci_generator(n: int):
    """Генератор для послідовного виведення перших n чисел Фібоначчі."""
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b


def demonstrate_iterators_and_generators():
    print("--- 3. Демонстрація ітераторів та генераторів ---")
    
    # Використання власного ітератора
    print("Робота кастомного ітератора (Зворотний відлік від 3 до 0):")
    countdown = CountdownIterator(3)
    for number in countdown:
        print(f"  Відлік: {number}")
        
    # Використання генератора
    n_terms = 7
    print(f"\nРобота генератора (Перші {n_terms} чисел Фібоначчі):")
    fib_gen = fibonacci_generator(n_terms)
    for fib_val in fib_gen:
        print(f"  {fib_val}", end=" ")
    print("\n")


# =====================================================================
# Головна точка входу програми
# =====================================================================
if __name__ == "__main__":
    print("=" * 65)
    print(" ЗАПУСК КОНСОЛЬНОЇ ПРОГРАМИ: САМОСТІЙНА РОБОТА №1")
    print(" Виконано студенткою групи КБ-25: Григор'євська")
    print("=" * 65 + "\n")
    
    # Виклик розрахунку факторіала
    test_num = 5
    fact_res = calculate_factorial(test_num)
    print(f"Факторіал числа {test_num} дорівнює: {fact_res}\n")
    
    # Виклик інших блоків демонстрації
    analyze_geometry()
    demonstrate_data_structures()
    demonstrate_iterators_and_generators()
    
    print("=" * 65)
    print(" ПРОГРАМУ УСПІШНО ВИКОНАНО")
    print("=" * 65)
