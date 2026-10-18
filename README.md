
const {
  Client,
  GatewayIntentBits
} = require('discord.js');

const client = new Client({
  intents: [
    GatewayIntentBits.Guilds,
    GatewayIntentBits.GuildMessages,
    GatewayIntentBits.MessageContent
  ]
});

const prefix = '!';

client.once('ready', () => {
  console.log(`Bot online: ${client.user.tag}`);
});

client.on('messageCreate', async message => {
  if (message.author.bot) return;
  if (!message.content.startsWith(prefix)) return;

  const args = message.content
    .slice(prefix.length)
    .trim()
    .split(/\s+/);

  const command = (args.shift() || '').toLowerCase();

  if (command === 'ping') {
    await message.reply('🏓 Pong! O bot está funcionando.');
  }

  if (command === 'oi') {
    await message.reply(`Olá, ${message.author}!`);
  }
});

client.login(process.env.DISCORD_TOKEN);
