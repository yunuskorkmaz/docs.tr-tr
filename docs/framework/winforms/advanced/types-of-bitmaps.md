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
ms.openlocfilehash: 2243c9ce2d8ba741143d301c38e8b88d7b196c98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914820"
---
# <a name="types-of-bitmaps"></a>Bit Eşlem Türleri
Bit eşlem, piksel dizisindeki her bir pikselin rengini belirleyen bir bit dizisidir. Tek bir piksele ayrılan bit sayısı, bu piksele atanabilecek renklerin sayısını belirler. Örneğin, her piksel 4 bit ile temsil edildiğinde, belirli bir piksel 16 farklı renkten biri atanabilir (2 ^ 4 = 16). Aşağıdaki tabloda, belirli bir bit sayısıyla temsil edilen bir piksel için atanabilecek renk sayısının birkaç örneği gösterilmektedir.  
  
|Bit/piksel|Bir pikselin atanabileceği renklerin sayısı|  
|--------------------|------------------------------------------------------|  
|1\.|2^1 = 2|  
|2|2^2 = 4|  
|4|2^4 = 16|  
|8|2^8 = 256|  
|16|2^16 = 65,536|  
|24|2^24 = 16,777,216|  
  
 Bit eşlemler depolayan disk dosyalarında genellikle piksel başına bit sayısı, her satırdaki piksel sayısı ve dizideki satır sayısı gibi bilgileri depolayan bir veya daha fazla bilgi bloğu bulunur. Böyle bir dosya aynı zamanda bir renk tablosu (bazen renk paleti olarak adlandırılır) de içerebilir. Renk tablosu, bit eşlemdeki sayıları belirli renklere eşler. Aşağıdaki çizimde, bit eşlem ve renk tablosu ile birlikte büyütülmüş bir görüntü gösterilmektedir. Her piksel 4 bitlik bir sayıyla temsil edildiğinde, renk tablosunda 2 ^ 4 = 16 renk vardır. Tablodaki her renk 24 bitlik bir sayıyla temsil edilir: Kırmızı için 8 bit, yeşil için 8 bit ve mavi için 8 bit. Sayılar onaltılık (taban 16) biçiminde gösterilir: A = 10, B = 11, C = 12, D = 13, E = 14, F = 15.  
  
 ![Bit eşlem örneği](./media/aboutgdip03-art01.gif "AboutGdip03_Art01")  
  
 Görüntünün satır 3, sütun 5 ' teki pikseline bakın. Bit eşlemdeki karşılık gelen sayı 1 ' dir. Renk tablosu, 1 ' in kırmızı rengini temsil ettiğini, pikselin kırmızı olduğunu söyler. Bit eşlemin en üstteki satırındaki tüm girişler 3 ' dir. Renk tablosu, 3 ' ün mavi temsil ettiğini, böylece görüntünün en üstteki satırındaki tüm piksellerin mavi olduğunu söyler.  
  
> [!NOTE]
> Bazı bit eşlemler, alt biçimde saklanır; bit eşlemin ilk satırındaki sayılar görüntünün alt satırındaki piksellere karşılık gelir.  
  
 Bir renk tablosunda dizinleri depolayan bir bit eşlem, palette dizinli bit eşlem olarak adlandırılır. Bazı Bit eşlemlerin renk tablosuna ihtiyacı yoktur. Örneğin, bir bit eşlem piksel başına 24 bit kullanıyorsa, bu bit eşlem, renkleri bir renk tablosuna dizinler yerine kendi başlarına depolayabilirler. Aşağıdaki çizimde renk tablosu kullanmak yerine renkleri doğrudan depolayan bir bit eşlem (piksel başına 24 bit) gösterilmektedir. Çizimde de ilgili görüntünün büyütülmüş görünümü gösterilmektedir. Bit eşlemde FFFFFF beyaz, FF0000 kırmızıya, 00FF00 ise yeşil ve 0000FF, maviyi temsil eder.  
  
 ![Bit eşlem örneği](./media/aboutgdip03-art02.gif "AboutGdip03_Art02")  
  
