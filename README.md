<!-- @format -->

# 🤖 Aiogram Bot Template

Telegram botlar yaratish uchun tayyor shablon. Aiogram 2.x frameworki asosida qurilgan.

## 📋 Xususiyatlar

- ✅ Tayyor strukturaga ega loyiha
- ✅ Middlewares va filters qo'llab-quvvatlash
- ✅ Admin xabarnomalar tizimi
- ✅ Throttling (spam himoyasi)
- ✅ Logging tizimi
- ✅ Environment variables (.env)
- ✅ Virtual environment tayyor holda

## 🚀 O'rnatish

### 1. Repositoriyani klonlash

```bash
git clone https://github.com/username/aiogram-bot-template.git
cd aiogram-bot-template-master
```

### 2. Virtual environmentni faollashtirish

```bash
source env/bin/activate  # macOS/Linux
# yoki
env\Scripts\activate  # Windows
```

### 3. Kerakli kutubxonalarni o'rnatish

```bash
pip install aiohttp==3.11.0 environs==8.0.0 marshmallow==3.20.1
pip install --no-deps aiogram==2.25.2
pip install Babel certifi magic-filter
```

### 4. .env faylini sozlash

`.env.dist` faylidan `.env` yarating va o'z ma'lumotlaringizni kiriting:

```bash
cp .env.dist .env
```

`.env` faylini tahrirlang:

```env
BOT_TOKEN=1234567890:ABCdefGHIjklMNOpqrsTUVwxyz
ADMINS=123456789,987654321
ip=localhost
```

## 🎯 Ishga tushirish

```bash
python app.py
```

yoki virtual environment bilan:

```bash
env/bin/python app.py
```

## 📁 Loyiha Strukturasi

```
├── app.py                 # Asosiy fayl
├── loader.py             # Bot va dispatcher yuklanadi
├── requirements.txt      # Kerakli kutubxonalar
├── data/
│   ├── config.py        # Konfiguratsiya sozlamalari
├── filters/             # Custom filterlar
├── handlers/            # Xabar handlerlar
│   ├── users/          # Foydalanuvchi handlerlari
│   ├── groups/         # Guruh handlerlari
│   └── channels/       # Kanal handlerlari
├── keyboards/          # Klaviaturalar
│   ├── inline/        # Inline klaviaturalar
│   └── default/       # Reply klaviaturalar
├── middlewares/        # Middleware'lar
├── states/            # FSM holatlar
└── utils/             # Yordamchi funksiyalar
    ├── db_api/       # Database API
    └── misc/         # Boshqa funksiyalar
```

## 📝 Yangi handler qo'shish

1. `handlers/users/` papkasida yangi fayl yarating
2. Handler funksiyalarini yozing
3. `handlers/users/__init__.py` ga import qiling

Misol:

```python
# handlers/users/example.py
from aiogram import types
from loader import dp

@dp.message_handler(commands=['example'])
async def example_handler(message: types.Message):
    await message.answer("Bu misol handler!")
```

```python
# handlers/users/__init__.py
from . import start
from . import help
from . import echo
from . import example  # Yangi handler
```

## 🔧 Sozlamalar

### Environment Variables

- `BOT_TOKEN` - Telegram bot tokeni (@BotFather dan olinadi)
- `ADMINS` - Admin ID'lar ro'yxati (vergul bilan ajratilgan)
- `ip` - Server IP manzili

### Logging

Logging sozlamalari `utils/misc/logging.py` da joylashgan.

## 🛡️ Throttling

Spam himoyasi uchun throttling middleware ishlatiladi. Sozlamalar `middlewares/throttling.py` da.

## 🤝 Hissa qo'shish

1. Fork qiling
2. Feature branch yarating (`git checkout -b feature/AmazingFeature`)
3. O'zgarishlarni commit qiling (`git commit -m 'Add some AmazingFeature'`)
4. Branch'ga push qiling (`git push origin feature/AmazingFeature`)
5. Pull Request oching

## 📞 Murojaat

Savollar bo'lsa, issue oching yoki admin bilan bog'laning.

## 📄 Litsenziya

Bu loyiha MIT litsenziyasi ostida tarqatiladi.

## 🙏 Minnatdorchilik

- [Aiogram](https://github.com/aiogram/aiogram) - Telegram Bot API framework
- [Environs](https://github.com/sloria/environs) - Environment variables boshqaruvi

---

**Diqqat:** Python 3.13 bilan ishlatish uchun yuqoridagi o'rnatish ko'rsatmalariga amal qiling, chunki ba'zi kutubxonalar versiya muammolariga duch kelishi mumkin.
