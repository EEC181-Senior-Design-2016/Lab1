/// keys work here
int main(void)
{
	volatile int * led		= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int switch_valA = 0x00;
	int switch_valB = 0x00;
	int key_val = 0x00;

	while(1)
	{
		*(hexdisp3_0) = switch_valA;
		*(hexdisp5_4) = switch_valB;

		key_val = *(keyptr);

		switch(key_val){
			case KEY0:
				switch_valA = (H << (nextHex*3)) + (E << (nextHex*2)) + (L << (nextHex)) + L;
				break;
			case KEY1:
				switch_valB = (H << nextHex) + E;
				break;
			case KEY2:
				switch_valA = (O << (nextHex*3)) + (r << (nextHex*2)) + (L << (nextHex)) + d;
				break;
			case KEY3:
				switch_valB = (U << nextHex) + U;
				break;
			default:
				break;					


		}//switch

		*(led) = key_val;

/*
switch_valA = switch_valA << (nextHex);
    
    		if (switch_valA == (H << (nextHex*4)) ){
     		 switch_valA = H;
   		 }
*/



	}// while 1
}// main




/////////////////////
/////////////////// scrolling hello world

int main(void)
{
	volatile int * led		= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int hex3_0_val = 0;
	int hex5_4_val = 0;
	int hex5_4_bool = 0;
	int key_val = 0;
	int char_numA = 0;
	int char_numB = 0;
	int next_letterA = 0;
	int next_letterB = 0;
  	int i = 0;
  	int j = 0;

	while(1)
	{
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		//key_val = *(keyptr);
    
    		next_letterA = printhelloworld(char_numA);
		
		hex3_0_val = ((hex3_0_val << nextHex) + next_letterA) & 0x0FFFFFFF;
    
		if(char_numA == 12){
			char_numA = 0;
		}else{			 
			char_numA++;
		}// chk where in hello string





		if(char_numA == 5 ){
			hex5_4_bool = 1;		
		}

		if (hex5_4_bool){
			next_letterB = printhelloworld(char_numB);
			hex5_4_val = ((hex5_4_val << nextHex) + next_letterB) & 0x03FFF;
			if(char_numB == 12){
				char_numB = 0;
			}else{			 
				char_numB++;
			}// chk where in hello string

		}




    		for(i =0 ; i < 30000; i++){
      			for(j=0; j < 10000; j++){
      			}
    }

	}// while 1
}// main


///////////////////////////
////////// set hello world separate fxn

void displayHello(int *hex3_0_val, int *hex5_4_val,
		int *hex5_4_bool,
		int *char_numA,
		int *char_numB,
		int *next_letterA,
		int *next_letterB)
{

	(*next_letterA) = printhelloworld(&(*char_numA));
		
	(*hex3_0_val) = (((*hex3_0_val) << nextHex) + (*next_letterA)) & 0x0FFFFFFF;
	//set hex3_0
    


	if((*char_numA) == 12){
		(*char_numA) = 0;
	}else{			 
		(*char_numA)++;
	}// chk where in hello string




	if((*char_numA) == 5 ){
		(*hex5_4_bool) = 1;		
	}// check if hex3_0 is filled



	if ((*hex5_4_bool)){
		
		(*next_letterB) = printhelloworld(&(*char_numB));
		
		(*hex5_4_val) = (((*hex5_4_val) << nextHex) + (*next_letterB)) & 0x03FFF;

		if((*char_numB) == 12){
			(*char_numB) = 0;
		}else{			 
			(*char_numB)++;
		}// chk where in hello string

	}// start looping in hex5_4

	return;



}// displayHello


int printhelloworld(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case


}// printhelloworld


