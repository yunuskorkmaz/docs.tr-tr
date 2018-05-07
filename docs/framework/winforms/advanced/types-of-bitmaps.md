---
title: Bit Eşlem Türleri
ms.date: 03/30/2017
helpviewer_keywords:
- jpeg files
- TIFF files
- gif files
- Graphics Interchange Format
- Joint Photographic Experts Group
- .jpeg files
- .gif files
- graphics [Windows Forms], file formats
- images [Windows Forms], file formats
- Portable Network Graphics
- .bmp files
- EXIF file format
- PNG files
- pictures [Windows Forms], file formats
- Tag Image File Format
- bitmaps [Windows Forms], file format
- Exchangeable Image File
ms.assetid: 6be085a2-2c13-47c8-b80a-c18b32777d8d
ms.openlocfilehash: 1a79f34daac4238093693947f5fb5e73bb56213d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="types-of-bitmaps"></a>Bit Eşlem Türleri
Bir bit eşlem her piksel rengi piksel dikdörtgen bir dizi belirtin BITS dizisidir. BITS için tek bir piksel hoşlanıyorsanız sayısını o piksel atanabilir renk sayısını belirler. Her piksel 4 BITS tarafından temsil edilen, örneğin, ardından belirli bir piksel 16 farklı renk biri atanabilir (2 ^ 4 = 16). Aşağıdaki tabloda, BITS, verilen sayıda tarafından temsil edilen bir piksel atanabilir renklerin sayısı birkaç örneği gösterilmektedir.  
  
