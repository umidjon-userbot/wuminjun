# TG • LIVE — GitHub Pages + Telegram bot chat

## 🆕 group.html — Guruh nazorati paneli (jonli lenta + reply)

Bu alohida sahifa: `group.html`. Vazifasi boshqacha — shaxsiy chat emas, balki
**butun guruhdagi barcha xabarlarni real vaqtda ko'rsatadigan** panel.

### Qanday ishlaydi
1. Botni guruhga qo'shing va **admin qiling**. Bot guruhda admin bo'lsa, Telegram
   uni "privacy mode"dan mustasno qiladi — ya'ni bot guruhdagi barcha xabarlarni
   (nafaqat o'ziga yozilganlarini) ko'ra oladi. Alohida sozlash shart emas.
2. `group.html`'ni oching, kirish kodini kiriting (standart: `1234` —
   **buni albatta o'zgartiring**, fayl ichida `DEFAULT_ACCESS_CODE` qatorida).
3. Guruhda birontasi xabar yozgach, u yuqori qismdagi ro'yxatda avtomatik paydo bo'ladi
   — shuni tanlang. Shundan keyin barcha xabarlar jonli lentada chiqa boshlaydi.
4. Istalgan xabar ostidagi **"Javob berish"** tugmasini bosib, matn yozib yuborsangiz —
   javobingiz guruhda aynan o'sha kishining xabariga **reply** qilib chiqadi (hamma ko'radi,
   chunki bu shaxsiy emas, guruh ichidagi ochiq javob).

### Nega shaxsiy DM emas, balki guruh-reply?
Telegram bot API orqali bot faqat undan oldin **o'zi bilan suhbat boshlagan**
foydalanuvchilarga shaxsiy xabar yubora oladi — botga hech qachon yozmagan odamga
"nogohdan" DM yozib bo'lmaydi (bu Telegram'ning spamga qarshi qoidasi). Shuning
uchun eng tabiiy va ishlaydigan yo'l — guruh ichida o'sha odamning xabariga
**reply** qilish, xuddi odam qo'lda reply qilgandek.

### ⚠️ Muhim xavfsizlik eslatmasi
- Bu sahifa ochilsa, **guruhdagi barcha yozishmalar** ko'rinadi. Havolani hech kimga
  bermang, hech qayerga joylamang.
- Kirish kodi (`DEFAULT_ACCESS_CODE`) himoya emas — u ham shu faylning ichida,
  demak texnik jihatdan chetlab o'tish mumkin. Bu faqat tasodifiy/notanish odamlar
  kirib qolishining oldini oladi, real himoya emas.
- Jiddiy foydalanish uchun bu panelni umuman GitHub Pages'da emas, balki login talab
  qiladigan xususiy serverda joylashtirish tavsiya etiladi.

---

## index.html — Shaxsiy chat vidjeti (1-versiya)

- **Foydalanuvchi fayl/rasm yubora oladi** (📎 tugmasi orqali). Rasm bo'lsa — Telegram'da va
  saytda thumbnail sifatida, boshqa fayllar (pdf, docx, zip va h.k.) — fayl kartasi sifatida
  ko'rinadi.
- **Admin javobida ham fayl bo'lishi mumkin**: Telegram'da foydalanuvchining forward qilingan
  xabariga "Reply" qilib rasm/fayl yuborsangiz, u ham saytda o'sha foydalanuvchi oynasida chiqadi.
- **Fayl limiti**: yuklash uchun Telegram bot API 50 MB gacha ruxsat beradi, lekin saytda qayta
  ko'rsatish (`getFile`) uchun bot API cheklovi — **20 MB**. Xavfsizlik uchun sayt frontendida
  ham 20 MB dan katta fayllarni yubormaydi.
- **Local preview cheklovi**: foydalanuvchi o'zi yuborgan faylning ko'rinishi (thumbnail) faqat
  o'sha sessiya davomida ishlaydi; sahifa qayta yuklanganda faqat fayl nomi saqlanadi (fayl allaqachon
  Telegram'ga yetib bo'lgan bo'ladi, shunchaki brauzer preview havolasi vaqtinchalik bo'lgani uchun).

