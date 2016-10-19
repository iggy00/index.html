//T1A12-IFTTT-name.ino

bool myDoPublish2  = false;
bool myDoSubscribe = false;

void setup(){
    
    pinMode(D7, OUTPUT);
    pinMode(D2, INPUT_PULLDOWN);  // push button send to IFTTT
    pinMode(D4, INPUT_PULLDOWN);  // Push button to reset
    //  INPUT_PULLDOWN resets D0 to LOW if no power applied to it
    Particle.subscribe("my-lamp-on09", myD7Function);   // public
    // Particle.subscribe("my-lamp-on5555", myLampFunction, MY_DEVICES);   
    // change the number for uniqueness. Change 5555
}

void loop(){
     
    delay(10);

    if (myDoPublish2 == true){
        if (digitalRead(D2) == 1 ){   //if D2 on then send to IFTTT
           Particle.publish("my-lamp-on09", "SECRET-STUFF", 60, PUBLIC); 
           // Particle.publish("my-lamp-on3456", "SECRET-STUFF", 60, PRIVATE);  
           // change 5555 to call a different photon's lamb 
           myDoPublish2 = false;      // stop from doing it again
        }   
    }
    
    if (digitalRead(D4) == 1 ){  // reset everything
        myDoPublish2   = true;
        myDoSubscribe  = true;
        digitalWrite(D7, 1);    // D7 on
        delay(50);        
        digitalWrite(D7, 0);    // D7 off
        delay(50);        
        digitalWrite(D7, 1);
        delay(50);
        digitalWrite(D7, 0);
        delay(1000);
    }
  
}


void myD7Function(const char *event, const char *data){    
    if (myDoSubscribe == true){   
        if (String(data) == "SECRET-STUFF"){   // an attempt at security
          digitalWrite(D7, 1);   // D7 on to prove it works 
          delay(1000);        
          digitalWrite(D7, 0);
          myDoSubscribe = false; // stop it fromdoing it again
          
        }
     }
}








//now setup the IFTTT and the particle channel

