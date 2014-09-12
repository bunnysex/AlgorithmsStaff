AlgorithmsStaff
===============

staffs
package jeebus;
import java.util.*;
import java.math.*;
public class Jeebus {

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);	
	double[][] MatrixOfElements = new double [8][4];
	
	//Inferior Limits
	MatrixOfElements [0][0] = 0.01;
        MatrixOfElements [1][0] = 5952.85;
        MatrixOfElements [2][0] = 50524.93;
        MatrixOfElements [3][0] = 88793.05;
        MatrixOfElements [4][0] = 103218.01;
        MatrixOfElements [5][0] = 123580.21;
        MatrixOfElements [6][0] = 249243.49;
        MatrixOfElements [7][0] = 392841.97;
        
        //Superior Limits
        MatrixOfElements [0][1] = 5952.84;
        MatrixOfElements [1][1] = 50524.92;
        MatrixOfElements [2][1] = 88793.04;
        MatrixOfElements [3][1] = 103218.00;
        MatrixOfElements [4][1] = 123580.20;
        MatrixOfElements [5][1] = 249243.48;
        MatrixOfElements [6][1] = 392841.96;
        //Slot Section 7-1 has no limit therefor the only comparison will be made if it's higher then the below.
        
        //Fixed Fee
        MatrixOfElements [0][2] = 0.00;
        MatrixOfElements [1][2] = 114.24;
        MatrixOfElements [2][2] = 2966.76;
        MatrixOfElements [3][2] = 7130.88;
        MatrixOfElements [4][2] = 9438.6;
        MatrixOfElements [5][2] = 13087.44;
        MatrixOfElements [6][2] = 39929.04;
        MatrixOfElements [7][2] = 73703.4;
        
        //Percentage of taxation
        MatrixOfElements [0][3] = 1.92;
        MatrixOfElements [1][3] = 6.4;
        MatrixOfElements [2][3] = 10.88;
        MatrixOfElements [3][3] = 16.0;
        MatrixOfElements [4][3] = 17.92;
        MatrixOfElements [5][3] = 21.36;
        MatrixOfElements [6][3] = 23.52;
        MatrixOfElements [7][3] = 30.0;
        /* Exercise 11
        System.out.println("Hey, how much do ya get paid, mate?");
        double IA = s.nextDouble();
        double rsresult = ISR(IA, MatrixOfElements);
        System.out.println(rsresult);
                ;*/
        
        /*Exercise 1
        System.out.println("Gimme a sentence or somethin' mate.");
        String Exer1 = s.nextLine();
        String replaceAll = Exer1.replaceAll("\\s+","");
        int hml = replaceAll.length();
        System.out.println(replaceAll);
        System.out.println(hml);
        /*int Howmanyletters = Exer1.length();
        System.out.println(Howmanyletters);*/
        
        /*Exercise 2
        System.out.println("Gimme a sentence or somethin' mate.");
        System.out.println("Note: Sentence must begin with a Char and end with a char");
        String Exer2 = s.nextLine();
        int Wordcounter = 0;
        for(int i=0; i<Exer2.length();i++)
        {
            if(Exer2.charAt(i) == ' ')
            {
                Wordcounter++;
            }
            if( i == Exer2.length()-1)
            {
                Wordcounter++;
            }
        }
        System.out.println(Wordcounter);*/
        
        /*Exercise 3
        System.out.print("How long do you want the rectangle: ");
        int inputX = s.nextInt();
        System.out.print("How high do you want the rectangle: ");
        int inputY = s.nextInt();
        System.out.println();
        
        System.out.println("What coordinate do you want to confirm its residence");
        System.out.print("Give me it's X: ");
        int checkX = s.nextInt();
        System.out.print("Give me it's Y: ");
        int checkY = s.nextInt();
        System.out.println();
        boolean residence = false;
        if(checkX>=0&&checkX<=inputX&&checkY>=0&&checkY<=inputY)
        {
            residence = true;
        }
        if(residence)
        {
            System.out.println("Yep, it's there all right");
        }
        else
        {
            System.out.println("Nah captain, it aint there");
        }*/
        
        System.out.println("Give me a POSITIVE number to run in my 'Is Prime' machine");
        int pCh = s.nextInt();
        if(isPrime(pCh)){System.out.println("Yep it's prime.");}
        else{            System.out.println("Nop, all clear captain.");}
    }
    public static boolean isPrime(int pCh)
    {
        boolean isPrime = true;
        if(pCh <4 || pCh == 5 || pCh == 7){return true;}
        if(pCh % 2 == 0){return false;}
        if(pCh % 3 == 0){return false;}
        for(int i=5; i<= Math.sqrt(pCh);i+=2)
        {
            if(pCh%i==0){return false;}
        }
        
        return isPrime;
    }
    public static double ISR(double IA, double[][] x)
    {
      double CF = 0.0;
      double PC = 1.92;
      double IL = 0.0;
      boolean Continue = true;
      
      for(int i=7; i> -1 ; i--)
      {
          if(Continue)
          {
              if(IA>=x[i][0])
              {
                  IL = x[i][0];
                  CF = x[i][2];
                  PC = x[i][3];
                  Continue = false;
              }
              else if(x[i][0]<= IA && IA <= x[i][1])
              {
                  IL = x[i][0];
                  CF = x[i][2];
                  PC = x[i][3];
                  Continue = false;
              }
          }
      }
      /*
      Notes:
      IL = Limite inferior
      CF = Cuota Fija
      IA = Ingreso Anual
      PC = Porcentaje aplicado
      */
      double ISRre = CF+(IA-IL)*PC/100;
      return ISRre;
    }
    
    public int Howmanyletters(String x){
	return x.length();
}
}
/*
if(IA >= x[7][0])
      {
          IL = x[7][0];
          CF = x[7][2];
          PC = x[7][3];
      }
      if(x[6][0]<= IA && IA <= x[6][1])
      {
         IL = x[6][0];
         CF = x[6][2];
         PC = x[6][3];
      }
      if(x[5][0]<= IA && IA <= x[5][1])
      {
         IL = x[5][0];
         CF = x[5][2];
         PC = x[5][3];
      }
      if(x[4][0]<= IA && IA <= x[4][1])
      {
         IL = x[4][0];
         CF = x[4][2];
         PC = x[4][3];
      }
      if(x[3][0]<= IA && IA <= x[3][1])
      {
         IL = x[3][0];
         CF = x[3][2];
         PC = x[3][3];
      }
      if(x[2][0]<= IA && IA <= x[2][1])
      {
         IL = x[2][0];
         CF = x[2][2];
         PC = x[2][3];
      }
      if(x[1][0]<= IA && IA <= x[1][1])
      {
         IL = x[1][0];
         CF = x[1][2];
         PC = x[1][3];
      }
      if(x[0][0]<= IA && IA <= x[0][1])
      {
         IL = x[0][0];
         CF = x[0][2];
         PC = x[0][3];
      }
*/