## <a name="graphics-file-formats"></a>Grafik dosyası biçimleri  
 Bit eşlemleri disk dosyalarında kaydetmek için birçok standart biçim vardır. GDI+, aşağıdaki paragraflarda açıklanan grafik dosyası biçimlerini destekler.  
  
### <a name="bmp"></a>BMP  
 BMP, Windows tarafından cihazdan bağımsız ve uygulamayla bağımsız görüntüleri depolamak için kullanılan standart bir biçimdir. Belirli bir BMP dosyası için piksel başına bit sayısı (1, 4, 8, 15, 24, 32 veya 64) bir dosya üstbilgisinde belirtilir. 24 bit piksel başına BMP dosyaları yaygındır. BMP dosyaları genellikle sıkıştırılmaz ve bu nedenle, Internet üzerinden aktarım için uygun değildir.  
  
### <a name="graphics-interchange-format-gif"></a>Grafik Değişim Biçimi (GIF)  
 GIF, Web sayfalarında görünen görüntüler için ortak bir biçimdir. GIF 'Ler çizgi çizimlerinde, düz renk blokları olan resimlerde ve renkler arasında keskin sınırlara sahip resimler için uygundur. GIF 'Ler sıkıştırılır, ancak sıkıştırma işleminde bilgi kaybı yoktur; sıkıştırması açılmış bir görüntü, orijinaliyle tamamen aynıdır. Bir GIF 'teki bir renk saydam olarak belirlenebilir, böylece görüntünün onu görüntüleyen herhangi bir Web sayfasının arka plan rengi olur. GIF görüntülerinin sırası, animasyonlu bir GIF oluşturmak için tek bir dosyada depolanabilir. GIF 'Ler, her piksel için en fazla 8 bit boyutunda, 256 renklerle sınırlandırılmıştır.  
  
### <a name="joint-photographic-experts-group-jpeg"></a>Birleşik Fotoğraf Uzmanları Grubu (JPEG)  
 JPEG, taranmış fotoğraflar gibi doğal sahnelerde iyi bir şekilde çalışacak bir sıkıştırma şemadır. Sıkıştırma işleminde bazı bilgiler kaybolur, ancak genellikle kaybın insan gözle kaybı vardır. JPEG 'ler piksel başına 24 bit depolar, bu nedenle 16.000.000 'den fazla renk görüntüleme yeteneğine sahiptir. JPEG 'ler saydamlığı veya animasyonu desteklemez.  
  
 JPEG görüntülerinde sıkıştırma düzeyi yapılandırılabilir, ancak daha yüksek sıkıştırma düzeyleri (daha küçük dosyalar) daha fazla bilgi kaybına neden olur. 20:1 sıkıştırma oranı genellikle insan gözünün orijinalden ayırt edilmesi zor bulduğu bir görüntü oluşturur. Aşağıdaki çizimde, bir BMP görüntüsünü ve bu BMP görüntüsünden sıkıştırılan iki JPEG görüntüsü gösterilmektedir. İlk JPEG 4:1 sıkıştırma oranına sahiptir ve ikinci JPEG 'nin 8:1 hakkında bir sıkıştırma oranı vardır.  
  
 ![Filetype örnekleri](./media/aboutgdip03-art03.gif "AboutGdip03_Art03")  
  
 JPEG sıkıştırması çizgi çizimleri, düz renk blokları ve keskin sınırlar için iyi çalışmaz. Aşağıdaki çizimde, iki JPEG ve GIF ile birlikte bir BMP gösterilmektedir. JPEG 'ler ve GIF, BMP 'den sıkıştırıldı. Sıkıştırma oranı, GIF için 4:1, daha küçük JPEG için 4:1 ve daha büyük JPEG için 8:3. GIF 'in çizgiler üzerinde keskin sınırlar tuttuğunu, ancak JPEG 'ler sınırları bulanıklaştırmasını sağlar.  
  
 ![Dosya türleri](./media/aboutgdip03-art03a.gif "AboutGdip03_Art03A")  
  
 JPEG, bir dosya biçimi değil, bir sıkıştırma şemadır. JPEG dosya değişim biçimi (JıO), JPEG şemasına göre sıkıştırılan görüntüleri depolamak ve aktarmak için yaygın olarak kullanılan bir dosya biçimidir. Web tarayıcıları tarafından görüntülenmekte olan JFILES dosyaları. jpg uzantısını kullanır.  
  
