#include "p16F628a.inc"    ;incluir librerias relacionadas con el dispositivo
 __CONFIG _FOSC_INTOSCCLK & _WDTE_OFF & _PWRTE_OFF & _MCLRE_OFF & _BOREN_OFF & _LVP_OFF & _CPD_OFF & _CP_OFF    
;configuración del dispositivotodo en OFF y la frecuencia de oscilador
;es la del "reloj del oscilador interno" (INTOSCCLK)     
RES_VECT  CODE    0x0000            ; processor reset vector
    GOTO    START                   ; go to beginning of program
; TODO ADD INTERRUPTS HERE IF USED
MAIN_PROG CODE                      ; let linker place main program
;variables para el contador:
 i equ 0x30
 j equ 0x31
 k equ 0x32
;inicio del programa: 
START
MOVLW 0x07 ;Apagar comparadores
MOVWF CMCON
 
 
BCF STATUS, RP1 
BSF STATUS, RP0 
MOVLW b'00000000'
MOVWF TRISB 
BCF STATUS, RP0 
BCF PORTB, 3
BCF PORTB, 1
BCF PORTB, 2
BCF PORTB, 4
BCF PORTB, 5
BCF PORTB, 6
BCF PORTB, 7
BSF PORTB, 0


 
INICIO
BTFSC PORTB, 7 
GOTO DERECHA
call tiempo
RLF PORTB,1
call tiempo
BCF PORTB, 0

GOTO INICIO
 
DERECHA
BTFSC PORTB, 0 
GOTO INICIO
call tiempo
RRF PORTB,1
call tiempo
BTFSS PORTB, 0  
BCF PORTB, 0

GOTO DERECHA
 		
tiempo:	
 movlw d'3' 
 movwf i
	
iloop: movlw d'61' 
	movwf j
		
jloop: movlw d'130' 
       movwf k
       
kloop: decfsz k, f
	goto kloop
	decfsz j, f
	goto jloop
	decfsz i, f
	goto iloop
		
	return
    END
