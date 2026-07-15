```C
 // Connections
  #define IN 7
  #define OUT 3
 // Variables
  int statusN;
  int statusO = false;
  int LED = false;

 // set input/output
void setup() {
  pinMode(OUT, OUTPUT);
  pinMode(IN, INPUT);
}

// Loop
void loop() {
  statusN = digitalRead(IN); //read first
  if (statusO==false && statusN ==true) { //then check
      LED = !LED;
  }
  statusO = statusN; //then change state
  digitalWrite(OUT, LED); //output
  delay(75);
 }
```

