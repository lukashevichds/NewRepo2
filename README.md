using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;


// Использовать перезагрузку методов
//10 вариант

namespace Новое_задание_от_Рыбакова_15_янв
{
    class SurfaceAreaCalculator
    {
        //Метод для расчета площади поверхности куба
        public static double CalculateSurfaceArea(double a)
        {
            return 6 * Math.Pow(a, 2);
        }

        // Метод для расчета площади поверхности прямоугольного параллелепипеда
        public static double CalculateSurfaceArea(double a, double b, double c)
        {
            return 2 * (a * b + a * c + b * c);
        }

        // Метод для расчета площади поверхности цилиндра
        public static double CalculateSurfaceArea(double r, double h)
        {
            return 2 * Math.PI * r * (r + h);
        }

        // Метод ля рассчета площади поверхности шара
        public static double CalculateSurfaceArea(double r)
        {
            return 4 * Math.PI * Math.Pow(r, 2);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Пример использования методов

            // Площадь поверхности куба со стороной 3
            double cubeSide = 3;
            double cubeSurfaceArea = SurfaceAreaCalculator.CalculateSurfaceArea(cubeSide);

            Console.WriteLine($"Площадь поверхности куба: {cubeSurfaceArea}");

            // Площадь поверхности прямоугольного параллелепипеда с размерами 2, 3, 4
            double length = 2, width = 3, height = 4;
            double rectangularPrismSurfaceArea = SurfaceAreaCalculator.CalculateSurfaceArea(length, width, height);
            Console.WriteLine($"Площадь поверхности прямоугольного параллелепипеда: {rectangularPrismSurfaceArea}");

            // Площадь поверхности цилиндра с радиусом 5 и высотой 10
            double radius = 5, cylinderHeight = 10;
            double cylinderSurfaceArea = SurfaceAreaCalculator.CalculateSurfaceArea(radius, cylinderHeight);
            Console.WriteLine($"Площадь поверхности цилиндра: {cylinderSurfaceArea}");

            // Площадь поверхности шара с радиусом 7
            double sphereRadius = 7;
            double sphereSurfaceArea = SurfaceAreaCalculator.CalculateSurfaceAreaSphere(sphereRadius);
            Console.WriteLine($"Площадь поверхности шара: {sphereSurfaceArea}");
        }
    }
}



//Рассчитать с помощью полиморфизма. 
using System;

abstract class Shape
{
    public abstract double CalculateSurfaceArea();
}

class Cube : Shape
{
    private double side;

    public Cube(double side)
    {
        this.side = side;
    }

    public override double CalculateSurfaceArea()
    {
        return 6 * Math.Pow(side, 2);
    }
}

class RectangularPrism : Shape
{
    private double length;
    private double width;
    private double height;

    public RectangularPrism(double length, double width, double height)
    {
        this.length = length;
        this.width = width;
        this.height = height;
    }

    public override double CalculateSurfaceArea()
    {
        return 2 * (length * width + length * height + width * height);
    }
}

class Cylinder : Shape
{
    private double radius;
    private double height;

    public Cylinder(double radius, double height)
    {
        this.radius = radius;
        this.height = height;
    }

    public override double CalculateSurfaceArea()
    {
        return 2 * Math.PI * radius * (radius + height);
    }
}

class Sphere : Shape
{
    private double radius;

    public Sphere(double radius)
    {
        this.radius = radius;
    }

    public override double CalculateSurfaceArea()
    {
        return 4 * Math.PI * Math.Pow(radius, 2);
    }
}

class Program
{
    static void Main(string[] args)
    {
        Shape[] shapes = new Shape[]
        {
            new Cube(3),
            new RectangularPrism(2, 3, 4)
            new Cylinder(5, 10)
            new Sphere(6)
        };

        foreach (var shape in shapes)
        {
            Console.WriteLine($"Площадь поверхности: {shape.CalculateSurfaceArea()}");
        }
    }
}
