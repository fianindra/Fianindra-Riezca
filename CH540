package HW2Thread;

import java.util.Random;

public class HW2PidThread {
  
   //Declare the range of pid values
           private staticfinal int MIN_PID = 300;
           private staticfinal int MAX_PID = 5000;
          
           //memorylocation
           private staticint[] pids;
          
           //memory tostory the pids
           public staticint allocatMap() {
             
              pids = new int[MAX_PID - MIN_PID];
             
              if (pids == null) {
                  System.out.println("Memoryallocation failed. ");
                  return -1;
              }
             
              for (int i=0; i<pids.length; i++) {
                  pids[i] = 0;
              }
             
              System.out.println("Memory allocatedsuccessfully. ");
              return 1;
           }
          
           //This methodused to allocated and return a pid
           public staticint allocatPID() {
             
              if(pids == null) {
                  System.out.println("PIDManager is not initialized. ");
                  return -1;
              }
             
              int PidNum = -1;
             
              for(int i=0; i<pids.length; i++) {
                  if (pids[i] ==0) {
                      pids[i] =1;
                      PidNum = i+ MIN_PID;
                     break;
                  }
              }
          
              return PidNum;
           }
           public staticvoid releasePID(int PidNum) {
             
              if (pids == null) {
                  System.out.println("PIDManager is not initialized ");
                  return;
              }
             
              if (PidNum<MIN_PID || PidNum>MAX_PID){
                  System.out.println("Given PIDis out or Range");
              }
             
              int NewPid = PidNum - MIN_PID;
              if (pids[NewPid] == 0) {
                  System.out.println("PID " +PidNum + " is already released ");
                  return;
              }
             
              pids[NewPid] = 0;
           }
   public static void main(String[] args) {
       allocatMap();
       //Creating object for classThreadrun
       Runnable run = newThreadrun();
       //initalizing an array size
       Thread threads[] = newThread[1000];
  
       //Using for loop for 100thread
       for (int i =0;i<100;i++) {
           threads[i] = newThread(run,i + " ");
          threads[i].start();
       }
      

   }
  
   public static class Threadrun implementsRunnable{
       public void run() {
           Thread t =Thread.currentThread();
           int PID;
           int time;
          
           //Initializedrandom object for sleeping random amount of time
           Random rand =new Random();
          
           time =rand.nextInt(1000);
           try {
              PID = allocatPID();
              System.out.println("Thread " + t.getName()+"request pid " + PID);
              System.out.println("Thread " + t.getName()+"sleeping for " + time);
             
              Thread.sleep(time);
              System.out.println("Thread " + t.getName()+"released PID ");
             
              releasePID(PID);
           } catch(InterruptedException e) {
              e.printStackTrace();
           }
       }
  
       }
   }
