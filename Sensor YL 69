// Deklarasi pustaka
#include <LiquidCrystal.h>

// Deklarasi pin LCD
#define LCD_RS 12
#define LCD_E 11
#define LCD_D4 5
#define LCD_D5 4
#define LCD_D6 3
#define LCD_D7 2

// Deklarasi objek LCD
LiquidCrystal lcd(LCD_RS, LCD_E, LCD_D4, LCD_D5, LCD_D6, LCD_D7);

// Deklarasi pin sensor kelembaban tanah
const int sensorPin = A0;

// Deklarasi global untuk calibrationFactor (bisa diakses di setup() dan loop())
float calibrationFactor;

void setup() {
  // Inisialisasi Serial Monitor
  Serial.begin(9600);

  // Inisialisasi LCD
  lcd.begin(16, 2);
  lcd.setCursor(0, 0);
  lcd.print("Sensor Kelembaban Tanah");

  // Kalibrasi sensor dan simpan nilai di calibrationFactor
  int sensorValue = analogRead(sensorPin);
  calibrationFactor = (100.0 / sensorValue);
}

void loop() {
  // Baca nilai sensor
  int sensorValue = analogRead(sensorPin);

  // Hitung nilai kelembaban tanah menggunakan calibrationFactor
  float moistureLevel = (sensorValue * calibrationFactor);

  // Tampilkan nilai kelembaban tanah di Serial Monitor
  Serial.print("Kelembaban Tanah: ");
  Serial.print(moistureLevel);
  Serial.println("%");

  // Tampilkan nilai kelembaban tanah di LCD
  lcd.setCursor(0, 1);
  lcd.print("Kelembaban: ");
  lcd.print(moistureLevel);
  lcd.print("%");

  // Tunggu 1 detik
  delay(300);
