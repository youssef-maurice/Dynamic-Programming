import java.util.*;

public class DP {

    public static int weight(int[] plates) {
        int rows= plates.length + 1;
        int cols= 1001;
        //We are going to use the same approach used to solve the
        //knapsack problem
        //create a matrix (2D array), where the number of rows is the
        //number of plates+1, and the number of columns is 1001
        int[][] matrix = new int[rows][cols];
        //if plates only has one element, return it
        if(plates.length==1){
            return plates[0];
        }
        //initialize all the slots in the first column to 0
        for(int row=0; row<rows; row++){
            matrix[row][0]=0;
        }
        //initialize all the slots in the row column to 0
        for(int w= 0; w<cols; w++){
            matrix[0][w]=0;
        }
        //array to store all plates over or equal the weight limit (1000)
        int[] over= new int[plates.length];
        //this code was taken from the knapsack problem slides
        //from the lectures
        for(int i= 1; i<rows; i++){
            for(int w= 1; w<cols; w++){
                if(plates[i-1] >= 1000){
                    over[i-1]= plates[i-1];
                }
                //if plate is heavier than the weight limit (wi)
                if(plates[i-1] > w){
                    //do not choose plate
                    matrix[i][w]=matrix[i-1][w];
                } else{
                    //take the maximum between the following:
                    //1)the plate not being chosen
                    //2)the plate being chosen
                    matrix[i][w]= Math.max(matrix[i-1][w], plates[i-1]+matrix[i-1][w-plates[i-1]]);
                }
            }
        }
        //get biggest value stored in the matrix
        int num= matrix[rows-1][cols-1];
        int w = 1000;
        int n= rows-1;
        //array to store the plates that were used
        int[] used= new int[plates.length];
        //array to store the plates that were not used
        int[] notused= new int[plates.length];
        for (int row = n; row > 0 && num > 0; row--) {
            //if the value is not the same as the one above it, 
            //that means we used it
            if (!(num == matrix[row - 1][w])){
                //add the plate to the array used at the same index
                used[row-1]=plates[row-1];
                //update the value we are checking
                num = num - plates[row - 1];
            }
        }

        for(int i= 0; i< plates.length; i++){
            //if plate is not in the array used
            if(plates[i]!=used[i]){
                //add plate to the array notused
                notused[i]=plates[i];
            }
        }
        //sort the array notused
        Arrays.sort(notused);
        int min_notused=0;
        //get the smallest plate not used
        for(int i: notused){
            if(i!=0){
                min_notused=i;
                //stop loop after encountering the first plates that is !=0
                break;
            }
        }
        //sort the array over
        Arrays.sort(over);
        int min_over=0;
        //get the smallest plate over the weight limit (1000)
        for(int i: over){
            if(i!=0){
                min_over=i;
                //stop loop after encountering the first plates that is !=0
                break;
            }
        }
        //biggest possible value under 1000
        int under= matrix[rows-1][cols-1];
        if(min_over!=0 && min_notused!=0){
            //if the difference between the smallest value bigger than or equal to 1000
            //is smaller than the difference between 1000 and the biggest value
            //under 1000. And if that value is less than the biggest value under 1000 +
            //the smallest plate not used.
            if((min_over-1000)<=1000-under && min_over<=(under+min_notused)){
                return min_over;
            }
            //the biggest value under 1000 + the smallest plate not used is smaller than
            //the smallest value over 1000. And if the difference between the biggest value
            // under 1000 and the smallest value over 1000 is the same, return the latter
            if((under+min_notused)<=min_over&&(under+min_notused)-1000<=1000-under){
                return under+min_notused;
            }
        }
        //if the difference between the biggest value under 1000 and
        //the smallest value over 1000 is the same, return the latter
        if((under+min_notused)-1000<=1000-under){
            return under+min_notused;
        }
        //if not return the biggest value under 1000
        return under;
    }
}
