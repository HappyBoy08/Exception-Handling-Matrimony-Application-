# Exception-Handling-Matrimony-Application-
package Matrimony;
import java.util.Scanner;

class OverAgeException extends Exception
{
	public String getMessage()
    {
	  return" We don't Entertain Senior Citizen's profile for the Matrimony";
	}
}

class UnderAgeException extends Exception
{
	public String getMessage()
	{
		return "We don't Entertain Minor's profile for the Matrimony";
	}
}
class MatrimonyCandidate
{
	int age;
	void getData()
	{
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter the age :");
		age= sc.nextInt();
	}
	void Verify() throws OverAgeException,UnderAgeException
	{
		if(age>60)
		{
			OverAgeException oae = new OverAgeException();
			System.out.println(oae.getMessage());
			throw oae;
		}
		else if(age<18)
		{
			UnderAgeException oae = new UnderAgeException();
			System.out.println(oae.getMessage());
			throw oae;
		}
		else
		{
			System.out.println("Welcome to the World of Matrimony . Please Subscribe by Paying 5000Rs to your Account");
		}
		
	}
}
class MatrimonyApp
{
	void useApp(MatrimonyCandidate mc)
	{
		try
		{
			mc.getData();
			mc.Verify();
		}
		catch(OverAgeException|UnderAgeException e1)
		{
			try
			{
				mc.getData();
				mc.Verify();
			}
			catch(OverAgeException|UnderAgeException e2)
			{
				try
				{
					mc.getData();
					mc.Verify();
				}
				catch(OverAgeException|UnderAgeException e3)
				{
					System.out.println("Candidate Account is Blocked ");
				}
				
			}
			
		}
	}
}
public class LaunchMatrimony {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		MatrimonyCandidate mc1= new MatrimonyCandidate();
		MatrimonyCandidate mc2= new MatrimonyCandidate();
		MatrimonyCandidate mc3= new MatrimonyCandidate();
		MatrimonyCandidate mc4= new MatrimonyCandidate();
		MatrimonyApp mapp = new MatrimonyApp();
		System.out.println("Candidate-1");
		mapp.useApp(mc1);
		System.out.println("Candidate-2");
		mapp.useApp(mc2);
		System.out.println("Candidate-3");
		mapp.useApp(mc3);
		System.out.println("Candidate-4");
		mapp.useApp(mc4);

	}

}




