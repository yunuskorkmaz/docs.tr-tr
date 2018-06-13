---
title: Görsel Taslaklara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 36922dce795443a4c1136f6442eff1c297f3c641
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566905"
---
# <a name="storyboards-overview"></a>Görsel Taslaklara Genel Bakış
Bu konuda nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Storyboard> Animasyonların düzenlenmesi ve nesnelere. Etkileşimli olarak nasıl işleneceğini açıklayan <xref:System.Windows.Media.Animation.Storyboard> nesneleri ve dolaylı özellik hedeflemesi sözdizimini açıklar.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için farklı animasyon türleri ve bunların temel özellikleri hakkında bilgi sahibi olmanız gerekir. Animasyon giriş için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Ayrıca, ekli özelliklerinin nasıl kullanılacağını bilmeniz gerekir. Ekli özellikler hakkında daha fazla bilgi için bkz: [bağlı özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>Film şeridi nedir?  
 Animasyon zaman çizelgesi yalnızca yararlı bir tür değildir. Diğer zaman çizelgesi sınıfları zaman çizelgeleri kümelerinin düzenlenmesine yardımcı olmak ve zaman çizelgelerini özelliklerine uygulamak için sağlanır. Kapsayıcı zaman çizelgeleri türetilen <xref:System.Windows.Media.Animation.TimelineGroup> sınıfı ve dahil <xref:System.Windows.Media.Animation.ParallelTimeline> ve <xref:System.Windows.Media.Animation.Storyboard>.  
  
 A <xref:System.Windows.Media.Animation.Storyboard> içerdiği zaman çizelgeleri için hedefleme bilgisini sağlayan kapsayıcı zaman çizelgesi türüdür. Film şeridi herhangi bir türde içerebilir <xref:System.Windows.Media.Animation.Timeline>diğer kapsayıcı zaman çizelgeleri ve animasyonları dahil olmak üzere. <xref:System.Windows.Media.Animation.Storyboard> nesneleri, düzenlemek ve karmaşık zamanlama davranışlarını denetlemek kolaylaşır tek bir zaman çizelgesi ağacında, çeşitli nesneleri ve özellikleri etkileyen zaman çizelgelerini birleştirmenize olanak sağlar. Örneğin, bu üç şeyi yapan bir düğme istediğinizi varsayalım.  
  
-   Büyüme ve kullanıcı düğmesini seçtiğinde rengini değiştirin.  
  
-   Küçülür ve tıklatıldığında geri özgün boyutuna büyüt.  
  
-   Daraltma ve devre dışı kalır, yüzde 50 opaklık silinerek.  
  
 Bu durumda, aynı nesneye uygulanan bir animasyon birden çok kümelerine sahip ve farklı zamanlarda düğmenin durumunu bağımlı yürütmek istediğiniz. <xref:System.Windows.Media.Animation.Storyboard> nesneleri, animasyonları düzenlemenizi ve gruplar halinde bir veya daha fazla nesneye uygulamanızı sağlar.  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>Burada bir film şeridi kullanabilir miyim?  
 A <xref:System.Windows.Media.Animation.Storyboard> canlandırılabilir sınıfların bağımlılık özellikleri animasyon için kullanılabilir (bir sınıfı neyin canlandırılabilir yapacağı hakkında daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)). Film şeridi yapma framework düzeyi bir özellik olduğundan, ancak nesne ait olmalı <xref:System.Windows.NameScope> , bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>.  
  
 Örneğin, kullanabilirsiniz bir <xref:System.Windows.Media.Animation.Storyboard> aşağıdakileri yapmak için:  
  
-   Animasyon bir <xref:System.Windows.Media.SolidColorBrush> (çerçevesi olmayan öğe), boyar düğmesinin arka plan (bir tür <xref:System.Windows.FrameworkElement>),  
  
-   Animasyon bir <xref:System.Windows.Media.SolidColorBrush> (çerçevesi olmayan öğe), boyar dolgusunu bir <xref:System.Windows.Media.GeometryDrawing> (çerçevesi olmayan öğe) kullanarak görüntülenen bir <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).  
  
