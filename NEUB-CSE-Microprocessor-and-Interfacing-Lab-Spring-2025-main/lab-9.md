# NEUB CSE Microprocessor and Interfacing Lab Spring 2025 Lab 9

## Task 1
Write a code to drive differential drive robot with two dc motors using L298 motor driver.

Circuit:
![Lab 9 Task 1 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-9/CSE-06133118-322-2501-lab9-task-1-3CKT_bb.png)


Code:
```c
int mls1=3;
int mls2=4;
int mrs1=7;
int mrs2=8;
int mlen=5;
int mren=9;


void setup() {
  pinMode(mls1, OUTPUT);
  pinMode(mls2, OUTPUT);
  pinMode(mrs1, OUTPUT);
  pinMode(mrs2, OUTPUT);
  pinMode(mlen, OUTPUT);
  pinMode(mren, OUTPUT);

  Serial.begin(115200);
  //We are not using PWM for now
  digitalWrite(mlen, HIGH);
  digitalWrite(mren, HIGH);
}

void loop() {
  //Moving Forward
  //Left Motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2, LOW);
  //Right Motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2, LOW);
  delay(1000);

  //Moving Backward
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, HIGH);
  // right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, HIGH);
  delay(1000);
  
  //Stop
  //Left motor Stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, LOW);
  //Right Motor Stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, LOW);
  delay(1000);

  //Turning Right
  //Left Motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2, LOW);
  //Right Motor Stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, LOW);
  delay(1000);

  //Turning Left  
  //Left motor Stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, LOW);
  //Right Motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2, LOW);
  delay(1000);

}
```

## Task 2
Write a code to drive differential drive robot with two dc motors using L298 motor driver. Different movement should be incorporated using individual functions.

Circuit:
![Lab 9 Task 2 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-9/CSE-06133118-322-2501-lab9-task-1-3CKT_bb.png)

Code:
```c
int mls1=3;
int mls2=4;
int mrs1=7;
int mrs2=8;
int mlen=5;
int mren=9;


void setup() {
  pinMode(mls1, OUTPUT);
  pinMode(mls2, OUTPUT);
  pinMode(mrs1, OUTPUT);
  pinMode(mrs2, OUTPUT);
  pinMode(mlen, OUTPUT);
  pinMode(mren, OUTPUT);

  Serial.begin(115200);
  //We are not using PWM for now
  digitalWrite(mlen, HIGH);
  digitalWrite(mren, HIGH);
}

void loop() {
  moveForward();
  delay(1000);
  moveBackward();
  delay(1000);  
  carStop();
  delay(1000);
  moveForwardRight();
  delay(1000);
  moveForwardLeft();
  delay(1000);

}

void moveForward(){
  //Moving Forward
  //Left Motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2, LOW);
  //Right Motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2, LOW);
}

void moveBackward(){
  //Moving Backward
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, HIGH);
  // right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, HIGH);
}

void carStop(){
  //Stop
  //Left motor Stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, LOW);
  //Right Motor Stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, LOW);
}

void moveForwardRight(){
  //Turning Right
  //Left Motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2, LOW);
  //Right Motor Stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, LOW);
}

void moveForwardLeft(){
  //Turning Left  
  //Left motor Stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, LOW);
  //Right Motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2, LOW);
}

void moveBackwardRight(){
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, HIGH);
  //Right Motor Stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, LOW);
}

void moveBackwardLeft(){
  //Left motor Stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, LOW);
  // right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, HIGH);  
}
```

## Task 3
Write a code to drive a differential drive robot with two dc motors with variable speed using L298 motor driver. Different movement should be incorporated using individual functions.

Circuit:
![Lab 9 Task 3 Circuit in breadboard](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-9/CSE-06133118-322-2501-lab9-task-1-3CKT_bb.png)

