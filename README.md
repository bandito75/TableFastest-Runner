# TableFastest-Runner
import java.util.*;
public class FastestRunner {
// creates two arrays, one with name's of runners, and their other their times
// sorts the times and displays the fastest runner, and second
// with their name,time in minutes, and time in hours. 
	public static void main(String[] args) { 
		int numRun, fastRunner,secFastRunner;
	    numRun = 16;
	    
	   String [] name = inNames();
	   int [] time = inTime();
	   
		table(name,time,numRun);
		fastRunner = fastRun(name,time,numRun);
		secFastRunner = secFastRun(name,time,numRun,fastRunner);
		
		for(int i = 0; i<numRun; i++){
			if(fastRunner == time[i]){
			   System.out.println(name[i] + "\t" + "\t" + time[i] + " mins" + "\t" 
			                      + timeHour(fastRunner) + " hours");
			}
		}
		
		for(int i = 0; i<numRun; i++){
			if(secFastRunner == time[i]){
			   System.out.println("Second-best runner: ");
			   System.out.println(name[i] + "\t"  + "\t" + time[i] + " mins" + "\t" 
			                      + timeHour(secFastRunner) + " hours");
			}
		 }
	   }
	
	public static int[] inTime() {
		int[] times ={341, 273, 278, 329, 445, 402, 388, 275, 243, 334, 412, 
			      393, 299,343, 317, 265};
		return times;
	}

	public static String[] inNames() {
		String[] names = {"Elena", "Thomas", "Hamilton", "Suzie", "Phil", "Matt",
		      "Alex", "Emma", "John", "James", "Jane", "Emily", "Daniel", 
		      "Neda","Aaron", "Kate"};
		return names;
	}

	public static int fastRun(String[] name, int[] time, int numRun) {
		int fastNum;
		fastNum = 1000;
		for(int i = 0; i<numRun; i++){
			if(fastNum > time[i]){
			   fastNum = time[i];
			}
		}
		return fastNum;	
	}
   public static int secFastRun(String[] name, int[] time, int numRun, int fastNum) {
	   int secfastNum;
		secfastNum = 1000;
		for(int i = 0; i<numRun; i++){
			if(secfastNum > time[i] && time[i] > fastNum){
			   secfastNum = time[i];
			}
		}
		return secfastNum;
	}

	public static void table(String[] name, int[] time, int numRun) {
	   System.out.printf("%-12s%-18s%s\n", "Name", "Time(minutes)", "Time(hours)");
	   System.out.println("_____________________________________________");
		
	   for(int i = 0; i< numRun; i++){
		  if(name[i].length() <= 7){
			 System.out.printf(name[i] + "\t" + "\t" + time[i] + "\t" + "\t" + timeHour(time[i])+ "\n");
			 System.out.print("-----------------------------------------");
		  }else{
			 System.out.print(name[i] + "\t" + time[i] + "\t" + "\t" + timeHour(time[i])+ "\n");
			 System.out.print("-----------------------------------------");
		  }
		  System.out.println("");			
	   }
	   System.out.println("_____________________________________________\nFastest runner: ");
	}

	public static double timeHour(double x) {
	   double hour;
	   hour = 0;
		
	   while(x - 60 >= 0 ){
		  hour += 1;
		  x -= 60;
	   }
	   x = Math.abs(x);
	   hour += x/100;
	   return hour ;
	}
}
