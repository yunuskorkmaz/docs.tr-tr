---
title: WPF Genel Bakışında Çift Yönlü Özellikler
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 16cf232ccbdcca496aaa18fc2cfac280072ca24f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655483"
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF Genel Bakışında Çift Yönlü Özellikler
Herhangi diğer geliştirme platformu, farklı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çift yönlü içeriği hızlı geliştirilmesini destekleyen birçok özellik vardır, örneğin, verileri karma soldan sağa ve için sağ aynı belgede sol. Aynı anda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Arapça ve kullanıcıların konuşma İbranice gibi çift yönlü özellikler ihtiyaç duyan kullanıcılar için mükemmel bir deneyim oluşturur.  
  
 Aşağıdaki bölümlerde, çift yönlü içerik en iyi görünümü elde etmek nasıl bulunacağını gösteren örnekler birlikte birçok çift yönlü özellikler açıklanmaktadır. Örneklerin en sık kullandığınız [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], kavramlarını da kolayca uygulayabilirsiniz ancak C# veya Microsoft Visual Basic kod.  

<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 İçerik akışı yönü tanımlayan temel özellik bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Bu özellik, iki numaralandırma değerlerinden birine ayarlanabilir <xref:System.Windows.FlowDirection.LeftToRight> veya <xref:System.Windows.FlowDirection.RightToLeft>. Bu özellik tüm kullanılabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] devralacak öğeleri <xref:System.Windows.FrameworkElement>.  
  
 Aşağıdaki örnekler akış yönünü ayarlama bir <xref:System.Windows.Controls.TextBox> öğesi.  
  
 **Soldan sağa akış yönü**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Sağdan sola akış yönü**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Aşağıdaki grafikte, önceki kod nasıl işlediğini gösterir.  
    
 ![Farklı akış yönergeleri gösteren grafik.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)  
  
 İçindeki bir öğeye bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ağaç devralacaktır <xref:System.Windows.FrameworkElement.FlowDirection%2A> kendi kapsayıcısından. Aşağıdaki örnekte, <xref:System.Windows.Controls.TextBlock> içinde bir <xref:System.Windows.Controls.Grid>, içinde bulunduğu bir <xref:System.Windows.Window>. Ayarı <xref:System.Windows.FrameworkElement.FlowDirection%2A> için <xref:System.Windows.Window> için ayarlama gelir <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Controls.TextBlock> de.  
  
 Aşağıdaki örnek ayar gösterir <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 En üst düzey <xref:System.Windows.Window> sahip bir <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, içerdiği tüm öğeleri de aynı devral <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Bir öğenin belirtilen geçersiz kılma <xref:System.Windows.FrameworkElement.FlowDirection%2A> gibi ikinci bir açık yönü değişikliği eklemelisiniz <xref:System.Windows.Controls.TextBlock> değişikliklerini önceki örnekte <xref:System.Windows.FlowDirection.LeftToRight>. Hiçbir <xref:System.Windows.FrameworkElement.FlowDirection%2A> tanımlanan varsayılan <xref:System.Windows.FlowDirection.LeftToRight> uygular.  
  
 Aşağıdaki grafikte, önceki örnek çıktı gösterilmektedir:

 ![Açık akış yönü değişiklik gösteren grafik.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)  

