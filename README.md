#include <kipr/botball.h>
//DECLARE VARIABLES
int l_motor = 0; 
int r_motor = 3; 
int l_bump = 0;
int r_bump = 9;
int m_bump = 4;
int forward = -75;
int backward = 75;
int turn_around = 3500;
int pause = 2000;
int five_minutes = 300;
int counter = 0;

int main()
{
    shut_down_in(five_minutes);
    while(1){ //as long as the log test is true...
     forwards();
        	if(digital(l_bump)==1){ //if it hits something backup and turn right
        			backwards();
        			right();
                	counter=counter+1;
            }
        	if(digital(r_bump)==1){ //if it hits something backup and turn left
                	backwards();
                    left();
                	counter=counter+1;
            }
        	if(counter==5){ //backup and make a large left turn
                	turn();
            		counter=0;
            }
        	
    }
    printf("Hello World\n");
    return 0;
}

//FUNCTION DEFINITIONS//
void forwards(){
    motor(l_motor,forward);
    motor(r_motor,forward);
}
void backwards(){
 	motor(l_motor,backward);
    motor(r_motor,backward);
    msleep(pause);
    ao();
}
void right(){
 	motor(l_motor,forward);
    msleep(pause);
    ao();
}
void left(){
    motor(r_motor,forward);
    msleep(pause);
    ao();
}
void turn(){
 	motor(r_motor,backward);
    msleep(turn_around);
    ao();
}    
