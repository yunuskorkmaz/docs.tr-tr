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
ms.openlocfilehash: 6b178ac6b93205afebb1bea45f1b7e94826cb670
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124845"
---
# <a name="storyboards-overview"></a>Görsel Taslaklara Genel Bakış
Bu konu nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Storyboard> animasyonların ve düzenleme nesneleri. Etkileşimli olarak nasıl işleneceğini açıklar <xref:System.Windows.Media.Animation.Storyboard> nesneleri ve söz dizimi hedefleyen dolaylı özelliği tanımlar.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için temel özelliklerine animasyon farklı türleri ile ilgili bilgi sahibi olmalıdır. Animasyon bir giriş için bkz [animasyona genel bakış](animation-overview.md). Ayrıca, ekli özelliklerinin nasıl kullanılacağını bilmeniz gerekir. Ekli özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>Görsel taslak nedir?  
 Animasyon zaman çizelgesi yalnızca yararlı bir tür değil. Diğer zaman çizelgesi sınıfları, zaman çizelgeleri kümelerinin düzenlemenize yardımcı olur ve zaman çizelgeleri özellikleri uygulamak için sağlanır. Kapsayıcı zaman çizelgeleri türetilen <xref:System.Windows.Media.Animation.TimelineGroup> sınıfı ve dahil <xref:System.Windows.Media.Animation.ParallelTimeline> ve <xref:System.Windows.Media.Animation.Storyboard>.  
  
 A <xref:System.Windows.Media.Animation.Storyboard> kapsayıcı zaman çizelgesi için içerdiği zaman çizelgelerini hedefleme bilgileri sağlayan bir tür. Herhangi bir türde bir görsel taslak içerebilir <xref:System.Windows.Media.Animation.Timeline>diğer kapsayıcı zaman çizelgeleri ve animasyonları dahil olmak üzere. <xref:System.Windows.Media.Animation.Storyboard> nesneleri, nesnelerle ve özelliklerle çeşitli düzenlemek ve karmaşık zamanlama davranışlarını denetlemek kolaylaştıran bir tek bir zaman çizelgesi ağacında etkileyen zaman çizelgelerini birleştirmenizi sağlar. Örneğin, şu üç şeyi yapar bir düğme istediğinizi varsayalım.  
  
-   Büyütme ve kullanıcı düğmeyi seçtiğinde rengini değiştirin.  
  
-   Ardından tıklandığında geri özgün durumuna küçülür ve artırabilirsiniz.  
  
-   Daralt ve devre dışı kalırsa, yüzde 50 opaklık için Soluklaştır.  
  
 Bu durumda, birden fazla aynı nesneye uygulanan bir animasyon sahip ve farklı saatler yerine düğmeyi durumuna bağımlı yürütmek istediğiniz. <xref:System.Windows.Media.Animation.Storyboard> nesneleri, animasyonları düzenlemek ve bir veya daha fazla nesneye gruplar halinde uygulamanızı sağlar.  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>Burada bir görsel taslak kullanabilir miyim?  
 A <xref:System.Windows.Media.Animation.Storyboard> canlandırılabilir sınıfların bağımlılık özelliklerine animasyon uygulamak için kullanılabilir (bir sınıf canlandırılabilir kılan hakkında daha fazla bilgi için bkz. [animasyona genel bakış](animation-overview.md)). Görsel taslak bir çerçeve düzeyi özelliği olduğundan, ancak nesne ait olmalıdır <xref:System.Windows.NameScope> , bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>.  
  
 Örneğin, kullanabileceğinizi bir <xref:System.Windows.Media.Animation.Storyboard> aşağıdakileri yapmak için:  
  
-   Animasyon bir <xref:System.Windows.Media.SolidColorBrush> (çerçevesi olmayan öğe), boyar bir düğmenin arka planı (bir tür <xref:System.Windows.FrameworkElement>),  
  
-   Animasyon bir <xref:System.Windows.Media.SolidColorBrush> (çerçevesi olmayan öğe), boyar dolgusunu bir <xref:System.Windows.Media.GeometryDrawing> (çerçevesi olmayan öğe) kullanarak görüntülenen bir <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>).  
  
