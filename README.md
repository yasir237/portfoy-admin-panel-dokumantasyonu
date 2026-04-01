# Portfolio Projesi — Kurulum ve Kullanım Dokümantasyonu

## Proje Hakkında

Bu proje, kullanıcının portfolyosunu modern ve profesyonel bir şekilde sergilemesini sağlayan bir web sitesidir.

| Katman | Teknoloji |
|--------|-----------|
| Frontend | Next.js |
| Backend | Next.js API Routes (ayrı sunucu yok) |
| Veri | JSON dosyaları + GitHub API |
| Tasarım | Minimal, responsive, akıcı animasyonlu UI |

---

## Kurulum

### 1. İletişim Mesajları

İletişim mesajları alabilmek için [Resend](https://resend.com/) platformu kullanıldı.

1. [Resend](https://resend.com/) platformunda kayıt olun.
2. **API Keys** sekmesine gidin.

   ![API Keys sekmesi](image.png)

3. Yeni bir API anahtarı oluşturun.

   ![Yeni API anahtarı oluşturma](image-1.png)

4. İstediğiniz ismi girerek **Add** butonuna tıklayın.

   ![Yeni API anahtarı formu](image-2.png)

5. Oluşturulan API anahtarını kopyalayın — ilerleyen adımlarda `.env.local` dosyasına eklenecek.

   ![Anahtarı almak](image-3.png)

---

### 2. Projeyi GitHub'a Yüklemek

1. [GitHub](https://github.com) platformunda kayıt olun.
2. Yeni bir depo oluşturun.

   ![GitHub sayfası](image-4.png)

3. Depo ismini girin, görünürlüğü **Public** olarak ayarlayın ve **Create repository** butonuna tıklayın.

   ![Yeni repo oluşturma](image-5.png)

4. Dosya yükleme seçeneğini tıklayın.

   ![Proje yükleme](image-9.png)

   ![Proje yükleme ekranı](image-10.png)

5. İndirdiğiniz proje dosyasını ayıklayın.

   ![Ayıklama](image-6.png)
   ![Ayıklama](image-7.png)

6. Ayıklanan klasörün içine girin ve tüm dosyaları görüntüleyin.

   ![Proje dosyaları](image-8.png)

7. GitHub yükleme ekranına dönün ve proje dosyalarını sürükleyip yükleyin.

[🎥 Videoyu indir / izle](./proje-yukle.mp4)

8. **Commit changes** butonuna tıklayın.

   ![Commit butonu](image-11.png)

9. Tüm dosyaların yüklendiği son ekran görünümü:

   ![GitHub ekranı](image-12.png)

---

### 3. GitHub Token Almak

1. GitHub ayarlarına gidin.

   ![GitHub seçenekleri](image-13.png)

2. Sol menüden **Developer Settings** seçeneğine tıklayın.

   ![GitHub seçenekleri](image-14.png)

3. **Personal access tokens → Tokens (classic)** seçeneğini seçin.

   ![Seçenekler](image-15.png)

4. **Generate new token** butonuna tıklayın.

   ![Generate new token](image-18.png)

5. Açılan menüden **Generate new token (classic)** seçeneğini seçin.

   ![Classic token seçimi](image-17.png)

6. **Note** kısmına istediğiniz bir isim girin, yalnızca **repo** iznini seçin.

   ![Token ayarları](image-16.png)

7. Son kullanım tarihi olarak **No expiration** seçeneğini seçin.

   ![Son kullanım tarihi](image-20.png)

8. Sayfanın en altındaki **Generate token** butonuna tıklayın.

   ![Generate token butonu](image-19.png)

9. Oluşturulan tokeni kopyalayın ve kimseyle paylaşmayın.

   ![Token](image-21.png)

---

### 4. Resend ve GitHub API Bağlantısı

1. Proje klasöründe `.env.local` adında yeni bir dosya oluşturun.

   ![.env.local dosyası oluşturma](image-23.png)
   ![.env.local dosyası oluşturma](image-22.png)

2. Dosyayı bir metin editörüyle açın ve aşağıdaki değerleri doldurun.  
   > ⚠️ Köşeli parantezleri `[ ]` **dahil etmeden** kendi bilgilerinizi yazın.

```env
ADMIN_USERNAME=[panele giriş için kullanılacak kullanıcı adı]
ADMIN_PASSWORD=[panele giriş için kullanılacak şifre]
ADMIN_SECRET=[panelin güvenliği için kullanılacak 32 haneli anahtar]

RESEND_API_KEY=[Resend platformundan alınan API anahtarı]
CONTACT_EMAIL=[iletişim mesajlarını almak istediğiniz e-posta adresi]

GITHUB_TOKEN=[GitHub'dan alınan kişisel erişim tokeni]
GITHUB_OWNER=[GitHub hesabınızın kullanıcı adı]
GITHUB_REPO=[projeyi yüklediğiniz deponun adı]
GITHUB_BRANCH=[kullandığınız branch, genellikle: main]
```

**Örnek:**

```env
ADMIN_USERNAME=admin
ADMIN_PASSWORD=sifre123
ADMIN_SECRET=kgmshy478b7aslp00hnmx65f44dso91h

RESEND_API_KEY=re_xxxxxxxxxxxx
CONTACT_EMAIL=ornek@mail.com

GITHUB_TOKEN=ghp_xxxxxxxxxxxx
GITHUB_OWNER=kullanici-adi
GITHUB_REPO=portfolio
GITHUB_BRANCH=main
```

Aşağıdaki görseller gerekli bilgilerin nereden alınacağını göstermektedir:

| Bilgi | Görsel |
|-------|--------|
| GitHub Token | ![](image-21.png) |
| Kullanıcı adı | ![](image-24.png) |
| Repo adı | ![](image-25.png) |
| Branch | ![](image-26.png) |

---

## Projeyi Lokal Olarak Çalıştırma

Gerekli paketleri yükleyin:

```bash
npm install
```

Geliştirme sunucusunu başlatın:

```bash
npm run dev
```

Tarayıcıda açın:

```
http://localhost:3000/
```

> **Not:** Henüz dil eklenmediği için `404` hatası görebilirsiniz. Devam etmek için aşağıdaki adımları izleyin.

---

## İlk Dil Kurulumu

1. Admin paneline gidin:
   ```
   http://localhost:3000/admin
   ```

2. Sol menüden **Dil Yönetimi** seçeneğini seçin.

3. Dil eklemek için iki yöntemden birini kullanabilirsiniz:
   - **Manuel:** Boş bir dil oluşturup kendiniz doldurun.
   - **Hazır paket:** [portfolio-languages](https://github.com/yasir237/portfolio-languages) sayfasından ilgili dil dosyasını indirip projenize yükleyin.