<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Gibi birçok geliştirme platformları [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ve Java çift yönlü içerik geliştirme için özel destek sağlar. Biçimlendirme diller gibi [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] içerik yazıcılar gerekli bir yönde örneğin metni görüntülemek için gerekli biçimlendirme vermek [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 etiketi, "" rtl"veya"ltr"değerleri alır dir". Bu etiket benzer <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği, ancak <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni metinsel içeriği daha gelişmiş bir biçimde çalışır ve metin dışında içerik için kullanılabilir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Documents.FlowDocument> bir yönlüdür [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] metin, tablolar, resimler ve diğer öğeleri birleşimi barındırabilir öğesi. Aşağıdaki bölümlerde örnekleri, bu öğeyi kullanırsınız.  
  
 Metne ekleme bir <xref:System.Windows.Documents.FlowDocument> daha bir bu şekilde yapılabilir. Bunu yapmak için basit bir yolu bir <xref:System.Windows.Documents.Paragraph> olduğu gibi metin içeriği gruplandırmak için kullanılan bir blok düzeyinde öğe. Metin için örnekleri kullanın düzeydeki öğeler eklemek için <xref:System.Windows.Documents.Span> ve <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span> diğer satır içi öğeleri gruplandırmak için kullanılan bir düzeyi satır içi akış içeriği öğe sırada bir <xref:System.Windows.Documents.Run> öğesi amaçlanan bir çalıştırma biçimlendirilmemiş metin içeren bir satır içi düzeydeki akışı içeriktir. A <xref:System.Windows.Documents.Span> birden çok içerebilir <xref:System.Windows.Documents.Run> öğeleri.  
  
 Paylaşım adları bir dizi ağ sahip bir belge ilk belge örneği içerir. Örneğin `\\server1\folder\file.ext`. Bu ağ bağlantısı olup Arapça veya İngilizce bir belgede her zaman aynı şekilde görünmesini istediğiniz. Aşağıdaki grafikte Span öğesi kullanılması gösterilmektedir ve bir Arapça ' bağlantıyı gösterir <xref:System.Windows.FlowDirection.RightToLeft> belge:

 ![Span öğesi kullanarak gösteren grafik. ](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")  
  
 Metin olduğundan <xref:System.Windows.FlowDirection.RightToLeft>, tüm özel karakterleri, gibi "\\", sağdan sola düzeni metinde ayırın. Doğru sırayla gösteriliyor değil bağlantıda sonuçları, bu nedenle bu sorunu çözmek için metin ayrı bir korumak için gömülmesi <xref:System.Windows.Documents.Run> akan <xref:System.Windows.FlowDirection.LeftToRight>. Ayrı bir yerine <xref:System.Windows.Documents.Run> her dil için daha az sık kullanılan İngilizce metni daha büyük bir Arapça gömmek için sorunu çözmenize daha iyi bir yolu olan <xref:System.Windows.Documents.Span>.  
  
 Aşağıdaki grafikte bir Span öğesi içinde gömülü çalışma öğesini kullanarak bunu göstermektedir:

 ![Çalışma öğesi çizildiği grafik bir Span öğesi içinde gömülü.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)  
  
 Aşağıdaki örneği kullanarak göstermektedir <xref:System.Windows.Documents.Run> ve <xref:System.Windows.Documents.Span> belgelerde öğeleri.  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span öğeleri  
 <xref:System.Windows.Documents.Span> Metinler ile akış farklı yönleri arasında sınır ayırıcı olarak çalışır.  Hatta <xref:System.Windows.Documents.Span> aynı akış yönü öğelerle anlamına farklı çift yönlü kapsamlar değerlendirilir <xref:System.Windows.Documents.Span> öğeleri kapsayıcının içinde sıralı <xref:System.Windows.FlowDirection>, yalnızca içeriği içinde <xref:System.Windows.Documents.Span> öğesi Aşağıdaki <xref:System.Windows.FlowDirection> , <xref:System.Windows.Documents.Span>.  
  
 Aşağıdaki grafikte birkaç akış yönünü gösterir <xref:System.Windows.Controls.TextBlock> öğeleri.  
    
 ![Metin blokları farklı akış yönergeleri ile gösteren grafik.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Documents.Span> ve <xref:System.Windows.Documents.Run> öğeleri önceki grafikte gösterilen istediğiniz sonuçları vermeyebilir.  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 İçinde <xref:System.Windows.Controls.TextBlock> örnek öğelerinde <xref:System.Windows.Documents.Span> öğeleri düzenlenir göre <xref:System.Windows.FlowDirection> ebeveynleri, ancak her metin <xref:System.Windows.Documents.Span> öğesi akışlar göre kendi <xref:System.Windows.FlowDirection>. Bu, Latin ve Arapça – veya başka bir dil için geçerlidir.  
  
### <a name="adding-xmllang"></a>XML: lang ekleme  
 Sayılar ve aritmetik ifadeler gibi kullanan başka bir örnek aşağıda görüldüğü `"200.0+21.4=221.4"`. Yalnızca bildirimi <xref:System.Windows.FlowDirection> ayarlanır.  
    
 ![Yalnızca FlowDirection kullanarak numaralarını gösteren grafik.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)  
  
 Bu uygulamanın kullanıcıları üzüntü çıktı tarafından olsa bile <xref:System.Windows.FlowDirection> sayılar değil Arapça numaraları şeklinde gibi şeklinde doğru olduğundan.  
  
 XAML öğeleri içerebilir bir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] özniteliği (`xml:lang`), her öğenin dil tanımlar. XAML da destekler bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dil İlkesi yapabildiği `xml:lang` ağaç içinde üst öğelere uygulanan değerleri, alt öğeler tarafından kullanılır. Önceki örnekte, bir dil için tanımlı değil çünkü <xref:System.Windows.Documents.Run> öğe veya herhangi bir en üst düzey öğeleri, varsayılan `xml:lang` kullanılan olduğu `en-US` XAML için. Dahili numara şekillendirme algoritmasının [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] seçer sayıları karşılık gelen dilde – bu durumda İngilizce. Arapça yapmak numaraları işleme doğru `xml:lang` ayarlanması gerekir.  
  
 Aşağıdaki grafikte örnek ile gösterir `xml:lang` eklendi.  
    
 ![Grafik, sağdan sola akış Arapça sayıları gösterir.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)  
  
 Aşağıdaki örnek ekler `xml:lang` uygulama.  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Birçok dilde farklı olduğunu unutmayın `xml:lang` hedeflenen bölge için bağlı olarak değerleri `"ar-SA"` ve `"ar-EG"` Arapça iki çeşidi gösterir. Önceki örneklerin her ikisi de tanımlamanız gerekecek göstermek `xml:lang` ve <xref:System.Windows.FlowDirection> değerleri.  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection metin olmayan öğeler ile  
 <xref:System.Windows.FlowDirection> yalnızca nasıl metin değerinin metinsel bir öğe aynı zamanda, neredeyse diğer akış yönü içinde akışları tanımlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğesi. Aşağıdaki grafik gösterildiği bir <xref:System.Windows.Controls.ToolBar> yatay kullanan <xref:System.Windows.Media.LinearGradientBrush> sol ile arka planı doğru gradyanın.  

 ![Bir soldan sağa gradyan ile bir araç çubuğunu gösteren grafik.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)  
  
 Ayarlanmasından sonra <xref:System.Windows.FlowDirection> için <xref:System.Windows.FlowDirection.RightToLeft>, yalnızca <xref:System.Windows.Controls.ToolBar> düğmeleri ancak bile, soldan sağa düzenlenmiştir <xref:System.Windows.Media.LinearGradientBrush> sağdan sola akış uzaklıkları, yeniden hizalar.  
  
 Aşağıdaki grafikte, yeniden hizalama gösterilmektedir <xref:System.Windows.Media.LinearGradientBrush>.  
    
 ![Bir sağdan sola gradyan ile bir araç çubuğunu gösteren grafik.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)  
  
 Aşağıdaki örnek çizen bir <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (Sağdan sola çizip için kaldırın <xref:System.Windows.FlowDirection> özniteliği <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>FlowDirection özel durumları  
 Birkaç durum vardır. burada <xref:System.Windows.FlowDirection> beklendiği gibi davranmaz. Bu bölüm iki bu özel durumları kapsar.  
  
 **Görüntü**  
  
 Bir <xref:System.Windows.Controls.Image> resim görüntüleyen bir denetimi temsil eder. İçinde [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ile kullanılabilir bir <xref:System.Windows.Controls.Image.Source%2A> tanımlayan özellik [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] , <xref:System.Windows.Controls.Image> görüntülenecek.  
  
 Diğer aksine [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri bir <xref:System.Windows.Controls.Image> devralmaz <xref:System.Windows.FlowDirection> kapsayıcısından. Ancak, varsa <xref:System.Windows.FlowDirection> açıkça ayarlanmış <xref:System.Windows.FlowDirection.RightToLeft>, bir <xref:System.Windows.Controls.Image> yatay çevrilmiş görüntülenir. Bu, çift yönlü içeriğinin geliştiriciler için kullanışlı bir özellik olarak uygulanır; Bazı durumlarda, yatay görüntü çevirme çünkü istenen efekti oluşturur.  
  
 Aşağıdaki grafikte bir çevrilen gösterilmektedir <xref:System.Windows.Controls.Image>.  
    
 ![Döndürülen resim gösteren grafik.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)  
  
 Aşağıdaki örnek, gösterir <xref:System.Windows.Controls.Image> devralmak başarısız <xref:System.Windows.FlowDirection> gelen <xref:System.Windows.Controls.StackPanel> , içerir. **Not** adlı bir dosya olmalıdır **ms_logo.jpg** , C:\ üzerinde Bu örneği çalıştırmak için sürücü.  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Not** indirme dosyalarında dahil olduğu bir **ms_logo.jpg** dosya. Kod .jpg dosyasını projenize içinde değil ancak C:\ sürücüsüne yere olduğunu varsayar. .jpg C:\ sürücünüzde konumundan proje dosyaları kopyalayın veya proje içine dosyayı aramak için kodda değişiklik gerekir. Bu değişikliği yapmak için `Source="file://c:/ms_logo.jpg"` için `Source="ms_logo.jpg"`.  
  
 **Yolları**  
  
 Ek olarak bir <xref:System.Windows.Controls.Image>, başka bir ilgi çekici bir öğedir <xref:System.Windows.Shapes.Path>. Bir yolu, bir dizi bağlantılı çizgiler ve eğrilerdir çizebilirsiniz bir nesnedir. Benzer şekilde davranan bir <xref:System.Windows.Controls.Image> ilgili kendi <xref:System.Windows.FlowDirection>; Örneğin, <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> bir yatay yansıması kendi <xref:System.Windows.FlowDirection.LeftToRight> bir. Ancak, farklı bir <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> devralır, <xref:System.Windows.FlowDirection> kapsayıcı ve bir açıkça belirtmeniz gerekmez.  
  
 Aşağıdaki örnek, 3 satır kullanarak basit bir ok çizer. Birinci oka devralan <xref:System.Windows.FlowDirection.RightToLeft> akış yönünü <xref:System.Windows.Controls.StackPanel> böylece kendi başlangıç ve bitiş noktalarını işlecin sağ tarafındaki bir kök ölçülür. Açık olan ikinci ok <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> sağ tarafta da başlatır. Ancak üçüncü oku, sol taraftaki başlangıç kök sahiptir. Bkz: çizim hakkında daha fazla bilgi için <xref:System.Windows.Media.LineGeometry> ve <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Aşağıdaki grafikte, önceki örnek çıktısı okları kullanarak gösterir. `Path` öğesi:

 ![Grafik, yol öğesi kullanılarak çizilen oklar gösterilmektedir.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)  
  
 <xref:System.Windows.Controls.Image> Ve <xref:System.Windows.Shapes.Path> iki örnek bir nasıl [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanan <xref:System.Windows.FlowDirection>. Yerleştirme yanında [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] belirli bir yönde bir kapsayıcı içindeki öğeleri <xref:System.Windows.FlowDirection> öğelerle gibi kullanılabilir <xref:System.Windows.Controls.InkPresenter> bir yüzeydeki mürekkebi işler <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Sol davranışı sağa doğru davranışları sola taklit eden içeriğiniz için ihtiyaç duyduğunuzda ya da tam tersi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bu yeteneği sağlar.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Sayı değiştirme  
 Tarihsel olarak, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] sayı değiştirme örnek numaraları içinde depolanan için iç depolaması ve birleşik farklı yerel ayarlar arasında bu basamakları tutarken farklı kültürel şekiller için aynı rakam temsilini sağlayarak desteklenir iyi bilinen onaltılık değerlerini, 0x40, 0x41, ancak göre seçilen dilde görüntülenir.  
  
 Bu, bunları bir dilden diğerine dönüştürmek zorunda kalmadan sayısal değerleri işlemek için uygulamaları izin, örneğin bir kullanıcı açabilirsiniz bir [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] elektronik tabloda yerelleştirilmiş Arapça [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve Arapça'şeklinde sayıları görmek, ancak açın Avrupa sürümünü [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve aynı sayıların Avrupa gösterimine bakın. Bunlar genellikle aynı belgede numaraları eşlik çünkü virgül ayraçları ve yüzde simgesi gibi bu ayrıca diğer semboller için gereklidir.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aynı geleneğini devam ettirmektedir ve daha fazla değiştirme ne zaman ve nasıl kullanılır üzerinde daha fazla kullanıcı denetim sağlayan bu özellik için destek ekler. Bu özellik, herhangi bir dil için tasarlandığından, belirli bir dil basamak şekillendirme genellikle Uygulama geliştiricileri için bir sınama uygulama çalıştırılabileceği çeşitli kültürlerde nedeniyle burada çift yönlü içerik özellikle yararlı olur.  
  
 Nasıl sayı değiştirme denetleme çekirdek özelliği içinde çalıştığı [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olduğu <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> bağımlılık özelliği. <xref:System.Windows.Media.NumberSubstitution> Sınıfını nasıl görüntülenecek metin numaraları olan belirtir. Davranışını tanımlayan üç genel özellikleri var. Özelliklerin her birini bir özeti aşağıda verilmiştir.  
  
 **CultureSource:**  
  
 Bu özellik, sayılar için kültür nasıl belirlendiğini belirtir. Bu üç birini alır <xref:System.Windows.Media.NumberCultureSource> sabit listesi değerleri.  
  
- Geçersiz kıl: Sayı kültüre ait olduğu <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> özelliği.  
  
- Metin: Çalıştırma metin kültürünü sayı kültürdür. Biçimlendirme içinde bu olacaktır `xml:lang`, veya diğer adıyla `Language` özelliği (<xref:System.Windows.FrameworkElement.Language%2A> veya <xref:System.Windows.FrameworkContentElement.Language%2A>). Ayrıca, türetilen sınıflar için varsayılan olarak etkin <xref:System.Windows.FrameworkContentElement>. Bu tür sınıflar içeren <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> ve benzeri.  
  
- Kullanıcı: Geçerli iş parçacığı kültürünü sayı kültürdür. Bu özellik tüm alt sınıflar için varsayılan değer <xref:System.Windows.FrameworkElement> gibi <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> ve <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> Özelliği yalnızca kullanılan <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> özelliği <xref:System.Windows.Media.NumberCultureSource.Override> , aksi halde yoksayılır. Bu numara kültürü belirtir. Değerini `null`, varsayılan değer, en-US yorumlanır.  
  
 **Değiştirme**:  
  
 Bu özellik gerçekleştirmek için sayı değiştirme türünü belirtir. Aşağıdakilerden birini alır <xref:System.Windows.Media.NumberSubstitutionMethod> sabit listesi değerleri.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: Değiştirme yöntemi sayı kültürün üzerinde belirlenir <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> özelliği. Bu varsayılandır.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Sayı kültür Arapça veya Farsça bir kültür ise, rakamları içeriğine bağlı olduğunu belirtir.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Sayıları, her zaman Avrupa basamaklı olarak işlenir.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Sayılar, kültürün tarafından belirtilen sayı kültür için Ulusal basamak kullanarak işlenir <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Sayılar, sayı kültürü için geleneksel basamak kullanarak işlenir. Çoğu kültürde için aynı budur <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Ancak, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> sonuçlanıyor Latin basamak bazı Arapça kültürler için bu değer tüm kültürler için kullanılabilecek Arapça Arapça basamaklı sonucunu.  
  
 Bu değerleri bir çift yönlü içerik geliştirici için anlamı nedir? Çoğu durumda, geliştirici yalnızca tanımlamanız gerekebilir <xref:System.Windows.FlowDirection> ve her metin dili [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğesi, örneğin `Language="ar-SA"` ve <xref:System.Windows.Media.NumberSubstitution> mantığının doğru göre numaraları görüntüleme üstlenir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Aşağıdaki örnek Arapça ve İngilizce numaralarını kullanarak gösterir bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Arapça bir sürümünde çalışan uygulama [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Görüntülenen Arapça ve İngilizce numaralarıyla Arapça bir Windows sürümünde çalıştırıyorsanız, aşağıdaki grafikte önceki örnek çıktı gösterilmektedir:

 ![Arapça ve İngilizce sayılarını gösteren grafik.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)  
  
 <xref:System.Windows.FlowDirection> Ayarlama çünkü bu durumda önemli olduğunu <xref:System.Windows.FlowDirection> için <xref:System.Windows.FlowDirection.LeftToRight> Avrupa basamak yerine veriyor. Aşağıdaki bölümlerde, belge boyunca basamak birleşik bir görünümünü sağlamak nasıl açıklanmaktadır. Bu örnek Arapça Windows üzerinde çalışmıyorsa, Avrupa basamakla tüm basamakları görüntüler.  
  
 **Değiştirme'kurallarını tanımlama**  
  
 Gerçek bir uygulamada dil programlı olarak ayarlamanız gerekebilir. Örneğin, ayarlamak istediğiniz `xml:lang` sistem tarafından kullanılanla aynı olması için öznitelik [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], veya belki de uygulama durumu bağlı olarak dili.  
  
 Hale getirmek isterseniz değişikliklere göre uygulamanın durumu, olun tarafından sağlanan diğer özelliklerin kullanmanız [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 İlk olarak, uygulama bileşen kümesi `NumberSubstitution.CultureSource="Text"`. Bu ayar kullanılarak yapar ayarları gelen gelmeyen emin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] "Kullanıcı" gibi varsayılan olarak sahip metin öğelerin <xref:System.Windows.Controls.TextBlock>.  
  
Örneğin:  

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

Karşılık gelen C# ayarlayın, kod `Language` özelliği, örneğin `"ar-SA"`.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

Ayarlanacak ihtiyacınız varsa `Language` özelliği geçerli kullanıcının kullanıcı Arabirimi dili için aşağıdaki kodu kullanın.  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Çalışma zamanında geçerli iş parçacığı tarafından kullanılan geçerli kültürü temsil eder.  
  
 Son [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] örnek aşağıdaki örneğe benzer olmalıdır.  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Son C# örnek aşağıdakine benzer olmalıdır.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Aşağıdaki grafikte, pencerenin Arapça numaraları görüntüleme ya da programlama dili için nasıl göründüğünü gösterir:
     
 ![Arapça numaralarını gösteren grafik.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)  
  
 **Değiştirme özelliğini kullanma**  
  
 İçinde çalıştığı şekilde sayı değiştirme [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] hem metin öğesinin diline bağlıdır ve kendi <xref:System.Windows.FlowDirection>. Varsa <xref:System.Windows.FlowDirection> Avrupa basamak işlenen sonra soldan sağa, olur. Ancak Arapça metne göre öncesinde ya da "ar" için ayarlar dil ve <xref:System.Windows.FlowDirection> olduğu <xref:System.Windows.FlowDirection.RightToLeft>, Arapça basamak yerine işlenir.  
  
 Ancak, bazı durumlarda, örneğin Avrupa basamak tüm kullanıcılar için birleşik bir uygulama oluşturmak isteyebilirsiniz. Veya Arapça basamak <xref:System.Windows.Documents.Table> belirli bir hücrelerle <xref:System.Windows.Style>. Kullanan yapmak kolay yollarından biri <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> özelliği.  
  
 Aşağıdaki örnekte, ilk <xref:System.Windows.Controls.TextBlock> olmayan <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> özelliği ayarlamak, böylece beklendiği gibi algoritma Arapça basamak görüntüler. Ancak ikinci <xref:System.Windows.Controls.TextBlock>değiştirme Varsayılan değiştirme Arapça sayılar için geçersiz kılma Avrupa için ayarlanır ve Avrupa rakamları görüntülenir.  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
