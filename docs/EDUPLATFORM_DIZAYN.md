# EduPlatform — dizayn yo‘riqnomasi

Ushbu hujjat foydalanuvchi yuborgan EduSmart dashboard namunasi asosida EduPlatform interfeysining vizual yo‘nalishini belgilaydi. Maqsad — namunadagi binafsha ranglar, chap navigatsiya paneli, kurs kartalari va o‘quv progressi g‘oyalarini EduPlatform uchun mos, qulay va responsiv ko‘rinishda qo‘llash. Bu dizayn yo‘nalishidan ilhomlanadi, lekin EduPlatform brendi va mazmuniga moslashtiriladi.

## 1. Umumiy uslub

- Zamonaviy, yorqin va ta’limga mos dashboard.
- Asosiy ranglar: to‘q binafsha, binafsha, lavanda va oq.
- Yordamchi ranglar: progress uchun yashil, ogohlantirish uchun sariq/to‘q sariq, xatolar uchun qizil.
- Oq yoki juda och lavanda fon, yumaloq burchakli kartalar va yengil soyalar.
- Sarlavhalar aniq ierarxiyaga ega, matnlar o‘qilishi qulay bo‘lsin.
- Kichik ekranlarda ham yetarli kontrast, o‘qiladigan shrift o‘lchami va katta bosiladigan tugmalar saqlansin.

## 2. Dashboard joylashuvi

### Chap navigatsiya paneli

Desktop ko‘rinishida sahifaning chap tomonida to‘q binafsha rangli, doimiy sidebar bo‘ladi:

- EduPlatform logotipi va qisqa shiori.
- Bosh sahifa.
- Kurslar.
- Mening kurslarim.
- Bildirishnomalar (son belgisi bilan).
- Profil.
- Sozlamalar.
- Chiqish.

Joriy bo‘lim yorqin binafsha fon yoki chapdagi rangli indikator bilan ajratiladi. Sidebar mobil ko‘rinishda menyu tugmasi orqali ochiladigan panelga aylanadi.

### Yuqori panel

Asosiy kontent ustida quyidagilar joylashadi:

- Kurs, mavzu yoki o‘qituvchi bo‘yicha qidiruv maydoni.
- Mavjud bo‘lsa, och/to‘q rejimni almashtirish tugmasi.
- Bildirishnoma belgisi.
- Profil rasmi, foydalanuvchi ismi va profil menyusi.

Mobil ekranda qidiruv maydoni ixchamlanadi yoki alohida qatorga tushadi; profil va bildirishnoma elementlari ko‘rinib qoladi.

### Bosh sahifa kontenti

1. **Salomlashuv va banner:** foydalanuvchiga xush kelibsiz matni, qisqa rag‘batlantiruvchi izoh va kurslar sahifasiga o‘tish tugmasi. Binafsha gradient yoki ta’lim mavzusidagi rasm ishlatilishi mumkin.
2. **Statistika kartalari:** o‘quvchining kurslari soni, tugallangan darslari, umumiy progressi va yutuqlari.
3. **Mening kurslarim:** rasmli kurs kartalari, kategoriya, kurs nomi, darslar soni, davomiylik, bajarilish foizi va “Davom ettirish” tugmasi.
4. **Mashhur kurslar:** katalogdagi tavsiya etilgan kurslar.
5. **Yaqin darslar yoki reja:** desktopda o‘ng yon ustunda kalendar va yaqin darslar; kichik ekranda asosiy kontent ostida.
6. **Yutuq/progress kartasi:** o‘quvchining natijasi yoki rag‘batlantiruvchi xabar.

## 3. Kurs kartasi tarkibi

Har bir kurs kartasida imkon qadar quyidagilar bo‘ladi:

- Kurs muqovasi yoki kategoriya rasmini.
- Kategoriya yorlig‘i.
- Kurs nomi.
- Darslar soni va taxminiy davomiyligi.
- O‘quv progressini ko‘rsatuvchi progress bar va foiz.
- “Davom ettirish” yoki “Kursni ko‘rish” amaliy tugmasi.

