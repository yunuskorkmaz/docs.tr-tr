---
title: GlyphRun Nesnesi ve Karakter Öğesine Giriş
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 9e40a9656bd1d89203b167860ef6951d5e30377c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918396"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>GlyphRun Nesnesi ve Karakter Öğesine Giriş
Bu konu, <xref:System.Windows.Media.GlyphRun> nesnesini <xref:System.Windows.Documents.Glyphs> ve öğesini açıklar.  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>GlyphRun 'a giriş  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]biçimlendirmeden sonra metni kesme ve kalıcı hale getirmek isteyen müşterilere doğrudan erişim <xref:System.Windows.Documents.Glyphs> ile glif düzeyinde biçimlendirme dahil gelişmiş metin desteği sağlar. Bu özellikler, aşağıdaki senaryolardan her birinde farklı metin işleme gereksinimleri için kritik destek sağlar.  
  
1. Sabit biçimli belgelerin ekran görüntüsü.  
  
2. Yazdırma senaryoları.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir cihaz yazıcı dili olarak.  
  
    - Microsoft XPS Belge Yazıcısı.  
  
    - Önceki yazıcı sürücüleri, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalardan Sabit biçime çıkış.  
  
    - Yazdırma kuyruğu biçimi.  
  
3. Önceki Windows sürümleri ve diğer bilgi işlem cihazlarının istemcileri de dahil olmak üzere, sabit biçimli belge temsili.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Controls.Label> , [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ve<xref:System.Windows.Controls.TextBlock>gibi genel düzen ve senaryolar için birkaç öğe sağlar. Düzen ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolar hakkında daha fazla bilgi için bkz. [WPF 'de tipografi](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>GlyphRun nesnesi  
 <xref:System.Windows.Media.GlyphRun> Nesnesi tek bir yazı tipindeki tek bir yüzden ve tek bir işleme stiliyle bir karakter dizisini temsil eder.  
  
 <xref:System.Windows.Media.GlyphRun>glif <xref:System.Windows.Documents.Glyphs.Indices%2A> ve ayrı karakter konumları gibi yazı tipi ayrıntılarını içerir. Ayrıca, çalıştırmanın oluşturulduğu orijinal [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kod noktalarını, karakter-karakter arabelleği fark eşleme bilgilerini ve karakter başına ve karakter başına bayrakları da içerir.  
  
 <xref:System.Windows.Media.GlyphRun><xref:System.Windows.FrameworkElement> ,<xref:System.Windows.Documents.Glyphs>karşılık gelen bir üst düzeydir. <xref:System.Windows.Documents.Glyphs>öğe ağacında ve çıktıyı göstermek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Media.GlyphRun> için biçimlendirme içinde kullanılabilir.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Glyphs öğesi  
 Öğesi, <xref:System.Windows.Media.GlyphRun> içindeki[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]çıktısınıtemsileder. <xref:System.Windows.Documents.Glyphs> Aşağıdaki biçimlendirme sözdizimi, <xref:System.Windows.Documents.Glyphs> öğesini tanımlamakta kullanılır.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Aşağıdaki özellik tanımları, örnek biçimlendirmesinde ilk dört özniteliğe karşılık gelir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Kaynak tanımlayıcısını belirtir: dosya adı, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]veya kaynak başvurusu. exe veya kapsayıcı.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Çizim yüzeyi birimlerinde yazı tipi boyutunu belirtir (varsayılan. 96 inç).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Kalın ve Italik stiller için bayrakları belirtir.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Çift yönlü düzen düzeyini belirtir. Çift sayılı ve sıfır değerler soldan sağa düzeni göstermez; tek sayılı değerler sağdan sola düzeni göstermez.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Dizinler özelliği  
 <xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği, glif belirtimlerinin bir dizesidir. Bir karakter dizisinin tek bir küme olarak ayarlandığı yerlerde, kümedeki ilk glifin belirtimi, küme oluşturmak için kaç karakter ve kaç tane kod noktasının birleştirildiği hakkında bir belirtimdir. <xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği, aşağıdaki özellikleri bir dizede toplar.  
  
- Glif dizinleri  
  
- Glif öncelikli genişlikleri  
  
- Glif eki vektörlerini birleştirme  
  
- Kod noktalarından karakterlere karakter eşleme  
  
- Glif bayrakları  
  
 Her glif belirtiminin aşağıdaki biçimi vardır.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Glif ölçümleri  
 Her glif, nasıl hizalanacağını <xref:System.Windows.Documents.Glyphs>belirleyen ölçümleri tanımlar. Aşağıdaki grafik iki farklı karakter karakterlerinin çeşitli tipografik kalitelerini tanımlar.  
  
 ![Glif ölçümlerinin Diagraf](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Glif biçimlendirmesi  
 Aşağıdaki kod örneği, içindeki <xref:System.Windows.Documents.Glyphs> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]öğesinin çeşitli özelliklerinin nasıl kullanıldığını gösterir.  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de Tipografi](typography-in-wpf.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Metin](optimizing-performance-text.md)
