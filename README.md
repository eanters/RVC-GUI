<div align="center">

<h1>RVC GUI<br><br>
  
For audio file inference only

  <br>

  

</div>

  

 

  
## GUI

![GUI](https://github.com/Tiger14n/RVC-GUI/raw/main/docs/GUI.JPG)
 <br><br>
  
## Direct setup for Windows users
## [Windows-pkg](https://github.com/Tiger14n/RVC-GUI/releases/tag/Windows-pkg)
  
<br><br>
## Preparing the environment


* Install Python version +3.8 if you have not:

* Execute these commands

Windows with Nvidia cards
```bash
python -m pip install -U pip setuptools wheel
pip install -U torch torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install -r requirements.txt
```
Other
```
python -m pip install -U pip setuptools wheel
pip install -U torch torchaudio 
pip install -r requirements.txt
```

Apple silicon Macs fix
```
pip install --pre torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/nightly/cpu

export PYTORCH_ENABLE_MPS_FALLBACK=1
```
<br>

* Downlaod [hubert_base.pt](https://huggingface.co/lj1995/VoiceConversionWebUI/resolve/main/hubert_base.pt/) and place it in the root folder

<br>
 
* Then use this command to start RVC GUI:
```bash
python rvcgui.py
```
Or run this file on windows
```
RVC-GUI.bat
```

# Loading models
use the import button to import a model from a zip file, 
* The .zip must contain the ".pth" weight file. 
* The .zip is recommended to contain the feature retrieval files ".index"

Or place the model manually in root/models
```
models
├───Person1
│   ├───xxxx.pth
│   ├───xxxx.index
│   └───xxxx.npy
└───Person2
    ├───xxxx.pth
    ├───...
    └───...
````
<br>


<br> 

### How to get models?.
* Join the[ AI Hub](https://discord.gg/aihub) Discord 
* [Community Models on HuggingFace](https://huggingface.co/QuickWick/Music-AI-Voices/tree/main) by Wicked aka QuickWick

<br>

K7#4523

Selam. Konuyu uzatmadan başlayacağım öncelikle bize lazım olan şeyler.
Dipnot: Sitenin güvenilirliği hakkımda bilgim yoktur fakat yapacak olanların yeni hesap açıp öyle yapmalarını öneririm.

Colab linki: Google Colaboratory

Gerekenler:

5-10 dakika arasında temiz ses örneği (isterseniz daha fazla yapabilirsiniz). WAV olarak kaydetmeyi unutmayın (içinde Ö, J, I, ç gibi harfleri bulunduran cümleleri kurmanız daha iyi olacaktır)

Bir şarkının vokalini birçok siteden veya program ile ayırabilirsiniz.

Adım 1
Attığım linkteki colabı açın ve ilk hücreyi başlatın indirmeler bittikten sonra public URL: "burada bir link olur" o linke tıklayarak giriş yapıyoruz.

publicurl.png

Adım 2: GUI kısmına giriş
Linke tıkladıktan sonra karşımıza şöyle bir ekran geliyor ve kırmızı kutucukla işaretlediğim "train" kısmına geçiyoruz.

gui2.png

Colab ekranına geri dönüp -evc- klasörünün içine "dataset" isminde bir klasör açıp içine ses kaydımızı atıyoruz kaydı attıktan sonra train kısmına dönüyoruz.

Adım 3: Modeli trainlemek
Train kısmında ilk olarak "process the dataset" butonuna basıyoruz ve işlem bittiğinde onun altındaki kutucukta endpreprocess yazıcaktır ( işlem bittiğinde 3. satırda endpreprocess yazmalıdır eğer daha uzunsa hata gelmiştir)

gui3.png

Yeşil yer endpreprocess in yazacağı yerdir.
Endpreprocessden sonra 2. buton yani "pitch Extraction'a basıcağız onun altındaki boşlukta all-feature-done yazısını gördüğümüzde 2. işlemde bitmiş demektir.
Geldik trainlemenin son kısımlarına 3. buton "train model"butonuna basmadan önce onun üstündeki epoch kısmını 200'e çekiyoruz (200 genelde en iyi sonucu verir fazla yaparsanız bozulabilir)
Train modele bastığınızda Colab'e geri dönün ve epoch işlemlerinin başladığını göreceksiniz belirlediğiniz epoch'a göre uzun sürer bittiğinde colabde şöyle bir yazı yazar.

gui4.png

Bu da tamamlandığına göre 4. buton yani "train ındex" butonuna basabiliriz bu çok kısa sürecektir bittiğinde şunun gibi bir yazı çıkar.

gui5.png

İsteğe bağlı kısım: eğer siz modelinizi kaydetmek istiyorsanız 5. butona yani "download model" butonuna tıkladıktan sonra.

istek.png

Buna benzer 2 dosya çıkar bu iki dosyayı sağdan "download" tuşuna basıp indiriyoruz ve yeniden kullanmak istiyorsak bu iki dosyayı ZIP haline getirip Google Drive'a yüklüyoruz ve linki kopyalıyoruz.
Ardından GUI ekranından "download model" sekmesine geliyoruz.

istek2.png

En baştaki yere ZIP dosyasının Drive linki 2. kısma koymak istediğiniz isim sonra download tuşuna basıyoruz ve modellerimize gelmiş olacak.

Final
Colab'e dönüp -evc- klasörünün içindeki "audios" klasörünün içine istediğiniz şarkının vokalini atıyoruz ve GUI ekranına geri dönüyoruz.
GUI'daki "ınference" sekmesine gelip "choose your model" yazısının sağındaki "Refresh" butonuna tıklıyoruz yenileme bittikten sonra "choose your modeli" yazısının biraz sağındaki çentiğe tıklayıp oradan sizin ismini belirlediğiniz modelin "modelinismi. Pth" olan halini seçiyorsunuz.

pth.png

Ardından "choose your Audio" yazısının sağındaki Refresh butonuna tıklıyoruz ardından görseldeki çentiğe tıklayıp.

1689194075621.png

Audios klasörüne attığımız şarkının vokalini seçiyoruz.
Son olarak sağ üstten converte tıklamadan önce bir bilgi vereyim eğer kadın senini erkeğe çevirecekseniz convertin solunda kalan 0'ı -12 yapın eğer erkek sesini kadına çevirecekseniz 12 yapın veya erkek sesini erkeğe kadın sesini kadın sesine çevirecekseniz 0 yapın.
Dediğim gibi sağ üstteki "convert" butonuna tıklıyoruz ve bekliyoruz.

1689194225407.png

İşlem bittiğinde Convert'in altında sesimizin oluştuğunu göreceğiz onu sağ üç noktaya tıklayıp indirebilirsiniz.

?hash=85859bce05190f26031c10c73cd6d7de.png

Evet bitti sorunlarınızı yazabilirsiniz çok kötü anlatmış olabilirim kusura bakmayın.

