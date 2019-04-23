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
ms.openlocfilehash: f41585ba8816e0b1894a9f01163191848ae391e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089179"
---
# <a name="types-of-bitmaps"></a>Bit Eşlem Türleri
Bir bit eşlem piksel dikdörtgen bir dizi her piksel rengi belirtin BITS dizisidir. Tek bir piksele şekillendiriyorsa bit sayısı kadar bu piksele atanabilir renk sayısını belirler. Her piksel 4 BITS tarafından temsil edilir, örneğin, ardından belirli bir pikselin 16 farklı renkler birini atanabilir (2 ^ 4 = 16). Aşağıdaki tabloda, BITS, verilen sayıda tarafından temsil edilen bir piksele atanabilir renklerin sayısı birkaç örnek gösterilmektedir.  
  
|Piksel başına bit|Bir piksele atanabilir renk sayısı|  
|--------------------|------------------------------------------------------|  
|1.|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Bit eşlemler genellikle depolama disk dosyaları, dizide piksel, her bir satırdaki piksel sayısı ve satır sayısı başına bit sayısı gibi bilgileri depolayan bir veya daha fazla bilgi bloğu içerir. Böyle bir dosya (renk paleti olarak da adlandırılır) bir renk tablosu da içerebilir. Bir renk tablosu bit eşlem numaraları belirli bir renge eşler. Aşağıdaki çizim, bit eşlem ve renk tablosunu yanı sıra genişletilmiş bir görüntü gösterir. 2 olduklarından her piksel 4 bit bir sayı tarafından temsil edilen ^ 4 = 16 renk tablosunda renkleri. Tablodaki her renk, 24 bit bir sayı temsil edilir: 8 bit kırmızı, yeşil için 8 bit ve mavi için 8 bit. Sayıları, onaltılık (16 tabanında) biçiminde gösterilir: A 10, B = 11, C = 12, D = 13, E = 14, F = = 15.  
  
 ![Bit eşlem örnek](./media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Satır 3'te, görüntünün sütun 5 piksel bakın. Bit eşlem karşılık gelen sayısı 1'dir. Renk tablosunu bize 1 piksel kırmızı renkte kırmızı renk temsil ettiğini gösterir. Tüm bit eşlemin en üst sıradaki 3 girişlerdir. Renk tablosunu bize görüntünün üst satırdaki tüm pikselleri mavi şekilde 3 mavi temsil ettiğini söyler.  
  
> [!NOTE]
>  Bazı bit eşlemler, aşağıdan yukarıya biçiminde depolanır; sayıları ilk satırında bit eşlemin piksel cinsinden görüntü en alt satırında karşılık gelir.  
  
 Bir renk tablosunu dizinleri depolayan bir bit eşlem palet-dizinli bir bit eşlem olarak adlandırılır. Bazı bit eşlemler bir renk tablosu gerek vardır. Bir bit eşlem 24 bit / piksel kullanıyorsa, örneğin, bu bit eşlem dizinleri yerine renkleri kendilerini bir renk tablosunu depolayabilirsiniz. Aşağıdaki çizimde, bir renk tablosu kullanmak yerine doğrudan renkleri (24 bit / piksel) depolayan bir bit eşlem gösterir. Çizim, ayrıca karşılık gelen görüntü genişletilmiş bir görünümünü gösterir. Bit eşlem FFFFFF beyaz temsil eder, FF0000 temsil eden kırmızı, yeşil 00FF00 temsil eder ve 0000FF mavi temsil eder.  
  
 ![Bit eşlem örnek](./media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Grafik dosya biçimleri  
 Bit eşlemleri kaydetme disk dosyaları için birçok standart biçimi vardır. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Dosya grafikler aşağıdaki paragrafta açıklanan biçimlerini destekler.  
  
### <a name="bmp"></a>BMP  
 BMP, CİHAZDAN bağımsız ve uygulama bağımsız görüntüleri depolamak için Windows tarafından kullanılan standart bir biçimidir. Bit / piksel (1, 4, 8, 15, 24, 32 veya 64) için belirli bir BMP dosya sayısı, dosya üst bilgisinde belirtilir. BMP dosyaları 24 bit / piksel ile yaygındır. BMP dosyaları, genellikle değil sıkıştırılır ve bu nedenle, Internet üzerinden aktarım için uygun değildir.  
  
### <a name="graphics-interchange-format-gif"></a>Grafik Değişim Biçimi (GIF)  
 GIF, Web sayfalarında görünen görüntüleri için ortak bir biçimidir. GIF çizimlerde, düz renk bloklarını resimlerle ve renkler arasında NET sınırları resimler için çalışır. GIF sıkıştırılır ancak hiçbir bilgi sıkıştırma işlemde kaybolur; sıkıştırması açılmış bir görüntü tam olarak özgün ile aynıdır. Bir renk bir GIF görüntüsünü görüntüler herhangi bir Web sayfasında arka plan rengini sahip olmasını saydam belirlenebilir. GIF görüntülerini bir dizi animasyonlu GIF oluşturmak için bir tek dosyasında depolanabilir. GIF, 256 renkleri sınırlı olduğundan en fazla 8 bit / piksel, depolar.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>JPEG Dosya Değişim Biçimi (JPEG)  
 JPEG taranmış fotoğraflar gibi doğal sahneler için iyi çalışan bir sıkıştırma düzenidir. Sıkıştırma işleminde bazı bilgileri kaybolur, ancak genellikle İnsan gözüyle imperceptible kaybı. 16 milyondan fazla renkleri görüntüleyebilen şekilde 24 bit / piksel, JPEG depolayın. JPEG, saydam veya animasyon desteklemez.  
  
 JPEG görüntüleri sıkıştırma düzeyi yapılandırılabilir, ancak yüksek sıkıştırma düzeyleri (daha küçük dosyalar) daha fazla bilgi kaybına neden. 20:1 sıkıştırma oranı genellikle İnsan gözüyle orijinalden ayırt etmek zor bulur bir görüntü oluşturur. Bir BMP görüntüsünü ve bu BMP görüntüsünü sıkıştırılan iki JPEG görüntüleri aşağıda gösterilmiştir. İlk JPEG sıkıştırma oranı 4:1 ve ikinci JPEG sıkıştırma yaklaşık 8:1 oranında sahiptir.  
  
 ![Dosya türü örnekleri](./media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 JPEG sıkıştırma de satır çizimler için düz renk bloklarını çalışma ve sınırları diyez desteklemez. Bir BMP iki JPEG ve bir GIF ile birlikte aşağıda gösterilmiştir. JPEG ve GIF BMP sıkıştırıldı. Sıkıştırma oranı 4:1 GIF, 4:1 küçük JPEG ve 8:3 büyük JPEG için var. GIF satırları sharp bölümlere korur, ancak JPEG sınırları bulanıklaştıran eğilimindedir unutmayın.  
  
 ![Dosya türleri](./media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG bir sıkıştırma, bir dosya biçimi kullanılır. JPEG dosyası Değişim Biçimi (JFIF), depolama ve aktarma JPEG düzenine uygun sıkıştırılmış görüntüleri için yaygın olarak kullanılan bir dosya biçimidir. Web tarayıcıları tarafından görüntülenen JFIF dosyaları .jpg uzantısını kullanır.  
  
### <a name="exchangeable-image-file-exif"></a>Değiştirilebilir görüntü dosyası (EXIF)  
 EXIF, dijital kamera tarafından yakalanan fotoğraflar için kullanılan bir dosya biçimidir. EXIF dosya JPEG belirtimine göre sıkıştırılmış görüntü içerir. EXIF dosya fotoğraf hakkında bilgiler de içerir. (alındığı tarih, perde hızı, tehditlere maruz kalabileceği süreyi vb.) ve kamera (üreticisi, modeli vb.) hakkında bilgi.  
  
### <a name="portable-network-graphics-png"></a>Taşınabilir Ağ Grafikleri (PNG)  
 PNG biçiminde GIF biçimi avantajları birçoğu korur, ancak GIF, ötesinde yetenekleri de sağlar. GIF dosyaları gibi PNG dosyaları bilgi kaybı olmadan ile sıkıştırılır. PNG dosyaları, 8, 24, veya 48 bit / piksel ve çok sayıda gri ton 1, 2, 4, 8 veya 16 bit / piksel renklerle depolayabilirsiniz. Buna karşılık, GIF dosyaları yalnızca 1, 2, 4 veya 8 bit / piksel kullanabilirsiniz. Bir PNG dosyası, alfa değeri için o piksel rengi ile arka plan rengi harmanlanan belirtir her piksel olarak da depolayabilirsiniz.  
  
 PNG, aşamalı bir görüntü yeteneğini üzerinde GIF geliştirir (diğer bir deyişle, resmin daha iyi ve daha iyi tahminleri olarak görüntülemek için bir ağ bağlantısı üzerinden ulaşan). PNG dosyaları, böylece bu görüntüleri görüntüleme cihazları çeşitli üzerinde doğru bir şekilde işlenebilecek gama düzeltme ve renk düzeltme bilgileri içerebilir.  
  
### <a name="tag-image-file-format-tiff"></a>Etiketli Resim dosyası biçimi (TIFF)  
 TIFF çok çeşitli platformları ve görüntü işleme uygulamaları tarafından desteklenen esnek ve Genişletilebilir bir biçimidir. TIFF dosyaları sıkıştırma algoritmaları çeşitli dağıtabileceklerinizle ve tercihe bağlı sayıda piksel başına bit görüntüleri depolayabilirsiniz. Birkaç görüntüyü tek ve birden çok sayfalı TIFF dosyası depolanabilir. Görüntü (tarayıcı olun, ana bilgisayar, sıkıştırma, yönlendirme, piksel ve benzeri başına örnek türü) ilgili bilgileri dosyasında depolanan ve etiketleri kullanılarak düzenlenir. TIFF biçimi, yeni etiketleri eklenmesi ve onay gerektiği şekilde genişletilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
