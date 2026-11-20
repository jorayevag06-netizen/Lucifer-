# EduPlatform — Django MVT loyiha rejasi

## 1. Loyiha maqsadi

EduPlatform — o‘quvchilar onlayn kurslarni ko‘rishi, darslarni o‘rganishi, test topshirishi va o‘z natijalarini kuzatishi mumkin bo‘lgan ta’lim veb-tizimi. O‘qituvchi va administrator kurslar, darslar hamda o‘quvchilarni boshqaradi.

Loyiha Django’ning **MVT (Model–View–Template)** arxitekturasida quriladi. Frontend faqat **HTML, CSS va JavaScript** fayllaridan tashkil topadi. React, Vue yoki boshqa frontend freymvorklar ishlatilmaydi; HTML sahifalar Django Templates orqali serverda render qilinadi.

## 2. Texnologiyalar

- **Backend:** Python, Django
- **Arxitektura:** MVT
- **Frontend:** HTML5, CSS3, oddiy JavaScript
- **Ma’lumotlar bazasi:** dastlab SQLite (mahalliy ishlab chiqish), ishlab chiqarish muhitida PostgreSQL
- **Versiyalar nazorati:** Git va GitHub
- **Statik fayllar:** Django static files (`CSS`, `JS`, rasmlar)

## 3. Foydalanuvchi rollari

1. **Mehmon:** bosh sahifa va ochiq kurslar ro‘yxatini ko‘radi, ro‘yxatdan o‘tadi.
2. **O‘quvchi:** kursga yoziladi, darslarni o‘qiydi/ko‘radi, test topshiradi va natijalarni kuzatadi.
3. **O‘qituvchi:** o‘z kurslari, darslari va testlarini yaratadi hamda boshqaradi.
4. **Administrator:** foydalanuvchilar, kurslar va platformaning boshqa ma’lumotlarini boshqaradi. Django Admin’dan foydalanadi.

## 4. Asosiy funksiyalar

- Bosh sahifa va kurslar katalogi
- Kurslarni qidirish va kategoriya bo‘yicha filtrlash
- Kurs tafsilotlari: tavsif, o‘qituvchi, darslar va davomiylik
- Ro‘yxatdan o‘tish, tizimga kirish va chiqish
- O‘quvchi profili va shaxsiy kabineti
- Kursga yozilish va o‘quv jarayonini kuzatish
- Dars sahifalari (matn, havola yoki video joylashuv)
- Testlar va urinish natijalari
- O‘qituvchi uchun kurs/dars boshqaruvi
- Django Admin orqali platformani boshqarish

> To‘lov, sertifikat, xabar berish va ko‘p tillilik kabi qo‘shimcha imkoniyatlar birinchi versiya ishga tushgandan keyin alohida bosqichda qo‘shiladi.

## 5. MVT arxitekturasi

- **Model:** ma’lumotlar tuzilmasi va ular orasidagi bog‘lanishlar (`models.py`).
- **View:** so‘rovlarni qabul qilish, ruxsatlarni tekshirish, ma’lumotlarni olish va javob qaytarish (`views.py`).
- **Template:** foydalanuvchiga ko‘rsatiladigan HTML sahifalar (`templates/`).
- **URLconf:** URL manzillarni tegishli view’lar bilan bog‘lash (`urls.py`).
- **Static:** CSS, JavaScript va rasmlar (`static/`).

Ishlash oqimi: **Brauzer → URL → View → Model/ma’lumotlar bazasi → View → Template → HTML javobi**.

## 6. Tavsiya etiladigan loyiha tuzilmasi

```text
eduplatform/
├── manage.py
├── config/                  # Django loyiha sozlamalari va asosiy URL’lar
├── accounts/                # Ro‘yxatdan o‘tish, login va profil
├── courses/                 # Kurslar, kategoriyalar va yozilishlar
├── lessons/                 # Darslar va o‘tilgan darslar
├── assessments/             # Testlar, savollar va natijalar
├── templates/               # Umumiy HTML shablonlar
│   ├── base.html
│   ├── includes/
│   ├── accounts/
│   ├── courses/
│   ├── lessons/
│   └── assessments/
├── static/
│   ├── css/
│   ├── js/
│   └── images/
├── media/                   # Yuklangan rasmlar (ishlab chiqish muhiti)
├── requirements.txt
└── README.md
```

