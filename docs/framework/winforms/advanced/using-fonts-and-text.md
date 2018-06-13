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
ms.openlocfilehash: d157b51e24009d847dede9ea6a9f81c8898c5b06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526269"
---
# <a name="using-fonts-and-text"></a>Yazı Tipleri ve Metin Kullanma
Tarafından sunulan birkaç sınıfı vardır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin Windows Forms'ta çizme. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> Sınıfına sahip birkaç <xref:System.Drawing.Graphics.DrawString%2A> metin yazı tipi ve biçimi dikdörtgen sınırlayıcı konum gibi çeşitli özelliklerini belirtmenize olanak veren yöntemler. Ayrıca, çizme ve ölçmek metinle [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] statik kullanarak <xref:System.Windows.Forms.TextRenderer.DrawText%2A> ve <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> yöntemleri tarafından sunulan `TextRenderer` sınıfı. [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] Yöntemleri de olanak tanır konumu, yazı tipi ve biçimini belirtin. Ya da seçebilirsiniz [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] veya [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] için metin işleme; ancak, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] teklifleri performansı ve daha doğru metin ölçme genellikle daha iyi. Metin işlemeye katkıda bulunan diğer sınıfları içerir `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, ve `TextFormatFlags`.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 Nasıl oluşturulacağını gösterir `Font` ve `FontFamily` nesneleri.  
  
 [Nasıl yapılır: Belirtilen bir Konuma Metin Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 Bir konumu belirli kullanarak metin çizme açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Nasıl yapılır: Dikdörtgende Sarmalanmış Metin](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 Dikdörtgen kullanarak metin çizme açıklanmaktadır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].  
  
 [Nasıl yapılır: GDI ile Metin Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 Nasıl kullanılacağı ortaya [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin çizme.  
  
 [Nasıl yapılır: Çizilmiş Metni Hizalama](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 Nasıl biçimlendirileceğini gösterir [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] ve [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] metin.  
  
 [Nasıl yapılır: Dikey Metin Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 Dikey olarak hizalanmış metinle çizmek açıklar [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Nasıl yapılır: Çizilmiş Metinde Sekme Durakları Ayarlama](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 Gösterir nasıl metin ile sekme durakları ile çizme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].  
  
 [Nasıl yapılır: Yüklü Yazı Tiplerini Numaralandırma](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 Yüklü yazı tiplerini adlarını listelemek açıklanmaktadır.  
  
 [Nasıl yapılır: Özel Yazı Tipi Koleksiyonu Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 Nasıl oluşturulacağını açıklar bir <xref:System.Drawing.Text.PrivateFontCollection> nesnesi.  
  
 [Nasıl yapılır: Yazı Tipi Ölçümleri Alma](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 Hücre Yokuş ve düşüşü gibi yazı tipi ölçümleri alma gösterilmektedir.  
  
 [Nasıl yapılır: Metinle Düzgünleştirme Kullanma](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 Metin çizim sırasında düzgünleştirme kullanımı açıklanmaktadır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Drawing.Font>  
 Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.  
  
 <xref:System.Drawing.FontFamily>  
 Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.  
  
 <xref:System.Windows.Forms.TextRenderer>  
 Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 Bu sınıf tanımlar ve üyeleri tümüne bağlantılar içerir.
