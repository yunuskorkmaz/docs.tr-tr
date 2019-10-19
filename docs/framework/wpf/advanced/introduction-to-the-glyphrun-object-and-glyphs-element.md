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
ms.openlocfilehash: 2f7bb3fb4f28b063c78dde9f9f354b38a5e707f3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581898"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>GlyphRun Nesnesi ve Karakter Öğesine Giriş
Bu konuda <xref:System.Windows.Media.GlyphRun> nesnesi ve <xref:System.Windows.Documents.Glyphs> öğesi açıklanmaktadır.  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>GlyphRun 'a giriş  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], biçimlendirmeden sonra metni kesme ve kalıcı hale getirmek isteyen müşteriler için <xref:System.Windows.Documents.Glyphs> doğrudan erişimi olan glif düzeyi biçimlendirme dahil gelişmiş metin desteği sağlar. Bu özellikler, aşağıdaki senaryolardan her birinde farklı metin işleme gereksinimleri için kritik destek sağlar.  
  
1. Sabit biçimli belgelerin ekran görüntüsü.  
  
2. Yazdırma senaryoları.  
  
    - cihaz yazıcı dili olarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
    - Microsoft XPS Belge Yazıcısı.  
  
    - Önceki yazıcı sürücüleri, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalardan Sabit biçime çıkış.  
  
    - Yazdırma kuyruğu biçimi.  
  
3. Önceki Windows sürümleri ve diğer bilgi işlem cihazlarının istemcileri de dahil olmak üzere, sabit biçimli belge temsili.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.TextBlock> gibi genel düzen ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryolar için birkaç öğe sağlar. Düzen ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolar hakkında daha fazla bilgi için [WPF 'de tipografi](typography-in-wpf.md)'e bakın.  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>GlyphRun nesnesi  
 @No__t_0 nesnesi tek bir yazı tipinin tek bir tarafındaki ve tek bir işleme stiliyle bir karakter dizisini temsil eder.  
  
 <xref:System.Windows.Media.GlyphRun>, glif <xref:System.Windows.Documents.Glyphs.Indices%2A> ve tek karakter konumları gibi yazı tipi ayrıntılarını içerir. Ayrıca, çalıştırmanın oluşturulduğu orijinal Unicode kod noktalarını, karakter-karakter arabelleği fark eşleme bilgilerini ve karakter başına ve karakter başına bayrakları da içerir.  
  
 <xref:System.Windows.Media.GlyphRun> ' a karşılık gelen bir üst düzey <xref:System.Windows.FrameworkElement> <xref:System.Windows.Documents.Glyphs> ' dir. <xref:System.Windows.Documents.Glyphs>, öğe ağacında ve <xref:System.Windows.Media.GlyphRun> çıktıyı göstermek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirmesinde kullanılabilir.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Glyphs öğesi  
 @No__t_0 öğesi, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir <xref:System.Windows.Media.GlyphRun> çıkışını temsil eder. Aşağıdaki biçimlendirme sözdizimi <xref:System.Windows.Documents.Glyphs> öğesini tanımlamakta kullanılır.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Aşağıdaki özellik tanımları, örnek biçimlendirmesinde ilk dört özniteliğe karşılık gelir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Kaynak tanımlayıcısını belirtir: dosya adı, Web Tekdüzen Kaynak tanımlayıcısı (URI) veya Application. exe veya Container içindeki kaynak başvurusu.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Çizim yüzeyi birimlerinde yazı tipi boyutunu belirtir (varsayılan. 96 inç).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Kalın ve Italik stiller için bayrakları belirtir.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Çift yönlü düzen düzeyini belirtir. Çift sayılı ve sıfır değerler soldan sağa düzeni göstermez; tek sayılı değerler sağdan sola düzeni göstermez.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Dizinler özelliği  
 @No__t_0 özelliği, glif belirtimlerinin bir dizesidir. Bir karakter dizisinin tek bir küme olarak ayarlandığı yerlerde, kümedeki ilk glifin belirtimi, küme oluşturmak için kaç karakter ve kaç tane kod noktasının birleştirildiği hakkında bir belirtimdir. @No__t_0 özelliği aşağıdaki özellikleri tek bir dizede toplar.  
  
- Glif dizinleri  
  
- Glif öncelikli genişlikleri  
  
- Glif eki vektörlerini birleştirme  
  
- Kod noktalarından karakterlere karakter eşleme  
  
- Glif bayrakları  
  
 Her glif belirtiminin aşağıdaki biçimi vardır.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Glif ölçümleri  
 Her glif, diğer <xref:System.Windows.Documents.Glyphs> ' la nasıl hizalanacağını belirten ölçümleri tanımlar. Aşağıdaki grafik iki farklı karakter karakterlerinin çeşitli tipografik kalitelerini tanımlar.  
  
 ![Glif ölçümlerinin Diagraf](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Glif biçimlendirmesi  
 Aşağıdaki kod örneği, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Documents.Glyphs> öğenin çeşitli özelliklerinin nasıl kullanılacağını gösterir.  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de Tipografi](typography-in-wpf.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Metin](optimizing-performance-text.md)
