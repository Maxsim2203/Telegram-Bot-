# Telegram-Bot-
Tg bot on Python 3.9



Основные команды  бота 
1) /start 
2) photo
3) id
4) Hi
5) /help
6) /website

Для работы с фотографиями загрузите фотографию в проект как это показано ниже:

![image](https://user-images.githubusercontent.com/95234863/200157237-bb1ed76a-a566-476a-8a74-3193b59bc6b6.png)

![image](https://user-images.githubusercontent.com/95234863/200157249-e53c28ba-23a4-494e-b529-06f8c47aa005.png)

 Для работы с ботом необходимо найти бота в телеграмме по ссылке ниже
 https://t.me/NRRProBot



 
Для создания бота был использован следующий код:

```
import types

import telebot

@bot.message_handler(commands=['start'])
def start(message):
    mess = f'Привет, <b>{message.from_user.first_name} <u>{message.from_user.last_name}</u></b>'
    bot.send_message(message.chat.id, mess, parse_mode='html')\

@bot.message_handler(content_types=['text'])
def get_user_text(message):
    if message.text == "Hi":
         bot.send_message(message.chat.id, "И тебе привет!", parse_mode='html')
    elif message.text == "id":
         bot.send_message(message.chat.id, f"Твой ID: {message.from_user.id}", parse_mode='html')
    elif message.text == "photo":
         photo = open('2.jpg', 'rb')
         bot.send_photo(message.chat.id, photo)
    else:
         bot.send_message(message.chat.id, f"Попробуй заново я тебя не понимаю", parse_mode='html')


@bot.message_handler(content_types=['photo'])
def get_user_photo(message):
    bot.send_message(message.chat.id, 'Вай крутая фотка')


@bot.message_handler(content_types=['website'])
def website(message):
    markup = types.InlineKeyboardMarkup()
    markup.add(types.InlineKeyboardButton("website", "https://www.youtube.com/"))
    bot.send_message(message.chat.id, 'Прейдите на WebSite', reply_maekup=markup)

    @bot.message_handler(content_types=['help'])
    def website(message):
        markup = types.ReplyKeyboardMarkup(resize_keyboard=True, row_width=1)
        website = types.KeyboardButton('Веб сайт')
        start = types.KeyboardButton('Старт')
        markup.add(website, start)
        bot.send_message(message.chat.id, 'Прейдите на website', reply_maekup=markup)

bot.polling(none_stop=True)

 '''
