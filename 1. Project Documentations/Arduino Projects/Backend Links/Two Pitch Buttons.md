```C
 // Connections
  #define INSO 7
  #define OUTSO 3
  #define INLA 8
  #define OUTLA 4
 // Variables
  int statusNLA;
  int statusNSO;
  int statusOLA = false;
  int statusOSO = false;
  int SO = false;
  int LA = false;

 // set input/output
void setup() {
  pinMode(OUTSO, OUTPUT);
  pinMode(INSO, INPUT);
  pinMode(INLA, INPUT);
  pinMode(OUTLA, OUTPUT);
  Serial.begin(9600);
}

// Loop
void loop() {

  //status for SO
  statusNSO = digitalRead(INSO); 
  if (statusOSO==false && statusNSO ==true) { 
      SO = !SO;  
  }
  statusOSO = statusNSO;

//status for LA
  statusNLA = digitalRead(INLA); 
  if (statusOLA==false && statusNLA ==true) { 
      LA = !LA;
  }
  statusOLA = statusNLA;

  //output if SO is true
  if (SO == true && LA == false) {
  tone(OUTSO, 784); 
  Serial.print("SO is playing");
  }
  else {
   noTone(OUTSO);
  }

  // output if LA is true
  if (LA == true && SO==false) {
  tone(OUTLA, 880); 
  Serial.print("LA is playing");
  }
  else {
   noTone(OUTLA);
  }
  
  delay(75);
  }

```