Tasvirlar belgilangan nisbatda kesiladi (`object-fit: cover`). Rasm topilmasa, mavzuga mos rangli fallback ko‘rsatiladi.

## 4. Responsive xulq

- **Keng desktop:** chap sidebar, markaziy kontent va o‘ngdagi qo‘shimcha panel yonma-yon joylashadi.
- **Planshet:** o‘ng panel asosiy kontent ostiga o‘tadi; kurs kartalari ikki ustunga moslashadi.
- **Telefon:** sidebar drawer/ochiladigan menyu bo‘ladi; kontent bir ustunda chiqadi; statistika kartalari ikki yoki bitta ustunga moslashadi; kurs kartalari bitta ustunda ko‘rsatiladi.
- Gorizontal scroll paydo bo‘lishiga yo‘l qo‘yilmaydi.
- Tugmalar va menyu elementlari touch orqali qulay bosiladigan o‘lchamda bo‘ladi.
- Kalendar kichik ekranda ixcham shaklga o‘tishi yoki yaqin darslar ro‘yxati bilan almashtirilishi mumkin.

## 5. Django MVT va frontend fayllari

Dizayn Django Templates orqali serverda render qilinadi. Frontend freymvork ishlatilmaydi.

Tavsiya etiladigan fayllar:

```text
 templates/
 ├── base.html
 ├── includes/
 │   ├── sidebar.html
 │   ├── topbar.html
 │   └── course_card.html
 └── dashboard/
     └── home.html

 static/
 ├── css/
 │   ├── base.css
 │   ├── dashboard.css
 │   └── responsive.css
 ├── js/
 │   └── dashboard.js
 └── images/
     ├── logo.svg
     └── course-covers/
```

- `base.html`: umumiy sahifa karkasi, navigatsiya va static fayllarni ulash.
- `dashboard/home.html`: dashboard ma’lumotlari va kartalar.
- CSS: ranglar, tipografiya, grid/flex joylashuv, holatlar va media query’lar.
- JavaScript: mobil menyu, kerakli dropdown va oddiy UI interaksiyalari.
- Django View dashboard uchun kurslar, statistikalar va bildirishnomalarni template kontekstiga uzatadi.
- Ruxsatlar va muhim biznes qoidalari faqat Django backend’da tekshiriladi.

## 6. Amalga oshirish tartibi

1. Dashboard sahifasining wireframe’ini desktop va telefon uchun tayyorlash.
2. Rang palitrasi, shriftlar, spacing va umumiy komponentlarni belgilash.
3. `base.html`, sidebar va topbar’ni yaratish.
4. Statistik kartalar, kurs kartalari va progress komponentlarini HTML/CSS’da qurish.
5. Django View’dan haqiqiy foydalanuvchi/kurs ma’lumotlarini template’ga uzatish.
6. Mobil menyu va zarur interaktiv elementlarni oddiy JavaScript’da bajarish.
7. 320px, telefon, planshet va desktop kengliklarida tekshirish.
8. Klaviatura bilan foydalanish, kontrast, label’lar va rasm `alt` matnlarini tekshirish.

## 7. Qabul mezonlari

- Dashboard yuborilgan namunadagi binafsha ta’lim platformasi kayfiyatini beradi.
- Sidebar, qidiruv, foydalanuvchi profili, statistika, kurs kartalari va progress ko‘rinadi.
- Barcha asosiy ma’lumotlar Django template’lari orqali backend’dan keladi.
- Frontend faqat HTML, CSS va oddiy JavaScript’dan iborat.
- Interfeys telefon, planshet va desktop’da qulay ishlaydi, gorizontal scroll chiqarmaydi.
- Matn va tugmalar o‘qilishi hamda bosilishi qulay, klaviatura fokus holatlari aniq.