|Bit / piksel|Bir piksel atanabilir renklerin sayısı|  
|--------------------|------------------------------------------------------|  
|1.|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Bit eşlemler genellikle depolamak disk dosyaları dizideki bit / piksel, her satırda piksel sayısı ve satır numarası sayısı gibi bilgileri depolayan bir veya daha fazla bilgi bloğu içerir. Böyle bir dosya (bazen bir renk paleti denir) bir renk tablosu da içerebilir. Bir renk tablosu numaraları bit eşlemde belirli renkleri eşler. Aşağıdaki çizimde, bit eşlem ve renk tablosu birlikte büyütülmüş görüntü gösterir. 2 olduklarından her piksel 4 bitlik bir sayı tarafından temsil edilen ^ 4 = 16 renklerin renk tablosunda. Her bir renk tablosundaki bir 24 bit sayıyla: 8 bit kırmızı, yeşil için 8 bit ve mavi için 8 bit. Sayıları onaltılı (16 tabanı) biçiminde gösterilir: A = 10, B = = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Bit eşlem örnek](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Satır 3'te, görüntünün sütun 5 piksel bakın. Bit eşlem karşılık gelen sayısı 1'dir. Renk tablosu bize kırmızı pikseli olacak şekilde 1 kırmızı renk temsil eden söyler. Bit eşlem üst satırında tüm girişleri 3 ' dir. Renk tablosu bize görüntünün üst satırdaki tüm pikselleri mavi; bu nedenle 3 mavi temsil eden söyler.  
  
> [!NOTE]
>  Bazı bit eşlemler aşağıdan yukarıya biçiminde depolanır; bit eşlem ilk satırının sayıları piksel cinsinden görüntü en alttaki karşılık gelir.  
  
 Bir renk tabloya dizinleri depolayan bir bit eşlem palet dizinli bir bit eşlem adı verilir. Bazı bit eşlemler gerekmez. bir renk tablosu var. Bir bit eşlem 24 bit / piksel kullanıyorsa, örneğin, bu bit eşlem dizinler yerine renkleri kendilerini bir renk tabloya depolayabilirsiniz. Aşağıdaki çizimde, bir renk tablosu kullanmak yerine doğrudan renkleri (24 bit / piksel) depolayan bir bit eşlem gösterir. Çizimde de karşılık gelen görüntü büyütülmüş bir görünümünü gösterir. Bit eşlem FFFFFF beyaz temsil eder, FF0000 kırmızı temsil eder, 00FF00 yeşil temsil eder ve 0000FF mavi temsil eder.  
  
 ![Bit eşlem örnek](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Grafik dosya biçimleri  
 Disk dosyalarında bit eşlemleri kaydetme için birçok standart biçimlerini vardır. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Aşağıdaki paragrafta açıklanan biçimleri grafik dosya destekler.  
  
### <a name="bmp"></a>BMP  
 BMP, cihaz ve uygulama bağımsız görüntüleri saklamak için Windows tarafından kullanılan standart bir biçimidir. Bit / piksel (1, 4, 8, 15, 24, 32 veya 64) için belirli bir BMP dosya sayısı, bir dosya üstbilgisi belirtilir. BMP dosyaları 24 bit / piksel ile yaygındır. BMP dosyaları genellikle değil sıkıştırılır ve bu nedenle, Internet'te aktarımı için uygun değildir.  
  
### <a name="graphics-interchange-format-gif"></a>Grafik Değişim Biçimi (GIF)  
 GIF, Web sayfalarında görüntülenir görüntüleri için ortak bir biçimidir. GIF çizimlerde, düz renk bloklarını resimler ve renk arasında NET sınırları resimleri için iyi çalışır. GIF sıkıştırılmış ancak hiçbir bilgi sıkıştırma işleminde kaybolur; açılan sıkıştırılmış görüntüyü tam olarak özgün ile aynıdır. Görüntü görüntülediği herhangi bir Web sayfasında arka plan rengini sahip olmasını GIF bir renk saydam olarak belirlenebilir. Animasyonlu GIF oluşturmak için tek dosyada GIF görüntüleri bir dizi depolanabilir. 256 renk sınırlı olacak şekilde en fazla 8 bit / piksel, GIF depolar.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>Birleşik Fotoğraf Uzmanları Grubu (JPEG)  
 JPEG taranmış fotoğraflar gibi doğal planda iyi çalışan bir sıkıştırma düzenidir. Sıkıştırma işleminde bazı bilgiler kaybolur, ancak kaybı İnsan göz imperceptible görülür. 16 milyondan fazla renkleri görüntüleyebilen şekilde JPEG 24 bit / piksel, depolar. JPEG saydamlık veya animasyon desteklemez.  
  
 JPEG görüntüleri sıkıştırma düzeyini yapılandırılabilir, ancak yüksek sıkıştırma düzeyleri (daha küçük dosyalar) daha fazla bilgi kaybına yol. 20:1 sıkıştırma oranı çoğunlukla İnsan göz özgün ayrım yapmak zor bulur bir görüntü üretiyor. Aşağıdaki çizimde, BMP resmini ve bu BMP görüntüden sıkıştırılan iki JPEG görüntüleri gösterir. İlk JPEG sıkıştırma oranı 4:1 ve ikinci JPEG sıkıştırma oranı, yaklaşık 8:1 sahiptir.  
  
 ![Dosya türü örnekleri](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 JPEG sıkıştırma değil de satır çizimler için düz renk bloklarını çalışır ve sınırları diyez. BMP iki JPEG ve GIF ile birlikte aşağıda gösterilmiştir. JPEG ve GIF, BMP sıkıştırılan. Sıkıştırma GIF, 4:1 için 4:1 küçük JPEG ve 8:3 büyük JPEG için orandır. Satırları sharp bölümlere GIF korur, ancak JPEG sınırları ölçeklendirilmelidir eğilimindedir unutmayın.  
  
 ![Dosya türleri](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG sıkıştırma düzeni, bir dosya biçimi ' dir. JPEG dosyası Değişim Biçimi (JFIF) depolamak ve JPEG düzenine uygun sıkıştırılmış görüntüleri aktarma için yaygın olarak kullanılan bir dosya biçimidir. Web tarayıcıları tarafından görüntülenen JFIF dosyaları .jpg uzantısını kullanır.  
  
### <a name="exchangeable-image-file-exif"></a>Değiştirilebilir görüntü dosyası (EXIF)  
 EXIF, dijital kamera tarafından yakalanan fotoğraf için kullanılan bir dosya biçimidir. EXIF dosya JPEG belirtimine göre sıkıştırılmış bir görüntü içerir. EXIF dosya fotoğraf hakkında bilgiler de içerir (çekildiği tarih, perde hızı, etkilenme zaman vb.) ve kamera (üreticisini, model vb.) hakkında bilgi.  
  
### <a name="portable-network-graphics-png"></a>Taşınabilir Ağ Grafikleri (PNG)  
 PNG biçimi GIF biçimi avantajları çoğunu korur ancak GIF, ötesinde yetenekleri de sağlar. GIF dosyaları gibi PNG dosyaları hiçbir bilgi kaybı ile sıkıştırılır. PNG dosyaları, 8, 24, veya 48 bit / piksel ve çok sayıda gri ton 1, 2, 4, 8 ile veya 16 bit / piksel renklerle depolayabilirsiniz. Buna karşılık, GIF dosyaları yalnızca 1, 2, 4 veya 8 bit / piksel kullanabilirsiniz. Bir PNG dosyası da arka plan rengiyle karıştırılan o piksel rengi için derecesini belirtir her piksel için alfa değeri depolayabilirsiniz.  
  
 PNG GIF üzerinde bir görüntüyü aşamalı olarak yeteneğini artırır (diğer bir deyişle, görüntünün daha iyi ve daha iyi yaklaşık değerler olarak görüntülemek için bir ağ bağlantısı üzerinden ulaşan). Görüntüleri görüntüleme cihazları çeşitli doğru şekilde işlenebilecek böylece PNG dosyaları gama düzeltmesi ve renk düzeltme bilgiler içerebilir.  
  
### <a name="tag-image-file-format-tiff"></a>Etiket görüntü dosyası biçimi (TIFF)  
 TIFF çok çeşitli platformlar ve görüntü işleme uygulamaları tarafından desteklenen esnek ve Genişletilebilir bir biçimidir. TIFF dosyaları sıkıştırma algoritmaları çeşitli uygulayabileceğiniz ve rasgele bir bit / piksel sayısı görüntülerle depolayabilirsiniz. Birkaç görüntüyü bir tek, birden çok sayfa TIFF dosyasında depolanabilir. Görüntünün (tarayıcı yapma, ana bilgisayarı, sıkıştırma, yönlendirme, piksel vb. başına örnek türü) için ilgili bilgiler dosyasında depolanabilir ve etiketleri kullanılarak düzenlenir. TIFF biçimi onay ve yeni etiketler eklenmesi tarafından gerektiği şekilde genişletilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Image?displayProperty=nameWithType>  
 <xref:System.Drawing.Bitmap?displayProperty=nameWithType>  
 <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>  
 [Görüntüler, Bit Eşlemler ve Meta Dosyaları](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
