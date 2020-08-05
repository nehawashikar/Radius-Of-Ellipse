# Ellipse_20475
/*
 * Homework 8, Date Due: 8/7/20
 * Author: Neha Washikar
 * and open the template in the editor.
 */

/**
 *
 * @author nehawashikar
 */
import java.util.*;

public class Ellipse_20475 {
    double minorRadius, majorRadius; 
    
    public Ellipse_20475( ) {
        double minorRadius =1, majorRadius =1;        
    }
    
    public Ellipse_20475(double minorRadius, double majorRadius) {        
    }
    
    /**
     * @param args the command line arguments
     */
    /** public void main(String[] args) {
        
        System.out.println("This program calculates the focus, area, " + 
                "and circumference of an ellipse");
        
        int status = validateInput(majorRadius, minorRadius);
        
        if (status== -1)
            System.out.println("Error: the input cannot be negative");
        else if (status == -2)
            System.out.println("Error: the major radius must not be " +
                    "smaller than the minor radius");
        else {
            System.out.println("Enter the major radius value or enter -1 to exit: " +
                getMajorRadius());
        
            while (majorRadius != -1) {
                System.out.println("Enter the minor radius value: " + 
                        getMinorRadius());        
                System.out.println("The focus of the ellipse is " + 
                        getEllipseFocus());        
                System.out.println("The ellipse area is " + 
                        getEllipseArea());
                System.out.println("The ellipse circumference is " + 
                        getEllipseCircumference());
            }
            
            System.out.print("Goodbye");
            
            

        }
    }*/
    
    /**
     * Perform Unit Test of an ellipse
     * @param majorRadius major radius
     * @param minorRadius minor radius
     */
public static void testEllipse(double majorRadius, double minorRadius)
 {
        int status = validateInput(majorRadius, minorRadius);
        
        if (status == -1)
            System.out.println("Ellipse (" + majorRadius+ ", " + minorRadius + 
                    ") has a negative radius.");
        else if (status == -2) 
            System.out.println("Ellipse (" + majorRadius+ ", " + minorRadius + 
                    ") cannot have major radius < minor radius");
        else 
        {
            Ellipse_20475 ellipse = new Ellipse_20475(majorRadius, minorRadius);
            System.out.println("The ellipse major radius is " + 
                    ellipse.getMajorRadius());
            System.out.println("The ellipse minor radius is " + 
                    ellipse.getMinorRadius());
            System.out.printf("The ellipse focus is %.2f\n" , 
                    ellipse.getEllipseFocus());
            System.out.printf("The ellipse area is %.2f\n", 
                    ellipse.getEllipseArea());
            System.out.printf("The ellipse circumference is %.2f\n" , 
                    ellipse.getEllipseCircumference());
        }
        
    }
    
    // main method for testing
    public static void main(String[] arg)
    {
        testEllipse(-1, 2);		// test negative major radius
        testEllipse(3, -2);		// test negative minor radius
        testEllipse(3, 5);		// test major radius < minor radius
        testEllipse(5.5, 3.3);		// good ellipse
    }

    
    public double getMajorRadius ( ) {
        Scanner keyboard = new Scanner(System.in);
        majorRadius = keyboard.nextDouble();
        return majorRadius;
    }
    
    public double getMinorRadius ( ) {
        Scanner keyboard = new Scanner(System.in);
        minorRadius = keyboard.nextDouble();
        return minorRadius;
    }
    
    public double getEllipseFocus ( ) {
        double focus;
        focus= Math.sqrt(Math.pow(majorRadius, 2) - Math.pow(minorRadius, 2));
        return focus;
    }
    
    public double getEllipseArea ( ) {
        double area;
        area= Math.PI * majorRadius * minorRadius;
        return area;
    }
    
    public double getEllipseCircumference ( ) {
        double circ;
        circ = Math.PI*(3*(majorRadius+minorRadius)- Math.sqrt((10*majorRadius*
                minorRadius) + 3*(Math.pow(majorRadius, 2)+ 
                Math.pow(majorRadius, 2))));
        return circ;
    }
    
    public static int validateInput(double majorRadius, double minorRadius) {
        int status;
        
        if (majorRadius<= 0 || minorRadius <= 0)
            status= -1;
        else if (majorRadius <= minorRadius)
            
            status= -2;
        else 
            status=0;
        
        return status;
            
    }
}
