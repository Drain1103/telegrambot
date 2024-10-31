mkdir my-telegram-bot
cd my-telegram-bot
npm init -y
npm install node-telegram-bot-api
const TelegramBot = require('node-telegram-bot-api');

// Replace with your bot's API token
const token = 'YOUR_TOKEN_HERE';

// Create a bot that uses 'polling' to fetch new updates
const bot = new TelegramBot(token, { polling: true });

// Handle the /start command
bot.onText(/\/start/, (msg) => {
    const chatId = msg.chat.id;
    const opts = {
        reply_markup: {
            inline_keyboard: [
                [
                    { text: 'Option 1', callback_data: '1' },
                    { text: 'Option 2', callback_data: '2' }
                ]
            ]
        }
    };
    bot.sendMessage(chatId, 'Choose an option:', opts);
});

// Handle button callbacks
bot.on('callback_query', (callbackQuery) => {
    const chatId = callbackQuery.message.chat.id;
    const option = callbackQuery.data;

    // Respond to the selected option
    bot.sendMessage(chatId, `You selected option: ${option}`);
});

// Additional feature example: echoing messages
bot.on('message', (msg) => {
    const chatId = msg.chat.id;
    if (msg.text && msg.text !== '/start') {
        bot.sendMessage(chatId, `You said: ${msg.text}`);
    }
});
node bot.js
bot.onText(/\/help/, (msg) => {
    const chatId = msg.chat.id;
    bot.sendMessage(chatId, 'This is a help message!');
});
npm install axios
const axios = require('axios');

bot.onText(/\/weather/, async (msg) => {
    const chatId = msg.chat.id;
    try {
        const response = await axios.get('API_URL_HERE');
        bot.sendMessage(chatId, `Weather: ${response.data.weather[0].description}`);
    } catch (error) {
        bot.sendMessage(chatId, 'Error fetching weather data.');
    }
});
