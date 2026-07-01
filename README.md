# TG • LIVE — GitHub Pages + Telegram bot chat

## Nima qilingan
- `index.html` — bitta faylli sayt (dizayn + chat + Telegram Login Widget hammasi shu ichida).
- Ziyoratchi xabar yozsa → bot orqali sizning Telegram'ingizga (`660086073`) yuboriladi.
- Sayt har 3.5 soniyada `getUpdates` chaqirib, sizning javoblaringizni chatga chiqarib turadi.
- Telegram Login Widget avtomatik ravishda bot username'ni `getMe` orqali topib, tugmani chizadi.

## O'rnatish qadamlari

1. **Repo yarating**: GitHub'da yangi repository oching, masalan `username.github.io` yoki oddiy repo (keyin Pages'ni yoqasiz).
2. `index.html` faylini repo root'iga joylang, commit va push qiling.
3. Repo **Settings → Pages** bo'limida branch'ni tanlab, saytni yoqing.
4. Bir necha daqiqadan so'ng sayt manzili tayyor bo'ladi: `https://username.github.io/repo-nomi/`.

## Telegram Login Widget uchun MAJBURIY qadam

Widget ishlashi uchun bot domeningizni tasdiqlashi kerak:

1. Telegram'da **@BotFather** ga o'ting.
2. `/setdomain` buyrug'ini yuboring.
3. Botingizni tanlang, so'ng saytingiz domenini kiriting (masalan `username.github.io`).

Bu qadam bajarilmasa, login tugmasi chiqmaydi yoki xato beradi.

## Muhim eslatmalar

- **Token ochiq**: `index.html` ichidagi bot token brauzerda hamma uchun ko'rinadi. Buni faqat
  shaxsiy/sinov loyihalarida ishlating. Jiddiy foydalanish uchun tokenni serverless funksiya
  (Cloudflare Worker, Vercel Function) orqali yashirish tavsiya etiladi — xohlasangiz shuni
  ham tayyorlab beraman.
- **Umumiy chat**: barcha tashrifchilar bitta Telegram chat (`660086073`) orqali gaplashadi,
  shuning uchun texnik jihatdan barcha xabarlar bitta oqimda aralashadi. Demo/shaxsiy foydalanish
  uchun yetarli, lekin ko'p foydalanuvchili "alohida suhbatlar" kerak bo'lsa, backend kerak bo'ladi.
- **Fayl yuborish** ataylab qo'shilmagan (so'rovga ko'ra).

## Ranglar/Dizayn tokenlari (o'zgartirish uchun)
`index.html` ichidagi `:root` bo'limida:
- `--accent-a` / `--accent-b` — asosiy gradient (ko'k → indigo)
- `--surface` / `--surface-2` — fon qatlamlari
- Shriftlar: sarlavha uchun *Space Grotesk*, matn uchun *Inter*, vaqt/teglar uchun *JetBrains Mono*
