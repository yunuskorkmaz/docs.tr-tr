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
ms.openlocfilehash: c9fe16752223203806c7d3828f632aad0cab0c28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769425"
---
# <a name="using-fonts-and-text"></a>Yazı Tipleri ve Metin Kullanma
Tarafından sunulan çeşitli sınıfı vardır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin Windows Forms'ta çizme. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Sınıfına sahip birkaç <xref:System.Drawing.Graphics.DrawString%2A> yöntemleri metnin konumu, dikdörtgen, yazı tipi ve biçim sınırlayıcı gibi çeşitli özelliklerini belirlemenize olanak tanır. Ayrıca, çizme ve ölçmek metinle [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 'using static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> ve <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> yöntemleri tarafından sunulan `TextRenderer` sınıfı. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Yöntemleri de belirtmenize olanak tanır konumu, yazı tipi ve biçimi. Ya da tercih edebilirsiniz [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] veya [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ; metin işleme için ancak [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] performans ve daha doğru metin ölçme genellikle daha iyi sunar. Metin işlemeyle katkıda bulunan diğer sınıfları `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, ve `TextFormatFlags`.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yazı tipi aileleri ve yazı tipleri](how-to-construct-font-families-and-fonts.md)  
 Oluşturma işlemi gösterilmektedir `Font` ve `FontFamily` nesneleri.  
  
 [Nasıl yapılır: Belirtilen bir konuma metin çizme](how-to-draw-text-at-a-specified-location.md)  
 Bir konum belirli kullanarak metin çizme açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Nasıl yapılır: Bir dikdörtgende sarmalanmış metin çizme](how-to-draw-wrapped-text-in-a-rectangle.md)  
 Metin kullanarak bir dikdörtgen çizmek kullanılan nasıl açıklanmaktadır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Nasıl yapılır: GDI ile metin çizme](how-to-draw-text-with-gdi.md)  
 Nasıl kullanılacağını gösteren [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin çizme.  
  
 [Nasıl yapılır: Çizilmiş metni hizalama](how-to-align-drawn-text.md)  
 Biçimlendirilecek nasıl gösterir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin.  
  
 [Nasıl yapılır: Dikey metin oluşturma](how-to-create-vertical-text.md)  
 Dikey hizalı metin çizme açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Nasıl yapılır: Çizilmiş metinde sekme durakları ayarlama](how-to-set-tab-stops-in-drawn-text.md)  
 Programlarını nasıl sekme durakları ile ile metin çizme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
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
