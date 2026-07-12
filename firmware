#include <ESP8266WiFi.h>
#include <WiFiClientSecure.h>

#define SENSOR D2

const char* ssid = "jiya_maru";
const char* password = "jiya_maru";

String BOTtoken = "8613169428:AAEIPbLCHqHutgVwc0BnPGcow91rbweH6kA";
String chatID = "5270423658";

bool lastState;

WiFiClientSecure client;

void connectWiFi() {

  WiFi.mode(WIFI_STA);
  WiFi.begin(ssid, password);

  Serial.print("WiFi Connecting");

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  Serial.println("\nWiFi Connected");
}

void sendTelegram(String msg) {

  client.setInsecure();
  client.setTimeout(15000);

  Serial.println("Connecting Telegram...");

  // IMPORTANT FIX: direct IP (avoids DNS fail)
  if (!client.connect("149.154.167.220", 443)) {
    Serial.println("Telegram Failed (No Connection)");
    return;
  }

  String url = "/bot" + BOTtoken +
               "/sendMessage?chat_id=" + chatID +
               "&text=" + msg;

  client.print(String("GET ") + url + " HTTP/1.1\r\n" +
               "Host: api.telegram.org\r\n" +
               "Connection: close\r\n\r\n");

  delay(1000);

  client.stop();

  Serial.println("Telegram Sent: " + msg);
}

void setup() {

  Serial.begin(115200);

  pinMode(SENSOR, INPUT);

  connectWiFi();

  lastState = digitalRead(SENSOR);
}

void loop() {

  if (WiFi.status() != WL_CONNECTED) {
    connectWiFi();
  }

  bool currentState = digitalRead(SENSOR);

  if (currentState != lastState) {

    if (currentState == HIGH) {
      Serial.println("Door OPEN");
      sendTelegram("Door OPEN");
    } else {
      Serial.println("Door CLOSED");
      sendTelegram("Door CLOSED");
    }

    lastState = currentState;

    delay(2000);
  }
}
