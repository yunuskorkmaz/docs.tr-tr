---
title: Yazı Tipleri ve Metin Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
ms.openlocfilehash: 73a4af5fe7367e777fcb83af8c84c09be91e5b1e
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505114"
---
# <a name="using-fonts-and-text"></a>Yazı Tipleri ve Metin Kullanma
Windows Form üzerinde metin çizim GDI +'da ve GDI tarafından sunulan çeşitli sınıfı vardır. GDI + <xref:System.Drawing.Graphics> sınıfına sahip birkaç <xref:System.Drawing.Graphics.DrawString%2A> yöntemleri metnin konumu, dikdörtgen, yazı tipi ve biçim sınırlayıcı gibi çeşitli özelliklerini belirlemenize olanak tanır. Ayrıca, çizme ve'using static GDI ile metin ölçmek <xref:System.Windows.Forms.TextRenderer.DrawText%2A> ve <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> yöntemleri tarafından sunulan `TextRenderer` sınıfı. GDI yöntemleri konumu, yazı tipi ve biçim belirtmenizi sağlar. GDI veya GDI +'da metin işleme için seçebilirsiniz; Ancak, GDI genellikle daha iyi performans ve daha doğru metin ölçme sunar. Metin işlemeyle katkıda bulunan diğer sınıfları `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, ve `TextFormatFlags`.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yazı tipi aileleri ve yazı tipleri](how-to-construct-font-families-and-fonts.md)  
 Oluşturma işlemi gösterilmektedir `Font` ve `FontFamily` nesneleri.  
  
 [Nasıl yapılır: Belirtilen bir konuma metin çizme](how-to-draw-text-at-a-specified-location.md)  
 GDI +'da ve GDI kullanarak bir belirli konumda metin çizme açıklar.  
  
 [Nasıl yapılır: Bir dikdörtgende sarmalanmış metin çizme](how-to-draw-wrapped-text-in-a-rectangle.md)  
 GDI +'da ve GDI kullanarak dikdörtgene metin çizme açıklanmaktadır.  
  
 [Nasıl yapılır: GDI ile metin çizme](how-to-draw-text-with-gdi.md)  
 Metin çizim GDI nasıl yapılacağı açıklanır.  
  
 [Nasıl yapılır: Çizilmiş metni hizalama](how-to-align-drawn-text.md)  
 GDI +'da ve GDI metnin nasıl biçimlendirileceğini gösterir.  
  
 [Nasıl yapılır: Dikey metin oluşturma](how-to-create-vertical-text.md)  
 GDI +'da dikey hizalı metin çizme açıklar.  
  
 [Nasıl yapılır: Çizilmiş metinde sekme durakları ayarlama](how-to-set-tab-stops-in-drawn-text.md)  
 Programlarını nasıl GDI + ile sekme durakları ile metin çizin.  
  
 [Nasıl yapılır: Yüklü yazı tiplerini numaralandırma](how-to-enumerate-installed-fonts.md)  
 Yüklü yazı tiplerini adlarını listelemek açıklanmaktadır.  
  
 [Nasıl yapılır: Özel yazı tipi koleksiyonu oluşturma](how-to-create-a-private-font-collection.md)  
 Nasıl oluşturulacağını açıklar bir <xref:System.Drawing.Text.PrivateFontCollection> nesne.  
  
 [Nasıl yapılır: Yazı tipi ölçümleri alma](how-to-obtain-font-metrics.md)  
 Hücre ascent ve iniş gibi yazı tipi ölçümleri alma işlemi gösterilmektedir.  
  
 [Nasıl yapılır: Metinle düzgünleştirme kullanma](how-to-use-antialiasing-with-text.md)  
 Metin çizim sırasında düzgünleştirme kullanma açıklanmaktadır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing.Font>  
 Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.  
  
 <xref:System.Drawing.FontFamily>  
 Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.  
  
 <xref:System.Windows.Forms.TextRenderer>  
 Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 Bu sınıf açıklar ve tüm üyelerini bağlantılar içerir.