### <a name="exchangeable-image-file-exif"></a>Takas edilebilir görüntü dosyası (EXIF)  
 EXIF, dijital kameralar tarafından yakalanan fotoğraflar için kullanılan bir dosya biçimidir. Bir EXIF dosyası JPEG belirtimine göre sıkıştırılan bir görüntü içerir. Bir EXIF dosyası ayrıca fotoğrafla ilgili bilgileri (Çekildiği Tarih, perde hızı, pozlama süresi vb.) ve kamera (üretici, model vb.) hakkındaki bilgileri içerir.  
  
### <a name="portable-network-graphics-png"></a>Taşınabilir Ağ Grafikleri (PNG)  
 PNG biçimi, GIF biçiminin birçok avantajını korur, ancak aynı zamanda GIF 'in ötesinde yetenekler sağlar. GIF dosyaları gibi, PNG dosyaları da hiçbir bilgi kaybı olmadan sıkıştırılır. PNG dosyaları, renkleri 8, 24 veya piksel başına 48 bit ve 1, 2, 4, 8 veya piksel başına 16 bit ile gri ölçeklendirilen şekilde saklayabilir. Buna karşılık, GIF dosyaları her piksel için yalnızca 1, 2, 4 veya 8 bit kullanabilir. Bir PNG dosyası her piksel için bir alfa değeri de saklayabilir, bu da bu pikselin renginin arka plan rengiyle karışan derecesini belirtir.  
  
 PNG, GIF üzerinde, bir görüntüyü aşamalı olarak görüntüleme (yani bir ağ bağlantısının üzerine geldiğinde görüntünün daha iyi ve daha iyi bir şekilde gösterilmesi için) özelliğini geliştirir. PNG dosyaları, görüntülerin çeşitli görüntü cihazlarında doğru şekilde işlenebilmesi için gama düzeltmesi ve renk düzeltme bilgileri içerebilir.  
  
### <a name="tag-image-file-format-tiff"></a>Etiketli resim dosyası biçimi (TIFF)  
 TIFF, çok çeşitli platformlar ve görüntü işleme uygulamaları tarafından desteklenen esnek ve genişletilebilir bir biçimdir. TIFF dosyaları, görüntüleri piksel başına rastgele sayıda bit ile saklayabilir ve çeşitli sıkıştırma algoritmaları kullanabilir. Birçok görüntü tek, çok sayfalı bir TIFF dosyasında depolanabilir. Görüntüyle ilgili bilgiler (tarayıcı oluşturma, ana bilgisayar, sıkıştırma türü, yönlendirme, piksel başına örnek vb.) dosyada depolanabilir ve Etiketler kullanılarak düzenlenebilir. TIFF biçimi, onay ve yeni etiketlerin eklenmesi için gereken şekilde genişletilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Image?displayProperty=nameWithType>
- <xref:System.Drawing.Bitmap?displayProperty=nameWithType>
- <xref:System.Drawing.Imaging.PixelFormat?displayProperty=nameWithType>
- [Görüntüler, Bit Eşlemler ve Meta Dosyaları](images-bitmaps-and-metafiles.md)
- [Görüntüler, Bit Eşlemler, Simgeler ve Meta Dosyaları ile Çalışma](working-with-images-bitmaps-icons-and-metafiles.md)
