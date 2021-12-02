#include <SPI.h>       // Haberleşme için kullanılan kütüphane.
#include <RFID.h>      // RFID kütüphanesi.
#include <Keyboard.h>  // Klavye girişi yapabilmemiz için gerekli kütüphane

#define SS_PIN 10      // Rfid kartının pin bağlantılarının olduğu konum.
#define RST_PIN 9      // Rfid kartının pin bağlantılarının olduğu konum.

RFID rfid(SS_PIN, RST_PIN); 
int ledpini = 13;
 
void setup()
{ 
  pinMode(ledpini,OUTPUT);
  SPI.begin();           //SPI iletişimini başlatıyoruz 
  rfid.init();
  Keyboard.begin();      //Klavye olarak kullanmak için bu özelliği açıyoruz.
  digitalWrite(ledpini,LOW);
}

void loop()
{
    
    if (rfid.isCard()) {                 //Yeni bir RFID kart okundu mu onu kontrol ediyoruz
        if (rfid.readCardSerial()) {     // Rfid kartımızın kart id'si.
            if(rfid.serNum[0] == 105
             && rfid.serNum[1] == 45
             && rfid.serNum[2] == 215
             && rfid.serNum[3] == 162
             && rfid.serNum[4] == 49
            ) {               
              Keyboard.press(KEY_RETURN);    //Klavyeden ENTER tuşuna basıyoruz
              delay(50);
              Keyboard.releaseAll();          //Basılı olan tuşu geri çekmek için bu fonksiyonu kullanıyoruz. Bu fonksiyon olmazsa enter tuşu hep basılıkalıyor
              delay(500);
              Keyboard.print("378868185264");    //Buraya Bilgisayar şifresini yazıyoruz
             } else {
               digitalWrite(ledpini,HIGH);    //Farklı kart okutulduğunda Arduino üzerindeki ledi yaktırıyor.
               delay(10);
             }
             digitalWrite(ledpini,LOW);       //Doğru kart okutulduğunda yanacak ışık.
          }
          if (rfid.readCardSerial()) {     // Rfid kartımızın kart id'si.
            if(rfid.serNum[0] == 73
             && rfid.serNum[1] == 165
             && rfid.serNum[2] == 63
             && rfid.serNum[3] == 155
             && rfid.serNum[4] == 72
            ) {               
              Keyboard.press(KEY_RETURN);    //Klavyeden ENTER tuşuna basıyoruz
              delay(50);
              Keyboard.releaseAll();          //Basılı olan tuşu geri çekmek için bu fonksiyonu kullanıyoruz. Bu fonksiyon olmazsa enter tuşu hep basılıkalıyor
              delay(500);
              Keyboard.print("your password");    //Buraya Bilgisayar şifresini yazıyoruz
             } else {
               digitalWrite(ledpini,HIGH);    //Farklı kart okutulduğunda Arduino üzerindeki ledi yaktırıyor.
               delay(10);
             }
             digitalWrite(ledpini,LOW);       //Doğru kart okutulduğunda yanacak ışık.
          }
    }

    
    rfid.halt();
}
