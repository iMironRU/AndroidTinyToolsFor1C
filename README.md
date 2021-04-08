#### 1. Работа с Bluetooth сканером штрихкодов. 

Функция GetBluetoothDevicesList();

Возвращает строку со списком доступных Bluetooth устройств, в формате НазваниеУстройства///MACадрес,

Например: Scanner1///00:EA:1A:AA:6E:77

          Scanner2///00:EA:1A:AA:6E:78
          

Каждое устройство отделено от другого символом перевода строки.

Функция StartBluetoothScannerHandler(<MACадрес>)
где,

<MACадрес> - MAC адрес bluetooth сканера штрихкодов.

Функция запускает обработчик сообщений от сканера и при получении сообщения,
генерирует событие ВнешнееСобытие, 
где,
Источник = "AndroidTinyTools"
Событие = "Barcode"
Данные = Считанный штрихкод

Функция StopBluetoothScannerHandler() - Отключает обработчик сообщений от сканера.

Функция IsBluetoothScannerHandlerConnected() - Возвращает Истина, если установлено подключение к сканеру штрихкодов, и Ложь, если не установлено.

#### 2. Подписка на прием широковещательных оповещений. 

При получении оповещения, вызывается обработчик события ВнешнееСобытие у всех открытых форм.

Запуск подписки:

StartBroadcastReceiver(<ИмяСобытия>, <ИмяПараметра>);

где,

<ИмяСобытия> - имя события, на которое устанавливается подписка.

<ИмяПараметра> - имя параметра, в котором будут содержаться полученные данные события.
 

Пример:

AndroidTools.StartBroadcastReceiver("com.google.android.c2dm.intent.RECEIVE", "data");

Важно чтобы переменная с объектом компоненты (AndroidTools) была глобальной в модуле формы, поскольку подписка будет работать до тех пор, пока переменная остается в памяти.

#### 3. Вибрация

Vibrate([<Длительность вибрации в миллисекундах>]);

По умолчанию, длительность вибрации - 500 миллисекунд.

#### 4. Воспроизведение короткого сигнала

Beep([<Код сигнала>]);

где

Код сигнала- Числовая константа, определяющая то, какой именно звуковой сигнал будет проигран. По умолчанию = TONE_PROP_BEEP = 24.

Доступные значения можно посмотреть в Android SDK, у класса ToneGenerator.
 

#### 5. Toast - всплывающее стандартное окно сообщений. 

Окно появляется на короткое время и затем исчезает.

Toast("Привет!");

 

