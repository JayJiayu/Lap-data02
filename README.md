# Lap-data02
//stat coding


import java.util.Random;
import java.util.Scanner;

public class Blackjack {
    private int[] cardYou = new int[5];
    private int[] cardComputer = new int[2];
    private int sumYou,sumComputer = 0;
    private String winner;
    private boolean isEnd;
    
    //Initialize game data
    Random rand = new Random();
    
    public Blackjack(){
        //Player
        cardYou[0] = rand.nextInt(11)+1;
        cardYou[1] = rand.nextInt(11)+1;

                
        //Dealer
        cardComputer[0] = rand.nextInt(11)+1;
        cardComputer[1] = rand.nextInt(11)+1;     
        //Sum
        sumyou();
        sumComputer = cardComputer[0]+cardComputer[1];
        //Check both 11
        if(sumYou==22){
        	cardYou[1] = 1;
        	sumYou=12;
        }
        if(sumComputer==22){
        
            cardComputer[1] = 1;
            sumComputer=12;
        }
    }
    public int sumyou() {
    	sumYou = cardYou[0]+cardYou[1]+cardYou[2]+cardYou[3]+cardYou[4];
    	return sumYou;
    }
    public void showPlayerCard(){
    	System.out.print("You :");
    	for(int i=0;i<cardYou.length;i++) {
    		System.out.print(cardYou[i]+" ");
    	}
    	System.out.println();
    	System.out.println("Computer : ??");
    }
    public void showplayercard() {
    	System.out.print("You :");
    	for(int i=0;i<cardYou.length;i++) {
    		System.out.print(cardYou[i]+" ");
    	}
    	System.out.println();
    }
    public void showComputerCard(){
    	System.out.print("Computer : ");
    	for(int value:cardComputer) {
    		System.out.print(value+" ");
    	}
    	System.out.println();
    }
    
    public void showSumCard(){
    	System.out.println("Sum of your cards = "+sumYou);
    	System.out.println("Sum of Computer cards = "+sumComputer);
    	System.out.println();
    }
    
    public void checkWinner(){
 	
       if(sumYou>21){
           winner = "Computer";
           }    		
        else if (sumYou > sumComputer) {
    		winner = "You";
    		}
        else {
        	winner = "Computer";
        }
    }
    public String getwinner() {  	
    	return winner;
    }
    public boolean isEnd() {
    int sumnumber = sumyou() ;
    if(sumnumber > 21) {
    	return false;
    }
 	   return true ;
    }
    public void addMoreCard() { 
    	Scanner Sc = new Scanner(System.in);
    	int i = 1;   	
    	while(isEnd()){
    		
    		 System.out.print("Want another card? (y/n)...");
        	 char s = Sc.next().charAt(0); 
    		 i++;
    		 if(i==5) {
    			break;
    		 }
    		 if (s == 'n') {
       		 isEnd = false ;
       		    break;     		 
       	 	 }
    		 else if(s == 'y'){
       		 cardYou[i] = rand.nextInt(11)+1;
       		 sumyou();
       		 isEnd = true;
       	 	 }
         	showPlayerCard(); 
    	 }
    }	
    public static void main(String[] args){ 
        Blackjack bj = new Blackjack();
        bj.showPlayerCard();
        bj.addMoreCard();
        bj.showplayercard();
        bj.showComputerCard();        
        System.out.println();
        bj.showSumCard();
        bj.checkWinner();
        System.out.println("The winner is "+bj.getwinner());
    }
}
