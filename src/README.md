#include <Servo.h>

#include <Wire.h>
#include "ABlocks_LiquidCrystal_I2C.h"

double S0;
double dist_izq_x;
double dist_der_x;
double dis_y_final;
double vel_ap;
double S1;
double VEL;
double dist_inicio_der;
double dist_inicio_izq;
double ac_izq;
double angulo_izq;
double dist_ade;
double S2;
double vel_cur;
double dist_ade_y;
double ANGULO_CENTRO;
double dis_izq;
double ac_der;
double angulo_der;
double S3;
double Dis_y_hacia;
double dis_der;
double var_ang;
double dist23;
double dist_23_inicio;
double VERDE;
double OUT;
double y_centro;
double c_cruzes;
boolean b_VERDE_REAL;
boolean b_ROJO_REAL;
Servo servo_1;
LiquidCrystal_I2C lcd_1(0x27,16,2);

void valores_ccero() {
	vel_ap = 0;
	dist_ade = 0;
	dis_izq = 0;
	dist_izq_x = 0;
	angulo_izq = 0;
	angulo_der = 0;
	dist_ade_y = 0;
	dist_der_x = 0;
}
double fnc_ultrasonic_distance(int _t, int _e){
	unsigned long dur=0;
	digitalWrite(_t, LOW);
	delayMicroseconds(5);
	digitalWrite(_t, HIGH);
	delayMicroseconds(10);
	digitalWrite(_t, LOW);
	dur = pulseIn(_e, HIGH, 18000);
	if(dur==0)return 999.0;
	return (dur/57);
}

void datos_iniciales() {
	VEL = 145;
	vel_cur = 120;
	ANGULO_CENTRO = 95;
	dist_inicio_izq = fnc_ultrasonic_distance(3,2);
	dist_inicio_der = fnc_ultrasonic_distance(9,4);
	dist_23_inicio = 135;
	servo_1.write(ANGULO_CENTRO);
	lcd_1.begin();
	lcd_1.noCursor();
	lcd_1.backlight();
	var_ang = 5;
}
void datos_y() {
	dis_y_final = (1.8 * fnc_ultrasonic_distance(10,11));
	dist_ade_y = dist_ade;
	Dis_y_hacia = (dist_ade - 4);
}
void datos_en_pista() {
	lcd_1.setCursor(8, 0);
	lcd_1.print(String("D "));
	lcd_1.setCursor(8, 1);
	lcd_1.print(String("Ad"));
	lcd_1.setCursor(0, 0);
	lcd_1.print(String("A"));
	lcd_1.setCursor(0, 1);
	lcd_1.print(String("I "));
	lcd_1.setCursor(1, 0);
	lcd_1.print(dist_ade);
	lcd_1.setCursor(9, 0);
	lcd_1.print(dis_der);
	lcd_1.setCursor(10, 1);
	lcd_1.print(angulo_der);
	lcd_1.setCursor(1, 1);
	lcd_1.print(dis_izq);
}
void adelante() {
	servo_1.write(ANGULO_CENTRO);
	digitalWrite(7,LOW);
	digitalWrite(8,HIGH);
	analogWrite(5,VEL);
}
void datos_en_calculo() {
	lcd_1.setCursor(8, 0);
	lcd_1.print(String("F"));
	lcd_1.setCursor(8, 1);
	lcd_1.print(String("A"));
	lcd_1.setCursor(0, 0);
	lcd_1.print(String("D"));
	lcd_1.setCursor(0, 1);
	lcd_1.print(String("DI"));
	lcd_1.setCursor(1, 0);
	lcd_1.print(dist23);
	lcd_1.setCursor(9, 0);
	lcd_1.print(dis_y_final);
	lcd_1.setCursor(10, 1);
	lcd_1.print(dist_ade);
	lcd_1.setCursor(2, 1);
	lcd_1.print(dist_23_inicio);
}
void datos_x() {
	dist_izq_x = dis_izq;
	dist_der_x = dis_der;
}
void apagar() {
	digitalWrite(7,LOW);
	digitalWrite(8,LOW);
	analogWrite(5,vel_ap);
}
void hacer_algo() {
	ac_izq = (atan(((((y_centro - 15)) / dist_inicio_izq))) * ((180 / 3.1416)));
	ac_der = (atan(((((y_centro - 15)) / dist_inicio_der))) * ((180 / 3.1416)));
	if ((dist_izq_x > (dist_inicio_izq - 5))) {
		y_centro = (dist_ade + 125);
	}
	else if ((dist_der_x > (dist_inicio_der - 5))) {
		y_centro = (dist_ade - 125);
	}

}
void giro_derecho() {
	digitalWrite(7,LOW);
	digitalWrite(8,HIGH);
	analogWrite(5,vel_cur);
	servo_1.write(angulo_der);
}
void giro_izquierdad() {
	digitalWrite(7,LOW);
	digitalWrite(8,HIGH);
	analogWrite(5,vel_cur);
	servo_1.write(angulo_izq);
}
void retrodecer() {
	digitalWrite(7,HIGH);
	digitalWrite(8,LOW);
	analogWrite(5,VEL);
}

void setup()
{
  	pinMode(3, OUTPUT);
	pinMode(2, INPUT);
	pinMode(9, OUTPUT);
	pinMode(4, INPUT);
	servo_1.attach(1);
	pinMode(10, OUTPUT);
	pinMode(11, INPUT);
	pinMode(7, OUTPUT);
	pinMode(8, OUTPUT);
	pinMode(5, OUTPUT);

	for (int count = 0; count < 1; count++) {
		delay(2500);
	}
	valores_ccero();
	datos_iniciales();

}


void loop()
{

  	angulo_izq = (var_ang + (atan(((((((dist_ade_y + 10.5)) / 2)) / ((dist_izq_x / 1))))) * ((180 / 3.14))));
  	angulo_der = (var_ang + ((180 - (atan(((((((dist_ade_y + 10.5)) / 2)) / ((dist_der_x / 1))))) * ((180 / 3.14))))));
  	dis_izq = fnc_ultrasonic_distance(3,2);
  	dist_ade = fnc_ultrasonic_distance(10,11);
  	dis_der = fnc_ultrasonic_distance(9,4);
  	dist23 = (dis_izq + dis_der);
  	adelante();
  	datos_en_pista();
  	if ((dist23 < dist_23_inicio)) {
  		datos_x();
  		datos_y();
  		datos_en_pista();
  	}

  	if ((((dist23 > dist_23_inicio) && (dis_der > dis_izq)) && (dist_ade < Dis_y_hacia))) {
  		while (!((dist_ade > dis_y_final))) {
  			dist_ade = fnc_ultrasonic_distance(10,11);
  			giro_derecho();
  			datos_en_pista();
  		}
  		if (false) {
  			c_cruzes=c_cruzes+(1);
  		}

  	}

  	if ((((dist23 > dist_23_inicio) && (dis_izq > dis_der)) && (dist_ade < Dis_y_hacia))) {
  		while (!((dist_ade > dis_y_final))) {
  			dist_ade = fnc_ultrasonic_distance(10,11);
  			giro_izquierdad();
  			datos_en_pista();
  		}
  		if (false) {
  			c_cruzes=c_cruzes+(1);
  		}

  	}

  	if ((dist_ade < 3)) {
  		while (!((dist_ade > dis_y_final))) {
  			dist_ade = fnc_ultrasonic_distance(10,11);
  			retrodecer();
  			datos_en_calculo();
  		}
  	}

}
