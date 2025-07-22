import logging
import os
from aiogram import Bot, Dispatcher, executor, types
from dotenv import load_dotenv

load_dotenv()
API_TOKEN = os.getenv("BOT_TOKEN")

logging.basicConfig(level=logging.INFO)
bot = Bot(token=API_TOKEN)
dp = Dispatcher(bot)

@dp.message_handler(commands=['start'])
async def send_welcome(message: types.Message):
    await message.answer(
        "🎮 Добро пожаловать в LuckyJet AI Бот!\n\n"
        "Выберите стратегию и укажите депозит:"
    )

if __name__ == '__main__':
    executor.start_polling(dp, skip_updates=True)
