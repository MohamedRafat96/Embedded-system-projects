#include "LCDControl.h"
#include <avr/interrupt.h>

volatile unsigned int i;

ISR (INT1_vect)       
{
	switch(i)
	{
		case 3:
		SendCommend(0x1c);
		_delay_ms(20);
		i=0;
		break;
		
	
		case  4:
		SendCommend(0x18);
		_delay_ms(20);
		i=0;
		break;
	}
}

int main()
{
	DDRC &= ~(1<<0);
	DDRC &= ~(1<<1);
	DDRC &= ~(1<<2);
	DDRC &= ~(1<<3);
	
	DDRC |= (1<<4);
	DDRC |= (1<<5);
	
	DDRA |=(1<<0);
	
	LCD_Initialize();			
	SendString("MOHAMED RAAFAT");
	
	GICR |= (1<<INT1);
	MCUCR = 1<<ISC01 | 1<<ISC00;
	
	
	
	while(1)
	{
		if ((PINC & (1<<0)))
		{
		
			i = 1;
		}
		else if (PINC & (1<<1))
		{
			i=2;
		}
		else if (PINC & (1<<2))
		{
			
			i=3;
			PORTC |= (1<<4);
			PORTC |= (1<<5);
			sei();
			
		}
		else if (PINC & (1<<3))
		{
			
			i=4;
			PORTC &= ~(1<<5);
			PORTC |= (1<<4);
			sei();
			
		}
		else
		{
			
		}
	}
	return 0;
}