-   Kodda, animasyon bir <xref:System.Windows.Media.SolidColorBrush> de içeren bir sınıf tarafından bildirilen bir <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Media.SolidColorBrush> adı ile kayıt <xref:System.Windows.FrameworkElement>.  
  
 Ancak, siz kullanılamadı bir <xref:System.Windows.Media.Animation.Storyboard> animasyon uygulamak için bir <xref:System.Windows.Media.SolidColorBrush> adıyla kaydetmemiş bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, veya bir özelliğini ayarlamak için kullanılmayan bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>.  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>Film şeridi ile animasyonların nasıl  
 Kullanılacak bir <xref:System.Windows.Media.Animation.Storyboard> animasyonların ve düzenlemek için animasyonları 'un alt zaman çizelgeleri olarak eklemeniz <xref:System.Windows.Media.Animation.Storyboard>. <xref:System.Windows.Media.Animation.Storyboard> SAX <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> ekli özellikler. Hedef nesne ve özelliği belirtmek için bir animasyon bu özellikleri ayarlayın.  
  
 Animasyonları hedeflerine uygulamak için başlamadan <xref:System.Windows.Media.Animation.Storyboard> tetikleyici eylem veya bir yöntem kullanarak. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullandığınız bir <xref:System.Windows.Media.Animation.BeginStoryboard> nesnesi ile bir <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>, veya <xref:System.Windows.DataTrigger>. Kod içinde de kullanabilirsiniz <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi.  
  
 Aşağıdaki tabloda farklı yerlerde gösterilmektedir burada her <xref:System.Windows.Media.Animation.Storyboard> başlamak teknik desteklenir: örnek başına, stil, denetim şablonu ve veri şablonu. "Örnek" animasyon veya film şeridi örneklerine doğrudan stil, denetim şablonu veya veri şablonu yerine bir nesne uygulama tekniği anlamına gelir.  
  
