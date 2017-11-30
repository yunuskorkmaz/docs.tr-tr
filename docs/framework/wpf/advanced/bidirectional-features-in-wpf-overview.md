---
title: "WPF Genel Bakışında Çift Yönlü Özellikler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 716774efdf62356c2e3253c588dabb51de74470c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF Genel Bakışında Çift Yönlü Özellikler
Tüm diğer geliştirme platformu, aksine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çift yönlü içeriğinin hızlı geliştirme desteği pek çok özellik vardır, örneğin, karma soldan sağa ve için sağa veri aynı belgede sol. Aynı anda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çift yönlü özellikler Arapça ve kullanıcıların konuşarak İbranice gibi isteyen kullanıcılar için mükemmel bir deneyim oluşturur.  
  
 Aşağıdaki bölümlerde, çift yönlü içerik en iyi görünümü elde etmek nasıl çalıştığını gösteren örnekler birlikte birçok çift yönlü özellikler açıklanmaktadır. Örneklerin en sık kullandığınız [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]kavramlara kolayca uygulayabilirsiniz ancak [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] veya [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] kodu.  
  

  
<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 İçerik akışı yönde tanımlayan temel özelliğini bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Bu özellik iki numaralandırma değerlerinden biri olarak ayarlanabilir <xref:System.Windows.FlowDirection.LeftToRight> veya <xref:System.Windows.FlowDirection.RightToLeft>. Özelliği için tüm kullanılabilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] devralınmalıdır öğeleri <xref:System.Windows.FrameworkElement>.  
  
 Aşağıdaki örnekler akış yönünü ayarlar bir <xref:System.Windows.Controls.TextBox> öğesi.  
  
 **Soldan sağa akış yönü**  
  
 [!code-xaml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Sağdan sola akış yönü**  
  
 [!code-xaml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Aşağıdaki grafikte, önceki kod nasıl işlediğini gösterir.  
  
 **FlowDirection gösteren grafik**  
  
 ![TextBlock hizalaması](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.PNG "LefttoRightRighttoLeft")  
  
 Bir öğenin içine bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ağaç devral <xref:System.Windows.FrameworkElement.FlowDirection%2A> kendi kapsayıcısından. Aşağıdaki örnekte, <xref:System.Windows.Controls.TextBlock> içinde bir <xref:System.Windows.Controls.Grid>, içinde bulunduğu bir <xref:System.Windows.Window>. Ayarı <xref:System.Windows.FrameworkElement.FlowDirection%2A> için <xref:System.Windows.Window> için ayarı gelir <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Controls.TextBlock> de.  
  
 Aşağıdaki örnek, ayarı gösterir <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 En üst düzey <xref:System.Windows.Window> sahip bir <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, içinde bulunan tüm öğeleri de aynı devralmak için <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Bir öğenin bir belirtilen geçersiz kılma <xref:System.Windows.FrameworkElement.FlowDirection%2A> ikinci gibi herhangi bir açık yönü değişiklik eklemelisiniz <xref:System.Windows.Controls.TextBlock> değişikliklerini önceki örnekte <xref:System.Windows.FlowDirection.LeftToRight>. Durumlarda <xref:System.Windows.FrameworkElement.FlowDirection%2A> tanımlanan varsayılan <xref:System.Windows.FlowDirection.LeftToRight> uygular.  
  
 Aşağıdaki grafikte, önceki örnekte çıktısını gösterir.  
  
 **Açıkça gösteren bir grafik FlowDirection atanan**  
  
 ![Akış yönü çizimi](../../../../docs/framework/wpf/advanced/media/flowdir.PNG "FlowDir")  
  
<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Gibi birçok geliştirme platformları [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ve Java çift yönlü içerik geliştirme için özel destek sağlar. Biçimlendirme diller gibi [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] içerik yazıcılarının metni herhangi bir gerekli yönde örneğin görüntülemek için gerekli biçimlendirme vermek [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 etiketi, "" rtl"veya"ltr"değerleri alır dir". Bu etiket benzer <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği, ancak <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni metinsel içeriği daha gelişmiş bir şekilde çalışır ve metin dışında içerik için kullanılabilir.  
  
 İçinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Documents.FlowDocument> bir yönlüdür [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] metin, tablolar, resimleri ve diğer öğeleri bileşimini barındırabilir öğesi. Aşağıdaki bölümlerde örnekleri bu öğeyi kullanın.  
  
 Metin ekleme bir <xref:System.Windows.Documents.FlowDocument> bu bir şekilde daha yapılabilir. Bunu yapmak için basit bir yol aracılığıyladır bir <xref:System.Windows.Documents.Paragraph> metin gibi içeriği gruplandırmak için kullanılan blok düzeyi bir öğeyi olduğu. Örnekler kullanmak iç düzeydeki öğeler için metin eklemek için <xref:System.Windows.Documents.Span> ve <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span>diğer satır içi öğeleri gruplandırmak için kullanılan bir satır içi düzeyi akış içerik öğe sırada bir <xref:System.Windows.Documents.Run> içi düzeyi akış öğesi hedeflenen biçimlendirilmemiş metin yürütülmesi içerecek şekilde içerik türüdür. A <xref:System.Windows.Documents.Span> birden çok içerebilir <xref:System.Windows.Documents.Run> öğeleri.  
  
 İlk belge örnek ağ paylaşım adları çeşitli sahip bir belge içerir; Örneğin `\\server1\folder\file.ext`. Bu ağ bağlantısı olup bir Arapça veya İngilizce, her zaman aynı şekilde görünmesini istediğiniz belgede. Aşağıdaki grafikte bir Arapça bağlantıyı gösterir <xref:System.Windows.FlowDirection.RightToLeft> belge.  
  
 **Span öğesi kullanarak gösteren grafik**  
  
 ![Sağdan sola akan belge](../../../../docs/framework/wpf/advanced/media/flowdocument.PNG "FlowDocument")  
  
 Metin olduğundan <xref:System.Windows.FlowDirection.RightToLeft>, tüm özel karakterleri, gibi "\\", sol sipariş sağa metnin ayırın. Doğru sırayla gösterildikten değil bağlantıda sonuçları, bu nedenle sorunu çözmeyi metni ayrı bir korumak için gömülü olması gerekir <xref:System.Windows.Documents.Run> akan <xref:System.Windows.FlowDirection.LeftToRight>. Ayrı bir sahip olmak yerine <xref:System.Windows.Documents.Run> her dil için daha az sık kullanılan İngilizce metin daha büyük bir Arapça katıştırmak için sorunu çözmek için iyi bir yolu olan <xref:System.Windows.Documents.Span>.  
  
 Aşağıdaki grafikte bu gösterilmektedir.  
  
 **Bir Span öğesi katıştırılmış çalışma öğesini kullanarak gösteren grafik**  
  
 ![XamlPad ekran görüntüsü](../../../../docs/framework/wpf/advanced/media/runspan.PNG "RunSpan")  
  
 Aşağıdaki örnek, kullanma gösterir <xref:System.Windows.Documents.Run> ve <xref:System.Windows.Documents.Span> belgelerde öğeleri.  
  
 [!code-xaml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span öğeleri  
 <xref:System.Windows.Documents.Span> Öğesi akış yönleri farklı olan metinleri arasında sınır ayırıcı olarak çalışır.  Hatta <xref:System.Windows.Documents.Span> aynı akış yönü öğeleriyle anlamına farklı çift yönlü kapsamlar için değerlendirilir <xref:System.Windows.Documents.Span> öğeleri kapsayıcının içinde sıralı <xref:System.Windows.FlowDirection>, yalnızca içinde içerik <xref:System.Windows.Documents.Span> öğesi izleyen <xref:System.Windows.FlowDirection> , <xref:System.Windows.Documents.Span>.  
  
 Aşağıdaki grafikte birkaç akış yönünü gösteren <xref:System.Windows.Controls.TextBlock> öğeleri.  
  
 **Birkaç TextBlock öğelerinde FlowDirection gösteren grafik**  
  
 ![Akış yönleri farklı olan metin blokları](../../../../docs/framework/wpf/advanced/media/span.PNG "aralık")  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Documents.Span> ve <xref:System.Windows.Documents.Run> önceki grafikte gösterildiği sonuçlar öğeleri.  
  
 [!code-xaml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 İçinde <xref:System.Windows.Controls.TextBlock> örnek öğelerinde <xref:System.Windows.Documents.Span> öğeleri düzenlenir göre <xref:System.Windows.FlowDirection> üst ancak her içindeki metni <xref:System.Windows.Documents.Span> öğesi akışları göre kendi <xref:System.Windows.FlowDirection>. Bu Latin ve Arapça – veya başka bir dil için geçerlidir.  
  
### <a name="adding-xmllang"></a>XML: lang ekleme  
 Sayılar ve aritmetik ifadeler gibi kullanan başka bir örnek aşağıda görüldüğü `"200.0+21.4=221.4"`. Yalnızca bildirim <xref:System.Windows.FlowDirection> ayarlanır.  
  
 **Yalnızca FlowDirection kullanarak numaraları görüntüleyen grafik**  
  
 ![Sağdan sola akış numaraları](../../../../docs/framework/wpf/advanced/media/langattribute.PNG "LangAttribute")  
  
 Bu uygulama kullanıcılarının üzüntü çıktı tarafından rağmen <xref:System.Windows.FlowDirection> sayıları değil Arapça sayılar şeklinde gibi şeklinde doğrudur.  
  
 XAML öğeleri dahil edebileceğiniz bir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] özniteliği (`xml:lang`) her öğenin dil tanımlar. XAML de destekler bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dil ilkesine yapabildiği `xml:lang` ağacında üst öğeler için geçerli değerler, alt öğeleri tarafından kullanılır. Önceki örnekte, bir dil için tanımlı değil çünkü <xref:System.Windows.Documents.Run> öğesi ya da herhangi bir kendi üst düzey öğeleri, varsayılan `xml:lang` kullanılan olduğu `en-US` XAML için. Dahili numara şekillendirme algoritmasının [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] karşılık gelen dil – seçer numaraları bu durumda İngilizce. Arapça yapmak için numaraları işleme doğru `xml:lang` ayarlanması gerekir.  
  
 Aşağıdaki grafikte örnek ile gösterir `xml:lang` eklendi.  
  
 **Grafik gösterilmektedir kullanarak XML: lang özniteliği**  
  
 ![Arapça sayılar arasında sağdan sola akan](../../../../docs/framework/wpf/advanced/media/langattribute2.PNG "LangAttribute2")  
  
 Aşağıdaki örnek, `xml:lang` uygulama.  
  
 [!code-xaml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Birçok dil farklı olduğunu unutmayın `xml:lang` değerleri hedeflenen bölge için bağlı olarak `"ar-SA"` ve `"ar-EG"` Arapça iki çeşidi temsil eder. Önceki örneklerde her ikisi de tanımlamanız gerekecek göstermeye `xml:lang` ve <xref:System.Windows.FlowDirection> değerleri.  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>Metin dışı öğelerle FlowDirection  
 <xref:System.Windows.FlowDirection>yalnızca nasıl metin metinsel öğe aynı zamanda, neredeyse her diğer akış yönü içinde akar tanımlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğesi. Aşağıdaki grafik gösterildiği bir <xref:System.Windows.Controls.ToolBar> yatay kullanan <xref:System.Windows.Media.LinearGradientBrush> , arka plan çizmek için.  
  
 **Bir araç çubuğu bir soldan sağa gradyan ile gösteren grafik**  
  
 ![Gradyan ekran görüntüsü](../../../../docs/framework/wpf/advanced/media/gradient.PNG "gradyan")  
  
 Ayar sonra <xref:System.Windows.FlowDirection> için <xref:System.Windows.FlowDirection.RightToLeft>, değil yalnızca <xref:System.Windows.Controls.ToolBar> düğmeleri sağdan sola ancak bile düzenlenir <xref:System.Windows.Media.LinearGradientBrush> sağdan sola akış için kendi uzaklıkları yeniden hizalar.  
  
 Yeniden hizalama'yı, aşağıda görüldüğü <xref:System.Windows.Media.LinearGradientBrush>.  
  
 **Bir hakkına sahip bir araç için sol gradyan gösteren grafik**  
  
 ![Sağdan sola akan gradyan](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.PNG "Gradient2_WPF")  
  
 Aşağıdaki örnek çizer bir <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (Sağdan sola çizip için kaldırın <xref:System.Windows.FlowDirection> özniteliği <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>FlowDirection özel durumlar  
 Bazı durumlar vardır nerede <xref:System.Windows.FlowDirection> beklendiği gibi davranır değil. Bu bölüm iki bu özel durumları içerir.  
  
 **Görüntü**  
  
 Bir <xref:System.Windows.Controls.Image> resim görüntüleyen bir denetimi temsil eder. İçinde [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] ile birlikte kullanılabilir bir <xref:System.Windows.Controls.Image.Source%2A> tanımlayan özelliğini [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] , <xref:System.Windows.Controls.Image> görüntülemek için.  
  
 Diğer aksine [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri, bir <xref:System.Windows.Controls.Image> devralmaz <xref:System.Windows.FlowDirection> kapsayıcısından. Ancak, varsa <xref:System.Windows.FlowDirection> açıkça ayarlamak <xref:System.Windows.FlowDirection.RightToLeft>, bir <xref:System.Windows.Controls.Image> yatay çevrilmiş görüntülenir. Bu, çift yönlü içerik geliştiriciler için kullanışlı bir özellik olarak uygulanır; Bazı durumlarda, yatay olarak görüntüyü çevirme olmadığından istenilen efekti üretir.  
  
 Aşağıdaki grafikte bir çevrilen gösterir <xref:System.Windows.Controls.Image>.  
  
 **Döndürülen resim gösteren grafik**  
  
 ![XamlPad ekran görüntüsü](../../../../docs/framework/wpf/advanced/media/image.PNG "görüntüsü")  
  
 Aşağıdaki örnekte gösterilmiştir <xref:System.Windows.Controls.Image> devralmak başarısız <xref:System.Windows.FlowDirection> gelen <xref:System.Windows.Controls.StackPanel> , içerir. **Not** adlı bir dosya olmalıdır **ms_logo.jpg** C:\ sürücünüzde Bu örneği çalıştırmak için.  
  
 [!code-xaml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Not** yükleme dosyalarına dahil olduğu bir **ms_logo.jpg** dosya. Kod .jpg dosya projenizi içinde değil, ancak herhangi bir yerde C:\ sürücüsünde olduğunu varsayar. .jpg C:\ sürücünüzde proje dosyalarını kopyalama veya projesi içinde dosya aramak için kodu değiştirmeniz gerekir. Bu değişikliği yapmak için `Source="file://c:/ms_logo.jpg"` için `Source="ms_logo.jpg"`.  
  
 **Yolları**  
  
 Ek olarak bir <xref:System.Windows.Controls.Image>, başka bir ilginç öğesi <xref:System.Windows.Shapes.Path>. Bir yol bağlı çizgiler ve eğrilerle bir dizi çizebilirsiniz bir nesnedir. Benzer şekilde davranır bir <xref:System.Windows.Controls.Image> ilgili kendi <xref:System.Windows.FlowDirection>; Örneğin, <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> yatay bir yansıması kendi <xref:System.Windows.FlowDirection.LeftToRight> biri. Ancak, farklı bir <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> devralır kendi <xref:System.Windows.FlowDirection> kapsayıcısı ve bir açıkça belirtmeniz gerekmez.  
  
 Aşağıdaki örnek, 3 satır kullanarak basit bir ok çizer. İlk oku devralır <xref:System.Windows.FlowDirection.RightToLeft> akış yönü <xref:System.Windows.Controls.StackPanel> böylece kendi başlangıç ve bitiş noktaları sağ tarafında bir kök ölçülür. Açık olan ikinci oku <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> da sağ tarafta başlatılır. Ancak, üçüncü ok başlangıç kökü sol tarafta vardır. Bkz: çizim hakkında daha fazla bilgi için <xref:System.Windows.Media.LineGeometry> ve <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xaml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Aşağıdaki grafikte, önceki örnekte çıktısını gösterir.  
  
 **Yol öğesi kullanılarak çizilen okları gösteren grafik**  
  
 ![Yollar](../../../../docs/framework/wpf/advanced/media/paths.PNG "yolları")  
  
 <xref:System.Windows.Controls.Image> Ve <xref:System.Windows.Shapes.Path> bir nasıl iki örnekleri [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] kullanan <xref:System.Windows.FlowDirection>. Yerleştirmek yanında [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bir kapsayıcı içindeki belirli bir yönde öğeleri <xref:System.Windows.FlowDirection> öğeleriyle gibi kullanılabilir <xref:System.Windows.Controls.InkPresenter> bir yüzeyinde mürekkep işler <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Sol davranışı sağa doğru davranış soldan taklit eder içeriğiniz için ihtiyaç duyduğunuzda veya tam tersi, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bu yeteneği sağlar.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Sayı değiştirme  
 Geçmişte, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] sayı değiştirme örnek sayılar depolanmış için farklı yerel ayarlara arasında birleşik bu rakam iç depolama korurken farklı kültürel şekiller aynı basamak için gösterimini vererek desteklenen iyi bilinen onaltılık değerleri, 0x40, ancak seçilen dile göre görüntülenen 0x41.  
  
 Uygulamaları bunları bir dilden diğerine dönüştürmeyi gerek kalmadan sayısal değerleri işlemek izin verilen, örneğin bir kullanıcı açabilir bir [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] elektronik tabloda yerelleştirilmiş Arapça [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve Arapça'şeklinde numaralarını görebilirsiniz, ancak bunu açın Avrupa sürümü [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] ve Avrupa temsilini aynı numaralarını görebilirsiniz. Bunlar genellikle aynı belgedeki numaraları eşlik çünkü virgül ayırıcıları ve yüzde sembol gibi bu aynı zamanda diğer simgelerini gereklidir.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]aynı gelenek devam eder ve daha fazla değiştirme nasıl ve ne zaman kullanılır üzerinde daha fazla kullanıcı denetimi sağlayan bu özellik için destek ekler. Bu özellik herhangi bir dil için tasarlanmış olsa da, belirli bir dil için basamak şekillendirme genellikle Uygulama geliştiricileri için bir sınama uygulama çalışabilir çeşitli kültürler nedeniyle burada çift yönlü içerik özellikle yararlı olacaktır.  
  
 İçinde nasıl sayı değiştirme denetleme çekirdek özelliği çalıştığı [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] olan <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> bağımlılık özelliği. <xref:System.Windows.Media.NumberSubstitution> Sınıfı metin numaraları nasıl görüntüleneceğini belirtir. Davranışını tanımlayan üç ortak özellikleri vardır. Özelliklerin her biri bir özeti verilmiştir.  
  
 **CultureSource:**  
  
 Bu özellik, kültür numaraları için nasıl belirlendiğini belirtir. Üç birini sürdüğünü <xref:System.Windows.Media.NumberCultureSource> numaralandırma değerleri.  
  
-   Geçersiz kılma: Sayı, kültürdür <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> özelliği.  
  
-   Metin: Sayı, metin çalıştırma kültürünü kültürdür. Biçimlendirme içinde bu olacaktır `xml:lang`, veya diğer adını `Language` özelliği (<xref:System.Windows.FrameworkElement.Language%2A> veya <xref:System.Windows.FrameworkContentElement.Language%2A>). Ayrıca, türetilen sınıflar için varsayılan değer <xref:System.Windows.FrameworkContentElement>. Bu tür sınıflar dahil <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> ve benzeri.  
  
-   Kullanıcı: Sayı, geçerli iş parçacığı kültürünü kültürdür. Bu özellik tüm alt sınıflar için varsayılan değer <xref:System.Windows.FrameworkElement> gibi <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> ve <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride**:  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> Özelliği, yalnızca aşağıdaki durumlarda kullanılır <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> özelliği ayarlanmış <xref:System.Windows.Media.NumberCultureSource.Override> , aksi halde yoksayılır. Sayı kültürü belirtir. Değerini `null`, varsayılan değer, en-US yorumlanır.  
  
 **Değiştirme**:  
  
 Bu özellik gerçekleştirmek için sayı değiştirme türünü belirtir. Aşağıdakilerden birini sürdüğünü <xref:System.Windows.Media.NumberSubstitutionMethod> numaralandırma değerleri.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: Değiştirme yöntemi sayı kültürün üzerinde belirlenir <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> özelliği. Bu varsayılandır.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Numara kültür Arapça veya Farsça kültür ise, rakamları içeriğine bağlı olduğunu belirtir.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Sayılar her zaman Avrupa basamaklı olarak işlenir.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Sayılar kültürün tarafından belirtilen sayı kültür için Ulusal basamak kullanarak işlenir <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Sayılar sayı kültürü için geleneksel basamak kullanarak işlenir. Çoğu kültür için bu aynıdır <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Ancak, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> sonuçlanıyor Latin basamak bazı Arapça kültürler için bu değer tüm kültürler için kullanılabilecek Arapça Arapça basamaklı sonucunu.  
  
 Bu değerler için çift yönlü içerik Geliştirici anlamı nedir? Çoğu durumda, geliştirici yalnızca tanımlamanız gerekebilir <xref:System.Windows.FlowDirection> ve her metin dili [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] örneğin öğesi `Language="ar-SA"` ve <xref:System.Windows.Media.NumberSubstitution> mantığı sayıları doğru göre görüntüleme mvc'deki [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Aşağıdaki örnek, Arapça ve İngilizce numaraları kullanarak gösterir bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Arapça bir sürümünde çalışan uygulama [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xaml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Arapça bir sürümünde çalıştırıyorsanız, önceki örnek çıktı aşağıda görüldüğü [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 **Görüntülenen Arapça ve İngilizce numaralarının gösteren grafik**  
  
 ![Numaralarıyla XamlPad ekran](../../../../docs/framework/wpf/advanced/media/numbers.PNG "numaraları")  
  
 <xref:System.Windows.FlowDirection> Ayarı çünkü bu durumda önemli olduğunu <xref:System.Windows.FlowDirection> için <xref:System.Windows.FlowDirection.LeftToRight> Avrupa basamak yerine verdiğini. Aşağıdaki bölümlerde, belge boyunca basamak birleşik bir görünümünü sağlamak nasıl ele almaktadır. Bu örnek Arapça Windows üzerinde çalışmıyorsa, tüm rakamları Avrupa basamaklı olarak görüntüler.  
  
 **Değiştirme kurallarını tanımlama**  
  
 Gerçek bir uygulamada dili programlı olarak ayarlamak gerekebilir. Örneğin, ayarlamak istediğiniz `xml:lang` sistemin tarafından kullanılanla aynı olacak şekilde özniteliği [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], belki de dili veya uygulama durumu bağlı olarak değiştirme.  
  
 Yapmak istiyorsanız değişiklikleri uygulamanın durumuna dayalı, olun tarafından sağlanan diğer özelliklerin kullanmak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 İlk olarak, uygulama bileşenin ayarlamak `NumberSubstitution.CultureSource="Text"`. Bu ayarı kullanarak yapar ayarları gelen gelmeyen emin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] "Kullanıcı" gibi varsayılan olarak sahip metin öğeleri için <xref:System.Windows.Controls.TextBlock>.  
  
 Örneğin:  
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 Karşılık gelen [!INCLUDE[TLA2#tla_lhcshrp](../../../../includes/tla2sharptla-lhcshrp-md.md)] kod, ayarlamak `Language` özelliği örneğin `"ar-SA"`.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 Ayarlamak gerekiyorsa `Language` özelliği için geçerli kullanıcının [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dil şu kodu kullanın.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A>Çalışma zamanında geçerli iş parçacığı tarafından kullanılan geçerli kültürü temsil eder.  
  
 Son [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] örnek aşağıdaki örneğe benzer.  
  
 [!code-xaml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Son [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] örnek aşağıdakine benzer.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Aşağıdaki grafikte penceresini nasıl ya da programlama dili için göründüğünü gösterir.  
  
 **Arapça numaralarını görüntüler grafiği**  
  
 ![Arapça sayılar](../../../../docs/framework/wpf/advanced/media/numbers2.PNG "Numbers2")  
  
 **Değiştirme özelliği kullanılarak**  
  
 İçinde çalıştığı şekilde sayı değiştirme [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin öğesi hem bir dili üzerinde bağlıdır ve kendi <xref:System.Windows.FlowDirection>. Varsa <xref:System.Windows.FlowDirection> Avrupa rakamları işlendiğini sonra soldan sağa, olur. Ancak Arapça metin tarafından öncesinde veya dil ayarladı "ar" ve <xref:System.Windows.FlowDirection> olan <xref:System.Windows.FlowDirection.RightToLeft>, Arapça basamak yerine işlenir.  
  
 Ancak, bazı durumlarda, örneğin Avrupa rakamları tüm kullanıcılar için birleştirilmiş bir uygulama oluşturmak isteyebilirsiniz. Veya Arapça basamak <xref:System.Windows.Documents.Table> belirli bir hücrelerle <xref:System.Windows.Style>. Kullanıyor yapmak için bir kolay şekilde <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> özelliği.  
  
 Aşağıdaki örnekte, ilk <xref:System.Windows.Controls.TextBlock> sahip olmayan <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> özelliğini ayarlayın, böylece beklendiği algoritmanın Arapça basamak görüntüler. Ancak ikinci <xref:System.Windows.Controls.TextBlock>değiştirme Varsayılan değiştirme Arapça sayılar için geçersiz kılma Avrupa için ayarlanır ve Avrupa rakamları görüntülenir.  
  
 [!code-xaml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