int main(void)
{
	volatile int * led		= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int hex3_0_val = 0;
	int hex5_4_val = 0;

	int hex5_4_bool = 0;
	int key_val = 0;
	int char_numA = 0;
	int char_numB = 0;
	int next_letterA = 0;
	int next_letterB = 0;

  	int i = 0;
  	int j = 0;

	while(1)
	{
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		//key_val = *(keyptr);
    
    		displayHello(&hex3_0_val, &hex5_4_val,
			&hex5_4_bool, &char_numA, &char_numB, &next_letterA, &next_letterB);


    		for(i =0 ; i < 20000; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main

/////////////////////////////////////////////////////////////////
//// key for hello world works


#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08

void displayHello(int *hex3_0_val, int *hex5_4_val,
		int *hex5_4_bool,
		int *char_numA,
		int *char_numB,
		int *next_letterA,
		int *next_letterB)
{

	(*next_letterA) = printhelloworld(&(*char_numA));
		
	(*hex3_0_val) = (((*hex3_0_val) << nextHex) + (*next_letterA)) & 0x0FFFFFFF;
	//set hex3_0
    


	if((*char_numA) == 12){
		(*char_numA) = 0;
	}else{			 
		(*char_numA)++;
	}// chk where in hello string




	if((*char_numA) == 5 ){
		(*hex5_4_bool) = 1;		
	}// check if hex3_0 is filled



	if ((*hex5_4_bool)){
		
		(*next_letterB) = printhelloworld(&(*char_numB));
		
		(*hex5_4_val) = (((*hex5_4_val) << nextHex) + (*next_letterB)) & 0x03FFF;

		if((*char_numB) == 12){
			(*char_numB) = 0;
		}else{			 
			(*char_numB)++;
		}// chk where in hello string

	}// start looping in hex5_4

	return;



}// displayHello


int printhelloworld(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case


}// printhelloworld


int main(void)
{
	volatile int * led		= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int hex3_0_val = 0;
	int hex5_4_val = 0;

	int hex5_4_bool = 0;
	int char_numA = 0;
	int char_numB = 0;
	int next_letterA = 0;
	int next_letterB = 0;
	

	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom

	int key_val = 0;
  	int i = 0;
  	int j = 0;

	while(1)
	{
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		key_val = *(keyptr);
    

		switch(key_val){
			case KEY0:
				if (state != 1){
					hex3_0_val = 0;
					hex5_4_val = 0;
	 				hex5_4_bool = 0;
	 				char_numA = 0;
	 				char_numB = 0;
	 				next_letterA = 0;
	 				next_letterB = 0;
					state = 1;
				}
				break;
			case KEY1:
				state = 2;
				break;
			case KEY2:
				
				break;
			case KEY3:
				
				break;
			default:
				break;					

		}//switch


		switch(state){
			case 1:
				displayHello(&hex3_0_val, &hex5_4_val,
			&hex5_4_bool, &char_numA, &char_numB, &next_letterA, &next_letterB);
				break;
			case 2:
				hex3_0_val = 0x0FFFFFFF;
				hex5_4_val = 0x03FF;
				break;
			default:
				break;					

		}//switch




    		for(i =0 ; i < 30000; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main

/////////////////////////////////////////////////////////////////////////////////////////
// simplified code ?

#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08

void displayHello(
		int *curr_str,
		int *char_num, //stores current position of hello world
		int *next_letter //hex value of next letter in displays 3-0
){
	
	(*next_letter) = printhelloworld(&(*char_num)); //determines next letter
	(*curr_str) = (((*curr_str) << nextHex) + (*next_letter)) & 0x03FFFFFFFFFF;
	

	if((*char_num) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*char_num) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*char_num)++;
	}// chk where in hello string

	return;



}// displayHello


int printhelloworld(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case


}// printhelloworld


int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int hex3_0_val = 0;
	int hex5_4_val = 0;

	int hex5_4_bool = 0;
	
	int curr_str3_0 = 0;
	int char_num3_0 = 0;
	int next_letter3_0 = 0;
	
	int curr_str5_4 = 0;
	int char_num5_4 = 0;
	int next_letter5_4 = 0;

	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom

	int key_val = 0;
  	int i = 0;
  	int j = 0;

	while(1)
	{
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		key_val = *(keyptr);
    

		switch(key_val){
			case KEY0: //if key0 is pressed
				if (state != 1){ //and not already displaying hello world, initialize these variables
					hex3_0_val = 0;
					hex5_4_val = 0;
					
					hex5_4_bool = 0;
					
					curr_str3_0 = 0;
	 				char_num3_0 = 0;
	 				next_letter3_0 = 0;
					
					curr_str5_4 = 0;
					char_num5_4 = 0;
					next_letter5_4 = 0;
					
					state = 1;
				}
				break;
			case KEY1:
				state = 2;
				break;
			case KEY2:
				
				break;
			case KEY3:
				
				break;
			default:
				break;					

		}//switch


		switch(state){
			case 1: //if in state 1, run function "displayHello"
				displayHello(&curr_str3_0, &char_num3_0, &next_letter3_0);
				hex3_0_val = curr_str3_0 & 0x0FFFFFFF;
				
				if(char_num3_0 > 4){
					hex5_4_bool = 1;
				}
				
				if(hex5_4_bool){
					displayHello(&curr_str5_4, &char_num5_4, &next_letter5_4);
					hex5_4_val = curr_str5_4 & 0x03FFF;
				}					
				break;
			case 2:
				hex3_0_val = 0x0FFFFFFF;
				hex5_4_val = 0x03FFF;
				break;
			default:
				break;					

		}//switch




    		for(i =0 ; i < 30000; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main

////////////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////////////
/////////////// custom message displayed with key and switches, no scroll yet, speed increased

#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08

void displayHello(
		int *curr_str,
		int *char_num, //stores current position of hello world
		int *next_letter //hex value of next letter in displays 3-0
){
	
	(*next_letter) = printhelloworld(&(*char_num)); //determines next letter
	(*curr_str) = (((*curr_str) << nextHex) + (*next_letter));
	

	if((*char_num) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*char_num) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*char_num)++;
	}// chk where in hello string

	return;



}// displayHello


int printhelloworld(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case


}// printhelloworld


int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	int switch_val_hex = 0;
	
	int hex3_0_val = 0;
	int hex5_4_val = 0;

	int hex5_4_bool = 0;
	
	int curr_str3_0 = 0;
	int char_num3_0 = 0;
	int next_letter3_0 = 0;
	
	int curr_str5_4 = 0;
	int char_num5_4 = 0;
	int next_letter5_4 = 0;

	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom

  	int i = 0;
  	int j = 0;

	while(1)
	{
		key_val = *(keyptr);
		switch_val_led = *(switchptr);
		
		*(led) = switch_val_led;
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		switch(key_val){
			case KEY0: //if key0 is pressed
				if (state != 1){ //and not already displaying hello world, initialize these variables
					hex3_0_val = 0;
					hex5_4_val = 0;
					
					hex5_4_bool = 0;
					
					curr_str3_0 = 0;
	 				char_num3_0 = 0;
	 				next_letter3_0 = 0;
					
					curr_str5_4 = 0;
					char_num5_4 = 0;
					next_letter5_4 = 0;
					
					state = 1;
				}
				break;
			case KEY1:
				//if (state != 2){
					switch_val_hex = (*switchptr);
					state = 2;	
				//}
				break;
			case KEY2:
				
				break;
			case KEY3:
				
				break;
			default:
				break;					

		}//switch


		switch(state){
			case 1: //if in state 1, run function "displayHello"
				displayHello(&curr_str3_0, &char_num3_0, &next_letter3_0);
				hex3_0_val = curr_str3_0 & 0x0FFFFFFF;
				
				if(char_num3_0 > 4){
					hex5_4_bool = 1;
				}
				
				if(hex5_4_bool){
					displayHello(&curr_str5_4, &char_num5_4, &next_letter5_4);
					hex5_4_val = curr_str5_4 & 0x03FFF;
				}	

				
				break;
			case 2:
				hex3_0_val = switch_val_hex;
				hex5_4_val = 0x0;
				break;
			default:
				break;					

		}//switch




    		for(i =0 ; i < 20000; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main

///////////////////////////
//// scroll on hex3_0 works
#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08
#define HexLim3_0 0x0FFFFFFF
#define HexLim5_4 0x03FFF

int findNextLetter(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case
	
	return 0;
	
}// findNextLetter

void displayHello(
		int *curr_str,
		int *char_num, //stores current position of hello world
		int limiter
){
	(*curr_str) = (((*curr_str) << nextHex) + (findNextLetter(&(*char_num)))) & limiter;

	if((*char_num) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*char_num) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*char_num)++;
	}// chk where in hello string

	return;

}// displayHello


void displayCustom(
		long long int *curr_pattern,
		int *position
		//int *next_pattern
){
	if ((*position) > 4){
		(*position) = 0;
	}else{
		(*position)++;
	}
	
	(*curr_pattern) = ((*curr_pattern) << (nextHex * (*position))) & 0x0FFFFFFFFF;
	
	return;
	
}// displayCustom



int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	int switch_val_hex = 0;
	
	//vars for hello world
	int hex3_0_val = 0;
	int hex5_4_val = 0;

	int hex5_4_bool = 0;
	
	int curr_str3_0 = 0;
	int char_num3_0 = 0;
	
	int curr_str5_4 = 0;
	int char_num5_4 = 0;

	//vars for custom
	long long int curr_pattern3_0 = 0;
	int position3_0 = 0;
	//int next_pattern3_0 = 0;
	
	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom

  	int i = 0;
  	int j = 0;

	while(1)
	{
		key_val = *(keyptr);
		switch_val_led = *(switchptr);
		
		*(led) = switch_val_led;
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		switch(key_val){
			case KEY0: //if key0 is pressed
				if (state != 1){ //and not already displaying hello world, initialize these variables
					hex3_0_val = 0;
					hex5_4_val = 0;
					
					hex5_4_bool = 0;
					
					curr_str3_0 = 0;
	 				char_num3_0 = 0;
					
					curr_str5_4 = 0;
					char_num5_4 = 0;
					
					state = 1;
				}
				break;
			case KEY1:
				//if (state != 2){
					switch_val_hex = (*switchptr);
					state = 2;	
				//}
				break;
			case KEY2:
				
				break;
			case KEY3:
				
				break;
			default:
				break;					

		}//switch


		switch(state){
			case 1: //if in state 1, run function "displayHello"
				displayHello(&curr_str3_0, &char_num3_0, HexLim3_0);
				hex3_0_val = curr_str3_0;
				
				if(char_num3_0 > 4){
					hex5_4_bool = 1;
				}
				
				if(hex5_4_bool){
					displayHello(&curr_str5_4, &char_num5_4, HexLim5_4);
					hex5_4_val = curr_str5_4;
				}	

				
				break;
			case 2:
				curr_pattern3_0 = switch_val_hex;
				displayCustom(&curr_pattern3_0, &position3_0);//, &next_pattern3_0);
				hex3_0_val = curr_pattern3_0 >> nextHex;
				hex5_4_val = 0x0;
				break;
			default:
				break;					

		}//switch




    		for(i =0 ; i < 20000; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main


/////////////////////////////////////////////////////////////
///// scrolling custom done

#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08
#define HexLim3_0 0x0FFFFFFF
#define HexLim5_4 0x03FFF
#define PosLim3_0 5
#define PosLim5_4 6

int findNextLetter(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case
	
	return 0;
	
}// findNextLetter

void displayHello(
		int *curr_str,
		int *char_num, //stores current position of hello world
		int limiter
){
	(*curr_str) = (((*curr_str) << nextHex) + (findNextLetter(&(*char_num)))) & limiter;

	if((*char_num) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*char_num) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*char_num)++;
	}// chk where in hello string

	return;

}// displayHello


void displayCustom(
		long long int *curr_pattern,
		int *position,
		int poslim
){
	if ((*position) > poslim){
		(*position) = 0;
	}else{
		(*position)++;
	}
	
	(*curr_pattern) = ((*curr_pattern) << (nextHex * (*position))) & 0x0FFFFFFFFFFFFFF;
	
	return;
	
}// displayCustom



int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	int switch_val_hex = 0;
	
	//vars for hello world
	int hex3_0_val = 0;
	int hex5_4_val = 0;

	int hex5_4_bool = 0;
	
	int curr_str3_0 = 0;
	int char_num3_0 = 0;
	
	int curr_str5_4 = 0;
	int char_num5_4 = 0;

	//vars for custom
	long long int curr_pattern3_0 = 0;
	int position3_0 = 0;
	
	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom

  	int i = 0;
  	int j = 0;

	while(1)
	{
		key_val = *(keyptr);
		switch_val_led = *(switchptr);
		
		*(led) = switch_val_led;
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		switch(key_val){
			case KEY0: //if key0 is pressed
				if (state != 1){ //and not already displaying hello world, initialize these variables
					hex3_0_val = 0;
					hex5_4_val = 0;
					
					hex5_4_bool = 0;
					
					curr_str3_0 = 0;
	 				char_num3_0 = 0;
					
					curr_str5_4 = 0;
					char_num5_4 = 0;
					
					state = 1;
				}
				break;
			case KEY1:
				//if (state != 2){
					curr_pattern3_0 = 0;
					position3_0 = 0;
				//}
				hex5_4_bool = 0;
				switch_val_hex = (*switchptr);
				state = 2;
				break;
			case KEY2:
				
				break;
			case KEY3:
				
				break;
			default:
				break;					

		}//switch


		switch(state){
			case 1: //if in state 1, run function "displayHello"
				displayHello(&curr_str3_0, &char_num3_0, HexLim3_0);
				hex3_0_val = curr_str3_0;
				
				if(char_num3_0 > 4){
					hex5_4_bool = 1;
				}
				
				if(hex5_4_bool){
					displayHello(&curr_str5_4, &char_num5_4, HexLim5_4);
					hex5_4_val = curr_str5_4;
				}	

				
				break;
			case 2:
				
				curr_pattern3_0 = switch_val_hex;
				displayCustom(&curr_pattern3_0, &position3_0, PosLim3_0);
				hex3_0_val = curr_pattern3_0 >> nextHex;
				hex5_4_val = curr_pattern3_0 >> (nextHex * 5);
				
				break;
			default:
				break;					

		}//switch




    		for(i =0 ; i < 24000; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main


/////////////////////////////////////////////////////////////////
//////// custom optimized
#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08
#define HexLim3_0 0x0FFFFFFF
#define HexLim5_4 0x03FFF
#define PosLim 5
#define MaskCust 0x0FFFFFFFFFFFFFF

int findNextLetter(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case
	
	return 0;
	
}// findNextLetter

void displayHello(
		int *curr_str,
		int *char_num, //stores current position of hello world
		int limiter
){
	(*curr_str) = (((*curr_str) << nextHex) + (findNextLetter(&(*char_num)))) & limiter;

	if((*char_num) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*char_num) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*char_num)++;
	}// chk where in hello string

	return;

}// displayHello


void displayCustom(
		long long int *curr_pattern,
		int *position
){
	if ((*position) > PosLim){
		(*position) = 0;
	}else{
		(*position)++;
	}
	
	(*curr_pattern) = ((*curr_pattern) << (nextHex * (*position))) & MaskCust;
	
	return;
	
}// displayCustom



int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	int switch_val_hex = 0;
	
	//vars for hello world
	int hex3_0_val = 0;
	int hex5_4_val = 0;

	int hex5_4_bool = 0;
	
	int curr_str3_0 = 0;
	int char_num3_0 = 0;
	
	int curr_str5_4 = 0;
	int char_num5_4 = 0;

	//vars for custom
	long long int custom_pattern = 0;
	int custom_position = 0;
	
	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom

  	int i = 0;
  	int j = 0;

	while(1)
	{
		key_val = *(keyptr);
		switch_val_led = *(switchptr);
		
		*(led) = switch_val_led;
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		switch(key_val){
			case KEY0: //if key0 is pressed
				if (state != 1){ //and not already displaying hello world, initialize these variables
					hex3_0_val = 0;
					hex5_4_val = 0;
					
					hex5_4_bool = 0;
					
					curr_str3_0 = 0;
	 				char_num3_0 = 0;
					
					curr_str5_4 = 0;
					char_num5_4 = 0;
					
					state = 1;
				}
				break;
			case KEY1:
				custom_pattern = 0;
				custom_position = 0;
				switch_val_hex = (*switchptr);
				state = 2;
				break;
			case KEY2:
				
				break;
			case KEY3:
				
				break;
			default:
				break;					

		}//switch


		switch(state){
			case 1: //if in state 1, run function "displayHello"
				displayHello(&curr_str3_0, &char_num3_0, HexLim3_0);
				hex3_0_val = curr_str3_0;
				
				if(char_num3_0 > 4){
					hex5_4_bool = 1;
				}
				
				if(hex5_4_bool){
					displayHello(&curr_str5_4, &char_num5_4, HexLim5_4);
					hex5_4_val = curr_str5_4;
				}	

				
				break;
			case 2:
				
				custom_pattern = switch_val_hex;
				displayCustom(&custom_pattern, &custom_position);
				hex3_0_val = custom_pattern >> nextHex;
				hex5_4_val = custom_pattern >> (nextHex * 5);
				
				break;
			default:
				break;					

		}//switch




    		for(i =0 ; i < 24000; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main

///////////////////////////////////////////////////////////////////////////////
//////// optimized both fxns
#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08
#define PosLimCust 5
#define Mask_48b 0x0FFFFFFFFFFFFFF

int findNextLetter(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case
	
	return 0;
	
}// findNextLetter

void displayHello(
		long long int *curr_disp,
		int *curr_index //stores current position of hello world
){
	(*curr_disp) = (((*curr_disp) << nextHex) + (findNextLetter(&(*curr_index)))) & Mask_48b;

	if((*curr_index) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*curr_index) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*curr_index)++;
	}// chk where in hello string

	return;

}// displayHello


void displayCustom(
		long long int *curr_pattern,
		int *curr_pos
){
	if ((*curr_pos) > PosLimCust){
		(*curr_pos) = 0;
	}else{
		(*curr_pos)++;
	}
	
	(*curr_pattern) = ((*curr_pattern) << (nextHex * (*curr_pos))) & Mask_48b;
	
	return;
	
}// displayCustom



int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	int switch_val_hex = 0;
	

	int hex3_0_val = 0;
	int hex5_4_val = 0;
	
	//vars for hello world
	long long int hw_disp = 0;
	int char_index = 0;
	

	//vars for custom
	long long int custom_pattern = 0;
	int custom_position = 0;
	
	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom

  	int i = 0;
  	int j = 0;

	while(1)
	{
		key_val = *(keyptr);
		switch_val_led = *(switchptr);
		
		*(led) = switch_val_led;
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		switch(key_val){
			case KEY0: //if key0 is pressed
				if (state != 1){ //and not already displaying hello world, initialize these variables
					hw_disp = 0;
	 				char_index = 0;
					state = 1;
				}
				break;
			case KEY1:
				custom_pattern = 0;
				custom_position = 0;
				switch_val_hex = (*switchptr);
				state = 2;
				break;
			case KEY2:
				
				break;
			case KEY3:
				
				break;
			default:
				break;					

		}//switch


		switch(state){
			case 1: //if in state 1, run function "displayHello"
				displayHello(&hw_disp, &char_index);
				hex3_0_val = hw_disp;
				hex5_4_val = hw_disp >> (nextHex * 4);				
				break;
			case 2:
				custom_pattern = switch_val_hex;
				displayCustom(&custom_pattern, &custom_position);
				hex3_0_val = custom_pattern >> nextHex;
				hex5_4_val = custom_pattern >> (nextHex * 5);
				break;
			default:
				break;					

		}//switch

    		for(i =0 ; i < 24500; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main

////////////////////////////
///////// more optimized?
#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08
#define PosLimCust 5
#define Mask_44b 0x0FFFFFFFFFFFFF
#define Mask_42b 0x03FFFFFFFFFFFF

int findNextLetter(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case
	
	return 0;
	
}// findNextLetter

void displayHello(
		long long int *curr_disp,
		int *curr_index //stores current position of hello world
){
	(*curr_disp) = (((*curr_disp) << nextHex) + (findNextLetter(&(*curr_index)))) & Mask_44b;

	if((*curr_index) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*curr_index) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*curr_index)++;
	}// chk where in hello string

	return;

}// displayHello


void displayCustom(
		long long int *curr_pattern,
		long long int back2front
){
   
  back2front = ((*curr_pattern) >> (nextHex * 5)) & 0x07F;
  (*curr_pattern) = (((*curr_pattern) << (nextHex)) + back2front) & Mask_42b;
	
	return;
	
}// displayCustom



int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	

	int hex3_0_val = 0;
	int hex5_4_val = 0;
	
	//vars for hello world
	long long int hw_disp = 0;
	int char_index = 0;
	

	//vars for custom
	long long int custom_pattern = 0;
	int custom_position = 0;
	
	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom

  	int i = 0;
  	int j = 0;

	while(1)
	{
		key_val = *(keyptr);
		switch_val_led = *(switchptr);
		
		*(led) = switch_val_led;
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		switch(key_val){
			case KEY0: //if key0 is pressed
				if (state != 1){ //and not already displaying hello world, initialize these variables
					hw_disp = 0;
	 				char_index = 0;
					state = 1;
				}
				break;
			case KEY1:
				if (state != 2){
          custom_pattern = (*switchptr);
					custom_position = 0;
					state = 2;
				}
				break;
			case KEY2:
				
				break;
			case KEY3:
				
				break;
			default:
				break;					

		}//switch


		switch(state){
			case 1: //if in state 1, run function "displayHello"
				displayHello(&hw_disp, &char_index);
				hex3_0_val = hw_disp;
				hex5_4_val = hw_disp >> (nextHex * 4);				
				break;
			case 2:
        hex3_0_val = custom_pattern;
				hex5_4_val = custom_pattern >> (nextHex *4);
        
        displayCustom(&custom_pattern, custom_position);
				break;
			default:
				break;					

		}//switch

    		for(i =0 ; i < 24500; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main


///////////////////////////////////////////////
////////////// pause button implemented
#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08
#define PosLimCust 5
#define Mask_44b 0x0FFFFFFFFFFFFF
#define Mask_42b 0x03FFFFFFFFFFFF

int findNextLetter(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case
	
	return 0;
	
}// findNextLetter

void displayHello(
		long long int *curr_disp,
		int *curr_index //stores current position of hello world
){
	(*curr_disp) = (((*curr_disp) << nextHex) + (findNextLetter(&(*curr_index)))) & Mask_44b;

	if((*curr_index) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*curr_index) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*curr_index)++;
	}// chk where in hello string

	return;

}// displayHello


void displayCustom(
		long long int *curr_pattern,
		long long int wrapHex
){
   
  wrapHex = ((*curr_pattern) >> (nextHex * 5)) & 0x07F;
  (*curr_pattern) = (((*curr_pattern) << (nextHex)) + wrapHex) & Mask_42b;
	
	return;
	
}// displayCustom



int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	

	int hex3_0_val = 0;
	int hex5_4_val = 0;
	
	//vars for hello world
	long long int hw_disp = 0;
	int char_index = 0;
	

	//vars for custom
	long long int custom_pattern = 0;
	int custom_wrapHex = 0;
	
	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom
  
  int pause = 0;

  	int i = 0;
  	int j = 0;

	while(1)
	{
		key_val = *(keyptr);
		switch_val_led = *(switchptr);
		
		*(led) = switch_val_led;
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		switch(key_val){
			case KEY0: //if key0 is pressed
        if (pause == 0){
          if (state != 1){ //and not already displaying hello world, initialize these variables
            hw_disp = 0;
            char_index = 0;
            state = 1;
          }else{
            custom_pattern = (*switchptr);
            custom_wrapHex = 0;
            state = 2;
          }
        }// if not paused
				break;
			case KEY1:
          if(pause){
            pause = 0;
          }else{
            pause = 1;
          }
				break;
			case KEY2:
				
				break;
			case KEY3:
				
				break;
			default:
				break;					

		}//switch

    if (pause == 0){
      switch(state){
        case 1: //if in state 1, run function "displayHello"
          displayHello(&hw_disp, &char_index);
          hex3_0_val = hw_disp;
          hex5_4_val = hw_disp >> (nextHex * 4);				
          break;
        case 2:
          hex3_0_val = custom_pattern;
          hex5_4_val = custom_pattern >> (nextHex *4);
        
          displayCustom(&custom_pattern, custom_wrapHex);
          break;
        default:
          break;					

      }//switch
    }// if pause
    
    
    		for(i =0 ; i < 24500; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main

/////////////////////////////////////////////////////////////
/////// finished code i think

#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08
#define PosLimCust 5
#define Mask_44b 0x0FFFFFFFFFFFFF
#define Mask_42b 0x03FFFFFFFFFFFF

int findNextLetter(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case
	
	return 0;
	
}// findNextLetter

void displayHello(
		long long int *curr_disp,
		int *curr_index //stores current position of hello world
){
	(*curr_disp) = (((*curr_disp) << nextHex) + (findNextLetter(&(*curr_index)))) & Mask_44b;

	if((*curr_index) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*curr_index) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*curr_index)++;
	}// chk where in hello string

	return;

}// displayHello


void displayCustom(
		long long int *curr_pattern,
		long long int wrapHex
){
   
  wrapHex = ((*curr_pattern) >> (nextHex * 5)) & 0x07F;
  (*curr_pattern) = (((*curr_pattern) << (nextHex)) + wrapHex) & Mask_42b;
	
	return;
	
}// displayCustom



int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	

	int hex3_0_val = 0;
	int hex5_4_val = 0;
	
	//vars for hello world
	long long int hw_disp = 0;
	int char_index = 0;
	

	//vars for custom
	long long int custom_pattern = 0;
	int custom_wrapHex = 0;
	
	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom
	int timer = 25000;
  
  	int pause = 0;

  	int i = 0;
  	int j = 0;

	while(1)
	{
		key_val = *(keyptr);
		switch_val_led = *(switchptr);
		
		*(led) = switch_val_led;
		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;
		
		switch(key_val){
			case KEY0: //if key0 is pressed
       			 	if (pause == 0){
          				if (state != 1){ //and not already displaying hello world, initialize these variables
            					hw_disp = 0;
            					char_index = 0;
            					state = 1;
          				}else{
            					custom_pattern = (*switchptr);
            					custom_wrapHex = 0;
            					state = 2;
          				}
        			}// if not paused
				break;
			case KEY1:
       				if(pause){
            				pause = 0;
          			}else{
            				pause = 1;
          			}
				break;
			case KEY2:
				if ((pause == 0) & (timer <= 40000)){
					timer = timer + 5000;				
				}
				break;
			case KEY3:
				if ((pause == 0) & (timer >= 10000)){
					timer = timer - 5000;
				}
				break;
			default:
				break;					

		}//switch

    if (pause == 0){
      switch(state){
        case 1: //if in state 1, run function "displayHello"
          displayHello(&hw_disp, &char_index);
          hex3_0_val = hw_disp;
          hex5_4_val = hw_disp >> (nextHex * 4);				
          break;
        case 2:
          hex3_0_val = custom_pattern;
          hex5_4_val = custom_pattern >> (nextHex *4);
        
          displayCustom(&custom_pattern, custom_wrapHex);
          break;
        default:
          break;					

      }//switch
    }// if pause
    
    
    		for(i =0 ; i < timer; i++){
      			for(j=0; j < 10000; j++){
      			}
    	}

	}// while 1
}// main



/////////////////////////////////////////
// more fixing


















#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08
#define PosLimCust 5
#define Mask_44b 0x0FFFFFFFFFFFFF
#define Mask_42b 0x03FFFFFFFFFFFF

int findNextLetter(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case
	
	return 0;
	
}// findNextLetter

void displayHello(
		long long int *curr_disp,
		int *curr_index //stores current position of hello world
){
	(*curr_disp) = (((*curr_disp) << nextHex) + (findNextLetter(&(*curr_index)))) & Mask_44b;

	if((*curr_index) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*curr_index) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*curr_index)++;
	}// chk where in hello string

	return;

}// displayHello


void displayCustom(
		long long int *curr_pattern,
		long long int wrapHex
){
   
  wrapHex = ((*curr_pattern) >> (nextHex * 5)) & 0x07F;
  (*curr_pattern) = (((*curr_pattern) << (nextHex)) + wrapHex) & Mask_42b;
	
	return;
	
}// displayCustom



int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	

	int hex3_0_val = 0;
	int hex5_4_val = 0;
	
	//vars for hello world
	long long int hw_disp = 0;
	int char_index = 0;
	

	//vars for custom
	long long int custom_pattern = 0;
	int custom_wrapHex = 0;
	
	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom
	int timer = 25000;
  
  	int pause = 0;
	int keyPressed = 0;

  	int i = 0;
  	int j = 0;

	while(1)
	{
			
		if(keyPressed){
		switch(key_val){
			case KEY0: //if key0 is pressed
       			 	if (pause == 0){
          				if (state != 1){ //and not already displaying hello world, initialize these variables
            					hw_disp = 0;
            					char_index = 0;
            					state = 1;
          				}else{
            					custom_pattern = (*switchptr);
            					custom_wrapHex = 0;
            					state = 2;
          				}
        			}// if not paused
				break;
			case KEY1:
       				if(pause){
            				pause = 0;
          			}else{
            				pause = 1;
          			}
				break;
			case KEY2:
				if ((pause == 0) & (timer <= 40000)){
					timer = timer + 5000;				
				}
				break;
			case KEY3:
				if ((pause == 0) & (timer >= 10000)){
					timer = timer - 5000;
				}
				break;
			default:
				break;					

		}//switch
		keyPressed = 0;
		}// key is pressed






    if (pause == 0){
      switch(state){
        case 1: //if in state 1, run function "displayHello"
          displayHello(&hw_disp, &char_index);
          hex3_0_val = hw_disp;
          hex5_4_val = hw_disp >> (nextHex * 4);				
          break;
        case 2:
          hex3_0_val = custom_pattern;
          hex5_4_val = custom_pattern >> (nextHex *4);
        
          displayCustom(&custom_pattern, custom_wrapHex);
          break;
        default:
          break;					

      }//switch
    }// if pause
    
    


				*(hexdisp3_0) = hex3_0_val;
				*(hexdisp5_4) = hex5_4_val;



    		for(i =0 ; i < timer; i++){
      			for(j=0; j < 10; j++){
				switch_val_led = *(switchptr);
				*(led) = switch_val_led;
				
				key_val = *(keyptr);

				if(key_val != 0){
					keyPressed = 1;
					break;
				}// then break out of for loop
      			}// for j
		if(keyPressed){
			break;		
		}
    	}

	}// while 1
}// main



