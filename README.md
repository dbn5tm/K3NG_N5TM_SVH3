# K3NG_N5TM_SVH3
 
Hack of K3NG Rotator Controller code specically for SVH3 Slew Drive Az/El with a pair of quadrature encoders.
Calibration of this slew drive is based on 62-1 slew gears and 553-1 measured gear motor.  
Total pulses X2 = 68580 for full 360° rotation of the Azimuth gear.
(rotator_settings.h)
#define AZ_POSITION_INCREMENTAL_ENCODER_PULSES_PER_REV 68580.0 
#define EL_POSITION_INCREMENTAL_ENCODER_PULSES_PER_REV 68580.0

Note: this code uses the Incremental option which requires interrupt enabled input pins.  On the Mega 2, 3  18, 19 or 20,21.  See documentation for corresponding interupt assignments.  
(rotator_pins.h)
#ifdef FEATURE_AZ_POSITION_INCREMENTAL_ENCODER
  #define az_incremental_encoder_pin_phase_a 3 //3 must be an interrupt capable pin
  #define az_incremental_encoder_pin_phase_b 2 //3 // must be an interrupt capable pin
  //#define az_incremental_encoder_pin_phase_z 0 //4
  #define AZ_POSITION_INCREMENTAL_ENCODER_A_PIN_INTERRUPT 1             // Uno: pin 2 = interrupt 0, pin 3 = interrupt 1 ; Mega: pin 2 = interrupt 0, pin 3 = interrupt 1, pin 21 = interrupt 2, pin 20 = interrupt 3, pin 19 = interrupt 4, pin 18 = interrupt 5
  #define AZ_POSITION_INCREMENTAL_ENCODER_B_PIN_INTERRUPT 0           // Uno: pin 2 = interrupt 0, pin 3 = interrupt 1 ; Mega: pin 2 = interrupt 0, pin 3 = interrupt 1, pin 21 = interrupt 2, pin 20 = interrupt 3, pin 19 = interrupt 4, pin 18 = interrupt 5
  #ifdef FEATURE_EL_POSITION_INCREMENTAL_ENCODER
  #define el_incremental_encoder_pin_phase_a 19 //18 //2 // must be an interrupt capable pin
  #define el_incremental_encoder_pin_phase_b 18 //19 //3 // must be an interrupt capable pin
  //#define el_incremental_encoder_pin_phase_z 0 //22 //4
  #define EL_POSITION_INCREMENTAL_ENCODER_A_PIN_INTERRUPT 4 //5 //0             // Uno: pin 2 = interrupt 0, pin 3 = interrupt 1 ; Mega: pin 2 = interrupt 0, pin 3 = interrupt 1, pin 21 = interrupt 2, pin 20 = interrupt 3, pin 19 = interrupt 4, pin 18 = interrupt 5
  #define EL_POSITION_INCREMENTAL_ENCODER_B_PIN_INTERRUPT 5 //4 //1  

  NOTE: az_incremental_encoder_in_z and el_incremental_encoder_in_z are note used, as the encoders in the slew drive do not provide a calibration switch closure.
  
