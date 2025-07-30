ORG 0000H
 CLR P1.0 
    MOV A, P1 
    ANL A, #0FH
DISPLAY_LOOP:    MOV R3, #8
		 MOV A, #0EH
	LD:	 
		 RL A
		 MOV P1, A
		 DJNZ R3, LD
		 SJMP DISPLAY_LOOP
DELAY: 
   MOV R4, #1
;  MIDDLE:  MOV R6, #200
;   MOV R5, #250
;   L2: DJNZ R5, $
;   DJNZ R6, L2
;   DJNZ R4, MIDDLE
   RET 
END

   
 
 
; OUTER:  MOV R2,#250
; LOOP:	 MOV R1, #200 
;	 DJNZ R1, $
;	 DJNZ R2, LOOP
;	 DJNZ R3, OUTER 
;	 RET 
; OUTER:  MOV R2, 199
; LOOP:	 MOV R1, 250
;	 DJNZ R1, $
;	 DJNZ R2, LOOP
;	 DJNZ R3, OUTER 
;	 RET 



;MOV P0, #7
;MOV P1, #7
;MOV P3, #7
;
;LOOP: 
;     MOV R0, P0 
;     MOV R1, P1 
;     MOV R2, P3 
;      MOV R4, #8
;      MOV R3, #0 
;     COUNT_R0: 
;     MOV A, R0 
;     RRC A 
;     MOV R0, A 
;     JNC SKIP_R0
;      INC R3
;  SKIP_R0:
;	DJNZ R4, COUNT_R0 
;	MOV R4, #8
;      
;      COUNT_R1: 
;     MOV A, R1 
;     RRC A 
;     MOV R1, A 
;     JNC SKIP_R1
;      INC R3
;  SKIP_R1:
;	DJNZ R4, COUNT_R1 
;	MOV R4, #8
;	
;    COUNT_R2: 
;     MOV A, R2 
;     RRC A 
;     MOV R2, A 
;     JNC SKIP_R2
;      INC R3
;  SKIP_R2:
;	DJNZ R4, COUNT_R2
;	MOV R4, #8
;
;	
; CJNE R3, #12, CHECK_COUNT
;
; CHECK_COUNT: 
; 	JC LESS_THAN
; 	MOV P2, #01H 
;	JMP LOOP
;
; LESS_THAN: MOV P2, #00H 
;	    JMP LOOP
;      

;Start:
;
;
;
;KEY     EQU 30H
;
;ROW1    BIT P1.4
;ROW2    BIT P1.5
;ROW3    BIT P1.6
;ROW4    BIT P1.7
;
;COL1    BIT P1.0
;COL2    BIT P1.1
;COL3    BIT P1.2
;COL4    BIT P1.3
;
;        MOV P2, #00H
;
;LOOP:   ACALL READ_KEY
;        JNC LOOP            ; If no key detected, keep scanning
;
;        MOV A, KEY
;        MOV DPTR, #DIGIT_CODE
;        MOVC A, @A+DPTR
;        MOV P2, A
;
;        ACALL DELAY         ; Simple delay (debouncing)
;        SJMP LOOP
;
;
;; ------------ READ_KEY SUBROUTINE ----------------
;READ_KEY:
;        ; Reset rows to HIGH
;        SETB ROW1
;        SETB ROW2
;        SETB ROW3
;        SETB ROW4
;        CLR A               ; Counter A = 0
;
;        ; === Scan ROW1 ===
;        CLR ROW1
;        JB COL1, NOT0
;            MOV B, #0
;            INC A
;NOT0:   JB COL2, NOT1
;            MOV B, #1
;            INC A
;NOT1:   JB COL3, NOT2
;            MOV B, #2
;            INC A
;NOT2:   JB COL4, NOT3
;            MOV B, #3
;            INC A
;NOT3:   SETB ROW1
;
;        ; === Scan ROW2 ===
;        CLR ROW2
;        JB COL1, NOT4
;            MOV B, #4
;            INC A
;NOT4:   JB COL2, NOT5
;            MOV B, #5
;            INC A
;NOT5:   JB COL3, NOT6
;            MOV B, #6
;            INC A
;NOT6:   JB COL4, NOT7
;            MOV B, #7
;            INC A
;NOT7:   SETB ROW2
;
;        ; === Scan ROW3 ===
;        CLR ROW3
;        JB COL1, NOT8
;            MOV B, #8
;            INC A
;NOT8:   JB COL2, NOT9
;            MOV B, #9
;            INC A
;NOT9:   JB COL3, NOT10
;            MOV B, #10
;            INC A
;NOT10:  JB COL4, NOT11
;            MOV B, #11
;            INC A
;NOT11:  SETB ROW3
;
;        ; === Scan ROW4 ===
;        CLR ROW4
;        JB COL1, NOT12
;            MOV B, #12
;            INC A
;NOT12:  JB COL2, NOT13
;            MOV B, #13
;            INC A
;NOT13:  JB COL3, NOT14
;            MOV B, #14
;            INC A
;NOT14:  JB COL4, NOT15
;            MOV B, #15
;            INC A
;NOT15:  SETB ROW4
;
;        ; === Key detection logic ===
;        CJNE A, #0, TEST_MULTIPLE_KEYS
;        CLR C           ; No key pressed
;        RET
;
;TEST_MULTIPLE_KEYS:
;        CJNE A, #1, MULTIPLE_KEYS
;        MOV KEY, B      ; Single key press
;        SETB C
;        RET
;
;MULTIPLE_KEYS:
;        MOV KEY, #16    ; Multiple keys pressed
;        SETB C
;        RET
;
;
;; ------------ DELAY SUBROUTINE ----------------
;DELAY:
;        MOV R2, #255
;D1:     MOV R1, #255
;D2:     DJNZ R1, D2
;        DJNZ R2, D1
;        RET
;
;
;; ------------ DIGIT CODE TABLE (7-Segment) ----------------
;DIGIT_CODE: 
;        DB 00111111B ; 0
;        DB 00000110B ; 1
;        DB 01011011B ; 2
;        DB 01001111B ; 3
;        DB 01100110B ; 4
;        DB 01101101B ; 5
;        DB 01111101B ; 6
;        DB 00000111B ; 7
;        DB 01111111B ; 8
;        DB 01101111B ; 9
;        DB 01110111B ; A
;        DB 01111100B ; B
;        DB 00111001B ; C
;        DB 01011110B ; D
;        DB 01111001B ; E
;        DB 01110001B ; F
;        DB 00000000B ; 16 - default for multiple key press (blank)
; 
;
;
;END
;
;