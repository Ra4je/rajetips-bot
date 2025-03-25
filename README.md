import telebot
import os

# Pegando as variáveis do Render (você precisa adicioná-las depois)
TOKEN = os.getenv("TELEGRAM_BOT_TOKEN")
CHAT_ID = os.getenv("TELEGRAM_CHAT_ID")

bot = telebot.TeleBot(TOKEN)

# Comando para testar se o bot está funcionando
@bot.message_handler(commands=['start'])
def send_welcome(message):
    bot.send_message(CHAT_ID, "🚀 Bot de Apostas Ativado!")

# Monitora mensagens e responde
@bot.message_handler(func=lambda message: True)
def echo_all(message):
    bot.send_message(CHAT_ID, f"📢 {message.text}")

# Mantém o bot rodando
bot.polling()