## Yangilanishlar (v2)
- Endi **faqat Telegram orqali kirgan** foydalanuvchi yozishi mumkin (login bo'lmasa input/tugma o'chirilgan).
- GitHub Pages haqidagi ogohlantirish banneri olib tashlandi.
- **Har bir foydalanuvchining suhbati alohida** — ID orqali ajratiladi, boshqa foydalanuvchining
  xabari/aralashuvi bo'lmaydi.
- **2 tomonlama reply tizimi**: foydalanuvchi ID va username ko'rsatiladi, admin (siz)
  Telegram'da **shu foydalanuvchining forward qilingan xabariga "Reply" qilganda**, javob
  faqat o'sha foydalanuvchining brauzerida chiqadi.

## Bu qanday ishlaydi (muhim tushuncha)

Telegram Bot API'da bot o'zi yuborgan xabarni (`sendMessage`) qayta o'qiy olmaydi —
`getUpdates` faqat **foydalanuvchi botga yozganda** yangilanish beradi. Shuning uchun:

1. Ziyoratchi login qilib, xabar yozadi → xabar mana bunday formatda sizga (`660086073`) yuboriladi:
   ```
   #UID:123456789
   👤 Ism Familiya (@username)
   💬 Xabar matni
   ```
   Ushbu `#UID:...` qatori — ichki marker, faqat marshrutlash uchun ishlatiladi.

2. **Siz Telegram'da javob berayotganda, albatta o'sha xabarga "Reply" qiling**
   (uzoq bosib ushlab "Reply"ni tanlang, keyin javobingizni yozing).
   - Agar "Reply" qilmasdan oddiy yangi xabar yuborsangiz, tizim buni kimga
     yo'naltirishni bilmaydi va u hech kimning oynasida chiqmaydi (xavfsizlik uchun ataylab shunday).

3. Sayt sizning javobingizdagi "Reply to" xabaridan `#UID:...`ni o'qib, aynan o'sha
   foydalanuvchining brauzerida ko'rsatadi. Boshqa foydalanuvchilar buni ko'rmaydi.

Fayl yuborilganda ham xuddi shu marker **caption (izoh)** ichida keladi, shuning uchun
fayl xabariga "Reply" qilinganda ham marshrutlash xuddi shunday ishlaydi.

## O'rnatish qadamlari

1. GitHub'da repo yarating, `index.html` faylini root'ga joylang, push qiling.
2. **Settings → Pages** orqali saytni yoqing.
3. **@BotFather** da `/setdomain` orqali botingizga saytingiz domenini bog'lang
   (masalan `username.github.io`) — Login Widget shusiz ishlamaydi.

## Cheklovlar (halol aytib qo'yaman)

- **Token ochiq**: brauzerda ko'rinadi. Faqat shaxsiy/demo foydalanish uchun.
- **Login tekshiruvi brauzerda bajariladi**: texnik jihatdan konsol orqali chetlab
  o'tish nazariy jihatdan mumkin (chunki tekshiruvchi kod ham shu saytda ishlaydi).
  Jiddiy loyihada bu tekshiruv serverda bo'lishi kerak.
- **Tarix muddati**: Telegram tasdiqlanmagan `getUpdates`ni odatda ~24 soat yoki
  limitgacha saqlaydi. Foydalanuvchining o'z yozgan xabarlari brauzer `localStorage`'da
  saqlanadi (shu qurilma/brauzerda), lekin admin javoblari Telegram tomonidan yuqoridagi
  muddat ichida qayta tiklanadi.
- **Fayl yuborish** qo'shilmagan (so'rovga ko'ra).

## Xavfsizroq variant (agar kerak bo'lsa)
Tokenni butunlay yashirish va login tekshiruvini serverga o'tkazish uchun
Cloudflare Worker / Vercel Function orqali proxy backend qurish mumkin — xohlasangiz
shuni ham tayyorlab beraman.
