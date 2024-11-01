from flask import Flask, request

import requests

app = Flask(__name__)

# টেলিগ্রাম বটের তথ্য
BOT_TOKEN = '6657332138:AAECyh7HXVdAmROC0a4YCyYqCANWVAHlOT0'
CHAT_ID = '-1002111946136'


@app.route('/')
def home():
    return '''
        <h1>আমার ওয়েবসাইটে স্বাগতম</h1>
        <a href="/send_user_agent">ইউজার এজেন্ট পাঠান টেলিগ্রামে</a>
    '''


@app.route('/send_user_agent')
def send_user_agent():
    user_agent = request.headers.get('User-Agent')  # ইউজার এজেন্ট সংগ্রহ করা
    message = f'User Agent: {user_agent}'

    # টেলিগ্রামে পাঠানোর জন্য API কল
    response = requests.post(
        f'https://api.telegram.org/bot{BOT_TOKEN}/sendMessage',
        json={'chat_id': CHAT_ID, 'text': message}
    )

    if response.status_code == 200:
        return 'Live_SEX_JOIN ROOM'
    else:
        return 'NO'


if __name__ == '__main__':
    app.run(debug=True)
