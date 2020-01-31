---
title: Çift yönlü özelliklere genel bakış
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 17167b1afa5037998d9ea8ed679a66c89babe242
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741636"
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF Genel Bakışında Çift Yönlü Özellikler

Diğer tüm geliştirme platformlarından farklı olarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çift yönlü içeriğin hızlı bir şekilde geliştirilmesini destekleyen birçok özelliğe sahiptir, örneğin, soldan sağa ve sağdan sola verileri aynı belgede. Aynı zamanda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], Arapça ve Ibranice kullanıcılar gibi çift yönlü özellikler gerektiren kullanıcılar için mükemmel bir deneyim oluşturur.

Aşağıdaki bölümlerde çift yönlü içeriğin en iyi görüntüsüne nasıl ulaşılacağını gösteren örneklerle birlikte birçok çift yönlü özellikler açıklanmaktadır. Çoğu örnek XAML kullanır, ancak bu kavramları C# veya Microsoft Visual Basic koduna kolayca uygulayabilirsiniz.

<a name="FlowDirection"></a>

## <a name="flowdirection"></a>FlowDirection

Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamasındaki içerik akışı yönünü tanımlayan temel özellik <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Bu özellik, <xref:System.Windows.FlowDirection.LeftToRight> veya <xref:System.Windows.FlowDirection.RightToLeft>iki numaralandırma değerinden birine ayarlanabilir. Özelliği, <xref:System.Windows.FrameworkElement>devraldığı tüm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri için kullanılabilir.

Aşağıdaki örneklerde bir <xref:System.Windows.Controls.TextBox> öğesinin akış yönü ayarlanır.

**Soldan sağa akış yönü**

[!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]

**Sağdan sola akış yönü**

[!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]

Aşağıdaki grafik, önceki kodun nasıl işlediğini gösterir.

![Farklı akış yönlerini gösteren grafik.](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)

