# ArrayIndexOutOfBounds
/* 
   Write a program that meets the following requirements:
   1. Creates an array with 100 randomly chosen integers
   2. Prompts the user to enter the index of the array, then displays the corresponding element value. If the specified
      index is out of bounds, display the message "Out of Bounds".
 */
      
public class Array100 
{
    public static final Scanner input = new Scanner (System.in);
    public static boolean repeat = false;

    public static void main(String[] args) 
    {   
        int num = 0;
        System.out.println("This program will have an array with 100 random numbers. When you enter a number between 1 and 100, a random number will be displayed.");
        
        do
        {
            System.out.println("Please enter a number between 0 and 99: ");
            
            //This will check if the input from the user is an integer
            while(!input.hasNextInt())
            {  
                System.out.println("Invalid input. Please enter a valid number.");
                input.next();
            }
            num = input.nextInt();
           
          
            //This will take the user's input and call the array index method
            arrayIndex(num);

            System.out.println("Would you like to exit the program? To exit the program, please enter 1. If you would like to try a new"
                    + " number, enter 2.");
                    + 
            //This will call the runAgain method to prompt the user if they want to re-run the program.
            runAgain();
            
        }while(repeat);
        

    }
    
    
    //This method will store 100 random numbers in the array and lets the main method know that this method may cause an exception
    public static void arrayIndex(int num) throws ArrayIndexOutOfBoundsException
    {
        final int SIZE = 100;
        int [] array = new int [SIZE];
        
        for(int count = 0; count < array.length; count++)
        {
            //This will store random integers in the array
            array[count] = (int)(Math.random() * 100);
        }
    
        //This will attempt to print out the result of the chosen index in the array
        try
        {
            System.out.println("Your random number is: " + array[num]);
        }
        catch(ArrayIndexOutOfBoundsException ex)
        {
            System.out.println("Out of Bounds");
        }
    }
    
    
    //This method will take user input on whether they would like to re-run the program to try a new index or not
    public static boolean runAgain()
    {
        int option = 0;
        boolean check = false;
        
        do
        {
            while(!input.hasNextInt())
            {  
                System.out.println("Invalid input. Please enter a valid number.");
                input.next();
            }    
            option = input.nextInt();

            if (option < 1 || option > 2)
            {
                System.out.println("Invalid input. Please enter either 1 to quit the program or 2 to start over.");
                //input.next();
                check = true;
            }
            
            switch (option) 
            {
                case 1:
                    check = false;
                    repeat = false;
                    System.out.println("Thank you for running the program!");
                    break;
                    
                case 2:
                    check = false;
                    repeat = true;
                    break;
            }

        }
        while(check);

        return repeat;
    
    }
    
}

//============================================================== NO MORE CODE FOLLOWS =======================================================
