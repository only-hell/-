#include <iostream>
#include "triangle.h"

using namespace std;

int main()
{
    // Переменные для хранения координат точек
    float x1, y1, x2, y2, x3, y3;
    float offsetX, offsetY;

    // Ввод координат точек треугольника
    cout << "Enter coordinates of the first point (x y): ";
    cin >> x1 >> y1;
    cout << "Enter coordinates of the second point (x y): ";
    cin >> x2 >> y2;
    cout << "Enter coordinates of the third point (x y): ";
    cin >> x3 >> y3;

    // Проверяем, не образуют ли введенные точки вырожденный треугольник
    if ((x1 == x2 && y1 == y2) || (x1 == x3 && y1 == y3) || (x2 == x3 && y2 == y3)) {
        cout << "Error: Entered points form a degenerate triangle!" << endl;
        return 1;
    }

    // Создаем треугольник на основе введенных точек
    Triangle triangle(Point(x1, y1), Point(x2, y2), Point(x3, y3));

    // Выводим координаты точек треугольника
    cout << "Coordinates of points of the triangle:" << endl;
    cout << "Point 1: (" << triangle.point1().x() << ", " << triangle.point1().y() << ")" << endl;
    cout << "Point 2: (" << triangle.point2().x() << ", " << triangle.point2().y() << ")" << endl;
    cout << "Point 3: (" << triangle.point3().x() << ", " << triangle.point3().y() << ")" << endl;

    // Вводим значения сдвига по осям X и Y
    cout << "\nEnter offset values along X and Y axes: ";
    cin >> offsetX >> offsetY;

    // Сдвигаем треугольник
    triangle.Shift(offsetX, Axis::x);
    triangle.Shift(offsetY, Axis::y);

    // Выводим координаты точек треугольника после сдвига
    cout << "\nCoordinates of points of the triangle after shifting:" << endl;
    cout << "Point 1: (" << triangle.point1().x() << ", " << triangle.point1().y() << ")" << endl;
    cout << "Point 2: (" << triangle.point2().x() << ", " << triangle.point2().y() << ")" << endl;
    cout << "Point 3: (" << triangle.point3().x() << ", " << triangle.point3().y() << ")" << endl;

    return 0;
}
