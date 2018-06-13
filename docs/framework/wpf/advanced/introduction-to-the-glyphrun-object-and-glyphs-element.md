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
ms.openlocfilehash: 5750177c03cf859ebb884c5774b7ded03fa60628
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547387"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>GlyphRun Nesnesi ve Karakter Öğesine Giriş
Bu konuda açıklanmaktadır <xref:System.Windows.Media.GlyphRun> nesne ve <xref:System.Windows.Documents.Glyphs> öğesi.  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a>GlyphRun'a  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] doğrudan erişimli karakter düzeyinde biçimlendirme dahil olmak üzere Gelişmiş metin desteği sağlar <xref:System.Windows.Documents.Glyphs> kesecek ve metin biçimlendirme sonra devam etmek isteyen müşteriler için. Bu özellikler, işleme gereksinimleri aşağıdaki senaryoların her biri için farklı metin kritik destek sağlar.  
  
1.  Sabit biçimli belgelerin ekran görüntüsü.  
  
2.  Yazdırma senaryoları.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir aygıt yazıcı dili olarak.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Çıktı önceki yazıcı sürücüleri [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalarından sabit biçimde.  
  
    -   Yazdırma biriktirme biçimi.  
  
3.  Önceki sürümlerinde istemciler dahil olmak üzere sabit biçimli belge gösterimi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve diğer programlama cihazları.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumları ve yazdırma senaryoları için tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Çeşitli öğeleri için genel yerleşimi sağlar ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] gibi senaryoları <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.TextBlock>. Düzen hakkında daha fazla bilgi ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları bkz [WPF'de tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a>GlyphRun Nesnesi  
 <xref:System.Windows.Media.GlyphRun> Nesne dizisi karakterlerin tek boyutta ve tek işleme stiliyle tek bir yazı tipinin tek bir yazıtipi temsil.  
  
 <xref:System.Windows.Media.GlyphRun> karakter gibi her iki yazı tipi ayrıntıları içerir <xref:System.Windows.Documents.Glyphs.Indices%2A> ve bireysel karakter konumları. Ayrıca özgün içerir [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] kod Çalıştır karakter simgesi arabellek uzaklığı eşleme bilgileri ve karakter olmayan ve simge başına bayrakları, üretilen noktaları.  
  
 <xref:System.Windows.Media.GlyphRun> üst düzey karşılık gelen <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>. <xref:System.Windows.Documents.Glyphs> öğe ağacı ve kullanılabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] temsil etmek için işaretleme <xref:System.Windows.Media.GlyphRun> çıktı.  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a>Karakterlerin öğesi  
 <xref:System.Windows.Documents.Glyphs> Öğesi çıktısını temsil eden bir <xref:System.Windows.Media.GlyphRun> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Aşağıdaki biçimlendirme sözdizimi tanımlamak için kullanılan <xref:System.Windows.Documents.Glyphs> öğesi.  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Aşağıdaki özellik tanımları örnek biçimlendirme ilk dört özniteliklerin karşılık gelir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Bir kaynak tanımlayıcısını belirtir: dosya adı, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], veya uygulama .exe veya kapsayıcısındaki kaynak başvurusu.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|(.96 inç varsayılandır) Yüzey birimlerindeki çizim yazı tipi boyutunu belirtir.|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Kalın ve italik stillerinde bayrakları belirtir.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Çift yönlü Düzen düzeyini belirtir. Tek sayılı ve sıfır değerleri soldan sağa düzeni belirtir; Tek sayılı değerler sağdan sola düzeni belirtir.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a>Dizinler özelliği  
 <xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği karakter belirtimleri dizesidir. Tek bir küme dizisi karakterlerin forms burada küme içindeki ilk karakter belirtimi belirtimi kaç karakterlerin ve kümeyi oluşturmak için kaç tane kod noktaları birleştirme tarafından gelmelidir. <xref:System.Windows.Documents.Glyphs.Indices%2A> Özelliği bir dize içinde aşağıdaki özellikleri toplar.  
  
-   Karakter dizinler  
  
-   Karakter öncelikli genişlikler  
  
-   Karakter eki vektörlerini birleştirme  
  
-   Karakterlerin kod noktaları küme eşleme  
  
-   Karakter bayrakları  
  
 Her karakter belirtimi aşağıdaki biçime sahiptir.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a>Karakter ölçümü  
 Her karakteri nasıl diğer hizalar belirtin ölçüleri tanımlar <xref:System.Windows.Documents.Glyphs>. Aşağıdaki grafikte iki farklı simge karakteri çeşitli tipografi niteliklerini tanımlar.  
  
 ![Karakter ölçümleri diyagramı](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a>Karakterlerin biçimlendirme  
 Aşağıdaki kod örneğinde çeşitli özelliklerini kullanmayı gösterir <xref:System.Windows.Documents.Glyphs> öğesinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF'de Tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Metin](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
