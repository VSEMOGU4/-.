Разработка математической модели для предсказания изменения высоты полета дрона в зависимости от времени.
Пример кода математической модели полета на Python может варьироваться в зависимости от конкретной цели и уравнений, которые вы хотите смоделировать. Вот пример кода для симуляции простого движения тела под углом в 2D пространстве (баллистическая траектория без учета сопротивления воздуха):
import math
import matplotlib.pyplot as plt

# Константы
g = 9.81  # Ускорение свободного падения (м/с^2)

# Функция для расчета траекторий
def calculate_trajectory(v0, angle_deg):
    angle_rad = math.radians(angle_deg)  # Перевод угла в радианы
    v0x = v0 * math.cos(angle_rad)  # Горизонтальная компонента начальной скорости
    v0y = v0 * math.sin(angle_rad)  # Вертикальная компонента начальной скорости
    
    # Время в полете до достижения земли (рассчитываем как корня из квадратного уравнения)
    t_flight = 2 * v0y / g
    
    # Генерация временных точек
    t_points = [i * t_flight / 1000 for i in range(1001)]
    
    # Расчет координат (x, y)
    x_points = [v0x * t for t in t_points]
    y_points = [v0y * t - 0.5 * g * t**2 for t in t_points]
    
    return x_points, y_points

# Входные параметры
initial_velocity = 50.0  # Начальная скорость в м/с
launch_angle = 45.0  # Угол запуска в градусах

# Получение траекторий
x, y = calculate_trajectory(initial_velocity, launch_angle)

# Отображение результатов
plt.figure(figsize=(10, 5))
plt.plot(x, y)
plt.title('Траектория полета')
plt.xlabel('Расстояние (м)')
plt.ylabel('Высота (м)')
plt.grid(True)
plt.show()

Этот код выполняет следующие действия:
Определяет ускорение свободного падения g.
Определяет функцию calculate_trajectory для расчета координат (x, y) по заданным начальной скорости v0 и углу запуска angle_deg.
Рассчитывает горизонтальную и вертикальную компоненты начальной скорости.
Определяет время полета и временные точки для расчета координат.
Рассчитывает координаты для каждой временной точки и возвращает их.
Использует библиотеку matplotlib для построения и отображения траектории полета.
Этот пример делает некоторые упрощения, такие как игнорирование сопротивления воздуха. Для более сложных и точных моделей потребуются дополнительные уравнения и параметры.