|Şeridi başlatılır kullanarak...|Örnek başına|Stil|Denetim şablonu|Veri şablonu|Örnek|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve bir <xref:System.Windows.EventTrigger>|Evet|Evet|Evet|Evet|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve bir özelliği <xref:System.Windows.Trigger>|Hayır|Evet|Evet|Evet|[Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve <xref:System.Windows.DataTrigger>|Hayır|Evet|Evet|Evet|[Nasıl yapılır: veriler değiştiğinde animasyon tetikleme](http://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> Yöntemi|Evet|Hayır|Hayır|Hayır|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.Storyboard> animasyon için <xref:System.Windows.FrameworkElement.Width%2A> , bir <xref:System.Windows.Shapes.Rectangle> öğesi ve <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> , boyamak için kullanılan <xref:System.Windows.Shapes.Rectangle>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 Aşağıdaki bölümlerde <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> özellikleri daha ayrıntılı bağlı.  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Çerçeve öğeleri, çerçeve içerik öğeleri ve Freezables hedefleme  
 Önceki bölümde söz edilen bir animasyon hedefine bulmak bunu hedefin adını ve animasyon eklenecek özelliği bilmesi gerekir. Animasyon eklenecek özelliği belirten olan düz İleri: basitçe <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType> animasyon eklenecek özelliği adı.  Özellik ayarlayarak animasyon eklemek istediğiniz nesne adını belirtin <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> animasyon özelliği.  
  
 İçin <xref:System.Windows.Setter.TargetName%2A> özelliğinin çalışması için hedeflenen nesne bir adı olması gerekir. Bir ad atamak bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] için bir ad atamaktan farklı bir <xref:System.Windows.Freezable> nesne.  
  
 Çerçeve öğeleridir devralınmalıdır bu sınıfların <xref:System.Windows.FrameworkElement> sınıfı. Çerçeve öğeleri örneklerindendir <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>, ve <xref:System.Windows.Shapes.Rectangle>. Esas olarak tüm windows paneller ve denetimleri öğelerdir. Çerçeve içerik öğeleri devralınan bu sınıflardır <xref:System.Windows.FrameworkContentElement> sınıfı. Çerçeve içerik öğeleri örneklerindendir <xref:System.Windows.Documents.FlowDocument> ve <xref:System.Windows.Documents.Paragraph>. Bir tür çerçeve öğesi veya çerçeve içerik öğesi olup emin değilseniz, bir Name özelliğine sahip olup olmadığını denetleyin. Destekliyorsa, büyük olasılıkla çerçeve öğesi veya çerçeve içerik öğesi değil. Emin olmak için onun türüne ait sayfanın Devralma Hiyerarşisi bölümünü denetleyin.  
  
 Çerçeve öğesi veya bir çerçeve içerik öğesini hedeflemeyi etkinleştirmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ayarladığınız kendi <xref:System.Windows.FrameworkElement.Name%2A> özelliği. Kod içinde de kullanmanız gerekir <xref:System.Windows.NameScope.RegisterName%2A> yöntemi, oluşturduğunuz öğesi ile öğenin adını kaydetmek için bir <xref:System.Windows.NameScope>.  
  
 Önceki örnekten alınan aşağıdaki örnekte, adı atar `MyRectangle` bir <xref:System.Windows.Shapes.Rectangle>, bir tür <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 Bir ad sahip olduktan sonra o öğesi özelliği animasyon ekleyebilirsiniz.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> türleri devralınan bu sınıflardır <xref:System.Windows.Freezable> sınıfı. Örnekleri <xref:System.Windows.Freezable> dahil <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>, ve <xref:System.Windows.Media.GradientStop>.  
  
 Hedefleme etkinleştirmek için bir <xref:System.Windows.Freezable> animasyonda tarafından [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullandığınız [x: Name yönergesi](../../../../docs/framework/xaml-services/x-name-directive.md) bir ad atamak için. Kodda, kullandığınız <xref:System.Windows.NameScope.RegisterName%2A> yöntemi, oluşturduğunuz öğeyle adını kaydetmek için bir <xref:System.Windows.NameScope>.  
  
 Aşağıdaki örnekte bir isim atanmaktadır bir <xref:System.Windows.Freezable> nesnesi.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 Nesne sonra bir animasyon tarafından hedeflenebilir.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> nesneleri çözmek için ad kapsamları kullanın <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özelliği. WPF ad kapsamları hakkında daha fazla bilgi için bkz: [WPF XAML ad kapsamları](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md). Varsa <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özelliği atlanırsa, animasyon tanımlandığı veya, stiller, stilde öğe söz konusu olduğunda öğe hedefler.  
  
 Bir ad bazen atanamaz bir <xref:System.Windows.Freezable> nesnesi. Örneğin, bir <xref:System.Windows.Freezable> bir kaynak olarak bildirilen veya stil içinde bir özellik değerini ayarlamak için kullanılan bir adı verilemez. Bir ad olmadığından, doğrudan hedefleyemez — ancak dolaylı olarak hedeflenebilir. Aşağıdaki bölümlerde dolaylı hedeflemenin nasıl kullanılacağı açıklanmaktadır.  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>Dolaylı hedefleme  
 Zamanlar bir <xref:System.Windows.Freezable> ne zaman gibi bir animasyon tarafından doğrudan hedefleyemez <xref:System.Windows.Freezable> bir kaynak olarak bildirilen veya stil içinde bir özellik değerini ayarlamak için kullanılır. Bu durumlarda, doğrudan hedefleyemez olsa bile, yine animasyon uygulayabilirsiniz <xref:System.Windows.Freezable> nesnesi. Ayar yerine <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özellik adıyla <xref:System.Windows.Freezable>, bu öğenin adını için size <xref:System.Windows.Freezable> "aittir." Örneğin, bir <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılan <xref:System.Windows.Shapes.Shape.Fill%2A> bir dikdörtgen öğesi o dikdörtgene aittir. Fırça animasyon eklemek için animasyonun ayarlamalısınız <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> framework öğenin veya çerçeve içerik öğesinin özellik başlayan özellikler zinciri ile <xref:System.Windows.Freezable> ayarlamak için kullanılan ve ile biten <xref:System.Windows.Freezable> animasyon ekleme özelliği.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 Unutmayın <xref:System.Windows.Freezable> olan dondurulmuş, bir kopya yapılır ve bu kopya animasyonlu. Bu durumda, özgün nesnenin <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> özellik devam dönmek `false`, özgün nesne değil gerçekte animasyon eklenir. Kopyalama hakkında daha fazla bilgi için bkz: [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Ayrıca dolaylı özellik hedeflemesi kullanırken, mevcut olmayan hedef nesneler için olası olduğuna dikkat edin. Örneğin, varsayabilir <xref:System.Windows.Controls.Control.Background%2A> belirli bir düğmeyi ayarlandı bir <xref:System.Windows.Media.SolidColorBrush> rengini, aslında zaman animasyon denerseniz bir <xref:System.Windows.Media.LinearGradientBrush> düğmenin arka planı ayarlamak için kullanılır. Bu durumlarda, hiçbir özel durum oluşur; animasyonun olmadığından görünür bir etkiye sahip başarısız <xref:System.Windows.Media.LinearGradientBrush> değişikliklere tepki vermez <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliği.  
  
 Aşağıdaki bölümlerde dolaylı özellik hedeflemesi sözdizimini daha ayrıntılı açıklanmıştır.  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>XAML'de Freezable özelliğini dolaylı olarak hedefleme  
 Bir özellik içinde Freezable hedeflemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aşağıdaki sözdizimini kullanın.  
  
||  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName* özelliği <xref:System.Windows.FrameworkElement> hangi <xref:System.Windows.Freezable> ayarlamak için kullanılır ve  
  
-   *FreezablePropertyName* özelliği <xref:System.Windows.Freezable> animasyon uygulamak için.  
  
 Aşağıdaki kod animasyon gösterilmektedir <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılır.  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> bir dikdörtgen öğesi.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 Bazen freezable koleksiyonu veya dizisi bulunan hedef gerekir.  
  
 Bir koleksiyonda bulunan freezable hedeflemek için aşağıdaki yol sözdizimini kullanın.  
  
||  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 Burada *CollectionIndex* , dizisi ya da koleksiyon nesnesinde dizinidir.  
  
 Örneğin, bir dikdörtgen olduğunu varsayalım bir <xref:System.Windows.Media.TransformGroup> uygulanan kaynak kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliği ve içerdiği dönüşümler birini animasyon istediğinizde.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 Aşağıdaki kod animasyon gösterilmektedir <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliği <xref:System.Windows.Media.RotateTransform> önceki örnekte gösterilen.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Kod içinde Freezable özelliğini dolaylı olarak hedefleme  
 Kod içinde oluşturduğunuz bir <xref:System.Windows.PropertyPath> nesnesi. Oluştururken <xref:System.Windows.PropertyPath>, belirttiğiniz bir <xref:System.Windows.PropertyPath.Path%2A> ve <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 Oluşturmak için <xref:System.Windows.PropertyPath.PathParameters%2A>, türünde bir dizi oluşturmak <xref:System.Windows.DependencyProperty> bağımlılık özelliği tanımlayıcı alanlarını listesini içerir. İlk tanımlayıcı alan için özelliğidir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> , <xref:System.Windows.Freezable> ayarlamak için kullanılır. Sonraki tanımlayıcı alan özelliğini temsil eder <xref:System.Windows.Freezable> hedef. Bağlayan özellikler zinciri olarak düşünün <xref:System.Windows.Freezable> için <xref:System.Windows.FrameworkElement> nesnesi.  
  
 Aşağıdaki hedefleyen bir bağımlılık özelliği zinciri örneğidir <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılan <xref:System.Windows.Shapes.Shape.Fill%2A> bir dikdörtgen öğesi.  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 Ayrıca belirtmek zorunda bir <xref:System.Windows.PropertyPath.Path%2A>. A <xref:System.Windows.PropertyPath.Path%2A> olan bir <xref:System.String> , söyler <xref:System.Windows.PropertyPath.Path%2A> yorumlama kendi <xref:System.Windows.PropertyPath.PathParameters%2A>. Aşağıdaki sözdizimini kullanır.  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex* dizinidir <xref:System.Windows.DependencyProperty> tanımlayıcısını içeren bir dizi <xref:System.Windows.FrameworkElement> nesnenin özelliği, <xref:System.Windows.Freezable> ayarlamak için kullanılır ve  
  
-   *FreezablePropertyArrayIndex* dizinidir <xref:System.Windows.DependencyProperty> hedef özelliğine tanımlayıcısını içeren bir dizi.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.PropertyPath.Path%2A> ile birlikte <xref:System.Windows.PropertyPath.PathParameters%2A> önceki örnekte tanımlı.
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 Aşağıdaki örnek kod animasyon eklemek için önceki örneklerde birleştirir <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılan <xref:System.Windows.Shapes.Shape.Fill%2A> bir dikdörtgen öğesi.  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 Bazen freezable koleksiyonu veya dizisi bulunan hedef gerekir. Örneğin, bir dikdörtgen olduğunu varsayalım bir <xref:System.Windows.Media.TransformGroup> uygulanan kaynak kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliği ve içerdiği dönüşümler birini animasyon istediğinizde.  
  
 [!code-xaml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 Hedeflenecek bir <xref:System.Windows.Freezable> koleksiyonu bulunan aşağıdaki yol sözdizimini kullanın.  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 Burada *CollectionIndex* , dizisi ya da koleksiyon nesnesinde dizinidir.  
  
 Hedef <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliği <xref:System.Windows.Media.RotateTransform>, ikinci dönüştürme <xref:System.Windows.Media.TransformGroup>, aşağıdaki kullanırsınız <xref:System.Windows.PropertyPath.Path%2A> ve <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 Aşağıdaki örnek animasyon tam kodunu gösterir <xref:System.Windows.Media.RotateTransform.Angle%2A> , bir <xref:System.Windows.Media.RotateTransform> kapsamında yer alan bir <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Başlangıç noktası olarak Freezable ile dolaylı olarak hedefleme  
 Önceki bölümlerde açıklanan nasıl dolaylı olarak hedeflendiği bir <xref:System.Windows.Freezable> ile başlatarak bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> ve bir özellik zinciri oluşturma bir <xref:System.Windows.Freezable> alt özelliği. Aynı zamanda bir <xref:System.Windows.Freezable> başlangıç noktası ve dolaylı olarak birini hedef kendi <xref:System.Windows.Freezable> alt özellikleri. Bir ek kısıtlama uygulanır kullanırken bir <xref:System.Windows.Freezable> dolaylı hedefleme için bir başlangıç noktası olarak: Başlangıç <xref:System.Windows.Freezable> ve her <xref:System.Windows.Freezable> ve dolaylı olarak hedeflenen alt özelliği arasında dondurulmuş olması gerekmez.  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>XAML'de film şeridi etkileşimli olarak denetleme  
 Film şeridi başlatmak için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], kullandığınız bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylemi tetikler. <xref:System.Windows.Media.Animation.BeginStoryboard> nesneleri ve hareketli hale getirmeyi ve film şeridi başlatır özellikleri animasyonları dağıtır. (Bu işlem hakkında daha fazla ayrıntı için bkz: [animasyon ve zamanlama sistem genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).) Size, <xref:System.Windows.Media.Animation.BeginStoryboard> belirterek bir isim kendi <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> özelliği, onu bir denetlenebilir film şeridi yapın. Başlatıldıktan sonra film şeridi etkileşimli olarak denetleyebilirsiniz. Film şeridi denetlemek için olay tetikleyicileri ile kullanın denetlenebilir film şeridi eylemlerinin bir listesi verilmiştir.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Film şeridi duraklatır.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış film şeridi sürdürür.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Film şeridi'nın hızını değiştirir.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Varsa, film şeridi dolgu süresinin sonuna ilerletir.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Film şeridi durdurur.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Film şeridi kaldırır.  
  
 Aşağıdaki örnekte, denetlenebilir film şeridi eylemleri, etkileşimli olarak film şeridi denetlemek için kullanılır.  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Kod kullanarak bir film şeridi etkileşimli olarak denetleme  
 Önceki örneklerde tetikleyici eylemleri kullanarak nasıl animasyon ekleneceği göstermiştir. Kodda, etkileşimli yöntemlerini kullanarak film şeridi da denetleyebilirsiniz <xref:System.Windows.Media.Animation.Storyboard> sınıfı. İçin bir <xref:System.Windows.Media.Animation.Storyboard> kodda etkileşimli yapılabilmesi için film şeridi'nın uygun aşırı yüklemesine kullanmak <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi ve belirtin `true` denetlenebilir yapmak için. Bkz: <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> daha fazla bilgi için.  
  
 Aşağıdaki listede denetlemek için kullanılan yöntemleri gösterir bir <xref:System.Windows.Media.Animation.Storyboard> başlatıldıktan sonra:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 Bu yöntemleri kullanarak avantajı oluşturmanız gerekmez olan <xref:System.Windows.Trigger> veya <xref:System.Windows.TriggerAction> nesneleri; denetlenebilir başvuru yeterlidir <xref:System.Windows.Media.Animation.Storyboard> işlemek istediğiniz.  
  
 **Not:** alınan tüm etkileşimli eylemler bir <xref:System.Windows.Media.Animation.Clock>, bu nedenle da bir <xref:System.Windows.Media.Animation.Storyboard> , kısa süre içinde sonraki oluşturmadan önce olacağını zamanlama altyapısının sonraki değerinde meydana gelir. Örneğin, kullanırsanız <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> özellik değeri bir animasyon içinde başka bir noktaya atlamak için yöntemi anında değişmez, bunun yerine, değer değiştiği zamanlama altyapısının sonraki değerinde.  
  
 Aşağıdaki örnekte nasıl uygulanacağını ve etkileşimli yöntemlerini kullanarak animasyonların gösterir <xref:System.Windows.Media.Animation.Storyboard> sınıfı.  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>Bir Stile Animasyon Ekleme  
 Kullanabileceğiniz <xref:System.Windows.Media.Animation.Storyboard> animasyonları tanımlamak için nesneleri bir <xref:System.Windows.Style>. İle animasyon bir <xref:System.Windows.Media.Animation.Storyboard> içinde bir <xref:System.Windows.Style> kullanmaya benzer bir <xref:System.Windows.Media.Animation.Storyboard> başka bir yerde, aşağıdaki istisnalar üç:  
  
-   Belirtmeyin bir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; <xref:System.Windows.Media.Animation.Storyboard> her zaman öğeyi hedefler <xref:System.Windows.Style> uygulanır. Hedef <xref:System.Windows.Freezable> nesneleri dolaylı hedefleme kullanmanız gerekir. Dolaylı hedefleme hakkında daha fazla bilgi için bkz: [dolaylı hedefleme](#pathsyntaxforchangeable) bölümü.  
  
-   Belirtemeyeceğiniz bir <xref:System.Windows.EventTrigger.SourceName%2A> için bir <xref:System.Windows.EventTrigger> veya <xref:System.Windows.Trigger>.  
  
-   Ayarlamak için dinamik kaynak başvuruları ya da veri bağlama ifadeleri kullanamazsınız <xref:System.Windows.Media.Animation.Storyboard> veya animasyonun özellik değerlerini. Çünkü içindeki tüm öğeler bir <xref:System.Windows.Style> iş parçacığı, olmalıdır ve zamanlama sistemi gerekir <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> onları iş parçacığı güvenli hale getirmek için nesneleri. A <xref:System.Windows.Media.Animation.Storyboard> kendisi ya da alt zaman çizelgeleri dinamik kaynak başvuruları ya da veri bağlaması ifadelerini içeriyorsa dondurulmuş olamaz. Dondurma ve diğer hakkında daha fazla bilgi için <xref:System.Windows.Freezable> özellikleri, bkz. [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], olay işleyicileri bildiremezsiniz <xref:System.Windows.Media.Animation.Storyboard> veya animasyon olayları.  
  
 Film şeridi stilde tanımlamak nasıl gösteren bir örnek için bkz: [animasyon ekle stilinde](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md) örnek.  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>ControlTemplate İçinde Animasyon Ekleme  
 Kullanabileceğiniz <xref:System.Windows.Media.Animation.Storyboard> animasyonları tanımlamak için nesneleri bir <xref:System.Windows.Controls.ControlTemplate>. İle animasyon bir <xref:System.Windows.Media.Animation.Storyboard> içinde bir <xref:System.Windows.Controls.ControlTemplate> kullanmaya benzer bir <xref:System.Windows.Media.Animation.Storyboard> başka bir yerde, aşağıdaki istisnalar iki:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Alt nesneler için yalnızca başvurabilir <xref:System.Windows.Controls.ControlTemplate>. Varsa <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> belirtilmezse, animasyon hedefler öğesine <xref:System.Windows.Controls.ControlTemplate> uygulanır.  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A> İçin bir <xref:System.Windows.EventTrigger> veya <xref:System.Windows.Trigger> alt nesneler için yalnızca başvurabilir <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Ayarlamak için dinamik kaynak başvuruları ya da veri bağlama ifadeleri kullanamazsınız <xref:System.Windows.Media.Animation.Storyboard> veya animasyonun özellik değerlerini. Çünkü içindeki tüm öğeler bir <xref:System.Windows.Controls.ControlTemplate> iş parçacığı, olmalıdır ve zamanlama sistemi gerekir <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> onları iş parçacığı güvenli hale getirmek için nesneleri. A <xref:System.Windows.Media.Animation.Storyboard> kendisi ya da alt zaman çizelgeleri dinamik kaynak başvuruları ya da veri bağlaması ifadelerini içeriyorsa dondurulmuş olamaz. Dondurma ve diğer hakkında daha fazla bilgi için <xref:System.Windows.Freezable> özellikleri, bkz. [Freezable nesnelere genel bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
-   İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], olay işleyicileri bildiremezsiniz <xref:System.Windows.Media.Animation.Storyboard> veya animasyon olayları.  
  
 Bir film şeridi tanımlamak nasıl gösteren bir örnek için bir <xref:System.Windows.Controls.ControlTemplate>, bkz: [animasyon ekle ControlTemplate içinde](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md) örnek.  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>Özellik değeri değiştiğinde animasyon ekleme  
 Stilleri ve denetim şablonları, bir özellik değiştiğinde film şeridi başlatmak için tetikleyici nesnelerini kullanabilirsiniz. Örnekler için bkz: [bir animasyon bir özellik değeri değiştiğinde tetiklemek](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md) ve [animasyon ekle ControlTemplate içinde](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md).  
  
 Özelliği tarafından uygulanan bir animasyon <xref:System.Windows.Trigger> nesneleri davranırlar daha karmaşık bir şekilde <xref:System.Windows.EventTrigger> animasyonları veya animasyonları kullanılarak başlatılan <xref:System.Windows.Media.Animation.Storyboard> yöntemleri.  Bunlar animasyonları ile "iletimi diğer tarafından tanımlanan" <xref:System.Windows.Trigger> nesneleri, ancak oluşturma ile <xref:System.Windows.EventTrigger> ve yöntemi tetiklenen animasyonları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Freezable Nesnelerine Genel Bakış](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