/////////////////////////////////////
/////// FINISHEEDDDDD

#define H 0x76
#define E 0x79
#define L 0x38
#define O 0x3F
#define U 0x3E
#define r 0x50
#define d 0x5E
#define nextHex 7
#define KEY0 0x01 
#define KEY1 0x02
#define KEY2 0x04
#define KEY3 0x08
#define PosLimCust 5
#define Mask_44b 0x0FFFFFFFFFFFFF
#define Mask_42b 0x03FFFFFFFFFFFF

int findNextLetter(int *prev)
{
	switch ((*prev)){
		case 0:
			return H;
		case 1:
			return E;
		case 2:
		case 3:
		case 10:
			return L;
		
		case 4:
		case 8:
			return O;
		case 5:
		case 12:
			return 0;
		case 6:
		case 7:
			return U;
		case 9:
			return r;
		case 11:
			return d;
		

	}// case
	
	return 0;
	
}// findNextLetter

void displayHello(
		long long int *curr_disp,
		int *curr_index //stores current position of hello world
){
	(*curr_disp) = (((*curr_disp) << nextHex) + (findNextLetter(&(*curr_index)))) & Mask_44b;

	if((*curr_index) == 12){ //if current character is last character "_" in "hello world_", reset back to "h"
		(*curr_index) = 0;
	}else{	//if not, advance to next character in "hello world"		 
		(*curr_index)++;
	}// chk where in hello string

	return;

}// displayHello


