---
title: WPF Genel Bakışında Çift Yönlü Özellikler
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 4c3a39c1d1252951b0847638809c9e1e6be2a21e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856195"
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF Genel Bakışında Çift Yönlü Özellikler

Diğer herhangi bir geliştirme platformunun [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aksine, çift yönlü içeriğin hızlı bir şekilde geliştirilmesini destekleyen birçok özelliğe sahiptir, örneğin, soldan sağa ve sağdan sola verileri aynı belgede. Aynı zamanda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Arapça ve İbranice kullanıcılar gibi çift yönlü özellikler gerektiren kullanıcılar için mükemmel bir deneyim oluşturur.

Aşağıdaki bölümlerde çift yönlü içeriğin en iyi görüntüsüne nasıl ulaşılacağını gösteren örneklerle birlikte birçok çift yönlü özellikler açıklanmaktadır. Örneklerin çoğunun kullanımı [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], ancak kavramlarını C# veya Microsoft Visual Basic koduna kolayca uygulayabilir.

<a name="FlowDirection"></a>

## <a name="flowdirection"></a>FlowDirection

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bir<xref:System.Windows.FrameworkElement.FlowDirection%2A>uygulamadaki içerik akışı yönünü tanımlayan temel özellik. Bu özellik, ya <xref:System.Windows.FlowDirection.LeftToRight> <xref:System.Windows.FlowDirection.RightToLeft>da iki numaralandırma değerinden birine ayarlanabilir. Özelliği, öğesinden [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>devraldığı tüm öğeler için kullanılabilir.

Aşağıdaki örneklerde bir <xref:System.Windows.Controls.TextBox> öğenin akış yönü ayarlanır.

**Soldan sağa akış yönü**

[!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]

**Sağdan sola akış yönü**

[!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]

Aşağıdaki grafik, önceki kodun nasıl işlediğini gösterir.

![Farklı akış yönlerini gösteren grafik.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)

[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] Ağaç içindeki bir öğe, <xref:System.Windows.FrameworkElement.FlowDirection%2A> kapsayıcısını öğesinden devralacak. Aşağıdaki örnekte <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.Grid>, bir<xref:System.Windows.Window>içinde yer alır. İçin ayarı, <xref:System.Windows.Controls.Grid> ve içinayarlamayıgerektirir.<xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Window> <xref:System.Windows.FrameworkElement.FlowDirection%2A>

Aşağıdaki örnek ayarı <xref:System.Windows.FrameworkElement.FlowDirection%2A>gösterir.

[!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]

En üst düzey <xref:System.Windows.Window> bir <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>öğesine sahiptir, bu nedenle içinde yer alan tüm öğeler aynı zamanda <xref:System.Windows.FrameworkElement.FlowDirection%2A>aynı şekilde devralınır. Belirtilen <xref:System.Windows.FrameworkElement.FlowDirection%2A> bir öğenin geçersiz kılınması için <xref:System.Windows.Controls.TextBlock> , <xref:System.Windows.FlowDirection.LeftToRight>önceki örnekte olduğu gibi bir açık yön değişikliği eklemesi gerekir. Hiçbir <xref:System.Windows.FrameworkElement.FlowDirection%2A> değer tanımlandığında varsayılan değer <xref:System.Windows.FlowDirection.LeftToRight> geçerli olur.

Aşağıdaki grafikte, önceki örneğin çıktısı gösterilmektedir:

![Açık akış yönü değişikliğini gösteren grafik.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)

<a name="FlowDocument"></a>

## <a name="flowdocument"></a>FlowDocument

HTML [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ve Java gibi birçok geliştirme platformu çift yönlü içerik geliştirmeye yönelik özel destek sağlar. HTML gibi biçimlendirme dilleri içerik yazıcılarını, metni gerekli herhangi bir yöne (4,0 Örneğin, "RTL" veya "LTR" değeri olarak alan "dir") göstermek için gerekli işaretlemeleri sağlar. Bu etiket <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğine benzerdir, <xref:System.Windows.FrameworkElement.FlowDirection%2A> ancak özellik metin içeriğini düzene eklemek için daha gelişmiş bir şekilde çalışabilir ve metin dışındaki içerikler için kullanılabilir.

' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]De, <xref:System.Windows.Documents.FlowDocument> bir metin, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tablo, resim ve diğer öğelerin birleşimini barındırabileceğiniz çok yönlü bir öğedir. Aşağıdaki bölümlerdeki örnekler bu öğeyi kullanır.

Bir öğesine metin eklemek <xref:System.Windows.Documents.FlowDocument> , bir şekilde daha fazla yapılabilir. Bunu yapmanın basit bir yolu, metin gibi içerikleri <xref:System.Windows.Documents.Paragraph> gruplamak için kullanılan blok düzeyinde bir öğedir. Satır içi düzeyindeki öğelere metin eklemek için örnekleri ve <xref:System.Windows.Documents.Span> <xref:System.Windows.Documents.Run>kullanır. <xref:System.Windows.Documents.Span>, diğer satır içi öğeleri gruplandırmak için kullanılan bir satır içi düzey akış içerik öğesidir, ancak <xref:System.Windows.Documents.Run> biçimlendirilmemiş bir metnin çalıştırılmasını içeren bir satır içi düzey akış içerik öğesidir. , Birden çok <xref:System.Windows.Documents.Run> öğe içerebilir. <xref:System.Windows.Documents.Span>

İlk belge örneği, çeşitli ağ paylaşma adlarına sahip bir belge içerir; Örneğin `\\server1\folder\file.ext`. Arapça veya Ingilizce bir belgede bu ağ bağlantısına sahip olmanız, her zaman aynı şekilde görünmesini ister. Aşağıdaki grafik, span öğesinin kullanımını gösterir ve bir Arap <xref:System.Windows.FlowDirection.RightToLeft> belgesinde bağlantıyı gösterir:

![Span öğesini kullanmayı gösteren grafik.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")

Metin olduğu <xref:System.Windows.FlowDirection.RightToLeft>için, "\\" gibi tüm özel karakterler metni sağdan sola sırada ayırır. Bu, bağlantının doğru sırada gösterilmemektedir ve bu nedenle sorunu çözmek için metnin, ayrı <xref:System.Windows.Documents.Run> bir akışı <xref:System.Windows.FlowDirection.LeftToRight>korumak için katıştırılması gerekir. Her dil için ayrı <xref:System.Windows.Documents.Run> olmak yerine, sorunu çözmenin daha iyi bir yolu, daha az sıklıkta kullanılan İngilizce metni daha büyük bir Arap <xref:System.Windows.Documents.Span>içine katıştırmaktır.

Aşağıdaki grafikte, bir span öğesinde gömülü Run öğesi kullanılarak gösterilmektedir:

![Span öğesine gömülü Run öğesini gösteren grafik.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)

Aşağıdaki örnek, belgelerde ve <xref:System.Windows.Documents.Run> <xref:System.Windows.Documents.Span> öğelerinin kullanımını gösterir.

[!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]

<a name="SpanElements"></a>

## <a name="span-elements"></a>Span öğeleri

Öğesi <xref:System.Windows.Documents.Span> , farklı akış yönlerine sahip metinler arasında sınır ayırıcısı olarak da kullanılır.  Aynı <xref:System.Windows.Documents.Span> akış yönüne sahip öğeler çift yönlü kapsamlar <xref:System.Windows.Documents.Span> olacak şekilde değerlendirilir <xref:System.Windows.FlowDirection>, bu da öğelerin kapsayıcının içinde sıralandığı, yalnızca <xref:System.Windows.Documents.Span> öğenin içindeki içeridir <xref:System.Windows.FlowDirection> ' a<xref:System.Windows.Documents.Span>ait.

Aşağıdaki grafikte çeşitli <xref:System.Windows.Controls.TextBlock> öğelerin akış yönü gösterilmektedir.

![Farklı akış yönlerine sahip metin bloklarını gösteren grafik.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)

Aşağıdaki örnek, <xref:System.Windows.Documents.Span> ve <xref:System.Windows.Documents.Run> öğelerinin önceki grafikte gösterilen sonuçları oluşturmak için nasıl kullanılacağını gösterir.

[!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]

<xref:System.Windows.Documents.Span> <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection>Örnekteki <xref:System.Windows.Controls.TextBlock> öğelerdeöğeler,üstöğelerinegöredüzenlenir,ancakheröğeiçindekimetinkendi<xref:System.Windows.Documents.Span> kendine göre akar. Bu, Latin ve Arapça ya da başka bir dil için geçerlidir.

### <a name="adding-xmllang"></a>XML ekleme: lang

Aşağıdaki grafikte, `"200.0+21.4=221.4"`gibi sayılar ve aritmetik ifadeler kullanan başka bir örnek gösterilmektedir. Yalnızca <xref:System.Windows.FlowDirection> ayarlanmış olduğuna dikkat edin.

![Yalnızca FlowDirection kullanarak sayıları görüntüleyen grafik.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)

Bu uygulamanın kullanıcıları çıktı tarafından kaldırılır, ancak <xref:System.Windows.FlowDirection> doğru olsa bile sayılar Arapça sayılar şekillendirilmiş olmalıdır.

XAML öğeleri, her bir [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] öğenin dilini`xml:lang`tanımlayan bir özniteliği () içerebilir. XAML, ağaç içindeki [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] üst öğelere uygulanan `xml:lang` değerlerin alt öğeler tarafından kullanıldığı bir dil ilkesini de destekler. Önceki örnekte, bir dil <xref:System.Windows.Documents.Run> öğe veya en üst düzey öğelerinden herhangi biri için tanımlanmadığı için, varsayılan değer `xml:lang` xaml `en-US` için kullanılır. İç sayı şekillendirme algoritması, karşılık [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] gelen dilde (Bu örnekte İngilizce) sayıları seçer. Arapça sayıların doğru şekilde `xml:lang` işlemesini sağlamak için, ayarlanması gerekir.

Aşağıdaki grafikte, `xml:lang` eklenen örnek gösterilmektedir.

![Sağdan sola akan Arapça sayıları gösteren grafik.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)

Aşağıdaki örnek uygulamaya eklenir `xml:lang` .

[!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]

Örneğin, `xml:lang` `"ar-SA"` hedeflenen bölgeye bağlı olarak birçok dilin farklı değerlere sahip olduğunu unutmayın, ve `"ar-EG"` iki Arap çeşitlemelerini temsil edin. Önceki örneklerde, `xml:lang` ve <xref:System.Windows.FlowDirection> değerlerini tanımlamanız gerektiğini gösterir.

<a name="FlowDirectionNontext"></a>

## <a name="flowdirection-with-non-text-elements"></a>Metin olmayan öğelerle FlowDirection

<xref:System.Windows.FlowDirection>metnin bir metin öğesinde nasıl akar, ancak aynı zamanda neredeyse her [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğenin akış yönünü de tanımlar. Aşağıdaki grafikte, soldan sağa <xref:System.Windows.Controls.ToolBar> degradeyle arka planını <xref:System.Windows.Media.LinearGradientBrush> çizmek için yatay kullanılan bir gösterilmektedir.

![Soldan sağa degradeyle bir araç çubuğu gösteren grafik.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)

' I ' a ayarladıktan sonra, yalnızca <xref:System.Windows.Controls.ToolBar> düğmeler sağdan sola düzenlenirler, ancak hatta <xref:System.Windows.Media.LinearGradientBrush> uzaklıkları sağdan sola doğru hizalar. <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection.RightToLeft>

Aşağıdaki grafikte, <xref:System.Windows.Media.LinearGradientBrush>yeniden hizalaması gösterilmektedir.

![Sağdan sola degradeyle bir araç çubuğu gösteren grafik.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)

Aşağıdaki örnek bir <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>çizer. (Sola doğru çizmek için <xref:System.Windows.FlowDirection> <xref:System.Windows.Controls.ToolBar>üzerinde özniteliğini kaldırın.

[!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]

<a name="FlowDirectionExceptions"></a>

### <a name="flowdirection-exceptions"></a>FlowDirection özel durumları

Beklenen şekilde davranmayan birkaç durum <xref:System.Windows.FlowDirection> vardır. Bu bölümde bu özel durumların ikisi ele alınmaktadır.

**Görüntü**

Bir <xref:System.Windows.Controls.Image> görüntüyü görüntüleyen bir denetimi temsil eder. İçinde [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] , [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] <xref:System.Windows.Controls.Image.Source%2A> uygulamasının<xref:System.Windows.Controls.Image> görüntülenmesini tanımlayan bir özellik ile birlikte kullanılabilir.

Diğer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerin aksine, bir <xref:System.Windows.Controls.Image> , <xref:System.Windows.FlowDirection> kapsayıcısını sınıfından almaz. Ancak, <xref:System.Windows.FlowDirection.RightToLeft> açıkça<xref:System.Windows.Controls.Image> olarak ayarlandıysa, yatay olarak çevrilmiş görüntülenir. <xref:System.Windows.FlowDirection> Bu, çift yönlü içerik geliştiricileri için kullanışlı bir özellik olarak uygulanır; Bazı durumlarda görüntüyü yatay olarak çevirme istenen etkiyi üretir.

Aşağıdaki grafikte çevrilmiş <xref:System.Windows.Controls.Image>gösterilmektedir.

![Çevrilmiş bir görüntüyü gösteren grafik.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)

Aşağıdaki örnek, <xref:System.Windows.FlowDirection> öğesinden öğesini içeren <xref:System.Windows.Controls.Image> öğesinden <xref:System.Windows.Controls.StackPanel> devralmayı gösterir.

> [!NOTE]
> C:\ uygulamanızda **ms_logo. jpg** adlı bir dosyanız olmalıdır Bu örneği çalıştırmak için sürücü.

[!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]

> [!NOTE]
> İndirme dosyalarında yer alan bir **ms_logo. jpg** dosyasıdır. Kod. jpg dosyasının projenizin içinde, ancak C:\ ' da bir yerde olduğunu varsayar. sürücü. . Jpg dosyasını proje dosyalarından C:\ uygulamanıza kopyalamanız gerekir projenin içindeki dosyayı aramak için kodu sürücü olarak değiştirin veya değiştirin. Bu değişikliği `Source="file://c:/ms_logo.jpg"` `Source="ms_logo.jpg"`yapmak için.

**Yollar**

Buna ek <xref:System.Windows.Controls.Image>olarak, başka ilginç bir öğe olur <xref:System.Windows.Shapes.Path>. Yol, bir dizi bağlantılı çizgi ve eğri çizebileceğiniz bir nesnedir. Onunla <xref:System.Windows.Controls.Image> <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection.LeftToRight> ilgili benzer bir şekilde davranır ;Örneğin,onunyataybiryansımasıdır.<xref:System.Windows.FlowDirection> Bununla birlikte, bir <xref:System.Windows.Controls.Image> <xref:System.Windows.FlowDirection> sürümünden <xref:System.Windows.Shapes.Path> farklı olarak, kapsayıcısını kapsayımla devralır ve bir öğenin açıkça belirtilmesi gerekmez.

Aşağıdaki örnek 3 satır kullanarak basit bir ok çizer. İlk ok, başlangıç ve <xref:System.Windows.FlowDirection.RightToLeft> bitiş noktalarının sağ taraftaki <xref:System.Windows.Controls.StackPanel> bir köke göre ölçülmesi için akış yönünü öğesinden devralır. Bir açık <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> olan ikinci ok, sağ tarafta da başlatılır. Ancak, üçüncü ok sol tarafta başlangıç köküne sahiptir. Çizim hakkında daha fazla bilgi için <xref:System.Windows.Media.LineGeometry> bkz <xref:System.Windows.Media.GeometryGroup>. ve.

[!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]

Aşağıdaki grafik, bir önceki örneğin çıktısını `Path` öğesi kullanılarak çizilen oklarla gösterir:

![Yol öğesi kullanılarak çizilen okları gösteren grafik.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)

Ve <xref:System.Windows.Controls.Image> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] , öğesinin nasıl kullanılacağına dair iki <xref:System.Windows.FlowDirection>örnektir. <xref:System.Windows.Shapes.Path> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Öğelerin <xref:System.Windows.Controls.InkPresenter> bir <xref:System.Windows.Media.RadialGradientBrush>kapsayıcı içinde belirli bir yönde yerleştirme yanında,, <xref:System.Windows.Media.LinearGradientBrush>,,,,,,,, bir yüzey üzerinde mürekkep oluşturan,, ve gibi öğelerle birlikte kullanılabilir. <xref:System.Windows.FlowDirection> İçeriğiniz için, soldan sağa doğru davranışa veya bunun tersini sağlayan sağdan sola davranışa ihtiyacınız olduğunda, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bu özelliği sağlar.

<a name="NumberSubstitution"></a>

## <a name="number-substitution"></a>Sayı değiştirme

Tarihsel olarak, Windows, farklı kültürel şekillerin farklı yerel ayarlar arasında birleşirken aynı basamakların gösterimine izin vererek, sayı değişimini destekliyordu, örneğin sayılar bilinen onaltılık değerler, 0x40, 0x41, ancak seçilen dile göre gösteriliyor.

Bu, uygulamaların bir dilden diğerine dönüştürülmesi gerekmeden sayısal değerleri işlemesini izin bıraktı. Örneğin, bir Kullanıcı, yerelleştirilmiş bir Arap penceresinde bir [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] elektronik tablo açıp Arapça biçiminde şekillendirilmiş sayıları görebilir, ancak bunu bir Windows 'un Avrupa sürümü ve aynı sayıların Avrupa gösterimine bakın. Bu Ayrıca, genellikle aynı belgedeki sayıları karşılamadığı için virgül ayırıcıları ve yüzde simgesi gibi diğer semboller için de gereklidir.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]aynı gelenek devam eder ve bu özellik için, değiştirme ne zaman ve nasıl kullanıldığı konusunda daha fazla kullanıcı denetimine izin veren daha fazla destek ekler. Bu özellik herhangi bir dil için tasarlanırken, özellikle bir uygulamanın üzerinde çalışacağı çeşitli kültürler nedeniyle, belirli bir dile ait basamakların şekillendirmesinde genellikle uygulama geliştiricileri için bir zorluk olduğu çift yönlü içerik için yararlıdır.

' De [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> sayı değiştirme özelliğinin nasıl çalıştığını denetleyen Core özelliği, bağımlılık özelliğidir. Sınıfı <xref:System.Windows.Media.NumberSubstitution> , metindeki sayıların nasıl görüntüleneceğini belirtir. Davranışını tanımlayan üç ortak özelliği vardır. Aşağıda her bir özellik özeti verilmiştir.

**Külsal kaynak:**

Bu özellik, sayıların kültürünün nasıl belirlendiğini belirtir. Üç <xref:System.Windows.Media.NumberCultureSource> numaralandırma değerinden birini alır.

- Manızı Sayı kültürü özelliğin türüdür <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> .

- Metinleri Sayı kültürü, metin çalıştırmasının kültürüdür. Biçimlendirme ' de, bu ya `xml:lang`da diğer ad `Language` özelliği (<xref:System.Windows.FrameworkElement.Language%2A> veya <xref:System.Windows.FrameworkContentElement.Language%2A>) olur. Ayrıca, ' den <xref:System.Windows.FrameworkContentElement>türetilen sınıfların varsayılandır. Bu tür sınıflar <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> vb. içerir.

- Kullanıcısını Sayı kültürü geçerli iş parçacığının kültürüdür. <xref:System.Windows.FrameworkElement> Bu özellik <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> ve gibitümaltsınıflarıiçinvarsayılandır.<xref:System.Windows.Controls.TextBlock>

**CultureOverride**:

Özelliği yalnızca <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> özelliği olarak<xref:System.Windows.Media.NumberCultureSource.Override> ayarlanmışsa ve aksi durumda yoksayılırsa kullanılır. <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> Kültür sayısını belirtir. Değeri `null`, varsayılan değer en-US olarak yorumlanır.

**Değiştirme**:

Bu özellik, gerçekleştirilecek sayı değiştirme türünü belirtir. Aşağıdaki <xref:System.Windows.Media.NumberSubstitutionMethod> sabit listesi değerlerinden birini alır:

- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: Değiştirme yöntemi, sayı kültürünün <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> özelliğine göre belirlenir. Bu varsayılandır.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Sayı kültürü bir Arap veya Farsça kültürü ise, basamakların içeriğe göre olduğunu belirtir.

- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Sayılar her zaman Avrupa basamağı olarak işlenir.

- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Sayılar, kültür <xref:System.Globalization.CultureInfo.NumberFormat%2A>tarafından belirtildiği gibi, sayı kültürüne ilişkin ulusal basamaklar kullanılarak işlenir.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Sayılar, sayı kültürü için geleneksel basamaklar kullanılarak işlenir. Çoğu kültürde bu, ile <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>aynıdır. Ancak, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> bazı Arap kültürleri için Latin basamaklı sonuçlar oluşur, ancak bu değer tüm Arap kültürleri için Arap rakamlarına neden olur.

Bu değerler çift yönlü içerik geliştiricisi için ne anlama geliyor? Çoğu durumda, geliştirici yalnızca her <xref:System.Windows.FlowDirection> bir metinsel [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğenin yalnızca tanımlama ve dil için <xref:System.Windows.Media.NumberSubstitution> , örneğin `Language="ar-SA"` , [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]mantığa göre sayıların gösterilmesi için gerekli olacaktır. Aşağıdaki örnekte, Windows 'un Arapça bir sürümünde çalışan bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamada Arapça ve İngilizce sayıların kullanılması gösterilmektedir.

[!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]

Aşağıdaki grafikte, Arapça ve Ingilizce sayılarla Windows 'un Arapça bir sürümünde çalıştırıyorsanız önceki örneğin çıktısı gösterilmektedir:

![Arapça ve Ingilizce sayıları gösteren grafik.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)

Bu durumda, ' ın ' i olarak ayarlanması <xref:System.Windows.FlowDirection> , <xref:System.Windows.FlowDirection.LeftToRight> Avrupa rakamları olacak şekilde ayarlandığında önemlidir. <xref:System.Windows.FlowDirection> Aşağıdaki bölümlerde, belgenizin tamamında nasıl Birleşik bir basamak görüntüleneceği ele alınmaktadır. Bu örnek Arapça Windows üzerinde çalışmıyorsa, tüm basamaklar Avrupa rakamları olarak görüntülenir.

**Değiştirme kurallarını tanımlama**

Gerçek bir uygulamada dili programlı olarak ayarlamanız gerekebilir. Örneğin, `xml:lang` özniteliği [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]sistem tarafından kullanılan bir ile aynı olacak şekilde ayarlamak ya da uygulamanın durumuna bağlı olarak dili değiştirmek isteyebilirsiniz.

Uygulamanın durumuna göre değişiklik yapmak istiyorsanız, tarafından [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]sağlanmış diğer özelliklerden yararlanabilirsiniz.

İlk olarak, uygulama bileşeni `NumberSubstitution.CultureSource="Text"`' ni ayarlayın. Bu ayarın kullanılması, ayarların varsayılan [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.TextBlock>olarak "Kullanıcı" olan metin öğelerinden gelmediğinden emin olur.

Örneğin:

```xaml
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

Karşılık gelen C# kodda, `Language` özelliğini olarak `"ar-SA"`ayarlayın.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

`Language` Özelliği geçerli kullanıcının kullanıcı arabirimi diline ayarlamanız gerekiyorsa aşağıdaki kodu kullanın.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>çalışma zamanında geçerli iş parçacığı tarafından kullanılan geçerli kültürü temsil eder.

Son [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] örneğinizi aşağıdaki örneğe benzer olmalıdır.

[!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]

Son C# örneğinizi aşağıdakine benzer olmalıdır.

[!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]

Aşağıdaki grafik, pencerenin programlama dili için nasıl göründüğünü gösterir, Arapça sayıları görüntüler:

![Arapça sayıları görüntüleyen grafik.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)

**Değiştirme özelliğini kullanma**

' De [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sayı değiştirme çalışma yöntemi, hem metin öğesi hem de onun <xref:System.Windows.FlowDirection>diline bağlıdır. <xref:System.Windows.FlowDirection> Doğru ise, Avrupa rakamları işlenir. Ancak, daha önce Arapça metindiyse veya dili "ar" ve <xref:System.Windows.FlowDirection> ise <xref:System.Windows.FlowDirection.RightToLeft>, bu, bunun yerine Arapça basamaklar işlenir.

Ancak bazı durumlarda, birleştirilmiş bir uygulama oluşturmak isteyebilirsiniz, örneğin, tüm kullanıcılar için Avrupa rakamları. Ya da belirli <xref:System.Windows.Style>bir <xref:System.Windows.Documents.Table> hücrelerde Arapça basamaklar. Bunu yapmanın kolay bir yolu <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> özelliğini kullanmaktır.

Aşağıdaki örnekte, ilki <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> özellik kümesine sahip değildir, bu nedenle algoritma beklenen şekilde Arapça rakamları görüntüler. Bununla birlikte, ikinci <xref:System.Windows.Controls.TextBlock>olarak değiştirme, Arapça sayılar için varsayılan değişikliği geçersiz kılan Avrupa olarak ayarlanır ve Avrupa rakamları görüntülenir.

[!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
