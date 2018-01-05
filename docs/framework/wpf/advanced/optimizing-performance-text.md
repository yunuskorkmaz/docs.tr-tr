---
title: "Performansı İyileştirme: Metin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f345893ca79d820ebb066d920cb49c6c46c47297
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="optimizing-performance-text"></a>Performansı İyileştirme: Metin
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]sunu özelliklerini kullanarak zengin metin içeriği için destek içerir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] kontrol eder. Genel olarak üç katmanı metin oluşturma işlemi:  
  
1.  Kullanarak <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun> nesnelerini doğrudan.  
  
2.  Kullanarak <xref:System.Windows.Media.FormattedText> nesnesi.  
  
3.  Yüksek düzey denetimleri gibi kullanılarak <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesneleri.  
  
 Bu konu, metin işleme performans önerileri sağlar.  
  
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>Karakter düzeyinde metin oluşturma  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]doğrudan erişimli karakter düzeyinde biçimlendirme dahil olmak üzere Gelişmiş metin desteği sağlar <xref:System.Windows.Documents.Glyphs> kesecek ve metin biçimlendirme sonra devam etmek isteyen müşteriler için. Bu özellikler, işleme gereksinimleri aşağıdaki senaryoların her biri için farklı metin kritik destek sağlar.  
  
-   Sabit biçimli belgelerin ekran görüntüsü.  
  
-   Yazdırma senaryoları.  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir aygıt yazıcı dili olarak.  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)].  
  
    -   Çıktı önceki yazıcı sürücüleri [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] uygulamalarından sabit biçimde.  
  
    -   Yazdırma biriktirme biçimi.  
  
