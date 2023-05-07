---
title: Intercourse Pathing
author: Zhen
date: 2023-05-04
categories: [Projects, University Projects]
tags: [Projects, Cpp]
pin: true
---

# COMP3600 Course Project
[Source Code](https://github.com/WangZhen-Ryan/Shortest-path-analysis)

A software focuses on discovering connectivity between regions along with multiple fun features.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

Support for Linux envirment

### Installing
First navigate to the target folder
Then, In terminal:
    type 'g++ -std=c++11 Final-Project-source-code.cpp FD'
    then type './FD testFileName.txt'    

    Note there are a range of test to choose from
The interface will display several choice for you
  'Press 1 to select input from test file to test whole project, Press 2 to select input from command line, Press 3 to test each individual fsunctionality with test file'
  namely, enter 1 to start the whole program with the testFileName test file
               enter 2 to passing command by typing it one by one(manual mode in below DEMO part)
               enter 3 to test each individual functionality with testFileName test file
After enter 1, the plane and heap will be displayed, please scroll up the mouse for the plane size is so big
After enter 2, you enter the manual mode to type in instruction one by one
After enter 3, the interface will display several choice for you
        'Press 1 to test min-heap, Press 2 to test hash map, Press 3 to test Dijkstra's algorithm'
        namely, enter 1 to test min-heap with the testFileName test file 
                     enter 2 to test hash map with the testFileName test file 
                     enter 3 to test Dijkstra with the testFileName test file 
                     
                     
                     
Note that the heap test file is: test-f1-1.txt, test-f1-2.txt, test-f1-3.txt, test-f1-4.txt, test-f1-5.txt
                the hash map test file is: test-f2-1.txt, test-f2-2.txt, test-f2-3.txt, test-f2-4.txt, test-f2-5.txt
                the Dijkstra test file is: test-f3-1.txt, test-f3-2.txt, test-f3-3.txt, test-f3-4.txt, test-f3-5.txt
and a simple test for the whole program is: testwhole.txt

## Instruction

There two ways of passing command, typing command in the I/O port or passing the initialization is a .txt file in an expected format.

A list of command you may use:
1. quit         # quit the I/O
2. help        # print out instruction to help you start
3. clear       # clear the map
4. line  x1 y1 x2 y2       # line two point up
5. point x1 y1               # fill one point
6. region x1 y1 x2 y2 x3 y3 x4 y4  # draw a hollow region, please pass the two points coordinates in a circling order
7. obstacle x1 y1 x2 y2 x3 y3 x4 y4  # draw a hollow obstacle 
8. sphallway x1 y1 x2 y2 x3 y3 x4 y4  # draw a hollow obstacle
9. Dijkstra peoplename x0 y0 x1 y1        # run Dijkstra's algorithm on two region with people, x1 y1 is the coordinates of the destination while x0 and y0 is the current people's location
10. people name x1 x2          # add new people to the region
11. info              # print out all the current shapes and people's information, which might be a lot clear to see then the plane drawing shapes 

Demo symbols:
    symbol '-' is for pathway -> the '-' means a hallway
    symbol '*' is for region
    symbol '#' is for obstacles
    symbol '^' is for people



## Demo 

### auto input mode 
Inputing Demo example:
    type 'g++ -std=c++11 Final-Project-source-code.cpp FD'
    then type './FD testwhole.txt'  
    then select '1'
    
    
### manual input mode 
Inputing Demo example:
    Step1:  type in  'region 0 0 10 0 10 10 0 10'
    Step2:  type in  'sphallway 10 10 10 20 20 20 20 10  '
    Step3:  type in  'obstacle 10 20 20 20 20 30 30 20'
    Step4:  type in  'region 15 0 20 0 20 20 15 20'
    Step5:  people alice 0 1
    Step6:  Dijkstra alice 15 15 
The plane now is 
***********    ******                                                                                                                                
^         *    *    *                                                                                                                                
*         *    *    *                                                                                                                                
*         *    *    *                                                                                                                                
*         *    *    *                                                                                                                                
*         *    *    *                                                                                                                                
*         *    *    *                                                                                                                                
*         *    *    *                                                                                                                                
*         *    *    *                                                                                                                                
*         *    *    *                                                                                                                                
**********-----*----*                                                                                                                                
          -    *    *                                                                                                                                
          -    *    *                                                                                                                                
          -    *    *                                                                                                                                
          -    *    *                                                                                                                                
          -    *    *                                                                                                                                
          -    *    *                                                                                                                                
          -    *    *                                                                                                                                
          -    *    *                                                                                                                                
          -    *    *                                                                                                                                
          -----******##########                                                                                                                      
                    #       #                                                                                                                        
                    #      #                                                                                                                         
                    #     #                                                                                                                          
                    #    #                                                                                                                           
                    #   ##                                                                                                                           
                    #  #                                                                                                                             
                    # #                                                                                                                              
                    ##                                                                                                                               
                    #                                                                                                                                
                    #                                     
                                                 
Dijkstra alice 15 15  is executed 
Dijkstra condition are not meet please check closely 
transfer connectivity successfully                                                
                                                
The binary heap now is 
Heap is  0 1 2 10.0499 1 5 3 10.4403 10.198 3 1 16.4012 22.3607 4 6 13.4536 10.7703 12.2066 10.198 5 4 2 14.1421 17.2047 18.868 23.3238 22.8254 25 7 9 11.1803 14.1421 14.1421 12.8062 11.1803 20.6155 12.8062 11.6619 10.4403 15.0333 10.0499 7 8 15 6 18.0278 14.8661 26.2488 19.7231 21.4709 25 27.5862 25.6125 22.8254 23.3238 26.2488 25.6125 22.8254 8 15.6205 14.8661 17.2047 12.2066 18.868 22.3607 17 16 19 23.8537 24.4131 11.6619 23.8537 22.8254 20.025 13.4536 21.1896 20.8806 26.2488 10.7703 18.0278 15.1327 15.2971 16.5529 16.1555 21.2132 23.4307 9 19.8494 18.6011 20 10 34.7131 29.7321 30.4795 15.6205 34.6554 31.241 34.4093 20.5913 34.8281 28.2843 36.0555 26.2488 35.2278 28.2843 35 26.9072 35.2278 23.8537 24.4131 25 34.7131 26.9072 32.8024 27.5862 34.6554 23.3238 23.8537 24.4131 29.7321 18.0278 26.9072 16.4012 28.2843 19.7231 20.5913 21.4709 29 23.8537 25 28.2843 27.5862 22.8254 23.3238 18 30.4795 22.3607 25 26.2488 26.9072 27.5862 25.6125 23.3238 31.241 25.6125 26.2488 24.4131 26.9072 20.0998 20.2237 20.3961 35.3553 21.5407 25.6125 21.9317 27.5862 26.9072 27.5862 25.6125 34.8281 32.0156 32.0156 15.8114 33.6006 15.5242 24.4131 17 35 17.4929 34.4093 22.6716 35.2278 24.2074 21.9317 19.2094 35.2278 29 32.8024 20.5183 33.6006 28.2843 28.2843 14.1421 



Just as what is expected, it will print out error message on the pre-condition is not meet for doing Dijkstra.

*Note that: the DIjkstra still suffer from some bugs when asserting the hallway connectivity between two regions. It is so hard to implement how to formally argue that two regions is linked by a hallway.
