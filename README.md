# Meteostation
Соберите все компоненты по схеме из папки _Schemes_
Извлеките папки библиотек в папку Arduino/libraries
Для того чтобы узнать IC адресс дисплея подключите дисплей откройте папку Firmware и загрузите в плату прошивку Test_IC_Adress
Откройте COM порт и дождитесь получения адреса дисплея
В 9 строчке файла Code_itog_final
LiquidCrystal_I2C lcd(0x3F, 16, 2);
установите полученный адрес(вместо 0x3F)
если на дисплее не отображаются символы то покрутите подстроечный резистор на I2C переходнике
В строчке 
#define DHTPIN 5
вместо 5-го пина установите пин на котором у вас находится датчик DHT11
в строчке
#define BUT1_PIN 3
вместо пина d3 установите пин на котором находится кнопка
возможны пины d2 или d3 т.к реализована работа аппаратного прерывания
в случае выбора пина d2 необходимо в строчке 
attachInterrupt(1, myInterrupt , CHANGE);
изменить 1 на 0
установите характеристики используемой кнопки в строке
GButton butt1(BUT1_PIN, HIGH_PULL, NORM_OPEN);
если кнопка нормально разомкнутая то можете ничего не трогать
в противном слуучае измените параметр NORM_OPEN на NORM_CLOSE
пин пьезоизлучателя можно изменить в строчке
#define buzzerpin 8
всё готово
загружайте прошивку и наслаждайтесь
