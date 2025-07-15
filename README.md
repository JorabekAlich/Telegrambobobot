bot.py
from telegram import Update
from telegram.ext import ApplicationBuilder, CommandHandler, MessageHandler, filters, ContextTypes

async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text("Salom! Men doimiy ishlayman 🤖")

async def reply_text(update: Update, context: ContextTypes.DEFAULT_TYPE):
    user_text = update.message.text
    await update.message.reply_text(f"Siz yozdingiz: {user_text}")

if __name__ == '__main__':
    app = ApplicationBuilder().token("8038813301:AAGJ78uBp9PYpd2u7pplLecgnVPP4savEz0").build()
    app.add_handler(CommandHandler("start", start))
    app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, reply_text))
    print("Bot ishga tushdi...")
    app.run_polling()
