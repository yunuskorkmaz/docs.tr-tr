---
title: Üç Grafik Hizmeti Kategorisi
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: f7aa4de8a0d646c441d0921fb2561ef5a9480f4e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711245"
---
# <a name="three-categories-of-graphics-services"></a>Üç Grafik Hizmeti Kategorisi
Windows Forms'ta grafik teklifleri, aşağıdaki üç ana kategoriye ayrılır:  
  
-   İki boyutlu (2B) vektör grafikleri  
  
-   Görüntüleme  
  
-   Tipografi  
  
## <a name="2-d-vector-graphics"></a>2B vektör grafikleri  
 İki boyutlu bir vektör grafik ilkelleri olan; çizgiler, eğriler ve şekiller gibi; Bu, koordinat sistemi noktalarında kümesi tarafından belirtilir. Örneğin, düz bir çizgi kendi iki uç tarafından belirtilir ve bir dikdörtgen konumu, sol üst köşesinin ve bir çift sayı genişlik ve yükseklik vererek vermiş bir noktası tarafından belirtilir. Basit bir yolu, düz satırlarla bağlı noktaları dizisi ile belirtilir. Bézier eğri dört denetim noktaları tarafından belirtilen karmaşık bir eğri ' dir.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sınıfları ve temelleri hakkında bilgi depolamak yapıları, ilkel nasıl düzenleneceği hakkında bilgi depolamak sınıfları ve çizim yapan sınıfları sağlar. Örneğin, <xref:System.Drawing.Rectangle> yapısı depolar; dikdörtgen boyutunu ve konumunu <xref:System.Drawing.Pen> sınıfı satırı renk, çizgi genişliği ve çizgi stili; ilgili bilgileri depolar ve <xref:System.Drawing.Graphics> sınıfında çizim satırları, dikdörtgenler, yollar, yöntemleri ve diğer şekiller. Vardır da birkaç <xref:System.Drawing.Brush> hakkında bilgi depolamak sınıfları kapalı şekiller ve yollar, renkleri veya desenleri ile doldurulur.  
  
 Bir dizi grafik komut da vektör görüntü meta dosyası kaydedebilirsiniz. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sağlar <xref:System.Drawing.Imaging.Metafile> kaydı, görüntüleme ve meta dosyaları kaydetmek için sınıf. İle <xref:System.Drawing.Imaging.MetafileHeader> ve <xref:System.Drawing.Imaging.MetaHeader> sınıfları, meta dosyası üst bilgisinde depolanan verileri İnceleme.  
  
## <a name="imaging"></a>Görüntüleme  
 Belirli türde bir resim zor veya imkansız vektör grafikleri teknikleriyle görüntülenecek. Örneğin, araç çubuğu düğmeleri resimleri ve simgeler görünür resimleri çizgiler ve eğrilerle koleksiyonlarının belirtmek zordur. Yüksek çözünürlüklü dijital fotoğrafını kalabalık Beyzbol stadyum vektör teknikleri ile oluşturmak daha da zordur. Bu tür görüntüler, dizi tek nokta ekranında renklerini temsil eden sayı olan bit eşlemler olarak depolanır. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] sağlar <xref:System.Drawing.Bitmap> görüntüleme, düzenleme ve bit eşlemleri kaydetme sınıfı.  
  
## <a name="typography"></a>Tipografi  
 Tipografi yazı tipleri, boyutları ve stilleri çeşitli metin görüntülenir. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Bu karmaşık bir görev için kapsamlı destek sağlar. Yeni özelliklerden birini, [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] metin veren piksel düzgünleştirme daha sorunsuz bir görünümünü bir LCD ekranında işlenmeden.  
  
 Ayrıca, Windows Forms ile metin çizme seçeneği sunar [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] özelliklerinde, <xref:System.Windows.Forms.TextRenderer> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Grafiklere Genel Bakış](graphics-overview-windows-forms.md)
- [GDI+ Yönetilen Kodu Hakkında](about-gdi-managed-code.md)
- [Yönetilen Grafik Sınıflarını Kullanma](using-managed-graphics-classes.md)
