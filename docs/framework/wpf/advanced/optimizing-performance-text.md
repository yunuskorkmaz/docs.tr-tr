---
title: 'Performansı İyileştirme: Metin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rendering text [WPF]
- hyperlinks [WPF]
- formatted text [WPF]
- text [WPF], performance
- glyphs [WPF]
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
ms.openlocfilehash: 3e729458538353499f27f95ea2ca37fea1335238
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740348"
---
# <a name="optimizing-performance-text"></a>Performansı İyileştirme: Metin

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Özellik zengin [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] denetimleri kullanılarak metin içeriğinin sunumu için destek içerir. Genel olarak, metin işlemesini üç katmanda ayırabilirsiniz:

1. <xref:System.Windows.Documents.Glyphs> ve nesneleri doğrudan <xref:System.Windows.Media.GlyphRun> kullanma.

2. <xref:System.Windows.Media.FormattedText> nesnesini kullanma.

3. <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesneleri gibi üst düzey denetimleri kullanma.

Bu konu, metin işleme performans önerileri sağlar.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Glif düzeyinde metin işleme

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], biçimlendirmeden sonra metni kesme ve kalıcı hale getirmek isteyen müşteriler için <xref:System.Windows.Documents.Glyphs> doğrudan erişimi olan glif düzeyi biçimlendirme dahil gelişmiş metin desteği sağlar. Bu özellikler, aşağıdaki senaryolardan her birinde farklı metin işleme gereksinimleri için kritik destek sağlar.

- Sabit biçimli belgelerin ekran görüntüsü.

- Yazdırma senaryoları.

  - cihaz yazıcı dili olarak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].

  - Microsoft XPS Belge Yazıcısı.

  - Önceki yazıcı sürücüleri, Win32 uygulamalarından sabit biçime çıkış.

  - Yazdırma kuyruğu biçimi.

- Önceki Windows sürümleri ve diğer bilgi işlem cihazlarının istemcileri de dahil olmak üzere, sabit biçimli belge temsili.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun>, sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.TextBlock>gibi genel düzen ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] senaryolar için birkaç öğe sağlar. Düzen ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolar hakkında daha fazla bilgi için [WPF 'de tipografi](typography-in-wpf.md)'e bakın.

Aşağıdaki örneklerde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir <xref:System.Windows.Documents.Glyphs> nesnesinin özelliklerinin nasıl tanımlanacağı gösterilmektedir. <xref:System.Windows.Documents.Glyphs> nesnesi, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir <xref:System.Windows.Media.GlyphRun> çıkışını temsil eder. Örneklerde, yerel bilgisayardaki **c:\Windows\Fonts** klasöründe Arial, Courier New ve Times New Roman yazı tiplerinin yüklendiği varsayılır.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>DrawGlyphRun kullanma

Özel denetiminiz varsa ve glifleri işlemek istiyorsanız <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> yöntemini kullanın.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Media.FormattedText> nesnesinin kullanımı aracılığıyla özel metin biçimlendirmesi için alt düzey hizmetler de sağlar. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işlemenin en verimli yolu, <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun>kullanarak glif düzeyinde metin içeriği oluşturmaktan oluşur. Ancak, bu verimliliğin maliyeti, <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument>gibi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] denetimlerinin yerleşik özellikleri olan zengin metin biçimlendirmesinin kullanımı kolay bir işlemdir.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>FormattedText nesnesi

<xref:System.Windows.Media.FormattedText> nesnesi, metin içindeki her karakterin ayrı ayrı biçimlendirilebileceği çok satırlı metin çizmenizi sağlar. Daha fazla bilgi için bkz. [biçimli metin çizme](drawing-formatted-text.md).