Ilovalar va papkalar loyiha rivojlanishiga qarab moslashtirilishi mumkin. Har bir Django ilovasida o‘z `models.py`, `views.py`, `urls.py`, `admin.py` va kerak bo‘lsa `forms.py` fayllari bo‘ladi.

## 7. Ma’lumotlar modeli — boshlang‘ich taklif

- **User:** Django’ning maxsus yoki standart foydalanuvchi modeli; rol va profil ma’lumotlari.
- **Category:** kurs kategoriyasi (nomi, slug, tavsifi).
- **Course:** nomi, slug, tavsifi, kategoriya, o‘qituvchi, rasm, holati va yaratilgan sana.
- **Enrollment:** o‘quvchi va kurs orasidagi yozilish; holati va yozilgan sana.
- **Lesson:** kurs, sarlavha, matn/video manzili, tartib raqami va ochiqlik holati.
- **LessonProgress:** o‘quvchi, dars va bajarilgan holat.
- **Quiz:** kurs yoki darsga tegishli test, sarlavha va sozlamalar.
- **Question:** test savoli va javob variantlari.
- **Choice:** savolga tegishli javob varianti va to‘g‘ri javob belgisi.
- **QuizAttempt:** o‘quvchining test topshirishi, bali va topshirilgan vaqti.

Model yozishdan oldin rol, kursga yozilish qoidalari va test baholash tartibi aniqlashtiriladi. Migratsiyalar har bir model o‘zgarishidan keyin yaratiladi va tekshiriladi.

## 8. Ishni bajarish ketma-ketligi

### 1-bosqich: Talablarni aniqlash

- Birinchi versiyaga kiradigan funksiyalarni belgilash.
- Rollar va ularning ruxsatlarini yozib chiqish.
- Sahifalar xaritasini tuzish: bosh sahifa, katalog, kurs tafsiloti, login/ro‘yxatdan o‘tish, kabinet, dars va test.
- Kursga yozilish hamda testni baholash qoidalarini belgilash.

**Natija:** tasdiqlangan MVP (birinchi ishlaydigan versiya) talablari.

### 2-bosqich: Muhitni tayyorlash

- Python virtual muhitini yaratish va faollashtirish.
- Django va kerakli paketlarni o‘rnatish.
- Django loyihasi va ilovalarni yaratish.
- `settings.py` ichida ilovalar, template, static va media sozlamalarini kiritish.
- Git repository va `.gitignore` faylini tayyorlash.

**Natija:** ishga tushadigan bo‘sh Django loyihasi.

### 3-bosqich: Ma’lumotlar bazasi va modellar

- Foydalanuvchi profili/rollari va asosiy ta’lim modellarini loyihalash.
- Model bog‘lanishlari, majburiy maydonlar va cheklovlarni belgilash.
- Migratsiyalarni yaratish va qo‘llash.
- Django Admin’da modellarni ro‘yxatdan o‘tkazish.
- Sinov ma’lumotlarini kiritish.

**Natija:** ma’lumotlarni saqlash va admin orqali boshqarish mumkin.

### 4-bosqich: URL va View qatlamlari

- Har bir ilovada URL manzillarini tashkil qilish.
- Kurslar ro‘yxati, qidiruv, filtr va tafsilot view’larini yozish.
- Login, logout, ro‘yxatdan o‘tish va profil view’larini yaratish.
- Kursga yozilish, dars holatini belgilash va test topshirish view’larini qo‘shish.
- Login talab qilinadigan view’lar болон rolга хос рухсатлар билан ҳимоя қилиш.

**Natija:** sahifalarning server tomondagi ish jarayoni tayyor.

### 5-bosqich: HTML Template’lar

