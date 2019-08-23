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
ms.openlocfilehash: 318972c20f6461489226e19b3e517ba0ac069b28
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933358"
---
# <a name="optimizing-performance-text"></a>Performansı İyileştirme: Metin

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Özellik zengin [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] denetimlerin kullanımı aracılığıyla metin içeriği sunumu için destek içerir. Genel olarak, metin işlemesini üç katmanda ayırabilirsiniz:

1. <xref:System.Windows.Documents.Glyphs> Ve<xref:System.Windows.Media.GlyphRun> nesnelerini doğrudan kullanma.

2. <xref:System.Windows.Media.FormattedText> Nesnesini kullanarak.

3. <xref:System.Windows.Controls.TextBlock> Ve<xref:System.Windows.Documents.FlowDocument> nesneleri gibi üst düzey denetimleri kullanma.

Bu konu, metin işleme performans önerileri sağlar.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Glif düzeyinde metin işleme

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]biçimlendirmeden sonra metni kesme ve kalıcı hale getirmek isteyen müşterilere doğrudan erişim <xref:System.Windows.Documents.Glyphs> ile glif düzeyinde biçimlendirme dahil gelişmiş metin desteği sağlar. Bu özellikler, aşağıdaki senaryolardan her birinde farklı metin işleme gereksinimleri için kritik destek sağlar.

- Sabit biçimli belgelerin ekran görüntüsü.