-   Önceki sürümlerinde istemciler dahil olmak üzere sabit biçimli belge gösterimi [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve diğer programlama cihazları.  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs>ve <xref:System.Windows.Media.GlyphRun> sabit biçimli belge sunumları ve yazdırma senaryoları için tasarlanmıştır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Çeşitli öğeleri için genel yerleşimi sağlar ve [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] gibi senaryoları <xref:System.Windows.Controls.Label> ve <xref:System.Windows.Controls.TextBlock>. Düzen hakkında daha fazla bilgi ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] senaryoları bkz [WPF'de tipografi](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).  
  
 Aşağıdaki örnekler özelliklerini tanımlamak nasıl bir <xref:System.Windows.Documents.Glyphs> nesnesinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> Nesneyi temsil ediyor çıktısını bir <xref:System.Windows.Media.GlyphRun> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Örneklerde, Arial, Courier New ve kez yeni Latin yazı tipleri yüklenir varsayılmaktadır **C:\WINDOWS\Fonts** yerel bilgisayardaki klasör.  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>DrawGlyphRun Kullanma  
 Özel denetim sahibi ve karakterleri işlemek, kullanmak istediğiniz <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A> yöntemi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Özel metin kullanılarak biçimlendirme için alt düzey hizmetleri de sağlar <xref:System.Windows.Media.FormattedText> nesnesi. İşleme metinde en verimli şekilde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] karakter kullanarak düzeyinde metin içeriği oluşturarak olan <xref:System.Windows.Documents.Glyphs> ve <xref:System.Windows.Media.GlyphRun>. Ancak, bu verimliliği yerleşik özellikleri olan, kullanımı kolay zengin metin biçimlendirmesini kaybı maliyetidir, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] denetimleri gibi <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument>.  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>FormattedText nesnesi  
 <xref:System.Windows.Media.FormattedText> Nesnesi, metindeki her karakter ayrı ayrı biçimlendirilebilir çok satırlı metin Çiz olanak tanır. Daha fazla bilgi için bkz: [çizim biçimlendirilmiş metin](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md).  
  
 Biçimlendirilmiş metin oluşturmak için arama <xref:System.Windows.Media.FormattedText.%23ctor%2A> Oluşturucusu oluşturmak için bir <xref:System.Windows.Media.FormattedText> nesnesi. İlk biçimlendirilmiş metin dizesi oluşturduktan sonra bir aralık stilleri biçimlendirme uygulayabilirsiniz. Uygulamanız kendi düzenini uygulamak isterse sonra <xref:System.Windows.Media.FormattedText> nesnesidir bir denetim gibi kullanmaktan daha iyi seçim <xref:System.Windows.Controls.TextBlock>. Daha fazla bilgi için <xref:System.Windows.Media.FormattedText> nesne için bkz: [çizim biçimlendirilmiş metin](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md) .  
  
 <xref:System.Windows.Media.FormattedText> Nesnesi, alt düzey metin biçimlendirme yeteneği sağlar. Bir veya daha fazla karakterle birden çok biçimlendirme stilleri uygulayabilirsiniz. Örneğin, her ikisini çağırabilirsiniz <xref:System.Windows.Media.FormattedText.SetFontSize%2A> ve <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metindeki ilk beş karakter biçimlendirme değiştirmek için yöntemleri.  
  
 Aşağıdaki kod örneği oluşturur bir <xref:System.Windows.Media.FormattedText> nesne ve bunu işler.  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument, TextBlock ve etiket denetimleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ekrana metin çizme için birden çok denetim içerir. Her denetim için farklı bir senaryo hedeflenen ve kendi listesi özellikleri ve sınırlamaları vardır.  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument etkiler performans birden fazla TextBlock veya etiketi  
 Genel olarak, <xref:System.Windows.Controls.TextBlock> öğesi sınırlı metin desteği içindeki kısa tümce gibi gerekli olduğunda kullanılmalıdır bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>en az metin desteği gerekli olduğunda kullanılabilir. <xref:System.Windows.Documents.FlowDocument> Öğesi, zengin içerik sunusu destekleyen yeniden akışkan olabilen belgeler için bir kapsayıcı olduğunu ve bu nedenle, kullanmaktan daha büyük bir performans etkisi <xref:System.Windows.Controls.TextBlock> veya <xref:System.Windows.Controls.Label> kontrol eder.  
  
 Daha fazla bilgi için <xref:System.Windows.Documents.FlowDocument>, bkz: [akış belge genel bakış](../../../../docs/framework/wpf/advanced/flow-document-overview.md).  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>FlowDocument içinde TextBlock kullanmaktan kaçının  
 <xref:System.Windows.Controls.TextBlock> Öğesi türetilir <xref:System.Windows.UIElement>. <xref:System.Windows.Documents.Run> Öğesi türetilir <xref:System.Windows.Documents.TextElement>, daha az maliyetli olduğu bir <xref:System.Windows.UIElement>-türetilmiş bir nesne içermelidir. Mümkün olduğunda kullanın <xref:System.Windows.Documents.Run> yerine <xref:System.Windows.Controls.TextBlock> içindeki metin içeriğini görüntülemek için bir <xref:System.Windows.Documents.FlowDocument>.  
  
 Aşağıdaki biçimlendirme örneği içinde metin içeriği ayarlamanın iki yolunu gösterir bir <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xaml[Performance#PerformanceSnippet13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>Metin özelliklerini ayarlamak için Çalıştır'ı kullanarak kaçının  
 Genel olarak, kullanarak bir <xref:System.Windows.Documents.Run> içinde bir <xref:System.Windows.Controls.TextBlock> daha fazla performans açık bir kullanmadan daha yoğun olan <xref:System.Windows.Documents.Run> hiç nesne. Kullanıyorsanız bir <xref:System.Windows.Documents.Run> metin özelliklerini ayarlamak için doğrudan bu özellikleri ayarlayın <xref:System.Windows.Controls.TextBlock> yerine.  
  
 Aşağıdaki biçimlendirme örneği bu durumda, bir metin özelliğini ayarlamanın bu iki yolunu gösterir <xref:System.Windows.Controls.TextBlock.FontWeight%2A> özelliği:  
  
 [!code-xaml[Performance#PerformanceSnippet12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 Aşağıdaki tabloda, 1000 görüntüleme maliyetini gösterilmektedir <xref:System.Windows.Controls.TextBlock> nesneleri ile ve açık bir olmadan <xref:System.Windows.Documents.Run>.  
  
|**TextBlock türü**|**Oluşturma süresi (ms)**|**İşleme süresi (ms)**|  
|------------------------|------------------------------|----------------------------|  
|Run ayarı metin özellikleri|146|540|  
|TextBlock ayarı metin özellikleri|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Veri bağlama Label.Content özelliğine kaçının  
 Sahip olduğu bir senaryoyu düşünün bir <xref:System.Windows.Controls.Label> kaynağından sık sık güncelleştirilen nesneyi bir <xref:System.String> kaynak. Veri bağlama <xref:System.Windows.Controls.Label> öğenin <xref:System.Windows.Controls.ContentControl.Content%2A> özelliğine <xref:System.String> kaynak nesnesi, düşük performans karşılaşabilirsiniz. Her zaman kaynak <xref:System.String> güncelleştirilir, eski <xref:System.String> nesnesidir yoksayılır ve yeni bir <xref:System.String> yeniden — çünkü bir <xref:System.String> nesne değişmez, değiştirilemez. Bu, sırasıyla neden <xref:System.Windows.Controls.ContentPresenter> , <xref:System.Windows.Controls.Label> eski içeriği atmak ve yeni görüntülemek için yeni içeriği yeniden oluşturmak için nesne <xref:System.String>.  
  
 Bu sorun için çözüm, basit bir işlemdir. Varsa <xref:System.Windows.Controls.Label> özel olarak ayarlı değil <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> değeri, yerine <xref:System.Windows.Controls.Label> ile bir <xref:System.Windows.Controls.TextBlock> veri bağlaması kendi <xref:System.Windows.Controls.TextBlock.Text%2A> kaynak dizesi özelliğine.  
  
|**Veri bağlama özelliği**|**Güncelleştirme süresi (ms)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>Köprü  
 <xref:System.Windows.Documents.Hyperlink> Nesnesidir köprüler akış içeriği barındırmanıza olanak tanıyan bir satır içi düzeyde akış içeriği öğesidir.  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>Bir TextBlock nesnesinde köprüleri birleştirme  
 Birden çok kullanımını en iyi duruma getirebilirsiniz <xref:System.Windows.Documents.Hyperlink> birlikte içinde aynı gruplandırarak tarafından öğeleri <xref:System.Windows.Controls.TextBlock>. Bu nesneleri uygulamanızda Oluştur sayısını en aza indirmenize yardımcı olur. Örneğin, aşağıdaki gibi birden çok köprüleri görüntülemek isteyebilirsiniz:  
  
 MSN Giriş &#124; My MSN  
  
 Aşağıdaki biçimlendirme örneği birden çok gösterir <xref:System.Windows.Controls.TextBlock> köprüleri görüntülemek için kullanılan öğeleri:  
  
 [!code-xaml[Performance#PerformanceSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 Köprüler, bu süre, tek bir kullanarak görüntüleme daha etkili bir yol aşağıdaki biçimlendirme örneği gösterir <xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xaml[Performance#PerformanceSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Yalnızca MouseEnter Olayları üzerinde köprüleri alt çizgileri gösterme  
 A <xref:System.Windows.TextDecoration> nesnesi metne ekleyebileceğiniz görsel süslemedir; Bununla birlikte, performans örneği oluşturmak için yoğun olabilir. Kapsamlı kullanımını yaparsanız <xref:System.Windows.Documents.Hyperlink> öğeleri, göz önünde bulundurun altı çizili gibi yalnızca bir olay tetiklendiğinde gösteren <xref:System.Windows.ContentElement.MouseEnter> olay. Daha fazla bilgi için bkz: [belirtin olup olmadığını bir köprü çizilir](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).  
  
 ![TextDecorations görüntüleyen köprüler](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
MouseEnter üzerinde köprü  
  
 Aşağıdaki biçimlendirme örnek gösterildiği bir <xref:System.Windows.Documents.Hyperlink> ile ve bir alt çizginin olmadan tanımlanan:  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 Aşağıdaki tabloda, 1000 görüntüleme performans maliyeti gösterilmektedir <xref:System.Windows.Documents.Hyperlink> öğeleri ile ve bir alt çizginin olmadan.  
  
|**Köprü**|**Oluşturma süresi (ms)**|**İşleme süresi (ms)**|  
|-------------------|------------------------------|----------------------------|  
|Alt çizgi ile|289|1130|  
|Alt çizgi|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>Metin biçimlendirme özellikleri  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Zengin metin biçimlendirme otomatik hecelere ayırma gibi hizmetleri sağlar. Bu hizmetler, uygulama performansını etkileyebilir ve yalnızca gerekli olduğunda kullanılmalıdır.  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>Tireleme gereksiz kullanmaktan kaçının  
 Otomatik tireleme satırlık metin için kısa çizgi kesme noktalarını bulur ve satırlar için ek kesme konumlarına izin verir <xref:System.Windows.Controls.TextBlock> ve <xref:System.Windows.Documents.FlowDocument> nesneleri. Varsayılan olarak, bu nesneleri Otomatik heceleme özelliğini devre dışıdır. Nesnenin IsHyphenationEnabled özelliğini ayarlayarak bu özelliği etkinleştirmek `true`. Ancak, bu özelliği etkinleştirmek neden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] başlatmak için [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)] uygulama performansını etkileyebilir birlikte çalışabilirlik. Gerekmedikçe Otomatik heceleme kullanmamanız önerilir.  
  
### <a name="use-figures-carefully"></a>Şekilleri dikkatli kullanın  
 A <xref:System.Windows.Documents.Figure> öğesi konumlandırılmış, içerik sayfası içinde akış içeriğinin bölümünü temsil eder. Bazı durumlarda, bir <xref:System.Windows.Documents.Figure> konumuna yerleştirilmiş çıkış zaten içerik ile çakışırsa otomatik olarak yeniden biçimlendirmek sayfanın tamamını neden olabilir. Gereksiz gruplayarak yeniden biçimlendirme olasılığını en aza indirebilirsiniz <xref:System.Windows.Documents.Figure> birbirine veya bunları bir sabit sayfa boyutu senaryosunda içeriğin üstüne yakın bildirme yanındaki öğeleri.  
  
### <a name="optimal-paragraph"></a>En iyi paragraf  
 En iyi paragraf özelliği, <xref:System.Windows.Documents.FlowDocument> nesnesi, böylece boşluk mümkün olduğunca eşit dağıtılmış paragrafları yerleştirir. Varsayılan olarak, en uygun paragraf özelliği devre dışıdır. Nesnenin ayarlayarak bu özelliği etkinleştirebilirsiniz <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> özelliğine `true`. Ancak, bu özelliği etkinleştirmek, uygulama performansını etkiler. Gerekmedikçe en uygun paragraf özelliği kullanmamanız önerilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF Uygulama Performansını İyileştirme](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Uygulama Performansını Planlama](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Donanımdan Yararlanma](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Düzen ve Tasarım](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2B Grafikleri ve Görüntüleme](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Nesne Davranışı](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Uygulama Kaynakları](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Veri Bağlama](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Diğer Performans Önerileri](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
