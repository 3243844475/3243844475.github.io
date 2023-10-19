#include <reg51.h>
sfr smg=0x80;
unsigned char c[]={0xc0,0xf9,0xa4,0xb0,0x99,0x92,0x82,0xf8,0x80,0x90};
unsigned char d[]={0x01,0x02,0x04,0x08,0x10,0x20,0x40,0x80};
void delay(unsigned int i){
unsigned long int j;
for(j=0;j<i;j++);
}
void main(){
unsigned long int x,h=99999999,n=0;
while(1){
h--;
while(n!=19){
n++;
P3=0x01;
smg=c[h/10000000];
delay(50);
P3=0x02;
smg=c[h/1000000%10];
delay(50);
P3=0x04;
smg=c[h/100000%10];
delay(50);
P3=0x08;
smg=c[h/10000%10];
delay(50);
P3=0x10;
smg=c[h/1000%10];
delay(50);
P3=0x20;
smg=c[h/100%10];
delay(1500);
P3=0x40;
smg=c[h/10%10];
delay(50);
P3=0x80;
smg=c[h%10];
delay(50);
}
n=0;
if(h==0)h=99999999;
 }
}