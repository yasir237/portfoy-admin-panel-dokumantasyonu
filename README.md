# Portfolio Projesi Kurulum ve Kullanım Dokümantasyonu

## Proje Hakkında

Bu proje, kullanıcının portfolyosunu modern ve profesyonel bir şekilde sergilemesini sağlayan bir web sitesidir.

- Frontend: Next.js
- Backend: Next.js API Routes (ayrı sunucu yok)
- Veri: JSON dosyaları + GitHub API
- Tasarım: Minimal, responsive, akıcı animasyonlu UI

## Kurulum

### İletişim Mesajları

İletişim mesajları alabilmek için [Resend](https://resend.com/) platformunu kullandım kullanıldı.

- [Resend](https://resend.com/) platformunda kayıt olun.
- API Keys sekmesine gidin
  
  ![api keys sekmesi](image.png)
- Yeni bir api anahtarı oluştur
  
  ![yeni api anahtar oluşturma](image-1.png)
- İstediğiniz ismi girerek `Add` buttonuna tıklayarak yeni api anahtarınızı oluşturun
  
  ![Yeni api anahtar formu](image-2.png)
- Verilen api anahtarını kopyalayarak biraz sonra oluşturacağımız `.env.local` dosyasına yazılacak.
  ![anahtarı almak](image-3.png)

### Projeyi Github'a Yüklemek

- İlk adım [Github](https://github.com) platfomunda kayıt olun.
- Yeni bir depo oluşturun:
  ![github sayfası](image-4.png)
- depo ismini istediğinizi girin, görünürlüğü public yapın, yeni repoistory oluşturun
  ![yeni repo oluşturma](image-5.png)
- Projeyi yüklemek için bu seçeneğe tıklayın
  ![proje yükleme](image-9.png)
- Önününze bu ekran gelmiş olmalı
  ![proje yükleme ekranı](image-10.png)
- İndirdiğiniz proje dosyasını ayıklayın
  ![ayıklama](image-6.png)
  ![ayıklama](image-7.png)
- Yeni çıkarılan klasörün içine girin ve tüm dosyaları görüntüleyin
  ![proje dosyaları](image-8.png)
- Biraz önceki github ekranına dönün ve proje dosyları yükleyin
    <video width="600" controls>
        <source src="proje-yukle.mp4" type="video/mp4">
    </video>
- Commit buttonunu tıklayın
    ![commit buttonu](image-11.png)
- Son ekran görünüşü bu şekilde olmalı, tüm dosyalar yüklü hali
    ![github ekranı](image-12.png)

### Github Tokeni Almak
- Github ayarlarına gidin
    ![github seçenekleri](image-13.png)
- Sol menüsündeki seçeneklerin arasında `Developer Settings` tıklayın
    ![github seçenekleri](image-14.png)
- Yeni çıkan seçeneklerin arasından `Personel access tokens` seçeneğin altındaki `Tokens (classic)` seçeneğini seçin
    ![seçenekler](image-15.png)
- Yeni token oluşturmak için `Generate new token` buttonuna tıklayın
    ![alt text](image-18.png)
- Çıkan seçeneklerin arasından `Generate new token (classic)` seçeneğini seçin
    ![alt text](image-17.png)

- Note kısmına istediğinizi yazın ve aşağıdaki sadece repo seçeneğini seçin
    ![alt text](image-16.png)
    
- Son kullanım tarihi olarak son seçeneği olan `No expiration` seçeneğini seçin
    ![alt text](image-20.png)
- En aşağıdaki olan `Generate new token` buttonuna tıklayın
    ![button](image-19.png)
- Size verilen tokeni kopyalayın ve kimseyle paylaşmayın
    ![alt text](image-21.png)

### Resend ve Github API Bağlamak
- Projenizde yeni bir dosya oluşturun ve adını `.env.local`olarak adılandırın
    ![alt text](image-23.png)
    ![alt text](image-22.png)
- Oluşturulan `.env.local` dosyasını not defteri kullanarak açın.
- Paneli bağlamak için bunları doldurun parantezlerin arasında yazmayın
    ```txt
    ADMIN_USERNAME=[panele giriş yapmak için kullanılacak kullanıcı adı]
    ADMIN_PASSWORD=[panele giriş yapmak için kullanılacak şifre]
    ADMIN_SECRET=[panelin güvenliği için kullanılacak 32 haneli anahatar]
    ```

    örneğin:
    ```txt
    ADMIN_USERNAME=admin
    ADMIN_PASSWORD=sifre123
    ADMIN_SECRET=kgmshy478b7aslp00hnmx65f44dso91h
    ```

- Resend platformundan aldığımız anahtarı ve kayıt olduğumuz e-postayı aşağıdaki gibi de yazın
```txt
RESEND_API_KEY=[İletişim mesajları almak için aldığın anahtarı]
CONTACT_EMAIL=[İletişim mesajları almak istediğin e-postaya]
```
- Son olarak Github'a bağlamak için bu bilgilere ihtiyacımız var:
    - Biraz önce aldığımız token
        ![github token](image-21.png)
    - Github hesabınızın kullanıcı adı
        ![github kullanıcı adı](image-24.png)
    - Projeyi yüklediğimiz repo adı
        ![repo adı](image-25.png)
    - branch oda genelde `main` olur
        ![branch](image-26.png)
- bu bilgileri aşağıdaki gibi `.env.local` dosyasına yazılacak
```txt
ADMIN_USERNAME=[panele giriş yapmak için kullanılacak kullanıcı adı]
ADMIN_PASSWORD=[panele giriş yapmak için kullanılacak şifre]
ADMIN_SECRET=[panele giriş yapmak için kullanılacak gizli anahatar]


RESEND_API_KEY=[İletişim mesajları almak için aldığın anahtarı]
CONTACT_EMAIL=[İletişim mesajları almak istediğin e-postaya]

GITHUB_TOKEN=[aldığınız github tokeni]
GITHUB_OWNER=[github hesabın sahibinin kullanıcı adı]
GITHUB_REPO=[depolama yapacağın github repo]
GITHUB_BRANCH=[hangi branch üzerinde yapacaksın, genelde main yazılır]
```


## Projeyi Lokal Çalıştırma

- Gerekli paketleri indirmek için bu komut terminalde çalıştırılacaktır

```bash
npm install
```


- Projeyi çalıştırmak için
```bash
npm run dev
```

- Projeyi tarayıcıda açmak için bu url kullan
```bash
http://localhost:3000/
```

- Dil olmadığında dolayı `404` hatasını göreceksiniz
- Yeni dil eklemek için `admin paneli`'ine girmeniz gerek
- Admin paneline girmek için url'dan sonra `/admin` eklemeniz gerek, yani:
    ```bash
        http://localhost:3000/admin
    ```
- Admin panelindeki yan seçeneklerden `Dil Yönetimi` seçeneğini seçin
- Sekmeden boş bir dil ekleyerek siz doldurabilirsiniz veya hazırladığım [diller](https://github.com/yasir237/portfolio-languages) sayfasından dil dosyasını indirerek projenize yükleyebilirsiniz.