Biçimli metin oluşturmak için, bir <xref:System.Windows.Media.FormattedText> nesnesi oluşturmak üzere <xref:System.Windows.Media.FormattedText.%23ctor%2A> oluşturucusunu çağırın. İlk biçimlendirilmiş metin dizesini oluşturduktan sonra bir dizi biçimlendirme stili uygulayabilirsiniz. Uygulamanız kendi yerleşimini uygulamak isterse, <xref:System.Windows.Media.FormattedText> nesnesi, <xref:System.Windows.Controls.TextBlock>gibi bir denetim kullanmaktan daha iyi bir seçenektir. <xref:System.Windows.Media.FormattedText> nesnesi hakkında daha fazla bilgi için bkz. [biçimli metin çizme](drawing-formatted-text.md) .

<xref:System.Windows.Media.FormattedText> nesnesi alt düzey metin biçimlendirme yeteneği sağlar. Bir veya daha fazla karaktere birden çok biçimlendirme stili uygulayabilirsiniz. Örneğin, metindeki ilk beş karakterin biçimlendirmesini değiştirmek için hem <xref:System.Windows.Media.FormattedText.SetFontSize%2A> hem de <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> yöntemlerini çağırabilirsiniz.

Aşağıdaki kod örneği bir <xref:System.Windows.Media.FormattedText> nesnesi oluşturur ve onu işler.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument, TextBlock ve Label denetimleri

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ekrana metin çizme için birden çok denetim içerir. Her denetim farklı bir senaryoya yöneliktir ve kendi özellik ve kısıtlama listesine sahiptir.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument, performansı TextBlock veya Label 'tan daha fazla etkiler

Genellikle, bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]kısa bir cümle gibi sınırlı metin desteği gerektiğinde <xref:System.Windows.Controls.TextBlock> öğesi kullanılmalıdır. <xref:System.Windows.Controls.Label>, en az metin desteği gerekli olduğunda kullanılabilir. <xref:System.Windows.Documents.FlowDocument> öğesi, zengin içerik sunumunu destekleyen yeniden Flowable belgeler için bir kapsayıcıdır ve bu nedenle, <xref:System.Windows.Controls.TextBlock> veya <xref:System.Windows.Controls.Label> denetimleri kullanmaktan daha yüksek bir performans etkisi vardır.

