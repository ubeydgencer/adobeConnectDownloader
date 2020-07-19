# adobeConnectDownloader

Indirmek istenilen URL'nin ardina ```/output/filename.zip?download=zip``` ekledikten sonra zip olarak indirilebilir.
```
Directory of C:\Users\[...]\p6vwxp2d0c2f

02/09/2019  11:27 AM    <DIR>          .
02/09/2019  11:27 AM    <DIR>          ..
02/09/2019  11:00 AM        52,239,473 cameraVoip_1_11.flv
02/09/2019  11:00 AM         1,364,573 cameraVoip_1_11.xml
02/09/2019  11:00 AM         7,176,904 cameraVoip_1_15.flv
02/09/2019  11:00 AM           188,012 cameraVoip_1_15.xml
02/09/2019  11:00 AM             6,004 cameraVoip_1_3.flv
02/09/2019  11:00 AM             1,698 cameraVoip_1_3.xml
02/09/2019  11:00 AM        62,603,505 cameraVoip_1_7.flv
02/09/2019  11:00 AM         1,625,383 cameraVoip_1_7.xml
02/09/2019  11:00 AM             2,249 ftcontent1.flv
02/09/2019  11:00 AM             8,219 ftcontent1.xml
02/09/2019  11:00 AM            25,685 ftcontent13.flv
02/09/2019  11:00 AM            85,464 ftcontent13.xml
02/09/2019  11:00 AM           199,781 ftcontent5.flv
02/09/2019  11:00 AM           657,091 ftcontent5.xml
02/09/2019  11:00 AM           182,297 ftcontent9.flv
02/09/2019  11:00 AM           601,758 ftcontent9.xml
02/09/2019  11:00 AM             1,354 fttitle0.flv
02/09/2019  11:00 AM             3,272 fttitle0.xml
02/09/2019  11:00 AM             1,354 fttitle12.flv
02/09/2019  11:00 AM             3,298 fttitle12.xml
02/09/2019  11:00 AM             1,354 fttitle4.flv
02/09/2019  11:00 AM             3,290 fttitle4.xml
02/09/2019  11:00 AM             1,354 fttitle8.flv
02/09/2019  11:00 AM             3,298 fttitle8.xml
02/09/2019  11:00 AM         1,815,158 indexstream.flv
02/09/2019  11:00 AM         7,703,603 indexstream.xml
02/09/2019  11:00 AM         5,316,597 mainstream.flv
02/09/2019  11:00 AM        21,259,001 mainstream.xml
02/09/2019  11:00 AM       217,448,561 screenshare_2_10.flv
02/09/2019  11:01 AM         1,364,572 screenshare_2_10.xml
02/09/2019  11:01 AM        32,364,457 screenshare_2_14.flv
02/09/2019  11:01 AM           188,011 screenshare_2_14.xml
02/09/2019  11:01 AM           387,981 screenshare_2_2.flv
02/09/2019  11:01 AM             1,698 screenshare_2_2.xml
02/09/2019  11:01 AM       237,470,572 screenshare_2_6.flv
02/09/2019  11:01 AM         1,625,385 screenshare_2_6.xml
02/09/2019  11:01 AM                48 telephony-files.xml
02/09/2019  11:01 AM               691 transcriptstream.flv
02/09/2019  11:01 AM             2,391 transcriptstream.xml
              39 File(s)    653,935,396 bytes
               2 Dir(s)   1,590,358,016 bytes free
```  
Indirdigimiz bu zipte ses ve goruntu dosyalari birbirinden ayri sekildedir.Bunu ffmpeg ile terminalden kisa bir kodla birlestireniliriz.
```
ffmpeg -i cameraVoip_3_16.flv -i screenshare_2_14.flv -c copy -map 0:a:0 -map 1:v:0 -shortest output.flv
```
Daha sonra birlestirdigimiz ses ve goruntu dosyalarini tek bir dosya haline getirmek icin yine ffmpeg araciligiyla kolaylikla halledebiliriz.

Ismini ```file.txt``` olarak asagidaki gibi bir txt dosyasi olusturuyoruz.
```
file '/home/1.flv'
file '/home/2.flv'
```
Ayni pathde asagidaki komutu calistirdigimizda tek parca ve sesli bir video elde etmis oluyoruz.
```
ffmpeg -f concat -safe 0 -i input.txt -c copy output.flv

```
