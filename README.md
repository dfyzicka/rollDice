Данный репозиторий является форком https://github.com/treetrnk/rollem-telegram-bot
Я использую его для своих личных не комерческих целей, Я не програмист, а всего лишь энтузиаст Python и Linux
Я сделал лишь небольшую локализацию для родного языка и возможность быстрой сборки Docker контейнера для личного удобства



# rollDice Telegram Bot
Бот, бросающий многогранные кости для [Telegram] (https://telegram.org). Чтобы использовать этого бота в Telegram, [нажмите здесь](https://t.me/rollzkbot). Этот бот был создан для того, чтобы вы могли играть в настольные ролевые игры (RPG) через Telegram.

## Требует
* python-telegram-bot — см. https://github.com/python-telegram-bot/python-telegram-bot для получения инструкций по установке.

## Текущие функции
* `/roll [уравнение] [метка]` или `/r [уравнение] [метка]`
     * Уравнение обязательно, метка необязательна.
     * Бросьте кости, используя [обозначение кубиков] (https://en.wikipedia.org/wiki/Dice_notation) в качестве уравнения (включая Fate/Fudge Dice с 4dF). Не включайте пробелы в уравнение.
     * Пример: `/roll 4d8+16-2d4`
     * Взрывающиеся кости с восклицательным знаком: `/r 6d6!`
     * Самые высокие и самые низкие кубики сохраняются для преимущества/недостатка: `/r 2d20H Advantage`
* `/rf [модификатор] [метка]`
     * Модификатор и метка являются необязательными, но если заданы оба, модификатор должен стоять первым.
     * Бросьте 4 кубика Судьбы (Фадж).
     * Пример: `/rf 3 Легкая атлетика`
**[SEE THE WIKI](https://github.com/treetrnk/rollem-telegram-bot/wiki) for usage instructions and examples.**

## Запуск кода

Чтобы запустить код, колонируйте текущий репозиторий 
   git clone https://github.com/dfyzicka/rollDice.git
перейдите в папку
   cd rollBot/
Вам нужно будет использовать бота Bot Father для создания токена для вашего приложения. Получив этот токен, используйте приведенную ниже команду для запуска бота.
   python3 /PATH/TO/bot.py [YOUR_TOKEN_HERE]
Замените "/PATH/TO/: на путь к bot.py на вашем компьютере и "[YOUR_TOKEN_HERE]" на токен, который вы только что сгенерировали через Bot Father.

## Docker run
колонируйте текущий репозиторий 
   git clone https://github.com/dfyzicka/rollDice.git
перейдите в папку 
   cd rollBot/ 
переименуйте файл ex.env в .env и укажите в нём свой токен для теграмбота
    mv ex.env .env
соберите контейнер
   docker build -t rolldice .
запустите его
   docker run -d --restart always rolldice

## Troubleshooting

Если вы получаете сообщение об ошибке «Ответ сервера не может быть декодирован с использованием UTF-8», внесите следующие изменения в файл python-telegram-bot request.py: [Bug Fix Diff](https://github.com/python-telegram-bot/python-telegram-bot/pull/1623/files)