Code:
```c
int mls1=3;
int mls2=4;
int mrs1=7;
int mrs2=8;
int mlen=5;
int mren=9;


void setup() {
  pinMode(mls1, OUTPUT);
  pinMode(mls2, OUTPUT);
  pinMode(mrs1, OUTPUT);
  pinMode(mrs2, OUTPUT);
  pinMode(mlen, OUTPUT);
  pinMode(mren, OUTPUT);

  Serial.begin(115200);
  //We are not using PWM for now
  digitalWrite(mlen, HIGH);
  digitalWrite(mren, HIGH);
}

void loop() {
  moveForward(100);
  delay(1000);
  moveForward(50);
  delay(1000);
  moveBackward(50);
  delay(1000);  
  carStop();
  delay(1000);
  moveForwardRight(100);
  delay(1000);
  moveForwardLeft(100);
  delay(1000);

}

void moveForward(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen,pwmVal);
  analogWrite(mren,pwmVal);
  //Moving Forward
  //Left Motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2, LOW);
  //Right Motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2, LOW);
}

void moveBackward(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen,pwmVal);
  analogWrite(mren,pwmVal);
  //Moving Backward
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, HIGH);
  // right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, HIGH);
}

void carStop(){
  //Stop
  //Left motor Stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, LOW);
  //Right Motor Stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, LOW);
}

void moveForwardRight(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen,pwmVal);
  analogWrite(mren,pwmVal);
  //Turning Right
  //Left Motor forward
  digitalWrite(mls1,HIGH);
  digitalWrite(mls2, LOW);
  //Right Motor Stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, LOW);
}

void moveForwardLeft(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen,pwmVal);
  analogWrite(mren,pwmVal);
  //Turning Left  
  //Left motor Stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, LOW);
  //Right Motor forward
  digitalWrite(mrs1,HIGH);
  digitalWrite(mrs2, LOW);
}

void moveBackwardRight(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen,pwmVal);
  analogWrite(mren,pwmVal);
  //Left motor backward
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, HIGH);
  //Right Motor Stop
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, LOW);
}

void moveBackwardLeft(int percentSpeed){
  int pwmVal=map(percentSpeed,0,100,0,255);
  analogWrite(mlen,pwmVal);
  analogWrite(mren,pwmVal);
  //Left motor Stop
  digitalWrite(mls1,LOW);
  digitalWrite(mls2, LOW);
  // right motor backward
  digitalWrite(mrs1,LOW);
  digitalWrite(mrs2, HIGH);  
}
```

## General Discussion Regardig Robot Control

### Light Follower Robot:
![Light Follower Robot Structure](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-9/light%20Follower.png)
Light follower robot is a type of autonomous robot that uses light sensors to detect the direction of light and move towards it. The robot typically has three light sensors placed on front, which allows it to determine the direction of the light source. Based on the readings from these sensors, the robot can adjust its movement to follow the light.

### Line Follower Robot:
![Line Follower Robot Structure](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-9/line%20Follower.png)
Line follower robot is a type of autonomous robot that uses infrared sensors to detect the presence of a line on the ground and follow it. The robot typically has three or more infrared sensors placed on the front bottom, which allows it to determine whether it is on the line or off the line. Based on the readings from these sensors, the robot can adjust its movement to stay on the line.
The IR sensors are used to detect the line by emitting infrared light and measuring the reflection. When the robot is on the line, the sensors will detect a strong reflection, while when it is off the line, the reflection will be weak or absent.
The circuit for the IR sensors typically consists of an IR LED and a photodiode or phototransistor. The IR LED emits infrared light, which is reflected by the surface below. The photodiode or phototransistor detects the reflected light and sends a signal to the microcontroller, which can then determine whether the robot is on the line or off the line.
The circuit is as below:
![Line Follower IR Sensor Circuit](https://raw.githubusercontent.com/shparvez001/NEUB-CSE-Microprocessor-and-Interfacing-Lab-Spring-2025/main/lab-9/IR%20Sensor%20Circuit.png)

### Obstacle Avoidance Robot:

Obstacle avoidance robot is a type of autonomous robot that uses ultrasonic sensors or even IR sensors to detect obstacles in its path and avoid them. The robot typically has one or more ultrasonic sensors placed on the front, which allows it to measure the distance to the nearest obstacle. Based on the readings from these sensors, the robot can adjust its movement to avoid collisions.
For short distances, IR sensors can be used. The IR sensors work by emitting infrared light and measuring the reflection. When the robot is close to an obstacle, the reflection will be strong, indicating that the robot should stop or change direction.
For moderate distances, instead of IR sensors, ultrasonic sensors are used. Ultrasonic sensors work by emitting a high-frequency sound wave and measuring the time it takes for the sound wave to bounce back after hitting an obstacle. The distance to the obstacle can be calculated based on the speed of sound and the time taken for the sound wave to return.
For long distances, LIDAR sensors can be used. LIDAR (Light Detection and Ranging) sensors work by emitting laser beams and measuring the time it takes for the light to bounce back after hitting an obstacle. The distance to the obstacle can be calculated based on the speed of light and the time taken for the light to return.

## [Watch Class video Here](https://youtu.be/UoYoHAj5-Z4)
