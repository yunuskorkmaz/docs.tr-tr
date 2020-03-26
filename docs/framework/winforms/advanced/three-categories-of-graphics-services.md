---
title: Üç Grafik Hizmeti Kategorisi
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: fa7391ef0f7170ddb9d9d24aa5a1a03635bf46e0
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291733"
---
# <a name="three-categories-of-graphics-services"></a>Üç Grafik Hizmeti Kategorisi
Windows Formlar'daki grafik teklifleri aşağıdaki üç geniş kategoriye girer:  
  
- İki boyutlu (2-B) vektör grafikleri  
  
- Görüntüleme  
  
- Tipografi  
  
## <a name="2d-vector-graphics"></a>2D Vektör Grafikleri  
 Çizgiler, eğriler ve şekiller gibi iki boyutlu vektör grafikleri, koordinat sistemindeki nokta kümeleri tarafından belirtilen ilkel grafiklerdir. Örneğin, düz bir çizgi iki uç noktası yla belirtilir ve dikdörtgen, sol üst köşesinin konumunu veren bir nokta ve genişliğini ve yüksekliğini veren bir sayı çifti ile belirtilir. Basit bir yol, düz çizgilerle bağlanan bir dizi nokta tarafından belirtilir. Bézier spline dört kontrol noktası ile belirtilen karmaşık bir eğridir.  
  
 GDI+, ilkellerin kendileri hakkında bilgi depolayan sınıflar ve yapılar, ilkellerin nasıl çizilecekleri hakkında bilgi depolayan sınıflar ve çizimi gerçekten yapan sınıflar sağlar. Örneğin, <xref:System.Drawing.Rectangle> yapı bir dikdörtgenin konumunu ve boyutunu depolar; <xref:System.Drawing.Pen> sınıf çizgi rengi, çizgi genişliği ve çizgi stili hakkında bilgi depolar; ve <xref:System.Drawing.Graphics> sınıfın çizgiler, dikdörtgenler, yollar ve diğer şekiller çizmek için yöntemleri vardır. Kapalı şekillerin <xref:System.Drawing.Brush> ve yolların renkler veya desenlerle nasıl doldurulacağı hakkında bilgi depolayan çeşitli sınıflar da vardır.  
  
 Bir grafik komutları dizisi olan vektör görüntüsünü meta dosyaya kaydedebilirsiniz. GDI+, <xref:System.Drawing.Imaging.Metafile> meta dosyaların kaydedilmesi, görüntülenmesi ve kaydedilmesi için sınıfı sağlar. <xref:System.Drawing.Imaging.MetafileHeader> Ve <xref:System.Drawing.Imaging.MetaHeader> sınıflar ile, metadosya üstbilgisinde depolanan verileri inceleyebilirsiniz.  
  
## <a name="imaging"></a>Görüntüleme  
 Belirli türdeki resimlerin vektör grafik teknikleri ile görüntülenmesi zor veya imkansızdır. Örneğin, araç çubuğu düğmeleri üzerindeki resimler ve simge olarak görünen resimleri satır ve eğri koleksiyonları olarak belirtmek zordur. Kalabalık bir beyzbol stadyumunun yüksek çözünürlüklü dijital fotoğrafını vektör teknikleri ile oluşturmak daha da zordur. Bu tür görüntüler, ekrandaki tek tek noktaların renklerini temsil eden sayı dizileri olan bit eşlemler olarak depolanır. GDI+, <xref:System.Drawing.Bitmap> bit eşlemlerini görüntülemek, işlemek ve kaydetmek için sınıfı sağlar.  
  
## <a name="typography"></a>Tipografi  
 Tipografi, çeşitli yazı tiplerinde, boyutlarda ve stillerde metnin görüntülenmesidir. GDI+, bu karmaşık görev için kapsamlı destek sağlar. GDI+'daki yeni özelliklerden biri, LCD ekranda işlenen metinlere daha yumuşak bir görünüm sağlayan alt piksel antialiasing'dir.  
  
 Buna ek olarak, Windows Forms kendi <xref:System.Windows.Forms.TextRenderer> sınıfında GDI yetenekleri ile metin çizmek için seçenek salar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Grafiklere Genel Bakış](graphics-overview-windows-forms.md)
- [GDI+ Yönetilen Kodu Hakkında](about-gdi-managed-code.md)
- [Yönetilen Grafik Sınıflarını Kullanma](using-managed-graphics-classes.md)
