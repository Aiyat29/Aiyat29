import java.util.Scanner;

abstract class Shape {
    protected String name;

    public Shape(String name) {
        this.name = name;
    }

    public abstract double getArea();

    public abstract double getPerimeter();
}

class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(String name, double width, double height) {
        super(name);
        this.width = width;
        this.height = height;
    }

    
    public double getArea() {
        return width * height;
    }

    
    public double getPerimeter() {
        return 2 * (width + height);
    }
}

class Circle extends Shape {
    private double radius;

    public Circle(String name, double radius) {
        super(name);
        this.radius = radius;
    }

    @Override
    public double getArea() {
        return Math.PI * radius * radius;
    }

    @Override
    public double getPerimeter() {
        return 2 * Math.PI * radius;
    }
}

class Triangle extends Shape {
    private double side1;
    private double side2;
    private double side3;

    public Triangle(String name, double side1, double side2, double side3) {
        super(name);
        this.side1 = side1;
        this.side2 = side2;
        this.side3 = side3;
    }

    @Override
    public double getArea() {
        double s = (side1 + side2 + side3) / 2;
        return Math.sqrt(s * (s - side1) * (s - side2) * (s - side3));
    }

    @Override
    public double getPerimeter() {
        return side1 + side2 + side3;
    }
}

class Square extends Rectangle {
    public Square(String name, double side) {
        super(name, side, side);
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Choose a shape type:");
            System.out.println("1. Rectangle");
            System.out.println("2. Circle");
            System.out.println("3. Triangle");
            System.out.println("4. Square");
            System.out.println("5. Exit");
            System.out.print("Enter your choice: ");
            
            int choice = scanner.nextInt();
            scanner.nextLine();
            
            if (choice == 5) {
                break;
            }

            System.out.print("Enter the name of the shape: ");
            String name = scanner.nextLine();

            switch (choice) {
                case 1:
                    System.out.print("Enter width: ");
                    double width = scanner.nextDouble();
                    System.out.print("Enter height: ");
                    double height = scanner.nextDouble();
                    Rectangle rectangle = new Rectangle(name, width, height);
                    System.out.println("Area: " + rectangle.getArea());
                    System.out.println("Perimeter: " + rectangle.getPerimeter());
                    break;
                case 2:
                    System.out.print("Enter radius: ");
                    double radius = scanner.nextDouble();
                    Circle circle = new Circle(name, radius);
                    System.out.println("Area: " + circle.getArea());
                    System.out.println("Perimeter: " + circle.getPerimeter());
                    break;
                case 3:
                    System.out.print("Enter side1: ");
                    double side1 = scanner.nextDouble();
                    System.out.print("Enter side2: ");
                    double side2 = scanner.nextDouble();
                    System.out.print("Enter side3: ");
                    double side3 = scanner.nextDouble();
                    Triangle triangle = new Triangle(name, side1, side2, side3);
                    System.out.println("Area: " + triangle.getArea());
                    System.out.println("Perimeter: " + triangle.getPerimeter());
                    break;
                case 4:
                    System.out.print("Enter side length: ");
                    double sideLength = scanner.nextDouble();
                    Square square = new Square(name, sideLength);
                    System.out.println("Area: " + square.getArea());
                    System.out.println("Perimeter: " + square.getPerimeter());
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }

        scanner.close();
    }
}
