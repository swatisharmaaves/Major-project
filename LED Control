from telegram.ext import Updater,CommandHandler,MessageHandler,Filters
	from Adafruit_IO import Client,Data
	import os
	

	def turnoffthelight(update, context):
	  context.bot.send_message(chat_id=update.effective_chat.id, text="Okay,turning off the light")
	  context.bot.send_photo(chat_id=update.effective_chat.id,photo=’https://toppng.com/uploads/preview/transparent-light-bulb-11533043992eqclqqielo.png’)
	  send_value(0)
	def turnonthelight(update, context):
	  context.bot.send_message(chat_id=update.effective_chat.id, text="Okay,turning on the light")
	  context.bot.send_photo(chat_id=update.effective_chat.id,photo=’https://w1.pngwave.com/png/314/759/737/light-bulb-watercolor-paint-wet-ink-incandescent-light-bulb-lamp-electric-light-energy-conservation-png-clip-art.png’)
	  send_value(1)
	

	ADAFRUIT_IO_USERNAME = os.getenv('ADAFRUIT_IO_USERNAME')
	ADAFRUIT_IO_KEY = os.getenv('ADAFRUIT_IO_KEY')
	aio = Client(ADAFRUIT_IO_USERNAME,ADAFRUIT_IO_KEY)
	def send_value(value):
	  bot = aio.feeds('bot')
	  aio.send_data(bot.key,value)
	  
	

	def input_message(update, context):
	  text=update.message.text
	  if text == 'turnonthelight':
	    send_value(1)
	    context.bot.send_message(chat_id=update.effective_chat.id,text="Okay,turning on the light")
	    context.bot.send_photo(chat_id=update.effective_chat.id,photo=’https://w1.pngwave.com/png/314/759/737/light-bulb-watercolor-paint-wet-ink-incandescent-light-bulb-lamp-electric-light-energy-conservation-png-clip-art.png’)
	       
	  elif text == 'turnoffthelight':
	    send_value(0)
	    context.bot.send_message(chat_id=update.effective_chat.id,text="Okay,turning off the light")
	    context.bot.send_photo(chat_id=update.effective_chat.id,photo=’https://toppng.com/uploads/preview/transparent-light-bulb-11533043992eqclqqielo.png’)
	    
def start(update,context):
	  start_message='''
	/turnoffthelight or 'turn off':To turn off the led
	/turnonthelight or 'turn on'  :To turn on the led 
	'''
	  context.bot.send_message(chat_id=update.effective_chat.id, text=start_message)
	
  TOKEN =os.getenv('TOKEN')
	
	u=Updater(TOKEN,use_context=True)
	dp= u.dispatcher
	dp.add_handler(CommandHandler('turnoffthelight',turnoffthelight))
	dp.add_handler(CommandHandler('turnonthelight',turnonthelight))
	dp.add_handler(CommandHandler('start',start))
	dp.add_handler(MessageHandler(Filters.text & (~Filters.command),input_message))
	u.start_polling()
	u.idle()
	  