-   Kod içinde animasyon ekleme bir <xref:System.Windows.Media.SolidColorBrush> de içeren bir sınıf tarafından bildirilen bir <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Media.SolidColorBrush> adı ile kayıtlı <xref:System.Windows.FrameworkElement>.  
  
 Ancak, kullanamayabilirsiniz bir <xref:System.Windows.Media.Animation.Storyboard> animasyon uygulamak için bir <xref:System.Windows.Media.SolidColorBrush> adıyla kaydetmedi bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, veya bir özelliği ayarlamak için kullanılmayan bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>.  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>Bir görsel taslak animasyonları uygulama  
 Kullanılacak bir <xref:System.Windows.Media.Animation.Storyboard> animasyonların ve düzenlemek için animasyonları alt öğe zaman çizelgeleri eklemeniz <xref:System.Windows.Media.Animation.Storyboard>. <xref:System.Windows.Media.Animation.Storyboard> Sağlar sınıfını <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> iliştirilmiş özellikler. Özellik ve hedef nesne belirtmek için bir animasyon'de bu özellikleri ayarlayın.  
  
 Hedeflerine animasyon uygulamak için başlamadan <xref:System.Windows.Media.Animation.Storyboard> tetikleyici eylem veya bir yöntemi kullanarak. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullandığınız bir <xref:System.Windows.Media.Animation.BeginStoryboard> nesnesi ile bir <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>, veya <xref:System.Windows.DataTrigger>. Kod içinde de kullanabilirsiniz <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi.  
  
 Aşağıdaki tabloda farklı yerlere gösterilmektedir. burada her <xref:System.Windows.Media.Animation.Storyboard> başlamak teknik desteklenir: örnek başına, stil, denetim şablonu ve veri şablonu. "Örnek başına" animasyon veya görsel taslak örneklerine doğrudan bir stil, denetim şablonu veya veri şablonu değil, bir nesnenin uygulama tekniği anlamına gelir.  
  