[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ağaç içindeki bir öğe, <xref:System.Windows.FrameworkElement.FlowDirection%2A> kapsayıcısından devralınır. Aşağıdaki örnekte <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Window>bulunan bir <xref:System.Windows.Controls.Grid>içindedir. <xref:System.Windows.Window> için <xref:System.Windows.FrameworkElement.FlowDirection%2A> ayarlamak, <xref:System.Windows.Controls.Grid> ve <xref:System.Windows.Controls.TextBlock> için ayarlamayı da gerektirir.

Aşağıdaki örnek, <xref:System.Windows.FrameworkElement.FlowDirection%2A>ayarlamayı gösterir.

[!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]

En üst düzey <xref:System.Windows.Window> bir <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>sahiptir, bu nedenle içinde yer alan tüm öğeler aynı <xref:System.Windows.FrameworkElement.FlowDirection%2A>de devralınır. Bir öğenin belirtilen bir <xref:System.Windows.FrameworkElement.FlowDirection%2A> geçersiz kılması için, önceki örnekteki <xref:System.Windows.FlowDirection.LeftToRight>değişiklikler olan ikinci <xref:System.Windows.Controls.TextBlock> gibi bir açık yön değişikliği eklemesi gerekir. <xref:System.Windows.FrameworkElement.FlowDirection%2A> tanımlanmadığı zaman, varsayılan <xref:System.Windows.FlowDirection.LeftToRight> geçerli olur.

Aşağıdaki grafikte, önceki örneğin çıktısı gösterilmektedir:

![Açık akış yönü değişikliğini gösteren grafik.](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)

<a name="FlowDocument"></a>

## <a name="flowdocument"></a>FlowDocument

HTML, Win32 ve Java gibi birçok geliştirme platformu çift yönlü içerik geliştirmeye yönelik özel destek sağlar. HTML gibi biçimlendirme dilleri içerik yazıcılarını, metni gerekli herhangi bir yöne (4,0 Örneğin, "RTL" veya "LTR" değeri olarak alan "dir") göstermek için gerekli işaretlemeleri sağlar. Bu etiket <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğine benzer, ancak <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği metin içeriğini düzene eklemek için daha gelişmiş bir şekilde çalışabilir ve metin dışındaki içerikler için kullanılabilir.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir <xref:System.Windows.Documents.FlowDocument> metin, tablo, resim ve diğer öğelerin birleşimini barındırabileceğiniz çok yönlü bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğesidir. Aşağıdaki bölümlerdeki örnekler bu öğeyi kullanır.

Bir <xref:System.Windows.Documents.FlowDocument> metin eklemek tek bir şekilde yapılabilir. Bunu yapmanın basit bir yolu, metin gibi içerikleri gruplamak için kullanılan blok düzeyinde bir öğe olan <xref:System.Windows.Documents.Paragraph> kullanmaktır. Satır içi düzeyindeki öğelere metin eklemek için örnekler <xref:System.Windows.Documents.Span> ve <xref:System.Windows.Documents.Run>kullanır. <xref:System.Windows.Documents.Span>, diğer satır içi öğeleri gruplandırmak için kullanılan bir satır içi düzey akış içerik öğesidir. <xref:System.Windows.Documents.Run>, biçimlendirilmemiş bir metnin çalıştırılmasını sağlamak için bir satır içi düzey akış içerik öğesidir. <xref:System.Windows.Documents.Span> birden çok <xref:System.Windows.Documents.Run> öğesi içerebilir.

İlk belge örneği, çeşitli ağ paylaşma adlarına sahip bir belge içerir; Örneğin `\\server1\folder\file.ext`. Arapça veya Ingilizce bir belgede bu ağ bağlantısına sahip olmanız, her zaman aynı şekilde görünmesini ister. Aşağıdaki grafik, span öğesinin kullanımını gösterir ve bağlantıyı bir Arap <xref:System.Windows.FlowDirection.RightToLeft> belgesinde gösterir:

![Span öğesini kullanmayı gösteren grafik.](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")

Metin <xref:System.Windows.FlowDirection.RightToLeft>olduğundan, "\\" gibi tüm özel karakterler metni sağdan sola sırada ayırır. Bu, bağlantının doğru sırada gösterilmeme sonucu olarak, bu nedenle sorunu çözmek için metnin, ayrı bir <xref:System.Windows.Documents.Run> akan <xref:System.Windows.FlowDirection.LeftToRight>korunması için katıştırılması gerekir. Her dil için ayrı bir <xref:System.Windows.Documents.Run> olmak yerine, sorunu çözmenin daha iyi bir yolu, daha az sıklıkta kullanılan Ingilizce metni daha büyük bir Arap <xref:System.Windows.Documents.Span>içine gömmaktır.

Aşağıdaki grafikte, bir span öğesinde gömülü Run öğesi kullanılarak gösterilmektedir:

![Span öğesine gömülü Run öğesini gösteren grafik.](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)

Aşağıdaki örnek, belgelerindeki <xref:System.Windows.Documents.Run> ve <xref:System.Windows.Documents.Span> öğelerin kullanımını gösterir.

[!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]

<a name="SpanElements"></a>

## <a name="span-elements"></a>Span öğeleri

<xref:System.Windows.Documents.Span> öğesi, farklı akış yönlerine sahip metinler arasında sınır ayırıcısı olarak çalışarak.  Aynı akış yönüne sahip <xref:System.Windows.Documents.Span> öğeler çift yönlü kapsamlar olacak şekilde değerlendirilir, bu da <xref:System.Windows.Documents.Span> öğelerinin kapsayıcının <xref:System.Windows.FlowDirection>sıralı olduğu anlamına gelir. Bu, yalnızca <xref:System.Windows.Documents.Span> öğesi içindeki içerik <xref:System.Windows.FlowDirection> <xref:System.Windows.Documents.Span>izler.

Aşağıdaki grafikte, birkaç <xref:System.Windows.Controls.TextBlock> öğesinin akış yönü gösterilmektedir.

![Farklı akış yönlerine sahip metin bloklarını gösteren grafik.](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)

Aşağıdaki örnek, önceki grafikte gösterilen sonuçları oluşturmak için <xref:System.Windows.Documents.Span> ve <xref:System.Windows.Documents.Run> öğelerinin nasıl kullanılacağını gösterir.

[!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]

Örnekteki <xref:System.Windows.Controls.TextBlock> öğelerinde, <xref:System.Windows.Documents.Span> öğeleri üst öğelerinin <xref:System.Windows.FlowDirection> göre düzenlenir, ancak her <xref:System.Windows.Documents.Span> öğesi içindeki metin kendi <xref:System.Windows.FlowDirection>göre akar. Bu, Latin ve Arapça ya da başka bir dil için geçerlidir.

### <a name="adding-xmllang"></a>XML ekleme: lang

Aşağıdaki grafikte, `"200.0+21.4=221.4"`gibi sayılar ve aritmetik ifadeler kullanan başka bir örnek gösterilmektedir. Yalnızca <xref:System.Windows.FlowDirection> ayarlandığından emin olun.

![Yalnızca FlowDirection kullanarak sayıları görüntüleyen grafik.](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)

<xref:System.Windows.FlowDirection> doğru olsa bile, bu uygulamanın kullanıcıları çıktı tarafından geri alınacaktır ve Arapça sayıların şekillendirilmiş olması gerekir.

XAML öğeleri, her bir öğenin dilini tanımlayan bir XML özniteliği (`xml:lang`) içerebilir. XAML ayrıca ağaç içindeki üst öğelere uygulanan `xml:lang` değerlerinin alt öğeler tarafından kullanıldığı bir XML dili ilkesini destekler. Önceki örnekte, <xref:System.Windows.Documents.Run> öğesi veya en üst düzey öğelerinden herhangi biri için bir dil tanımlanmadığı için, varsayılan `xml:lang` kullanılmıştır, bu da XAML için `en-US`. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] iç numarası şekillendirme algoritması, karşılık gelen dilde (Bu örnekte Ingilizce) sayıları seçer. Arapça sayıların doğru şekilde işlemesini sağlamak için `xml:lang` ayarlanması gerekir.

Aşağıdaki grafikte `xml:lang` eklenen örnek gösterilmektedir.

![Sağdan sola akan Arapça sayıları gösteren grafik.](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)

Aşağıdaki örnek uygulamaya `xml:lang` ekler.

[!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]

Birçok dilin hedeflenen bölgeye göre farklı `xml:lang` değerlere sahip olduğunu unutmayın, örneğin, `"ar-SA"` ve `"ar-EG"` iki Arap çeşitlemelerini temsil eder. Önceki örneklerde `xml:lang` ve <xref:System.Windows.FlowDirection> değerlerinin her ikisini de tanımlamanız gerektiğini gösterir.

<a name="FlowDirectionNontext"></a>

## <a name="flowdirection-with-non-text-elements"></a>Metin olmayan öğelerle FlowDirection

<xref:System.Windows.FlowDirection>, metin öğesinde yalnızca metnin nasıl akacağını, aynı zamanda neredeyse her bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğesinin akış yönünü de tanımlar. Aşağıdaki grafikte, soldan sağa degradeyle arka planını çizmek için yatay bir <xref:System.Windows.Media.LinearGradientBrush> kullanan bir <xref:System.Windows.Controls.ToolBar> gösterilmektedir.

![Soldan sağa degradeyle bir araç çubuğu gösteren grafik.](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)

<xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection.RightToLeft>ayarlandıktan sonra, yalnızca <xref:System.Windows.Controls.ToolBar> düğmeleri sağdan sola düzenlenirler, ancak <xref:System.Windows.Media.LinearGradientBrush>, uzaklıkları sağdan sola doğru bir şekilde yeniden hizalar.

Aşağıdaki grafikte <xref:System.Windows.Media.LinearGradientBrush>yeniden hizalaması gösterilmektedir.

![Sağdan sola degradeyle bir araç çubuğu gösteren grafik.](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)

Aşağıdaki örnekte bir <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.Controls.ToolBar>çizilmiştir. (Sola doğru çizmek için, <xref:System.Windows.Controls.ToolBar><xref:System.Windows.FlowDirection> özniteliğini kaldırın.

[!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]

<a name="FlowDirectionExceptions"></a>

### <a name="flowdirection-exceptions"></a>FlowDirection özel durumları

<xref:System.Windows.FlowDirection> beklendiği gibi davranmayan birkaç durum vardır. Bu bölümde bu özel durumların ikisi ele alınmaktadır.

**Görüntü**

<xref:System.Windows.Controls.Image>, bir görüntüyü görüntüleyen bir denetimi temsil eder. XAML 'de, görüntülenecek <xref:System.Windows.Controls.Image> Tekdüzen Kaynak tanımlayıcısını (URI) tanımlayan bir <xref:System.Windows.Controls.Image.Source%2A> özelliği ile birlikte kullanılabilir.

Diğer [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğelerinden farklı olarak, bir <xref:System.Windows.Controls.Image>, kapsayıcıdan <xref:System.Windows.FlowDirection> almıyor. Ancak <xref:System.Windows.FlowDirection> açıkça <xref:System.Windows.FlowDirection.RightToLeft>olarak ayarlandıysa, yatay olarak çevrilmiş bir <xref:System.Windows.Controls.Image> görüntülenir. Bu, çift yönlü içerik geliştiricileri için kullanışlı bir özellik olarak uygulanır; Bazı durumlarda görüntüyü yatay olarak çevirme istenen etkiyi üretir.

Aşağıdaki grafikte çevrilmiş bir <xref:System.Windows.Controls.Image>gösterilmektedir.

![Çevrilmiş bir görüntüyü gösteren grafik.](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)

Aşağıdaki örnek, <xref:System.Windows.Controls.Image> <xref:System.Windows.FlowDirection> kendisini içeren <xref:System.Windows.Controls.StackPanel> devralmayı başarabileceğinizi gösterir.

> [!NOTE]
> C:\ uygulamanızda **ms_logo. jpg** adlı bir dosyanız olmalıdır Bu örneği çalıştırmak için sürücü.

[!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]

> [!NOTE]
> İndirme dosyalarında yer alan bir **ms_logo. jpg** dosyasıdır. Kod. jpg dosyasının projenizin içinde, ancak C:\ ' da bir yerde olduğunu varsayar. sürücü. . Jpg dosyasını proje dosyalarından C:\ uygulamanıza kopyalamanız gerekir projenin içindeki dosyayı aramak için kodu sürücü olarak değiştirin veya değiştirin. Bunu yapmak için `Source="file://c:/ms_logo.jpg"` `Source="ms_logo.jpg"`.

**Yollar**

Bir <xref:System.Windows.Controls.Image>ek olarak, başka bir ilgi çekici öğe <xref:System.Windows.Shapes.Path>. Yol, bir dizi bağlantılı çizgi ve eğri çizebileceğiniz bir nesnedir. <xref:System.Windows.FlowDirection>ilgili <xref:System.Windows.Controls.Image> benzer bir şekilde davranır; Örneğin <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>, <xref:System.Windows.FlowDirection.LeftToRight> bir yatay yansıtmadır. Ancak, bir <xref:System.Windows.Controls.Image>farklı olarak, <xref:System.Windows.Shapes.Path> <xref:System.Windows.FlowDirection> kapsayıcıdan devralır ve bunun açıkça belirtilmesi gerekmez.

Aşağıdaki örnek 3 satır kullanarak basit bir ok çizer. İlk ok, başlangıç ve bitiş noktalarının sağ taraftaki bir köke göre ölçülmesi için <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.FlowDirection.RightToLeft> akış yönünü devralır. Açık bir <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection> olan ikinci ok, sağ tarafta da başlatılır. Ancak, üçüncü ok sol tarafta başlangıç köküne sahiptir. Çizim hakkında daha fazla bilgi için bkz. <xref:System.Windows.Media.LineGeometry> ve <xref:System.Windows.Media.GeometryGroup>.

[!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]

Aşağıdaki grafikte, `Path` öğesi kullanılarak çizilen oklarla birlikte önceki örneğin çıktısı gösterilmektedir:

![Yol öğesi kullanılarak çizilen okları gösteren grafik.](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)

<xref:System.Windows.Controls.Image> ve <xref:System.Windows.Shapes.Path>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.FlowDirection>nasıl kullandığını gösteren iki örnektir. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğeleri bir kapsayıcı içinde belirli bir yönde yerleştirmek için <xref:System.Windows.FlowDirection>, bir yüzey, <xref:System.Windows.Media.LinearGradientBrush><xref:System.Windows.Media.RadialGradientBrush>mürekkebi işleyen <xref:System.Windows.Controls.InkPresenter> gibi öğeler ile kullanılabilir. İçeriğiniz için, soldan sağa doğru davranışa benzer veya tam tersi yönde bir sağdan sola davranışa ihtiyacınız olduğunda, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bu yeteneği sağlar.

<a name="NumberSubstitution"></a>

## <a name="number-substitution"></a>Sayı değiştirme

Tarihsel olarak, Windows, farklı kültürel şekillerin farklı yerel ayarlar arasında birleşirken aynı basamakların gösterimine izin vererek, sayı değişimini destekliyordu, örneğin sayılar bilinen onaltılık değerler, 0x40, 0x41, ancak seçilen dile göre gösteriliyor.

Bu, uygulamaların bir dilden diğerine dönüştürülmesi gerekmeden sayısal değerleri işlemesini izin bıraktı. Örneğin, bir Kullanıcı bir Microsoft Excel elektronik tablosunu yerelleştirilmiş bir Arapça penceresinde açabilir ve Arap dilinde şekillendirilmiş sayıları görebilir, ancak bunu bir Windows 'un Avrupa sürümü ve aynı sayıların Avrupa gösterimine bakın. Bu Ayrıca, genellikle aynı belgedeki sayıları karşılamadığı için virgül ayırıcıları ve yüzde simgesi gibi diğer semboller için de gereklidir.

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aynı gelenek devam eder ve bu özellik için, değiştirme ne zaman ve nasıl kullanıldığı konusunda daha fazla kullanıcı denetimine izin veren daha fazla destek ekler. Bu özellik herhangi bir dil için tasarlanırken, özellikle bir uygulamanın üzerinde çalışacağı çeşitli kültürler nedeniyle, belirli bir dile ait basamakların şekillendirmesinde genellikle uygulama geliştiricileri için bir zorluk olduğu çift yönlü içerik için yararlıdır.

Sayı değiştirme 'nin [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ' de nasıl çalıştığını denetleyen Core özelliği <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> Dependency özelliğidir. <xref:System.Windows.Media.NumberSubstitution> sınıfı, metindeki sayıların nasıl görüntüleneceğini belirtir. Davranışını tanımlayan üç ortak özelliği vardır. Aşağıda her bir özellik özeti verilmiştir:

**Külsal kaynak:**

Bu özellik, sayıların kültürünün nasıl belirlendiğini belirtir. Üç <xref:System.Windows.Media.NumberCultureSource> numaralandırma değerinden birini alır.

- Override: Number kültürü <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> özelliğinden oluşur.

- Metin: sayı kültürü, metin çalıştırmasının kültürüdür. Biçimlendirme ' de bu `xml:lang`veya diğer adı `Language` özelliği (<xref:System.Windows.FrameworkElement.Language%2A> ya da <xref:System.Windows.FrameworkContentElement.Language%2A>) olur. Ayrıca, <xref:System.Windows.FrameworkContentElement>türetilen sınıflar için varsayılandır. Bu tür sınıflar <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> vb. içerir.

- Kullanıcı: sayı kültürü geçerli iş parçacığının kültürüdür. Bu özellik, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> ve <xref:System.Windows.Controls.TextBlock>gibi tüm <xref:System.Windows.FrameworkElement> alt sınıfları için varsayılandır.

**CultureOverride**:

<xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> özelliği, yalnızca <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> özelliği <xref:System.Windows.Media.NumberCultureSource.Override> olarak ayarlandıysa ve aksi durumda yoksayılırsa kullanılır. Kültür sayısını belirtir. Varsayılan değer olan `null`değeri en-US olarak yorumlanır.

**Değiştirme**:

Bu özellik, gerçekleştirilecek sayı değiştirme türünü belirtir. Aşağıdaki <xref:System.Windows.Media.NumberSubstitutionMethod> numaralandırma değerlerinden birini alır:

- <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: değiştirme yöntemi, sayı kültürünün <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> özelliğine göre belirlenir. Bu varsayılandır.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: sayı kültürü bir Arap veya Farsça kültürü ise, basamakların içeriğe göre olduğunu belirtir.

- <xref:System.Windows.Media.NumberSubstitutionMethod.European>: sayılar her zaman Avrupa basamağı olarak işlenir.

- <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: sayılar, kültürün <xref:System.Globalization.CultureInfo.NumberFormat%2A>belirtildiği şekilde, sayı kültürü için ulusal basamaklar kullanılarak işlenir.

- <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: sayılar, sayı kültürü için geleneksel basamaklar kullanılarak işlenir. Çoğu kültürde, bu <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>aynıdır. Ancak, bazı Arap kültürleri için <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>, bu değer tüm Arap kültürleri için Arapça basamağa neden olur.

Bu değerler çift yönlü içerik geliştiricisi için ne anlama geliyor? Çoğu durumda, geliştiricinin yalnızca her bir metinsel [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] öğesi için <xref:System.Windows.FlowDirection> ve dilini tanımlama ihtiyacı vardır, örneğin `Language="ar-SA"` ve <xref:System.Windows.Media.NumberSubstitution> Logic, sayıları doğru [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]göre görüntüleme konusunda işlem gerçekleştirir. Aşağıdaki örnek, Windows 'un Arapça bir sürümünde çalışan bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamasındaki Arapça ve Ingilizce sayıların kullanımını gösterir.

[!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]

Aşağıdaki grafikte, Arapça ve Ingilizce sayılarla Windows 'un Arapça bir sürümünde çalıştırıyorsanız önceki örneğin çıktısı gösterilmektedir:

![Arapça ve Ingilizce sayıları gösteren grafik.](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)

<xref:System.Windows.FlowDirection>, <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection.LeftToRight> olarak ayarlanması, bu durumda, bu örnekte önemlidir. Aşağıdaki bölümlerde, belgenizin tamamında nasıl Birleşik bir basamak görüntüleneceği ele alınmaktadır. Bu örnek Arapça Windows üzerinde çalışmıyorsa, tüm basamaklar Avrupa rakamları olarak görüntülenir.

**Değiştirme kurallarını tanımlama**

Gerçek bir uygulamada dili programlı olarak ayarlamanız gerekebilir. Örneğin, `xml:lang` özniteliğini sistemin [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]tarafından kullanılan bir ile aynı olacak şekilde ayarlamak ya da uygulamanın durumuna bağlı olarak dili değiştirmek isteyebilirsiniz.

Uygulamanın durumuna göre değişiklik yapmak istiyorsanız, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]tarafından sunulan diğer özelliklerden yararlanabilirsiniz.

İlk olarak, uygulama bileşeni `NumberSubstitution.CultureSource="Text"`ayarlayın. Bu ayarın kullanılması, ayarların <xref:System.Windows.Controls.TextBlock>gibi "user" olan metin öğeleri için [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gelmediğinden emin olur.

Örneğin:

```xaml
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

Karşılık gelen C# kodda `Language` özelliğini, örneğin `"ar-SA"`olarak ayarlayın.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

`Language` özelliğini geçerli kullanıcının kullanıcı arabirimi diline ayarlamanız gerekirse aşağıdaki kodu kullanın.

```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, geçerli iş parçacığı tarafından çalışma zamanında kullanılan geçerli kültürü temsil eder.

Son XAML örneğinizi aşağıdaki örneğe benzer olmalıdır.

[!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]

Son C# örneğinizi aşağıdakine benzer olmalıdır.

[!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]

Aşağıdaki grafik, pencerenin programlama dili için nasıl göründüğünü gösterir, Arapça sayıları görüntüler:

![Arapça sayıları görüntüleyen grafik.](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)

**Değiştirme özelliğini kullanma**

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] değiştirme şekli, hem metin öğesi hem de <xref:System.Windows.FlowDirection>diline bağlıdır. <xref:System.Windows.FlowDirection> sağa doğru ise Avrupa rakamları işlenir. Ancak, daha önce Arapça metin veya dili "ar" olarak ayarlanmış ve <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection.RightToLeft>ise Arapça basamaklar işlenir.

Ancak bazı durumlarda, birleştirilmiş bir uygulama oluşturmak isteyebilirsiniz, örneğin, tüm kullanıcılar için Avrupa rakamları. Ya da belirli bir <xref:System.Windows.Style><xref:System.Windows.Documents.Table> hücrelerde Arapça basamaklar. Bunu yapmanın kolay bir yolu <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> özelliğini kullanmaktır.

Aşağıdaki örnekte, ilk <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> özelliği ayarlanmamış, bu nedenle algoritma, Arapça rakamları beklenen şekilde görüntülüyor. Ancak ikinci <xref:System.Windows.Controls.TextBlock>değiştirme, Arapça sayılar için varsayılan değişikliği geçersiz kılan Avrupa olarak ayarlanır ve Avrupa rakamları görüntülenir.

[!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