- Umumiy `base.html` layoutini yaratish.
- Navigatsiya, footer va qayta ishlatiladigan qismlarni `includes/` ichiga ajratish.
- Har bir sahifa uchun alohida Django template yozish.
- Django template merosi (`extends`, `block`) va kontekst ma’lumotlaridan foydalanish.
- Form xatolari, bo‘sh natijalar va muvaffaqiyat xabarlarini ko‘rsatish.

**Natija:** backend ma’lumotlari HTML ko‘rinishida chiqadi.

### 6-bosqich: CSS va JavaScript

- Mobil qurilmalarga mos, moslashuvchan dizayn yaratish.
- Ranglar, shriftlar, tugmalar, formalar va kartalar uchun yagona uslub belgilash.
- Oddiy JavaScript bilan menyu, tasdiqlash oynalari va zarur interaktiv elementlarni qo‘shish.
- CSS va JS fayllarini Django static tizimi orqali ulash.
- JavaScript’ni asosiy biznes qoidalari yoki ruxsatlarni tekshirish uchun ishlatmaslik; bular serverda tekshiriladi.

**Natija:** HTML/CSS/JS asosidagi ishlatishga qulay interfeys.

### 7-bosqich: Testlash va xavfsizlik

- Model, view, forma va asosiy foydalanuvchi oqimlari uchun Django testlarini yozish.
- Mehmon, o‘quvchi, o‘qituvchi va admin ruxsatlarini alohida tekshirish.
- CSRF himoyasi, forma validatsiyasi va login himoyasini tekshirish.
- Maxfiy sozlamalarni muhit o‘zgaruvchilarida saqlash; `DEBUG=False` va `ALLOWED_HOSTS` ni deployment uchun sozlash.
- Xatoli URL, bo‘sh katalog va ruxsatsiz kirish holatlarini tekshirish.

**Natija:** muhim funksiyalar va ruxsatlar sinovdan o‘tgan.

### 8-bosqich: Hужжатлаштириш ва жойлаштиришга тайёрлаш

- `README.md`’ga o‘rnatish, миграция, superuser yaratish ва ишга тушириш қадамларини ёзиш.
- `requirements.txt` ни янгилаш.
- PostgreSQL ва ишлаб чиқариш static/media сақлаш стратегиясини танлаш.
- Hosting муҳитида environment variables, HTTPS ва production sozlamalarini qo‘llash.
- Deploy’dan so‘ng asosiy sahifalar va foydalanuvchi oqimlarini tekshirish.

**Natija:** loyiha mahalliy muhitda va tanlangan serverda ishga tushirishga tayyor.

## 9. MVP qabul mezonlari

- Mehmon kurslarni ko‘ra oladi va qidiradi.
- Foydalanuvchi ro‘yxatdan o‘tib tizimga kira oladi.
- O‘quvchi kursga yozilib, kurs darslarini ko‘ra oladi.
- O‘quvchi dars bajarilganini belgilab, test topshira oladi.
- Test natijasi saqlanadi va o‘quvchiga ko‘rsatiladi.
- O‘qituvchi/admin kurs va darslarni boshqara oladi.
- Interfeys mobil va desktop ekranlarda ishlaydi.
- Ruxsatsiz foydalanuvchi himoyalangan sahifalarga kira olmaydi.

## 10. Ishga tushirish bo‘yicha dastlabki buyruqlar

Quyidagi buyruqlar loyiha katalogida bajariladi:

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

pip install django
 django-admin startproject config .
python manage.py startapp accounts
python manage.py startapp courses
python manage.py startapp lessons
python manage.py startapp assessments
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

> `django-admin` oldidagi ortiqcha bo‘sh joyni olib tashlab, buyruqni `django-admin startproject config .` shaklida bajaring.

## 11. Keyingi rivojlantirish

MVP ishlagandan so‘ng to‘lov integratsiyasi, sertifikatlar, email xabarnomalari, kurs sharhlari, ko‘p tillilik, hisobotlar va video kontentni himoyalash kabi imkoniyatlarni alohida talablar asosida rejalashtirish mumkin.
