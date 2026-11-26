# laba-2
Laba2

import math

def calculate_y(x: float) -> tuple:
    """
    Вычисляет значение кусочно-заданной функции.

    :param x: Аргумент функции
    :return: Кортеж (значение y, название участка, формула)
    :raises ValueError: Если x выходит за пределы области определения [-9, 9]
    """
    if -9 <= x <= -6:
        # 1. Левая полуокружность с центром (-6, 0)
        y = -math.sqrt(9 - (x + 6) ** 2)
        return y, "Левая полуокружность (центр в точке (-6, 0))", "y = -√(9 - (x + 6)²)"

    elif -6 < x < -3:
        # 2. Наклонная прямая от (-6, -3) до (-3, 0)
        y = x + 3
        return y, "Наклонная прямая (из (-6, -3) в (-3, 0))", "y = x + 3"

    elif -3 <= x <= 3:
        # 3. Центральная полуокружность с центром (0, 0)
        y = math.sqrt(9 - x ** 2)
        return y, "Центральная полуокружность (центр в точке (0, 0))", "y = √(9 - x²)"

    elif 3 < x <= 9:
        # 4. Наклонная прямая от (3, 0) до (9, 3)
        y = 0.5 * (x - 3)
        return y, "Наклонная прямая (из (3, 0) в (9, 3))", "y = 0.5 * (x - 3)"

    else:
        raise ValueError(f"Аргумент x={x} выходит за пределы области определения [-9, 9].")


def main():
    print("Программа для вычисления кусочно-заданной функции.")
    print("Область определения: x ∈ [-9, 9]")
    print()

    while True:
        user_input = input("Введите значение x (или 'q' для выхода): ").strip()

        if user_input.lower() in ('q', 'quit', 'exit'):
            print("Выход из программы.")
            break

        try:
            x = float(user_input)
            y, section, formula = calculate_y(x)

            print(f"Значение x: {x}")
            print(f"Участок: {section}")
            print(f"Формула: {formula}")
            print(f"Результат: y = {y:.4f}")
            print()

        except ValueError as e:
            if "could not convert" in str(e).lower():
                print("Ошибка: пожалуйста, введите корректное число.")
                print()
            else:
                print(f"Ошибка: {e}")
                print()
        except Exception as e:
            print(f"Непредвиденная ошибка: {e}")
            print()


if __name__ == "__main__":
    main()