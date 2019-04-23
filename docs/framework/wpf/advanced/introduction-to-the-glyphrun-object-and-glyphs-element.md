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
ms.openlocfilehash: 0e5ec2b89f015c7e061b59fea755eb368f1ac7a1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341055"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>GlyphRun Nesnesi ve Karakter Öğesine Giriş
Bu konu başlığı altında açıklanır <xref:System.Windows.Media.GlyphRun> nesne ve <xref:System.Windows.Documents.Glyphs> öğesi.  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>GlyphRun giriş  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Glif düzeyinde biçimlendirme doğrudan erişimle dahil olmak üzere gelişmiş destek sağlar <xref:System.Windows.Documents.Glyphs> kesebilir ve metin biçimlendirme sonra devam etmek isteyen müşteriler için. Bu özellikler, aşağıdaki senaryolardan her işleme gereksinimleri için farklı metin kritik destek sağlar.  
  
1. Sabit biçim belgeleri ekran görüntüsü.  
  
2. Yazdırma senaryoları.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir cihaz yazıcı dili olarak.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Çıktı, önceki yazıcı sürücülerini [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] sabit biçimde uygulamalar.  
  
    -   Yazdırma Biriktiricisi biçimi.  
  
3. Önceki sürümlerini istemciler dahil olmak üzere sabit biçimli belge gösterimi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve diğer bilgi işlem cihazları.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çeşitli öğeler için genel yerleşimi sağlar ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] gibi senaryoları <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.TextBlock>. Düzen hakkında daha fazla bilgi ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları için bkz: [WPF'de tipografi](typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>GlyphRun Nesnesi  
 <xref:System.Windows.Media.GlyphRun> Nesnesini temsil eder bir karakter dizisi tek bir yüz tek bir boyutta ve tek bir işleme bir stil ile tek bir yazı tipi.  
  
 <xref:System.Windows.Media.GlyphRun> Glif gibi her iki yazı tipi ayrıntılarını içeren <xref:System.Windows.Documents.Glyphs.Indices%2A> ve tek tek karakter konumları. Ayrıca orijinal içerir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] noktaları çalıştırma karakter simgesi arabellek uzaklığı eşleme bilgileri ve karakter başına ve simge başına bayrakları, oluşturulan kod.  
  
 <xref:System.Windows.Media.GlyphRun> üst düzey karşılık gelen <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs> öğe ağacı ve kullanılabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] temsil etmek için işaretleme <xref:System.Windows.Media.GlyphRun> çıktı.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Karakter öğesine  
 <xref:System.Windows.Documents.Glyphs> Öğesi çıktısını temsil eder bir <xref:System.Windows.Media.GlyphRun> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Aşağıdaki biçimlendirme sözdizimi tanımlamak için kullanılan <xref:System.Windows.Documents.Glyphs> öğesi.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Aşağıdaki özellik tanımları örnek biçimlendirmede ilk dört özniteliğine karşılık gelir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Bir kaynak tanımlayıcısı belirtir: dosya adı, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], ya da uygulama .exe veya kapsayıcı kaynak başvurusu.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Yazı tipi boyutunu çizim yüzeyi birimleri (varsayılan.96 inç olarak) belirtir.|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Kalın ve italik stil bayrakları belirtir.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Çift yönlü Düzen düzeyini belirtir. Tek sayılı ve sıfır değerleri soldan sağa düzen; kapsıyor. Tek sayılı değerleri sağdan sola düzen kapsıyor.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Dizinleri özelliği  
 <xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği karakter belirtimleri dizesidir. Glyphs dizisini tek bir küme oluşturur. Burada, kümedeki ilk karakter belirtimi kaç karakter belirtimi ve kümeyi oluşturmak için kaç tane kod noktaları birleştirmek gelmelidir. <xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği bir dize içinde aşağıdaki özellikleri toplar.  
  
-   Simge dizinleri  
  
-   Karakter öncelikli genişlikler  
  
-   Karakter eki vektörlerini birleştirme  
  
-   Glif kod noktaları küme eşleme  
  
-   Glif bayrakları  
  
 Her karakter belirtimi aşağıdaki biçime sahiptir.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Glif ölçümleri  
 Her karakter, birbirleriyle nasıl hizalandığını belirtin ölçümleri tanımlar <xref:System.Windows.Documents.Glyphs>. Aşağıdaki grafikte, çeşitli tipografik nitelikleri iki farklı simge karakteri tanımlar.  
  
 ![Karakter ölçümleri diyagramı](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Karakter biçimlendirme  
 Aşağıdaki kod örneği, çeşitli özelliklerinin nasıl kullanılacağını gösterir <xref:System.Windows.Documents.Glyphs> öğesinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de Tipografi](typography-in-wpf.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Metin](optimizing-performance-text.md)