<xref:System.Windows.Documents.FlowDocument>hakkında daha fazla bilgi için bkz. [Flow belgesine genel bakış](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>FlowDocument 'de TextBlock kullanmaktan kaçının

<xref:System.Windows.Controls.TextBlock> öğesi <xref:System.Windows.UIElement>türetilir. <xref:System.Windows.Documents.Run> öğesi, <xref:System.Windows.UIElement>türetilmiş bir nesneden daha az maliyetli olan <xref:System.Windows.Documents.TextElement>türetilir. Mümkün olduğunda, bir <xref:System.Windows.Documents.FlowDocument>metin içeriğini görüntülemek için <xref:System.Windows.Controls.TextBlock> yerine <xref:System.Windows.Documents.Run> kullanın.

Aşağıdaki biçimlendirme örneği, bir <xref:System.Windows.Documents.FlowDocument>metin içeriğini ayarlamanın iki yolunu gösterir:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Metin özelliklerini ayarlamak için çalıştırma kullanmaktan kaçının

Genel olarak, bir <xref:System.Windows.Controls.TextBlock> içinde <xref:System.Windows.Documents.Run> kullanılması, hiç açık bir <xref:System.Windows.Documents.Run> nesnesi kullanmaktan daha yoğun bir performans açısından daha hızlıdır. Metin özelliklerini ayarlamak için bir <xref:System.Windows.Documents.Run> kullanıyorsanız, bu özellikleri doğrudan <xref:System.Windows.Controls.TextBlock> üzerinde ayarlayın.

Aşağıdaki biçimlendirme örneği, bir metin özelliğini ayarlamanın iki yolunu gösterir, bu durumda <xref:System.Windows.Controls.TextBlock.FontWeight%2A> özelliği:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

Aşağıdaki tabloda, açık bir <xref:System.Windows.Documents.Run>olmayan 1000 <xref:System.Windows.Controls.TextBlock> nesneleri görüntüleme maliyeti gösterilmektedir.

|**TextBlock türü**|**Oluşturma zamanı (MS)**|**İşleme süresi (MS)**|
|------------------------|------------------------------|----------------------------|
|Çalışma ayarı metin özellikleri|146|540|
|TextBlock ayarı metin özellikleri|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Label. Content özelliğine veri bağlamayı önleyin

Bir <xref:System.String> kaynağından sık sık güncellenen bir <xref:System.Windows.Controls.Label> nesnesine sahip olduğunuz bir senaryoyu düşünün. Veri <xref:System.Windows.Controls.Label> öğenin <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini <xref:System.String> kaynak nesnesine bağladığınızda, düşük performansla karşılaşabilirsiniz. Kaynak <xref:System.String> her güncelleştirilişinde, eski <xref:System.String> nesne atılır ve yeni bir <xref:System.String> yeniden oluşturulur. çünkü bir <xref:System.String> nesnesi sabittir, değiştirilemez. Bu, sırasıyla, <xref:System.Windows.Controls.Label> nesnesinin <xref:System.Windows.Controls.ContentPresenter> eski içeriğini atıp yeni <xref:System.String>göstermek için yeni içeriği yeniden oluşturmasına neden olur.

Bu soruna yönelik çözüm basittir. <xref:System.Windows.Controls.Label> özel bir <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> değere ayarlanmamışsa, <xref:System.Windows.Controls.Label> bir <xref:System.Windows.Controls.TextBlock> ile değiştirin ve <xref:System.Windows.Controls.TextBlock.Text%2A> özelliğini kaynak dizeye bağlayın.

|**Veri bağlantılı özelliği**|**Güncelleştirme zamanı (MS)**|
|-----------------------------|----------------------------|
|Etiket. Içerik|835|
|TextBlock. Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Köprü

<xref:System.Windows.Documents.Hyperlink> nesnesi, akış içeriği içinde köprüler barındırmanıza olanak sağlayan satır içi düzey bir akış içerik öğesidir.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Köprüleri tek bir TextBlock nesnesinde birleştirme

Birden çok <xref:System.Windows.Documents.Hyperlink> öğesinin kullanımını aynı <xref:System.Windows.Controls.TextBlock>birlikte gruplayarak iyileştirebilirsiniz. Bu, uygulamanızda oluşturduğunuz nesne sayısını en aza indirmenize yardımcı olur. Örneğin, aşağıdakiler gibi birden çok köprü görüntülenmesini isteyebilirsiniz:

Msn ev &#124; ağım

Aşağıdaki biçimlendirme örneği, köprüleri göstermek için kullanılan birden çok <xref:System.Windows.Controls.TextBlock> öğesini gösterir:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

Aşağıdaki biçimlendirme örneği köprüleri, bu kez tek bir <xref:System.Windows.Controls.TextBlock>kullanarak görüntülemenin daha verimli bir yolunu gösterir:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Yalnızca MouseEnter olaylarında köprülerde alt çizgiler gösteriliyor

Bir <xref:System.Windows.TextDecoration> nesnesi, metne ekleyebileceğiniz görsel veya çok büyük bir yer olabilir; Ancak, örneği oluşturma performansı yoğun olabilir. <xref:System.Windows.Documents.Hyperlink> öğelerinden oluşan kapsamlı bir kullanım yaparsanız, yalnızca bir olayı tetiklerken, <xref:System.Windows.ContentElement.MouseEnter> olayı gibi bir alt çizgi göstermeyi düşünün. Daha fazla bilgi için bkz. [bir köprünün altı çizili olup olmadığını belirtme](how-to-specify-whether-a-hyperlink-is-underlined.md).

Aşağıdaki görüntüde, MouseEnter olayının altı çizili köprü nasıl tetiklediği gösterilmektedir:

![Textsüslemeleri görüntüleyen köprüler](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

Aşağıdaki biçimlendirme örneği, altı çizili olmadan ve ile tanımlanmış bir <xref:System.Windows.Documents.Hyperlink> gösterir:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

Aşağıdaki tabloda, 1000 <xref:System.Windows.Documents.Hyperlink> öğelerinin alt çizgiyle ve altı çizili olmadan görüntülenmesine yönelik performans maliyeti gösterilmektedir.

|**Bağlanan**|**Oluşturma zamanı (MS)**|**İşleme süresi (MS)**|
|-------------------|------------------------------|----------------------------|
|Altı çizili|289|1130|
|Altı çizili olmadan|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Metin biçimlendirme özellikleri

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Otomatik hecelere yönelik zengin metin biçimlendirme hizmetleri sağlar. Bu hizmetler, uygulama performansını etkileyebilir ve yalnızca gerektiğinde kullanılmalıdır.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Gereksiz heceleme kullanımını önleyin

Otomatik heceleme metin satırları için kısa çizgi kesme noktaları bulur ve <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesnelerinde satırlar için ek kesme konumlarına izin verir. Varsayılan olarak, otomatik heceleme özelliği bu nesnelerde devre dışıdır. Nesnenin ısshationenabled özelliğini `true`olarak ayarlayarak bu özelliği etkinleştirebilirsiniz. Ancak, bu özelliği etkinleştirmek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşen nesne modeli (COM) birlikte çalışabilirliğine neden olur ve bu da uygulama performansını etkileyebilir. İhtiyaç duymadığınız takdirde otomatik hecelemeyi kullanmanız önerilir.

### <a name="use-figures-carefully"></a>Rakamları dikkatle kullanın

Bir <xref:System.Windows.Documents.Figure> öğesi, bir içerik sayfasında mutlak olarak konumlandırılmış akış içeriğinin bir kısmını temsil eder. Bazı durumlarda <xref:System.Windows.Documents.Figure>, konumu zaten değiştirilmiş içerikle çakışıyorsa sayfanın tamamının otomatik olarak yeniden biçimlendirmeye neden olabilir. Her birinin yanındaki <xref:System.Windows.Documents.Figure> öğelerini gruplandırarak veya sabit bir sayfa boyutu senaryosunda içeriğin üst kısmına yaklaşarak, gereksiz yeniden biçimlendirme olasılığını en aza indirmenize olanak sağlayabilirsiniz.

### <a name="optimal-paragraph"></a>En iyi paragraf

<xref:System.Windows.Documents.FlowDocument> nesnesinin en iyi paragraf özelliği, beyaz alanın mümkün olduğunca eşit şekilde dağıtılması için paragrafları yerleştirir. Varsayılan olarak, en uygun paragraf özelliği devre dışıdır. Nesnenin <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> özelliğini `true`olarak ayarlayarak bu özelliği etkinleştirebilirsiniz. Ancak, bu özelliğin etkinleştirilmesi uygulama performansını etkiler. İhtiyaç duymadığınız takdirde en iyi paragraf özelliğini kullanmanız önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF Uygulama Performansını İyileştirme](optimizing-wpf-application-performance.md)
- [Uygulama Performansını Planlama](planning-for-application-performance.md)
- [Donanımdan Yararlanma](optimizing-performance-taking-advantage-of-hardware.md)
- [Düzen ve Tasarım](optimizing-performance-layout-and-design.md)
- [2B Grafikleri ve Görüntüleme](optimizing-performance-2d-graphics-and-imaging.md)
- [Nesne Davranışı](optimizing-performance-object-behavior.md)
- [Uygulama Kaynakları](optimizing-performance-application-resources.md)
- [Veri Bağlama](optimizing-performance-data-binding.md)
- [Diğer Performans Önerileri](optimizing-performance-other-recommendations.md)