|Görsel taslak kullanarak başladı...|Örnek başına|Stil|Denetim şablonu|Veri şablonu|Örnek|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve <xref:System.Windows.EventTrigger>|Evet|Evet|Evet|Evet|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve bir özelliği <xref:System.Windows.Trigger>|Hayır|Evet|Evet|Evet|[Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve <xref:System.Windows.DataTrigger>|Hayır|Evet|Evet|Evet|[Nasıl yapılır: Veriler değiştiğinde bir animasyonu tetikleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> Yöntemi|Evet|Hayır|Hayır|Hayır|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.Storyboard> animasyon uygulamak için <xref:System.Windows.FrameworkElement.Width%2A> , bir <xref:System.Windows.Shapes.Rectangle> öğesi ve <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> , boyamak için kullanılan <xref:System.Windows.Shapes.Rectangle>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 Aşağıdaki bölümlerde <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> iliştirilmiş özellikler daha ayrıntılı bir şekilde.  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Çerçeve hedefleme öğeleri, çerçeve içerik öğeleri ve Freezable nesneleri  
 Bir animasyon hedefine bulmak, bu hedefin adı ve animasyon uygulamak için özellik bilmeniz gerekir, önceki bölümde belirtilen. Özellik animasyon uygulamak için belirtimi, oldukça: ayarlamanız yeterlidir <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> animasyon uygulamak için özellik adı.  Özelliğini ayarlayarak animasyon uygulamak istediğiniz nesnenin adı belirttiğiniz <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> animasyon özelliği.  
  
 İçin <xref:System.Windows.Setter.TargetName%2A> özelliğinin çalışması için hedeflenen nesne bir adı olmalıdır. Bir ad atamak bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] için bir ad atamaktan farklı bir <xref:System.Windows.Freezable> nesne.  
  
 Çerçeve öğeleridir devralacak söz konusu sınıfın <xref:System.Windows.FrameworkElement> sınıfı. Çerçeve öğeleri örnekler <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>, ve <xref:System.Windows.Shapes.Rectangle>. Aslında tüm windows, panelleri ve denetimleri öğeleridir. Çerçeve içerik öğeleri devralınan bu sınıflardır <xref:System.Windows.FrameworkContentElement> sınıfı. Çerçeve içerik öğeleri örnekler <xref:System.Windows.Documents.FlowDocument> ve <xref:System.Windows.Documents.Paragraph>. Çerçeve öğesi veya bir framework içerik öğesi bir tür olup emin değilseniz, bir Name özelliğine sahip olup olmadığını denetleyin. Aksi halde bir çerçeve öğesi veya bir framework içerik öğesi olabilir. Emin olmak için tür sayfasının Devralma Hiyerarşisi bölümüne bakın.  
  
 Çerçeve öğesi veya bir çerçeve içerik öğesini hedefleyen etkinleştirmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ayarladığınız kendi <xref:System.Windows.FrameworkElement.Name%2A> özelliği. Kod içinde de kullanmanız gerekir <xref:System.Windows.NameScope.RegisterName%2A> öğenin adı için oluşturduğunuz öğe ile kaydetmek için yöntemi bir <xref:System.Windows.NameScope>.  
  
 Aşağıdaki örnek, önceki örnekten alınan ad atar `MyRectangle` bir <xref:System.Windows.Shapes.Rectangle>, bir tür <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 Bir ada sahip olduktan sonra o öğe bir özelliğine animasyon uygulayabilirsiniz.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> devralınan bu sınıflar türleridir <xref:System.Windows.Freezable> sınıfı. Örnekleri <xref:System.Windows.Freezable> dahil <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>, ve <xref:System.Windows.Media.GradientStop>.  
  
 Hedefleme, etkinleştirmek için bir <xref:System.Windows.Freezable> animasyon tarafından [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullandığınız [x: Name yönergesi](../../xaml-services/x-name-directive.md) bir ad atamak için. Kod içinde kullanmanız <xref:System.Windows.NameScope.RegisterName%2A> yöntemi için oluşturduğunuz bir öğeyle adını kaydetmek için bir <xref:System.Windows.NameScope>.  
  
 Aşağıdaki örnek için bir ad atar bir <xref:System.Windows.Freezable> nesne.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 Nesne, ardından bir animasyon tarafından hedeflenebilir.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> nesneleri çözmek için ad kapsamları kullanın <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özelliği. WPF ad kapsamları hakkında daha fazla bilgi için bkz. [WPF XAML ad kapsamları](../advanced/wpf-xaml-namescopes.md). Varsa <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özelliği atlanırsa, öğe tanımlandığı veya, stiller, stil uygulanmış öğesi söz konusu olduğunda animasyon hedefler.  
  
 Bir ad bazen atanamaz bir <xref:System.Windows.Freezable> nesne. Örneğin, bir <xref:System.Windows.Freezable> stil içinde bir özellik değerini ayarlamak için kullanılan veya bir kaynak olarak bildirilen bir ad verilemez. Bir adı olmadığı için doğrudan hedeflenemez — ancak dolaylı olarak hedeflenebilir. Aşağıdaki bölümlerde, dolaylı hedeflemenin nasıl kullanılacağı açıklanmaktadır.  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>Dolaylı hedefleme  
 Bazı durumlarda bir <xref:System.Windows.Freezable> doğrudan ne zaman gibi bir animasyon tarafından hedeflenemez <xref:System.Windows.Freezable> bir kaynak olarak bildirilen veya stilde bir özellik değerini ayarlamak için kullanılır. Bu gibi durumlarda, doğrudan hedefleyemezsiniz olsa da hala canlandırabilirsiniz <xref:System.Windows.Freezable> nesne. Ayar yerine <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özellik adıyla <xref:System.Windows.Freezable>, bu öğe adı, size <xref:System.Windows.Freezable> "ait." Örneğin, bir <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılan <xref:System.Windows.Shapes.Shape.Fill%2A> bir dikdörtgen öğesi o dikdörtgene aittir. Fırça animasyon eklemek gibi animasyonun ayarlarsınız <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> framework öğenin veya çerçeve içerik öğesinin özellik özellikleri zinciri ile <xref:System.Windows.Freezable> yapmak için kullanılır ve ile sona eren <xref:System.Windows.Freezable> animasyon uygulamak için özellik.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 Unutmayın <xref:System.Windows.Freezable> olan donmuş, bir kopya oluşturulur ve bu kopya animasyonlu. Bu durumda, özgün nesnenin <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> özelliği devam döndürülecek `false`, özgün nesneye değil gerçekten bir animasyon görünür. Kopyalama hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
 Ayrıca dolaylı özelliğini hedefleme kullanırken, mevcut olmayan hedef nesnelere mümkün olduğuna dikkat edin. Örneğin, varsayabilir <xref:System.Windows.Controls.Control.Background%2A> , belirli bir düğme ile ayarlanmış bir <xref:System.Windows.Media.SolidColorBrush> ve rengini, hatta zaman canlandırabilirsiniz bir <xref:System.Windows.Media.LinearGradientBrush> düğmenin arka plan yapmak için kullanılır. Bu gibi durumlarda, hiçbir özel durum harekete; bir animasyon görünür bir etkiye sahip başaramıyor <xref:System.Windows.Media.LinearGradientBrush> yapılan değişikliklere tepki vermez <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliği.  
  
 Aşağıdaki bölümlerde daha ayrıntılı söz dizimi hedefleyen dolaylı özellik açıklanmaktadır.  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>Dolaylı olarak özelliğini XAML içinde Freezable'ı hedefleme  
 Freezable'nın bir özelliğini hedefleyecek şekilde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aşağıdaki sözdizimini kullanın.  
  
| |  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName* özelliği <xref:System.Windows.FrameworkElement> hangi <xref:System.Windows.Freezable> ayarlamak için kullanılır ve  
  
-   *FreezablePropertyName* özelliği <xref:System.Windows.Freezable> animasyon uygulamak için.  
  
 Aşağıdaki kod, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılır  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> bir dikdörtgen öğesi.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 Bazen bir koleksiyon veya dizi içindeki freezable hedef gerekebilir.  
  
 Bir koleksiyonda yer alan freezable hedeflemek için aşağıdaki yol sözdizimini kullanın.  
  
| |  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 Burada *CollectionIndex* nesne, dizi veya koleksiyon içindeki dizinidir.  
  
 Örneğin, bir dikdörtgen olduğunu varsayalım. bir <xref:System.Windows.Media.TransformGroup> uygulanan kaynak kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliğini istediğiniz içerdiği dönüşümlerden birini animasyon uygulamak.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 Aşağıdaki kod, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliği <xref:System.Windows.Media.RotateTransform> önceki örnekte gösterilen.  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Dolaylı olarak bir özellik kod içinde Freezable hedefleme  
 Kod içinde oluşturduğunuz bir <xref:System.Windows.PropertyPath> nesne. Oluştururken <xref:System.Windows.PropertyPath>, belirttiğiniz bir <xref:System.Windows.PropertyPath.Path%2A> ve <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 Oluşturulacak <xref:System.Windows.PropertyPath.PathParameters%2A>, bir dizi türü oluşturmak <xref:System.Windows.DependencyProperty> , bağımlılık özelliği tanımlayıcı alanlarını listesini içerir. İlk tanımlayıcı alan özelliği için olan <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> , <xref:System.Windows.Freezable> ayarlamak için kullanılır. Sonraki tanımlayıcı alanı özelliğini temsil eden <xref:System.Windows.Freezable> hedef. Bağlayan zinciri özellikleri olarak düşünebilirsiniz <xref:System.Windows.Freezable> için <xref:System.Windows.FrameworkElement> nesne.  
  
 Bir bağımlılık özelliği zincirinin hedefleyen bir örneği verilmiştir <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılan <xref:System.Windows.Shapes.Shape.Fill%2A> bir dikdörtgen öğesi.  
  
 [!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 Ayrıca belirtmenize gerek bir <xref:System.Windows.PropertyPath.Path%2A>. A <xref:System.Windows.PropertyPath.Path%2A> olduğu bir <xref:System.String> başarısız olduğunu anlatan <xref:System.Windows.PropertyPath.Path%2A> yorumlama kendi <xref:System.Windows.PropertyPath.PathParameters%2A>. Aşağıdaki sözdizimini kullanır.  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex* dizinidir <xref:System.Windows.DependencyProperty> tanımlayıcısını içeren bir dizi <xref:System.Windows.FrameworkElement> nesnenin özellik, <xref:System.Windows.Freezable> ayarlamak için kullanılır ve  
  
-   *FreezablePropertyArrayIndex* dizinidir <xref:System.Windows.DependencyProperty> hedef özellik tanımlayıcısını içeren bir dizi.  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Windows.PropertyPath.Path%2A> ile birlikte <xref:System.Windows.PropertyPath.PathParameters%2A> önceki örnekte tanımlanan.
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 Aşağıdaki örnek kod önceki örneklerde animasyon uygulamak için birleştirir <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> ayarlamak için kullanılan <xref:System.Windows.Shapes.Shape.Fill%2A> bir dikdörtgen öğesi.  
  
 [!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 Bazen bir koleksiyon veya dizi içindeki freezable hedef gerekebilir. Örneğin, bir dikdörtgen olduğunu varsayalım. bir <xref:System.Windows.Media.TransformGroup> uygulanan kaynak kendi <xref:System.Windows.UIElement.RenderTransform%2A> özelliğini istediğiniz içerdiği dönüşümlerden birini animasyon uygulamak.  
  
 [!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 Hedef bir <xref:System.Windows.Freezable> bir koleksiyonda yer alan, aşağıdaki yol sözdizimini kullanın.  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 Burada *CollectionIndex* nesne, dizi veya koleksiyon içindeki dizinidir.  
  
 Hedef <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliği <xref:System.Windows.Media.RotateTransform>, ikinci dönüşüm <xref:System.Windows.Media.TransformGroup>, aşağıdaki kullanacağınız <xref:System.Windows.PropertyPath.Path%2A> ve <xref:System.Windows.PropertyPath.PathParameters%2A>.  
  
 [!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 Aşağıdaki örnek, animasyon için tam kod gösterilir <xref:System.Windows.Media.RotateTransform.Angle%2A> , bir <xref:System.Windows.Media.RotateTransform> içinde yer alan bir <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Freezable başlangıç noktası olarak ile dolaylı olarak hedefleme  
 Önceki bölümlerde açıklanan dolaylı olarak hedeflemek nasıl bir <xref:System.Windows.Freezable> ile başlatarak bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> ve bir özellik zinciri oluşturma bir <xref:System.Windows.Freezable> alt özellik. Ayrıca bir <xref:System.Windows.Freezable> başlangıç noktası ve dolaylı olarak biri hedef kendi <xref:System.Windows.Freezable> alt özellikleri. Bir ek kısıtlama uygulanır kullanırken bir <xref:System.Windows.Freezable> dolaylı hedeflemek için bir başlangıç noktası olarak: Başlangıç <xref:System.Windows.Freezable> ve her <xref:System.Windows.Freezable> o ve dolaylı olarak hedeflenen alt özellik arasında dondurulmuş olması gerekmez.  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>XAML içinde bir film şeridini etkileşimli olarak denetleme  
 İçinde bir film şeridi başlatmak için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], kullandığınız bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem tetikler. <xref:System.Windows.Media.Animation.BeginStoryboard> animasyon ve görsel taslak başlar özelliklerini ve nesneleri animasyonları dağıtır. (Bu işlem hakkında daha fazla ayrıntı için bkz: [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).) Size, <xref:System.Windows.Media.Animation.BeginStoryboard> bir ad belirterek, <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> özelliği yaptığınız, denetlenebilir bir film şeridi. Başlatıldıktan sonra film şeridi etkileşimli olarak denetleyebilirsiniz. Bir film şeridini denetlemek için olay tetikleyicilerini ile kullanma denetlenebilir bir film şeridi eylemlerin bir listesi verilmiştir.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Film duraklatılır.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış bir film şeridini sürdürür.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Şeridinin hızını değiştirir.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Varsa, bir görsel taslak dolgu süresinin sonuna ilerler.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Görsel taslak durdurur.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Görsel taslak kaldırır.  
  
 Aşağıdaki örnekte, denetlenebilir bir film şeridi Eylemler, etkileşimli bir film şeridini denetlemek için kullanılır.  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Kod kullanarak bir görsel taslak etkileşimli olarak denetleme  
 Önceki örneklerde, tetikleyici eylemleri kullanarak animasyonunu göstermiştir. Kod içinde bir film şeridi etkileşimli yöntemlerini kullanarak da denetleyebilirsiniz <xref:System.Windows.Media.Animation.Storyboard> sınıfı. İçin bir <xref:System.Windows.Media.Animation.Storyboard> kodda etkileşimli yapılabilmesi için görsel Taslak'ın uygun aşırı yüklemesini kullanın <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi belirtin `true` denetlenebilir yapmak için. Bkz: <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> daha fazla bilgi için.  
  
 Aşağıdaki liste işlemek için kullanılan yöntemleri gösterir. bir <xref:System.Windows.Media.Animation.Storyboard> başlatıldıktan sonra:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 Bu yöntemleri kullanarak oluşturmanız gerekmez avantajlarındandır <xref:System.Windows.Trigger> veya <xref:System.Windows.TriggerAction> nesneler; denetlenebilir bir başvuru yeterlidir <xref:System.Windows.Media.Animation.Storyboard> işlemek istediğiniz.  
  
 **Not:** Alınan tüm etkileşimli eylemleri bir <xref:System.Windows.Media.Animation.Clock>ve bu nedenle ayrıca bir <xref:System.Windows.Media.Animation.Storyboard> sonraki oluşturmadan önce kısa bir süre sonra gerçekleştirilecek zamanlama altyapısı sonraki değerinde meydana gelir. Örneğin, kullanırsanız <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemi özellik değeri bir animasyon başka bir noktaya atlamak için anında değiştirmez, bunun yerine, zamanlama altyapısı sonraki değer çizgisi değeri değiştirir.  
  
 Aşağıdaki örnek nasıl uygulanacağını ve etkileşimli yöntemleri kullanılarak animasyonların gösterir <xref:System.Windows.Media.Animation.Storyboard> sınıfı.  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>Bir Stile Animasyon Ekleme  
 Kullanabileceğiniz <xref:System.Windows.Media.Animation.Storyboard> animasyonları tanımlamak için nesneleri bir <xref:System.Windows.Style>. İle animasyon bir <xref:System.Windows.Media.Animation.Storyboard> içinde bir <xref:System.Windows.Style> kullanmaya benzer bir <xref:System.Windows.Media.Animation.Storyboard> başka bir yerde, aşağıdaki istisnalarla üç:  
  
-   Belirtmeyin bir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>; <xref:System.Windows.Media.Animation.Storyboard> her zaman öğeyi hedefleyen <xref:System.Windows.Style> uygulanır. Hedef <xref:System.Windows.Freezable> nesnelerini dolaylı hedefleme kullanmanız gerekir. Dolaylı hedefleme hakkında daha fazla bilgi için bkz. [dolaylı hedefleme](#pathsyntaxforchangeable) bölümü.  
  
-   Belirtemezsiniz bir <xref:System.Windows.EventTrigger.SourceName%2A> için bir <xref:System.Windows.EventTrigger> veya <xref:System.Windows.Trigger>.  
  
-   Dinamik kaynak başvuruları veya veri bağlama ifadeleri ayarlamak için kullanamazsınız <xref:System.Windows.Media.Animation.Storyboard> veya animasyon özellik değerleri. Çünkü içindeki her şey bir <xref:System.Windows.Style> iş parçacığı açısından güvenli olmalıdır ve zamanlama sistemi <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> bunları iş parçacığı açısından güvenli hale getirmek için nesneleri. A <xref:System.Windows.Media.Animation.Storyboard> veya onun alt öğe zaman çizelgelerini dinamik kaynak başvuruları veya veri bağlama ifadeleri içeriyorsa nelze zmrazit. Dondurma ve diğer hakkında daha fazla bilgi için <xref:System.Windows.Freezable> özellikler bkz [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
-   İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], için olay işleyicileri bildiremezsiniz <xref:System.Windows.Media.Animation.Storyboard> veya animasyon olayları.  
  
 Stil içinde bir film şeridi tanımlama gösteren bir örnek için bkz: [stil animasyon Ekle](how-to-animate-in-a-style.md) örnek.  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>ControlTemplate İçinde Animasyon Ekleme  
 Kullanabileceğiniz <xref:System.Windows.Media.Animation.Storyboard> animasyonları tanımlamak için nesneleri bir <xref:System.Windows.Controls.ControlTemplate>. İle animasyon bir <xref:System.Windows.Media.Animation.Storyboard> içinde bir <xref:System.Windows.Controls.ControlTemplate> kullanmaya benzer bir <xref:System.Windows.Media.Animation.Storyboard> başka bir yerde, aşağıdaki iki özel durum ile:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Alt nesneler için yalnızca yönlendirebiliriz <xref:System.Windows.Controls.ControlTemplate>. Varsa <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> belirtilmezse, animasyon öğeye hedefler <xref:System.Windows.Controls.ControlTemplate> uygulanır.  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A> İçin bir <xref:System.Windows.EventTrigger> veya <xref:System.Windows.Trigger> alt nesneler için yalnızca yönlendirebiliriz <xref:System.Windows.Controls.ControlTemplate>.  
  
-   Dinamik kaynak başvuruları veya veri bağlama ifadeleri ayarlamak için kullanamazsınız <xref:System.Windows.Media.Animation.Storyboard> veya animasyon özellik değerleri. Çünkü içindeki her şey bir <xref:System.Windows.Controls.ControlTemplate> iş parçacığı açısından güvenli olmalıdır ve zamanlama sistemi <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> bunları iş parçacığı açısından güvenli hale getirmek için nesneleri. A <xref:System.Windows.Media.Animation.Storyboard> veya onun alt öğe zaman çizelgelerini dinamik kaynak başvuruları veya veri bağlama ifadeleri içeriyorsa nelze zmrazit. Dondurma ve diğer hakkında daha fazla bilgi için <xref:System.Windows.Freezable> özellikler bkz [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).  
  
-   İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], için olay işleyicileri bildiremezsiniz <xref:System.Windows.Media.Animation.Storyboard> veya animasyon olayları.  
  
 İçinde bir film şeridini tanımlama gösteren bir örnek için bir <xref:System.Windows.Controls.ControlTemplate>, bkz: [ControlTemplate içinde animasyon Ekle](how-to-animate-in-a-controltemplate.md) örnek.  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>Bir özellik değeri değiştirildiğinde animasyon ekleme  
 Stiller ve denetim şablonları, bir özellik değiştiğinde film şeridi başlatmak için tetikleyici nesneleri kullanabilirsiniz. Örnekler için bkz [bir animasyon bir özellik değeri değiştiğinde tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md) ve [ControlTemplate içinde animasyon Ekle](how-to-animate-in-a-controltemplate.md).  
  
 Özelliği tarafından uygulanan animasyonlar <xref:System.Windows.Trigger> nesneleri davranır daha karmaşık bir biçimde <xref:System.Windows.EventTrigger> animasyonlar veya animasyonları kullanılarak başlatılan <xref:System.Windows.Media.Animation.Storyboard> yöntemleri.  Bunlar animasyonlarla "iletim diğer tarafından tanımlanan" <xref:System.Windows.Trigger> nesneleri, ancak compose ile <xref:System.Windows.EventTrigger> ve animasyonlar yöntemi tetiklendi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
