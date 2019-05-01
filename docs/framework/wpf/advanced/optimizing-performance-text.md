---
title: 'Performansı iyileştirme: Metin'
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
ms.openlocfilehash: 0cc1ac9adf40948a5109b37336d45a2be833e54f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032688"
---
# <a name="optimizing-performance-text"></a>Performansı iyileştirme: Metin
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kullanarak zengin metin içeriği sunumunu desteği içeren [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kontrol eder. Genel olarak, üç katmanda metin işleme ayırabilirsiniz:  
  
1. Kullanarak <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun> nesnelerini doğrudan.  
  
2. Kullanarak <xref:System.Windows.Media.FormattedText> nesne.  
  
3. Üst düzey denetimleri gibi kullanarak <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesneleri.  
  
 Bu konu, metin işleme performans önerileri sağlar.  

<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>Glif düzeyinde metin oluşturma  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Glif düzeyinde biçimlendirme doğrudan erişimle dahil olmak üzere gelişmiş destek sağlar <xref:System.Windows.Documents.Glyphs> kesebilir ve metin biçimlendirme sonra devam etmek isteyen müşteriler için. Bu özellikler, aşağıdaki senaryolardan her işleme gereksinimleri için farklı metin kritik destek sağlar.  
  
- Sabit biçim belgeleri ekran görüntüsü.  
  
- Yazdırma senaryoları.  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir cihaz yazıcı dili olarak.  
  
    - [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    - Çıktı, önceki yazıcı sürücülerini [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] sabit biçimde uygulamalar.  
  
    - Yazdırma Biriktiricisi biçimi.  
  
- Önceki sürümlerini istemciler dahil olmak üzere sabit biçimli belge gösterimi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve diğer bilgi işlem cihazları.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumu ve yazdırma senaryoları için tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] çeşitli öğeler için genel yerleşimi sağlar ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] gibi senaryoları <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.TextBlock>. Düzen hakkında daha fazla bilgi ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları için bkz: [WPF'de tipografi](typography-in-wpf.md).  
  
 Aşağıdaki örnekler özelliklerini tanımlamak nasıl bir <xref:System.Windows.Documents.Glyphs> nesnesine [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> Nesnesini çıktısını gösteren bir <xref:System.Windows.Media.GlyphRun> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Örneklerde Arial Courier yeni ve Times yeni Roman yazı tiplerinin yüklenir varsayılmaktadır **C:\WINDOWS\Fonts** yerel bilgisayarda klasör.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>DrawGlyphRun Kullanma  
 Özel denetiminiz varsa ve karakterleri işlemek, kullanmak istediğiniz <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> yöntemi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Özel metin biçimlendirmesi kullanımının düşük düzeyli hizmetleri de sağlar <xref:System.Windows.Media.FormattedText> nesne. En verimli şekilde işleme metin [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin içeriğini kullanarak glif düzeyinde oluşturarak olan <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun>. Ancak, bu verimlilik kaybı yerleşik özellikleri olan, kullanımı kolay zengin metin biçimlendirmesini maliyetidir, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] denetimleri gibi <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument>.  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>FormattedText nesnesi  
 <xref:System.Windows.Media.FormattedText> Nesne, metindeki her karakter ayrı ayrı biçimlendirilebilir, çok satırlı metin çizme olanak tanır. Daha fazla bilgi için [çizim biçimlendirilmiş metin](drawing-formatted-text.md).  
  
 Biçimlendirilmiş metin oluşturmak için arama <xref:System.Windows.Media.FormattedText.%23ctor%2A> oluşturmak için bir <xref:System.Windows.Media.FormattedText> nesne. İlk biçimlendirilmiş metin dizesi oluşturduktan sonra bir aralık stilleri biçimlendirme uygulayabilirsiniz. Uygulamanız kendi düzenini uygulamak isterse sonra <xref:System.Windows.Media.FormattedText> nesnedir gibi bir denetim kullanmaktan daha iyi bir seçenek <xref:System.Windows.Controls.TextBlock>. Daha fazla bilgi için <xref:System.Windows.Media.FormattedText> nesne, bkz: [çizim biçimlendirilmiş metin](drawing-formatted-text.md) .  
  
 <xref:System.Windows.Media.FormattedText> Nesnesi, alt düzey metin biçimlendirme yeteneği sağlar. Bir veya daha fazla karakterle birden çok biçimlendirme stil uygulayabilirsiniz. Örneğin, her ikisi de çağırabilirsiniz <xref:System.Windows.Media.FormattedText.SetFontSize%2A> ve <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> ilk beş karakterlerini biçimini değiştirmek için yöntem.  
  
 Aşağıdaki kod örneği oluşturur bir <xref:System.Windows.Media.FormattedText> nesne ve bunu işler.  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument TextBlock ve etiket denetimleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekrana metnin çizmek için birden fazla denetim içerir. Her denetim için farklı bir senaryo hedeflenen ve kendi listesi özellikler ve sınırlamalar vardır.  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument performans birden fazla TextBlock veya etiket etkiler  
 Genel olarak, <xref:System.Windows.Controls.TextBlock> öğesi sınırlı metin desteği kısa bir cümle gibi gerekli olduğunda kullanılmalıdır bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> en az metin desteği gerekli olduğunda kullanılabilir. <xref:System.Windows.Documents.FlowDocument> Öğesi içeriği zengin sunumu yeniden akışkan olabilen belgeler için bir kapsayıcıdır ve bu nedenle, kullanarak daha büyük bir performans etkisi olur <xref:System.Windows.Controls.TextBlock> veya <xref:System.Windows.Controls.Label> kontrol eder.  
  
 Daha fazla bilgi için <xref:System.Windows.Documents.FlowDocument>, bkz: [akış belgesine genel bakış](flow-document-overview.md).  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>FlowDocument içinde TextBlock kullanmaktan kaçının  
 <xref:System.Windows.Controls.TextBlock> Öğesi türetilen <xref:System.Windows.UIElement>. <xref:System.Windows.Documents.Run> Öğesi türetilen <xref:System.Windows.Documents.TextElement>, daha az masraflı olduğu bir <xref:System.Windows.UIElement>-türetilmiş bir nesneye. Mümkün olduğunda, kullanın <xref:System.Windows.Documents.Run> yerine <xref:System.Windows.Controls.TextBlock> içindeki metin içeriğini görüntülemek için bir <xref:System.Windows.Documents.FlowDocument>.  
  
 Aşağıdaki biçimlendirme örneği içinde metin içeriğini ayarlama iki yolunu gösterir bir <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>Metin özellikleri ayarlamak için Çalıştır'ı kullanarak kaçının  
 Genel olarak, kullanarak bir <xref:System.Windows.Documents.Run> içinde bir <xref:System.Windows.Controls.TextBlock> daha fazla performans açık bir kullanmadan daha yoğun olan <xref:System.Windows.Documents.Run> nesnesi. Kullanıyorsanız bir <xref:System.Windows.Documents.Run> metin özelliklerini ayarlamak için doğrudan bu özellikleri ayarlama <xref:System.Windows.Controls.TextBlock> yerine.  
  
 Aşağıdaki biçimlendirme örneği bu durumda, bir metin özelliğini ayarlayarak bu iki yolunu gösterir <xref:System.Windows.Controls.TextBlock.FontWeight%2A> özelliği:  
  
 [!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 Aşağıdaki tablo 1000 görüntüleme maliyetini gösterir <xref:System.Windows.Controls.TextBlock> nesneleri ve açık bir olmadan <xref:System.Windows.Documents.Run>.  
  
|**TextBlock türü**|**Oluşturma zamanı (ms)**|**İşleme süresi (ms)**|  
|------------------------|------------------------------|----------------------------|  
|Çalıştırma ayarı metin özellikleri|146|540|  
|TextBlock metin özelliklerini ayarlama|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Veri bağlama Label.Content özelliğine kaçının  
 Sahip olduğunuz bir senaryoyu düşünün bir <xref:System.Windows.Controls.Label> sık güncelleştirildiği nesne bir <xref:System.String> kaynak. Veri bağlama <xref:System.Windows.Controls.Label> öğenin <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğini <xref:System.String> kaynak nesnesi, kötü performansa karşılaşabilirsiniz. Her zaman kaynak <xref:System.String> güncelleştirilir, eski <xref:System.String> yoksayılır ve yeni bir nesne <xref:System.String> yeniden oluşturulur; çünkü bir <xref:System.String> nesne değişmez, değiştirilemez. Bu, buna neden <xref:System.Windows.Controls.ContentPresenter> , <xref:System.Windows.Controls.Label> eski içeriği atmak ve yeni görüntülemek için yeni içeriği yeniden oluşturmak için nesne <xref:System.String>.  
  
 Bu sorunun çözümü, basit bir işlemdir. Varsa <xref:System.Windows.Controls.Label> özel olarak ayarlı değil <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> değeri, değiştirin <xref:System.Windows.Controls.Label> ile bir <xref:System.Windows.Controls.TextBlock> ve veri bağlama, <xref:System.Windows.Controls.TextBlock.Text%2A> özelliğini kaynak dizesi.  
  
|**Veri bağlama özelliği**|**Güncelleştirme zamanı (ms)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>Köprü  
 <xref:System.Windows.Documents.Hyperlink> Köprüler akış içeriği barındırmanıza olanak tanır bir satır içi düzeydeki akış içerik öğesi nesnedir.  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>Bir TextBlock nesnesinde köprüler birleştirin  
 Birden çok kullanımını en iyi duruma getirebilirsiniz <xref:System.Windows.Documents.Hyperlink> içinde aynı gruplama yoluyla tarafından öğeleri <xref:System.Windows.Controls.TextBlock>. Bu, uygulamanızı oluşturduğunuz nesne sayısını en aza indirmek için yardımcı olur. Örneğin, aşağıdaki gibi birden çok köprüleri görüntülemek isteyebilirsiniz:  
  
 MSN Giriş &#124; My MSN  
  
 Aşağıdaki biçimlendirme örneği birden çok gösterir <xref:System.Windows.Controls.TextBlock> köprüleri görüntülemek için kullanılan öğeleri:  
  
 [!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 Aşağıdaki biçimlendirme örneği kullanarak tek bir bu süre, köprüler görüntülemenin daha verimli bir şekilde gösteren <xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Köprüleri MouseEnter olay üzerinde yalnızca alt çizgiler gösteriliyor  
 A <xref:System.Windows.TextDecoration> nesne metni ekleyebileceğiniz görsel bir süsleme; ancak, örneklemek için yoğun performans olabilir. Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri göz önünde bulundurun altçizgi gibi yalnızca bir olay tetiklendiğinde gösteren <xref:System.Windows.ContentElement.MouseEnter> olay. Daha fazla bilgi için [belirtin olmadığını köprünün altı çizilir](how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
  Aşağıdaki görüntüde, nasıl köprünün altı çizili MouseEnter olayı tetikler gösterilmektedir:

  ![Köprüler TextDecorations görüntüleme](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)   
  
 Aşağıdaki biçimlendirme örnek gösterildiği bir <xref:System.Windows.Documents.Hyperlink> ve alt çizgi olmadan tanımlanan:  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Aşağıdaki tablo performans maliyeti, 1000 görüntülemenin gösterir <xref:System.Windows.Documents.Hyperlink> öğeler ve alt çizgi olmadan.  
  
|**Köprü**|**Oluşturma zamanı (ms)**|**İşleme süresi (ms)**|  
|-------------------|------------------------------|----------------------------|  
|Alt çizgi ile|289|1130|  
|Alt çizgi|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>Metin biçimlendirme özellikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zengin metin biçimlendirmesini otomatik hecelere ayırma gibi hizmetleri sağlar. Bu hizmetler, uygulama performansını etkileyebilir ve yalnızca gerekli olduğunda kullanılmalıdır.  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>Gereksiz heceleme kullanmaktan kaçının  
 Otomatik heceleme tire kesme noktaları için çok metin satırı bulur ve satırlar için ek kesme konumları sağlayan <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesneleri. Varsayılan olarak, bu nesnelere Otomatik heceleme özellik devre dışıdır. Nesnenin IsHyphenationEnabled özelliğini ayarlayarak bu özelliği etkinleştirebilirsiniz `true`. Ancak, bu özelliğin etkinleştirilmesi neden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] başlatmak için [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] birlikte çalışabilirlik uygulama performansını etkileyebilir. Gerekmedikçe Otomatik heceleme kullanmamanız önerilir.  
  
### <a name="use-figures-carefully"></a>Şekilleri dikkatli kullanın  
 A <xref:System.Windows.Documents.Figure> öğesi konumlandırılmış içerisindeki bir sayfanın içeriğini akış içeriğinin bir kısmını temsil eder. Bazı durumlarda, bir <xref:System.Windows.Documents.Figure> konumuna düzenlenir genişletme zaten içerikle çakışırsa otomatik olarak yeniden biçimlendirmek bir sayfanın tamamını neden olabilir. Gereksiz gruplayarak biçimlendirme olasılığını en aza indirebilirsiniz <xref:System.Windows.Documents.Figure> birbiriyle veya bunları bir sabit sayfa boyutu senaryosunda içeriği üst kısmındaki bildirme yanındaki öğeleri.  
  
### <a name="optimal-paragraph"></a>En iyi paragraf  
 En iyi paragraf özelliği <xref:System.Windows.Documents.FlowDocument> nesne yerleştirir paragrafları böylece boşluk mümkün olduğunca eşit olarak dağıtılır. Varsayılan olarak, uygun paragraf özelliği devre dışıdır. Nesnenin ayarlayarak bu özelliği etkinleştirebilirsiniz <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> özelliğini `true`. Ancak, bu özellik etkinleştirildiğinde, uygulama performansını etkiler. Gerekmedikçe uygun paragraf özelliği kullanmayın önerilir.  
  
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