- Yazdırma senaryoları.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir cihaz yazıcı dili olarak.

  - Microsoft XPS Belge Yazıcısı.

  - Önceki yazıcı sürücüleri, [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalardan Sabit biçime çıkış.

  - Yazdırma kuyruğu biçimi.

- Önceki Windows sürümleri ve diğer bilgi işlem cihazlarının istemcileri de dahil olmak üzere, sabit biçimli belge temsili.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs>ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<xref:System.Windows.Controls.Label> , [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ve<xref:System.Windows.Controls.TextBlock>gibi genel düzen ve senaryolar için birkaç öğe sağlar. Düzen ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryolar hakkında daha fazla bilgi için bkz. [WPF 'de tipografi](typography-in-wpf.md).

Aşağıdaki örneklerde içindeki <xref:System.Windows.Documents.Glyphs> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir nesnesinin özelliklerinin nasıl tanımlanacağı gösterilmektedir. Nesnesi, <xref:System.Windows.Media.GlyphRun> içindeki[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]çıktısınıtemsileder. <xref:System.Windows.Documents.Glyphs> Örneklerde, yerel bilgisayardaki **c:\Windows\Fonts** klasöründe Arial, Courier New ve Times New Roman yazı tiplerinin yüklendiği varsayılır.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>DrawGlyphRun kullanma

Özel denetiminiz varsa ve glifleri işlemek istiyorsanız <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> yöntemini kullanın.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca <xref:System.Windows.Media.FormattedText> nesnenin kullanımı aracılığıyla özel metin biçimlendirmesi için alt düzey hizmetler sağlar. İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işlemenin en verimli yolu, ve <xref:System.Windows.Media.GlyphRun>kullanarak <xref:System.Windows.Documents.Glyphs> glif düzeyinde metin içeriği oluşturmaktan oluşur. Ancak, bu verimlilik maliyeti, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument>gibi denetimlerin yerleşik özellikleri olan zengin metin biçimlendirmesinin kullanımı kolay bir işlemdir.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>FormattedText nesnesi

<xref:System.Windows.Media.FormattedText> Nesnesi, metin içindeki her karakterin ayrı ayrı biçimlendirilebileceği çok satırlı metin çizmenizi sağlar. Daha fazla bilgi için bkz. [biçimli metin çizme](drawing-formatted-text.md).

Biçimlendirilen metin oluşturmak için, bir <xref:System.Windows.Media.FormattedText.%23ctor%2A> <xref:System.Windows.Media.FormattedText> nesnesi oluşturmak için oluşturucuyu çağırın. İlk biçimlendirilmiş metin dizesini oluşturduktan sonra bir dizi biçimlendirme stili uygulayabilirsiniz. Uygulamanız kendi yerleşimini <xref:System.Windows.Media.FormattedText> uygulamak istiyorsa,, gibi bir denetim <xref:System.Windows.Controls.TextBlock>kullanmaktan daha iyi bir seçenektir. <xref:System.Windows.Media.FormattedText> Nesnesi hakkında daha fazla bilgi için bkz. [biçimli metin çizme](drawing-formatted-text.md) .

<xref:System.Windows.Media.FormattedText> Nesnesi alt düzey metin biçimlendirme yeteneği sağlar. Bir veya daha fazla karaktere birden çok biçimlendirme stili uygulayabilirsiniz. Örneğin, metin içindeki ilk beş karakterin biçimlendirmesini <xref:System.Windows.Media.FormattedText.SetFontSize%2A> değiştirmek <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> için ve yöntemlerini çağırabilirsiniz.

Aşağıdaki kod örneği bir <xref:System.Windows.Media.FormattedText> nesnesi oluşturur ve onu işler.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument, TextBlock ve Label denetimleri

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekrana metin çizme için birden çok denetim içerir. Her denetim farklı bir senaryoya yöneliktir ve kendi özellik ve kısıtlama listesine sahiptir.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument, performansı TextBlock veya Label 'tan daha fazla etkiler

Genel <xref:System.Windows.Controls.TextBlock> olarak, öğesinde kısa bir cümle [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]gibi sınırlı metin desteği gerektiğinde öğesi kullanılmalıdır. <xref:System.Windows.Controls.Label>en az metin desteği gerekli olduğunda kullanılabilir. Öğesi, zengin içerik sunumunu destekleyen ve bu nedenle, <xref:System.Windows.Controls.TextBlock> veya <xref:System.Windows.Controls.Label> denetimlerini kullanmaktan daha fazla performans etkisi olan, yeniden Flowable belgeler için bir kapsayıcıdır. <xref:System.Windows.Documents.FlowDocument>

Hakkında <xref:System.Windows.Documents.FlowDocument>daha fazla bilgi için bkz. [Flow belgesine genel bakış](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>FlowDocument 'de TextBlock kullanmaktan kaçının

<xref:System.Windows.Controls.TextBlock> Öğesi öğesinden<xref:System.Windows.UIElement>türetilir. Öğesi, türetilmiş bir <xref:System.Windows.Documents.TextElement> <xref:System.Windows.UIElement>nesneden daha az maliyetli olan öğesinden türetilir. <xref:System.Windows.Documents.Run> Mümkün olduğunda, ' <xref:System.Windows.Documents.Run> deki metin <xref:System.Windows.Controls.TextBlock> içeriğini <xref:System.Windows.Documents.FlowDocument>görüntülemek için yerine kullanın.

Aşağıdaki biçimlendirme örneği, içindeki <xref:System.Windows.Documents.FlowDocument>metin içeriğini ayarlamanın iki yolunu gösterir:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Metin özelliklerini ayarlamak için çalıştırma kullanmaktan kaçının

Genel olarak, bir <xref:System.Windows.Documents.Run> <xref:System.Windows.Controls.TextBlock> içinde bir kullanmak, açık <xref:System.Windows.Documents.Run> bir nesne kullanmaktan daha yoğun bir performans açısından daha hızlıdır. Metin özelliklerini ayarlamak için bir <xref:System.Windows.Documents.Run> kullanıyorsanız, <xref:System.Windows.Controls.TextBlock> bunun yerine doğrudan bu özellikleri ayarlayın.

Aşağıdaki biçimlendirme örneği, bir metin özelliğini ayarlamanın iki yolunu gösterir, bu durumda <xref:System.Windows.Controls.TextBlock.FontWeight%2A> özelliği:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

Aşağıdaki tabloda, açık <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.Run>ve olmadan 1000 nesnelerinin görüntüleme maliyeti gösterilmektedir.

|**TextBlock türü**|**Oluşturma zamanı (MS)**|**İşleme süresi (MS)**|
|------------------------|------------------------------|----------------------------|
|Çalışma ayarı metin özellikleri|146|540|
|TextBlock ayarı metin özellikleri|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Label. Content özelliğine veri bağlamayı önleyin

<xref:System.Windows.Controls.Label> Bir<xref:System.String> kaynaktan sık güncellenen bir nesneniz olan bir senaryo düşünün. Veri, <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.ContentControl.Content%2A> öğenin özelliğini<xref:System.String> kaynak nesneye bağladığınızda, performansı düşük olabilir. Kaynak <xref:System.String> her güncelleştirildiği zaman, eski <xref:System.String> nesne atılır ve yeni <xref:System.String> bir yeniden oluşturulur, çünkü bir <xref:System.String> nesne sabit olduğu için değiştirilemez. Bu, buna karşılık, <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.Label> nesnesinin eski içeriğini atıp yeni içeriği yeniden oluşturmak için yeni <xref:System.String>içerik oluşturmasına neden olur.

Bu soruna yönelik çözüm basittir. <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock.Text%2A> Özel bir değere ayarlanmamışsa ,<xref:System.Windows.Controls.TextBlock> öğesini ile ve veri bağlama özelliğini kaynak dizeye değiştirin. <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.Label>

|**Veri bağlantılı özelliği**|**Güncelleştirme zamanı (MS)**|
|-----------------------------|----------------------------|
|Etiket. Içerik|835|
|TextBlock. Text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Köprü

<xref:System.Windows.Documents.Hyperlink> Nesnesi, akış içeriği içinde köprüler barındırmanıza olanak sağlayan satır içi düzey bir akış içerik öğesidir.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Köprüleri tek bir TextBlock nesnesinde birleştirme

Birden çok <xref:System.Windows.Documents.Hyperlink> öğenin kullanımını aynı <xref:System.Windows.Controls.TextBlock>şekilde bir araya getirerek iyileştirebilirsiniz. Bu, uygulamanızda oluşturduğunuz nesne sayısını en aza indirmenize yardımcı olur. Örneğin, aşağıdakiler gibi birden çok köprü görüntülenmesini isteyebilirsiniz:

Msn ev &#124; ağım

Aşağıdaki biçimlendirme örneği, köprüleri göstermek <xref:System.Windows.Controls.TextBlock> için kullanılan birden çok öğeyi göstermektedir:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

Aşağıdaki biçimlendirme örneği, bu kez, tek <xref:System.Windows.Controls.TextBlock>bir kullanarak köprüleri görüntülemenin daha verimli bir yolunu göstermektedir:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Yalnızca MouseEnter olaylarında köprülerde alt çizgiler gösteriliyor

Bir <xref:System.Windows.TextDecoration> nesne, metne ekleyebileceğiniz görsel bir görüntü oluşturur; ancak, örneği oluşturmak için performansı yoğun hale getirebilirsiniz. <xref:System.Windows.Documents.Hyperlink> Öğelerin yoğun kullanımını yaparsanız, <xref:System.Windows.ContentElement.MouseEnter> olay gibi yalnızca bir olay tetiklendiğinde alt çizgiyi göstermeyi düşünün. Daha fazla bilgi için bkz. [bir köprünün altı çizili olup olmadığını belirtme](how-to-specify-whether-a-hyperlink-is-underlined.md).

Aşağıdaki görüntüde, MouseEnter olayının altı çizili köprü nasıl tetiklediği gösterilmektedir:

![Textsüslemeleri görüntüleyen köprüler](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

Aşağıdaki biçimlendirme örneği, ile tanımlanmış <xref:System.Windows.Documents.Hyperlink> bir ve altı çizili olmayan bir şekilde gösterir:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

Aşağıdaki tabloda, altı çizili olmayan 1000 <xref:System.Windows.Documents.Hyperlink> öğelerinin görüntülenmesi için performans maliyeti gösterilmektedir.

|**Bağlanan**|**Oluşturma zamanı (MS)**|**İşleme süresi (MS)**|
|-------------------|------------------------------|----------------------------|
|Altı çizili|289|1130|
|Altı çizili olmadan|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Metin biçimlendirme özellikleri

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Otomatik hecelere yönelik zengin metin biçimlendirme hizmetleri sağlar. Bu hizmetler, uygulama performansını etkileyebilir ve yalnızca gerektiğinde kullanılmalıdır.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Gereksiz heceleme kullanımını önleyin

Otomatik heceleme metin satırları için kısa çizgi kesme noktaları bulur ve <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesnelerinde çizgiler için ek kesme konumlarına izin verir. Varsayılan olarak, otomatik heceleme özelliği bu nesnelerde devre dışıdır. Nesnenin ısshationenabled özelliğini olarak `true`ayarlayarak bu özelliği etkinleştirebilirsiniz. Ancak, bu özelliğin etkinleştirilmesi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama performansını etkileyebilecek bileşen nesne modeli (com) birlikte çalışabilirliğini başlatmalarına neden olur. İhtiyaç duymadığınız takdirde otomatik hecelemeyi kullanmanız önerilir.

### <a name="use-figures-carefully"></a>Rakamları dikkatle kullanın

Bir <xref:System.Windows.Documents.Figure> öğe, bir içerik sayfasında mutlak olarak konumlandırılmış akış içeriğinin bir kısmını temsil eder. Bazı durumlarda, konumu zaten <xref:System.Windows.Documents.Figure> değiştirilmiş içerikle çakışıyorsa bir sayfanın tamamının otomatik olarak yeniden biçimlendirmeye neden olabilir. Birbirini izleyen veya bir sabit sayfa boyutu senaryosunda içeriğin üst kısmına <xref:System.Windows.Documents.Figure> yaklaşarak, gereksiz yeniden biçimlendirme olasılığını en aza indirmenize olanak sağlayabilirsiniz.

### <a name="optimal-paragraph"></a>En iyi paragraf

<xref:System.Windows.Documents.FlowDocument> Nesnenin en iyi paragraf özelliği, beyaz alanın mümkün olduğunca eşit şekilde dağıtılması için paragrafları yerleştirir. Varsayılan olarak, en uygun paragraf özelliği devre dışıdır. Nesnenin <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> özelliğini olarak `true`ayarlayarak bu özelliği etkinleştirebilirsiniz. Ancak, bu özelliğin etkinleştirilmesi uygulama performansını etkiler. İhtiyaç duymadığınız takdirde en iyi paragraf özelliğini kullanmanız önerilir.

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