void displayCustom(
		long long int *curr_pattern,
		long long int wrapHex
){
   
  wrapHex = ((*curr_pattern) >> (nextHex * 5)) & 0x07F;
  (*curr_pattern) = (((*curr_pattern) << (nextHex)) + wrapHex) & Mask_42b;
	
	return;
	
}// displayCustom



int main(void)
{
	volatile int * led			= (int *) 0xFF200040; // red LED addr
	volatile int * switchptr	= (int *) 0xFF200030; // SW slider switch addr
	volatile int * keyptr		= (int *) 0xFF200000; // KEYS addr
	volatile int * hexdisp3_0	= (int *) 0xFF200020; // HEX3_0 addr
	volatile int * hexdisp5_4	= (int *) 0xFF200010; // HEX5_4 addr

	int key_val = 0;
	int switch_val_led = 0;
	

	int hex3_0_val = 0;
	int hex5_4_val = 0;
	
	//vars for hello world
	long long int hw_disp = 0;
	int char_index = 0;
	

	//vars for custom
	long long int custom_pattern = 0;
	int custom_wrapHex = 0;
	
	int state = 0; // state 0 = nothing, state 1 = Hello World, state 2 = custom
	int timer = 25000;
  
  	int pause = 0;
	int keyPressed = 0;
	int prev_key = 0;

  	int i = 0;
  	int j = 0;

	while(1)
	{
			
		if(keyPressed){
		switch(key_val){
			case KEY0: //if key0 is pressed
       			 	if (pause == 0){
          				if (state != 1){ //and not already displaying hello world, initialize these variables
            					hw_disp = 0;
            					char_index = 0;
            					state = 1;
          				}else{
            					custom_pattern = (*switchptr);
            					custom_wrapHex = 0;
            					state = 2;
          				}
        			}// if not paused
				break;
			case KEY1:
       				if(pause){
            				pause = 0;
          			}else{
            				pause = 1;
          			}
				break;
			case KEY2:
				if ((pause == 0) && (timer <= 40000)){
					timer = timer + 5000;				
				}
				break;
			case KEY3:
				if ((pause == 0) && (timer >= 10000)){
					timer = timer - 5000;
				}
				break;
			default:
				break;					

		}//switch
		keyPressed = 0;
		}// key is pressed






    if (pause == 0){
      switch(state){
        case 1: //if in state 1, run function "displayHello"
          displayHello(&hw_disp, &char_index);
          hex3_0_val = hw_disp;
          hex5_4_val = hw_disp >> (nextHex * 4);				
          break;
        case 2:
          hex3_0_val = custom_pattern;
          hex5_4_val = custom_pattern >> (nextHex *4);
        
          displayCustom(&custom_pattern, custom_wrapHex);
          break;
        default:
          break;					

      }//switch
    }// if pause
    
    


		*(hexdisp3_0) = hex3_0_val;
		*(hexdisp5_4) = hex5_4_val;

		prev_key = key_val;


    		for(i =0 ; i < timer; i++){
      			for(j=0; j < 10; j++){
				switch_val_led = *(switchptr);
				*(led) = switch_val_led;
				
				key_val = *(keyptr);

				if((key_val != 0) && (prev_key == 0)){
					keyPressed = 1;
					break;
				}// then break out of for loop
      			}// for j
		if(keyPressed){
			break;		
		}
    	}

	}// while 1
}// main














































































































