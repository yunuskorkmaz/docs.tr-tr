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
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181958"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a>GlyphRun Nesnesi ve Karakter Öğesine Giriş
Bu konu <xref:System.Windows.Media.GlyphRun> nesne ve <xref:System.Windows.Documents.Glyphs> öğeyi açıklar.  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a>GlyphRun'a Giriş  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]biçimlendirmeden sonra metni engellemek ve devam etmek isteyen <xref:System.Windows.Documents.Glyphs> müşterilere doğrudan erişim sağlayan glyph düzeyinde biçimlendirme dahil olmak üzere gelişmiş metin desteği sağlar. Bu özellikler, aşağıdaki senaryoların her birinde farklı metin oluşturma gereksinimleri için kritik destek sağlar.  
  
1. Sabit biçimli belgelerin ekran görüntüsü.  
  
2. Senaryoları yazdırın.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir aygıt yazıcı dili olarak.  
  
    - Microsoft XPS Belge Yazarı.  
  
    - Önceki yazıcı sürücüleri, Win32 uygulamalarından sabit formata çıktı.  
  
    - Makara biçimini yazdırın.  
  
3. Windows'un önceki sürümleri ve diğer bilgi işlem aygıtları için istemciler de dahil olmak üzere sabit biçimli belge gösterimi.  
  
> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]gibi genel düzen ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryolar <xref:System.Windows.Controls.Label> için <xref:System.Windows.Controls.TextBlock>çeşitli öğeler sağlar. Düzen ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolar hakkında daha fazla bilgi için [WPF'deki Tipografi'ye](typography-in-wpf.md)bakın.  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a>GlyphRun Nesnesi  
 Nesne, <xref:System.Windows.Media.GlyphRun> tek bir boyutta ve tek bir işleme stiliyle tek bir yazı tipinin tek bir yüzünden gelen bir glifler dizisini temsil eder.  
  
 <xref:System.Windows.Media.GlyphRun>glyph ve bireysel glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> pozisyonları gibi her iki yazı tipi ayrıntılarını içerir. Ayrıca, çalıştırmanın oluşturulduğu özgün Unicode kod noktaları, karakterden gph arabelleği eşleme bilgilerini ve karakter başına ve gph başına bayrakları içerir.  
  
 <xref:System.Windows.Media.GlyphRun>ilgili bir üst <xref:System.Windows.FrameworkElement>düzey <xref:System.Windows.Documents.Glyphs>vardır. <xref:System.Windows.Documents.Glyphs>öğe ağacında ve çıktıyı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] temsil <xref:System.Windows.Media.GlyphRun> etmek için biçimlendirmede kullanılabilir.  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a>Glifler Elementi  
 Öğe <xref:System.Windows.Documents.Glyphs> bir <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]çıktısını temsil eder. Aşağıdaki biçimlendirme sözdizimi öğeyi <xref:System.Windows.Documents.Glyphs> açıklamak için kullanılır.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Aşağıdaki özellik tanımları örnek biçimlendirmedeki ilk dört özniteliklere karşılık gelir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|Bir kaynak tanımlayıcısı belirtir: dosya adı, Web üniforması kaynak tanımlayıcısı (URI) veya uygulama .exe veya kapsayıcıdaki kaynak başvurusu.|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|Çizim yüzey birimlerinde yazı tipi boyutunu belirtir (varsayılan değer 0,96 inçtir).|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|Kalın ve Italik stiller için bayrakları belirtir.|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|Çift yönlü düzen düzeyini belirtir. Çift numaralı ve sıfır değerleri soldan sağa düzeni ima; tek numaralı değerler sağdan sola düzeni ima.|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a>Endeks özelliği  
 Özellik, <xref:System.Windows.Documents.Glyphs.Indices%2A> bir dizi glyph belirtimidir. Bir dizi gliflerin tek bir küme oluşturduğu durumlarda, kümedeki ilk gliflerin belirtimi, kümeyi oluşturmak için kaç gifif ve kaç kod noktasının biraraya geldiğine göre önce gelir. Özellik, <xref:System.Windows.Documents.Glyphs.Indices%2A> aşağıdaki özellikleri tek bir dize de toplar.  
  
- Glyph endeksleri  
  
- Glyph ileri genişlikleri  
  
- Gph ek vektörlerinin birleştirilmesi  
  
- Kod noktalarından gliflere küme eşleme  
  
- Glyph bayrakları  
  
 Her gph belirtimi aşağıdaki forma sahiptir.  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a>Glyph Ölçümleri  
 Her glyph, diğerleriyle <xref:System.Windows.Documents.Glyphs>nasıl hizaladığını belirten ölçümler tanımlar. Aşağıdaki grafik, iki farklı gliflerin çeşitli tipografik özelliklerini tanımlar.  
  
 ![Gliflerin diyagrafı](./media/glyph-example.png "glyph_example")  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a>Glyphs Biçimlendirme  
 Aşağıdaki kod örneği, <xref:System.Windows.Documents.Glyphs> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]'deki öğenin çeşitli özelliklerinin nasıl kullanılacağını gösterir.  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF'de Tipografi](typography-in-wpf.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Metin](optimizing-performance-text.md)
