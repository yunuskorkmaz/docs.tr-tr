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
ms.openlocfilehash: 5c058dbaf2ae209a198a8299790d4002447ac443
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559701"
---
# <a name="storyboards-overview"></a>Görsel Taslaklara Genel Bakış

Bu konuda, animasyonları düzenlemek ve uygulamak için <xref:System.Windows.Media.Animation.Storyboard> nesnelerinin nasıl kullanılacağı gösterilmektedir. <xref:System.Windows.Media.Animation.Storyboard> nesneleri etkileşimli olarak nasıl işleyebileceğinizi ve dolaylı Özellik hedefleme söz dizimini açıklar.

## <a name="prerequisites"></a>Prerequisites

Bu konuyu anlamak için, farklı animasyon türleri ve bunların temel özellikleri hakkında bilgi sahibi olmanız gerekir. Animasyona giriş için bkz. [animasyona genel bakış](animation-overview.md). Ayrıca ekli özelliklerin nasıl kullanılacağını da bilmeniz gerekir. Ekli Özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>Görsel taslak nedir?

Animasyonlar, zaman çizelgesinin yalnızca faydalı türü değildir. Diğer zaman çizelgesi sınıfları, zaman çizelgesi kümelerini düzenlemenize ve özellikleri zaman çizelgelerini uygulamanıza yardımcı olmak için sağlanır. Kapsayıcı zaman çizelgeleri <xref:System.Windows.Media.Animation.TimelineGroup> sınıfından türetilir ve <xref:System.Windows.Media.Animation.ParallelTimeline> ve <xref:System.Windows.Media.Animation.Storyboard>içerir.

<xref:System.Windows.Media.Animation.Storyboard>, sahip olduğu zaman çizelgeleri için hedefleme bilgilerini sağlayan bir kapsayıcı zaman çizelgesi türüdür. Görsel taslak, diğer kapsayıcı zaman çizelgeleri ve animasyonları dahil olmak üzere herhangi bir tür <xref:System.Windows.Media.Animation.Timeline>içerebilir. <xref:System.Windows.Media.Animation.Storyboard> nesneler, çeşitli nesneleri ve özellikleri tek bir zaman çizelgesi ağacında etkileyen zaman çizelgelerini birleştirerek karmaşık zamanlama davranışlarını düzenlemenizi ve denetlemenizi kolaylaştırır. Örneğin, bu üç şeyi yapan bir düğme istediğinizi varsayalım.

- Kullanıcı düğmeyi seçtiğinde büyüt ve rengi değiştir.

- , Öğesini daraltın ve sonra tıklandığı zaman özgün boyutuna büyüt.

- Devre dışı bırakıldığında, yüzde 50 opaklık ve daraltma.

Bu durumda, aynı nesneye uygulanan birden fazla animasyon kümesi vardır ve düğmenin durumuna bağlı olarak farklı zamanlarda yürütmek istersiniz. <xref:System.Windows.Media.Animation.Storyboard> nesneler, animasyonları düzenlemenize ve gruplar halinde bir veya daha fazla nesneye uygulamanıza olanak tanır.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Film şeridini nerede kullanabilirsiniz?

<xref:System.Windows.Media.Animation.Storyboard>, Animatable sınıflarının bağımlılık özelliklerine animasyon uygulamak için kullanılabilir (bir sınıf canlandırılacak olan nedir hakkında daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md)). Ancak, görsel taslak oluşturma bir çerçeve düzeyi özelliği olduğundan, nesne bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement><xref:System.Windows.NameScope> ait olmalıdır.

Örneğin, aşağıdakileri yapmak için bir <xref:System.Windows.Media.Animation.Storyboard> kullanabilirsiniz:

- Bir düğmenin (<xref:System.Windows.FrameworkElement>türü) arka planını boyayan bir <xref:System.Windows.Media.SolidColorBrush> (Framework olmayan öğe) animasyonunu yapın,

- <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>) kullanılarak görüntülenen bir <xref:System.Windows.Media.GeometryDrawing> (Framework olmayan öğe) dolgusunu boyayan bir <xref:System.Windows.Media.SolidColorBrush> (Framework olmayan öğe) animasyonunu yapın.

- Kod ' da, <xref:System.Windows.Media.SolidColorBrush> adını bu <xref:System.Windows.FrameworkElement>kaydettirirse, bir <xref:System.Windows.FrameworkElement>içeren bir sınıf tarafından tanımlanan <xref:System.Windows.Media.SolidColorBrush> canlandırın.

Ancak, adını bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>kaydetmeyen veya bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>özelliği ayarlamak için kullanılmamış bir <xref:System.Windows.Media.SolidColorBrush> hareketlendirmek için <xref:System.Windows.Media.Animation.Storyboard> kullanamazsınız.

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Görsel taslağa sahip animasyonları uygulama

Animasyonları düzenlemek ve uygulamak üzere bir <xref:System.Windows.Media.Animation.Storyboard> kullanmak için, animasyonları <xref:System.Windows.Media.Animation.Storyboard>alt zaman çizelgeleri olarak eklersiniz. <xref:System.Windows.Media.Animation.Storyboard> sınıfı, <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> ekli özellikleri sağlar. Bu özellikleri bir animasyon üzerinde, hedef nesnesini ve özelliğini belirtmek için ayarlarsınız.

Animasyonlara animasyon uygulamak için, bir tetikleyici eylemi veya bir yöntemi kullanarak <xref:System.Windows.Media.Animation.Storyboard> başlatın. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bir <xref:System.Windows.Media.Animation.BeginStoryboard> nesnesini <xref:System.Windows.EventTrigger>, <xref:System.Windows.Trigger>veya <xref:System.Windows.DataTrigger>ile kullanırsınız. Kodda, <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemini de kullanabilirsiniz.

Aşağıdaki tabloda her <xref:System.Windows.Media.Animation.Storyboard> Begin tekniğinin desteklendiği farklı konumlar gösterilmektedir: örnek başına, stil, denetim şablonu ve veri şablonu. "Örnek başına" bir animasyon veya görsel taslağı, bir stil, denetim şablonu veya veri şablonu yerine doğrudan nesnenin örneklerine uygulama tekniği anlamına gelir.

|Görsel taslak kullanılarak başlatıldı...|Örnek başına|Stil|Denetim şablonu|Veri şablonu|Örnek|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve <xref:System.Windows.EventTrigger>|Evet|Evet|Evet|Evet|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve bir özellik <xref:System.Windows.Trigger>|Hayır|Evet|Evet|Evet|[Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve <xref:System.Windows.DataTrigger>|Hayır|Evet|Evet|Evet|[Nasıl yapılır: veri değiştiğinde animasyon tetikleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi|Evet|Hayır|Hayır|Hayır|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|

Aşağıdaki örnek bir <xref:System.Windows.Shapes.Rectangle> öğesi <xref:System.Windows.FrameworkElement.Width%2A> hareketlendirmek için bir <xref:System.Windows.Media.Animation.Storyboard> kullanır ve bu <xref:System.Windows.Media.SolidColorBrush> boyamak için kullanılan bir <xref:System.Windows.Shapes.Rectangle><xref:System.Windows.Media.SolidColorBrush.Color%2A>.

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

Aşağıdaki bölümlerde <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve ekli özellikler <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> daha ayrıntılı olarak açıklanır.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Framework öğelerini, Framework Içerik öğelerini ve Freezable nesneleri hedefleme

Önceki bölümde, bir animasyonun hedefini bulması için hedefin adı ve animasyon uygulanacak özelliği bilmeleri gerekir. Animasyon uygulanacak özelliği belirtmek düz bir işlemdir: <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType>, animasyon eklenecek özelliğin adıyla ayarlayın.  Animasyonunda <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> özelliğini ayarlayarak, özelliğini hareketlendirmek istediğiniz nesnenin adını belirtirsiniz.

<xref:System.Windows.Setter.TargetName%2A> özelliğinin çalışması için, hedeflenen nesne bir ada sahip olmalıdır. Bir <xref:System.Windows.FrameworkElement> veya [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.FrameworkContentElement> bir adı atamak <xref:System.Windows.Freezable> nesnesine bir ad atamaktan farklıdır.

Framework öğeleri, <xref:System.Windows.FrameworkElement> sınıfından kalıtımla alan sınıflardır. Çerçeve öğelerine örnek olarak <xref:System.Windows.Window>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Button>ve <xref:System.Windows.Shapes.Rectangle>verilebilir. Temelde tüm pencereler, paneller ve denetimler öğelerdir. Framework içerik öğeleri, <xref:System.Windows.FrameworkContentElement> sınıfından kalıtımla alan sınıflardır. Framework içerik öğelerinin örnekleri <xref:System.Windows.Documents.FlowDocument> ve <xref:System.Windows.Documents.Paragraph>içerir. Bir türün çerçeve öğesi veya çerçeve içerik öğesi olup olmadığından emin değilseniz, bir ad özelliğine sahip olup olmadığını denetleyin. Bu, büyük olasılıkla bir çerçeve öğesi ya da çerçeve içerik öğesidir. Emin olmak için, tür sayfasının devralma hiyerarşisi bölümünü kontrol edin.

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]çerçeve öğesi veya çerçeve içerik öğesi hedeflemesini etkinleştirmek için, <xref:System.Windows.FrameworkElement.Name%2A> özelliğini ayarlarsınız. Kod içinde, öğe adını bir <xref:System.Windows.NameScope>oluşturduğunuz öğesiyle kaydetmek için <xref:System.Windows.NameScope.RegisterName%2A> yöntemini de kullanmanız gerekir.

Yukarıdaki örnekten alınan aşağıdaki örnek, bir tür <xref:System.Windows.FrameworkElement><xref:System.Windows.Shapes.Rectangle>`MyRectangle` adı atar.

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Bir ada sahip olduktan sonra, bu öğenin bir özelliğine animasyon uygulayabilirsiniz.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable> türler, <xref:System.Windows.Freezable> sınıfından kalıtımla alan sınıflardır. <xref:System.Windows.Freezable> örnekleri <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.RotateTransform>ve <xref:System.Windows.Media.GradientStop>içerir.

Bir <xref:System.Windows.Freezable> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir animasyon tarafından hedeflemesini etkinleştirmek için, bu adı atamak üzere [X:Name yönergesini](../../../desktop-wpf/xaml-services/xname-directive.md) kullanın. Kodda, adını <xref:System.Windows.NameScope>oluşturduğunuz öğesiyle kaydetmek için <xref:System.Windows.NameScope.RegisterName%2A> yöntemini kullanırsınız.

Aşağıdaki örnek bir <xref:System.Windows.Freezable> nesnesine bir ad atar.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

Nesne daha sonra bir animasyon tarafından hedeflenebilir.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard> nesneleri <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özelliğini çözümlemek için ad kapsamlarını kullanır. WPF ad kapsamları hakkında daha fazla bilgi için bkz. [WPF xaml namescopes](../advanced/wpf-xaml-namescopes.md). <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özelliği atlanırsa, animasyon tanımlanan öğeyi hedefler veya stiller söz konusu olduğunda stilli öğe.

Bazen <xref:System.Windows.Freezable> nesnesine bir ad atanamaz. Örneğin, bir <xref:System.Windows.Freezable> kaynak olarak bildirilirse veya bir stilde Özellik değeri ayarlamak için kullanılırsa, buna bir ad verilemez. Bir adı olmadığı için doğrudan hedeflenemez, ancak dolaylı olarak hedeflenebilir. Aşağıdaki bölümlerde dolaylı hedefleme kullanımı açıklanır.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Dolaylı hedefleme

Bir <xref:System.Windows.Freezable>, bir <xref:System.Windows.Freezable> kaynak olarak bildirildiği ya da bir stilde Özellik değeri ayarlamak için kullanıldığı durumlar gibi bir animasyon tarafından doğrudan hedeflenemez. Bu gibi durumlarda, doğrudan hedeflendiremeseniz bile <xref:System.Windows.Freezable> nesnesine animasyon uygulayabilirsiniz. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özelliğini <xref:System.Windows.Freezable>adı ile ayarlamak yerine, buna <xref:System.Windows.Freezable> "ait olduğu öğenin adını verirsiniz. Örneğin, bir dikdörtgen öğesinin <xref:System.Windows.Shapes.Shape.Fill%2A> ayarlamak için kullanılan bir <xref:System.Windows.Media.SolidColorBrush> bu dikdörtgene aittir. Fırçaya animasyon uygulamak için, animasyonun <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> çerçeve öğesi veya çerçeve içerik <xref:System.Windows.Freezable> öğesinin özelliğinde başlayan bir özellikler zinciri ile, animasyon için <xref:System.Windows.Freezable> özelliğini ayarlamak için kullanılan bir özellik zinciri ile ayarlarsınız.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

<xref:System.Windows.Freezable> dondurulmuşsa, bir kopyanın yapıldığını ve bu kopyanın animasyon olacağını unutmayın. Bu durumda, özgün nesne gerçekten canlandırılmış olmadığından, özgün nesnenin <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> özelliği `false`döndürmeye devam eder. Kopyalama hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).

Ayrıca, dolaylı Özellik hedefleme kullanılırken mevcut olmayan nesneleri hedeflemek mümkün olduğunu unutmayın. Örneğin, belirli bir düğmenin <xref:System.Windows.Controls.Control.Background%2A> bir <xref:System.Windows.Media.SolidColorBrush> ayarlandığını ve bu durumda düğmenin arka planını ayarlamak için bir <xref:System.Windows.Media.LinearGradientBrush> kullanıldığını gösteren rengi hareketlendirmek gerektiğini varsayabilirsiniz. Bu durumlarda, hiçbir özel durum oluşturulmaz; <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliğindeki değişikliklere tepki vermediğinden animasyon görünür etkiye sahip olmaz.

Aşağıdaki bölümlerde, dolaylı Özellik hedefleme sözdizimi daha ayrıntılı olarak açıklanır.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>XAML 'de Freezable 'ın bir özelliğini dolaylı olarak hedefleme

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir Freezable özelliğini hedeflemek için aşağıdaki sözdizimini kullanın.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Where

- *ElementPropertyName* , <xref:System.Windows.Freezable> ayarlamak için kullanılan <xref:System.Windows.FrameworkElement> özelliğidir ve

- *FreezablePropertyName* , hareketlendirmek için <xref:System.Windows.Freezable> özelliğidir.

Aşağıdaki kod, dikdörtgen bir öğenin <xref:System.Windows.Shapes.Shape.Fill%2A> ayarlamak için kullanılan bir <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.SolidColorBrush.Color%2A> nasıl hareketlendirileceğini gösterir.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Bazen bir koleksiyon veya dizide bulunan bir Freezable 'ı hedefleyebilirsiniz.

Bir koleksiyonda bulunan bir Freezable 'ı hedeflemek için aşağıdaki yol söz dizimini kullanın.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Burada *CollectionIndex* nesnesinin veya koleksiyonundaki nesnenin dizinidir.

Örneğin, bir dikdörtgenin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine uygulanmış <xref:System.Windows.Media.TransformGroup> bir kaynağı olduğunu ve içerdiği dönüşümlerden birine animasyon eklemek istediğinizi varsayalım.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

Aşağıdaki kod, önceki örnekte gösterilen <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliğinin nasıl hareketlendirileceğini gösterir.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Kod içinde Freezable 'ın bir özelliğini dolaylı olarak hedefleme

Kod ' de bir <xref:System.Windows.PropertyPath> nesnesi oluşturursunuz. <xref:System.Windows.PropertyPath>oluşturduğunuzda, bir <xref:System.Windows.PropertyPath.Path%2A> ve <xref:System.Windows.PropertyPath.PathParameters%2A>belirtirsiniz.

<xref:System.Windows.PropertyPath.PathParameters%2A>oluşturmak için, bağımlılık özelliği tanımlayıcı alanlarının bir listesini içeren <xref:System.Windows.DependencyProperty> türünde bir dizi oluşturun. İlk tanımlayıcı alanı, <xref:System.Windows.FrameworkElement> özelliği veya <xref:System.Windows.Freezable> ayarlamak için kullanılan <xref:System.Windows.FrameworkContentElement> içindir. Sonraki tanımlayıcı alanı, hedeflenecek <xref:System.Windows.Freezable> özelliğini temsil eder. <xref:System.Windows.Freezable> <xref:System.Windows.FrameworkElement> nesnesine bağlayan özelliklerin zinciri olarak düşünün.

Aşağıda, dikdörtgen bir öğenin <xref:System.Windows.Shapes.Shape.Fill%2A> ayarlamak için kullanılan bir <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.SolidColorBrush.Color%2A> hedefleyen bir bağımlılık özelliği zinciri örneği verilmiştir.

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Ayrıca bir <xref:System.Windows.PropertyPath.Path%2A>belirtmeniz gerekir. <xref:System.Windows.PropertyPath.Path%2A>, <xref:System.Windows.PropertyPath.PathParameters%2A>nasıl yorumlanacağı <xref:System.Windows.PropertyPath.Path%2A> bildiren bir <xref:System.String>. Aşağıdaki sözdizimini kullanır.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|

Where

- *OwnerPropertyArrayIndex* , <xref:System.Windows.Freezable> ayarlamak için kullanılan <xref:System.Windows.FrameworkElement> nesnenin özelliğinin tanımlayıcısını içeren <xref:System.Windows.DependencyProperty> dizisinin dizinidir ve

- *FreezablePropertyArrayIndex* , hedeflenecek özelliğin tanımlayıcısını içeren <xref:System.Windows.DependencyProperty> dizisinin dizinidir.

Aşağıdaki örnekte, önceki örnekte tanımlanan <xref:System.Windows.PropertyPath.PathParameters%2A> eşlik eden <xref:System.Windows.PropertyPath.Path%2A> gösterilmektedir.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

Aşağıdaki örnek, bir dikdörtgen öğesinin <xref:System.Windows.Shapes.Shape.Fill%2A> ayarlamak için kullanılan bir <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.SolidColorBrush.Color%2A> hareketlendirmek için önceki örneklerdeki kodu birleştirir.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Bazen bir koleksiyon veya dizide bulunan bir Freezable 'ı hedefleyebilirsiniz. Örneğin, bir dikdörtgenin <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine uygulanmış <xref:System.Windows.Media.TransformGroup> bir kaynağı olduğunu ve içerdiği dönüşümlerden birine animasyon eklemek istediğinizi varsayalım.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Bir koleksiyonda bulunan bir <xref:System.Windows.Freezable> hedeflemek için aşağıdaki yol söz dizimini kullanın.

| |
|-|
|`(` *OwnerPropertyArrayIndex* `).(` *Collectionchildrenpropertyarrayındex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|

Burada *CollectionIndex* nesnesinin veya koleksiyonundaki nesnenin dizinidir.

<xref:System.Windows.Media.TransformGroup>ikinci dönüşüm olan <xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.RotateTransform.Angle%2A> özelliğini hedeflemek için aşağıdaki <xref:System.Windows.PropertyPath.Path%2A> ve <xref:System.Windows.PropertyPath.PathParameters%2A>kullanırsınız.

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

Aşağıdaki örnek, bir <xref:System.Windows.Media.TransformGroup>içindeki bir <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform.Angle%2A> hareketlendirmek için tüm kodu gösterir.

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Başlangıç noktası olarak Freezable ile dolaylı olarak hedefleme

Önceki bölümlerde, bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> ile başlayıp bir <xref:System.Windows.Freezable> alt özelliğine bir özellik zinciri oluşturarak <xref:System.Windows.Freezable> dolaylı olarak nasıl hedeflendiği açıklanmaktadır. Ayrıca, bir <xref:System.Windows.Freezable> başlangıç noktası olarak kullanabilir ve <xref:System.Windows.Freezable> alt özelliklerinden birini dolaylı olarak hedefleyebilirsiniz. Bir <xref:System.Windows.Freezable> dolaylı hedefleme için başlangıç noktası olarak kullanıldığında bir ek kısıtlama geçerlidir: başlangıç <xref:System.Windows.Freezable> ve onunla dolaylı olarak hedeflenen alt özellik arasındaki her <xref:System.Windows.Freezable> dondurulmuş olmamalıdır.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>XAML 'de görsel taslağı etkileşimli olarak denetleme

[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir film şeridini başlatmak için <xref:System.Windows.Media.Animation.BeginStoryboard> tetikleyici eylemi kullanırsınız. <xref:System.Windows.Media.Animation.BeginStoryboard>, animasyonlarını Animasyon nesnelerin ve özelliklerine dağıtır ve film şeridini başlatır. (Bu işlem hakkındaki ayrıntılar için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).) <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> özelliğini belirterek <xref:System.Windows.Media.Animation.BeginStoryboard> bir ad verirseniz, denetlenebilir bir görsel taslak yaparsınız. Daha sonra film şeridini başladıktan sonra etkileşimli bir şekilde denetleyebilirsiniz. Bir film şeridini denetlemek için olay tetikleyicilerle birlikte kullandığınız denetlenebilir görsel taslak eylemlerinin bir listesi aşağıda verilmiştir.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: film şeridini duraklatır.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: duraklatılmış bir film şeridini sürdürür.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: görsel taslağın hızını değiştirir.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: bir film şeridini, varsa, kendi Fill döneminin sonuna Ilerletir.

- <xref:System.Windows.Media.Animation.StopStoryboard>: film şeridini sonlandırır.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: görsel taslağı kaldırır.

Aşağıdaki örnekte, denetlenebilir görsel taslak eylemleri görsel taslağı etkileşimli olarak denetlemek için kullanılır.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Kod kullanarak görsel taslağı etkileşimli olarak denetleme

Önceki örneklerde tetikleyici eylemleri kullanılarak nasıl animasyon ekleneceği gösterilmekte. Kodda, <xref:System.Windows.Media.Animation.Storyboard> sınıfının etkileşimli yöntemlerini kullanarak bir görsel taslağı da denetleyebilirsiniz. Kod içinde etkileşimli hale getirilme <xref:System.Windows.Media.Animation.Storyboard> için, görsel taslak <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yönteminin uygun aşırı yüklemesini kullanmanız ve denetlenebilir hale getirmek için `true` belirtmeniz gerekir. Daha fazla bilgi için <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29> sayfasına bakın.

Aşağıdaki listede, başlatıldıktan sonra bir <xref:System.Windows.Media.Animation.Storyboard> işlemek için kullanılabilecek yöntemler gösterilmektedir:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

Bu yöntemleri kullanmanın avantajı, <xref:System.Windows.Trigger> veya <xref:System.Windows.TriggerAction> nesneleri oluşturmanız gerekmez; yalnızca denetlemek istediğiniz denetlenebilir <xref:System.Windows.Media.Animation.Storyboard> bir başvuruya ihtiyacınız vardır.

> [!NOTE]
> Bir <xref:System.Windows.Media.Animation.Clock>gerçekleştirilen tüm etkileşimli eylemler ve bu nedenle, bir sonraki işleme göre kısa süre önce gerçekleştirilecek olan zamanlama altyapısının bir sonraki Tick 'i üzerinde de bir <xref:System.Windows.Media.Animation.Storyboard> oluşur. Örneğin, bir animasyondaki başka bir noktaya geçmek için <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemini kullanırsanız, özellik değeri anında değişmez; bunun yerine, değer zamanlama altyapısının bir sonraki değerinde değişir.

Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Storyboard> sınıfının etkileşimli yöntemleri kullanılarak animasyonların nasıl uygulanacağını ve denetleneceğini gösterir.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Bir Stile Animasyon Ekleme

Bir <xref:System.Windows.Style>animasyonları tanımlamak için <xref:System.Windows.Media.Animation.Storyboard> nesneleri kullanabilirsiniz. Bir <xref:System.Windows.Style> <xref:System.Windows.Media.Animation.Storyboard> ile hareketlendirmek, aşağıdaki üç özel durum dışında <xref:System.Windows.Media.Animation.Storyboard> başka bir yerde kullanılmasına benzerdir:

- <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>belirtmezsiniz; <xref:System.Windows.Media.Animation.Storyboard> her zaman <xref:System.Windows.Style> uygulandığı öğeyi hedefler. <xref:System.Windows.Freezable> nesneleri hedeflemek için, dolaylı hedefleme kullanmanız gerekir. Dolaylı hedefleme hakkında daha fazla bilgi için, bkz. [dolaylı hedefleme](#pathsyntaxforchangeable) bölümü.

- Bir <xref:System.Windows.EventTrigger> veya <xref:System.Windows.Trigger>için <xref:System.Windows.EventTrigger.SourceName%2A> belirtemezsiniz.

- <xref:System.Windows.Media.Animation.Storyboard> veya animasyon özelliği değerlerini ayarlamak için dinamik kaynak başvurularını veya veri bağlama ifadelerini kullanamazsınız. Çünkü <xref:System.Windows.Style> içindeki her şey iş parçacığı açısından güvenli olmalıdır ve zamanlama sisteminin iş parçacığı güvenli hale getirmek için <xref:System.Windows.Media.Animation.Storyboard> nesneleri <xref:System.Windows.Freezable.Freeze%2A>gerekir. Veya alt zaman çizelgeleri dinamik kaynak başvuruları veya veri bağlama ifadeleri içeriyorsa <xref:System.Windows.Media.Animation.Storyboard> dondurulamıyor. Dondurma ve diğer <xref:System.Windows.Freezable> özellikleri hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Media.Animation.Storyboard> veya animasyon olayları için olay işleyicileri bildiremezsiniz.

Bir stil içinde bir film şeridinin nasıl tanımlanacağını gösteren bir örnek için, [bir stil örneğine animasyon ekleme](how-to-animate-in-a-style.md) bölümüne bakın.

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>ControlTemplate İçinde Animasyon Ekleme

Bir <xref:System.Windows.Controls.ControlTemplate>animasyonları tanımlamak için <xref:System.Windows.Media.Animation.Storyboard> nesneleri kullanabilirsiniz. Bir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Media.Animation.Storyboard> ile hareketlendirmek, aşağıdaki iki özel durum dışında <xref:System.Windows.Media.Animation.Storyboard> başka bir yerde kullanılmasına benzerdir:

- <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> yalnızca <xref:System.Windows.Controls.ControlTemplate>alt nesnelerine başvurabilir. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> belirtilmemişse, animasyon <xref:System.Windows.Controls.ControlTemplate> uygulanan öğeyi hedefler.

- Bir <xref:System.Windows.EventTrigger> veya <xref:System.Windows.Trigger> için <xref:System.Windows.EventTrigger.SourceName%2A> yalnızca <xref:System.Windows.Controls.ControlTemplate>alt nesnelerine başvurabilir.

- <xref:System.Windows.Media.Animation.Storyboard> veya animasyon özelliği değerlerini ayarlamak için dinamik kaynak başvurularını veya veri bağlama ifadelerini kullanamazsınız. Çünkü <xref:System.Windows.Controls.ControlTemplate> içindeki her şey iş parçacığı açısından güvenli olmalıdır ve zamanlama sisteminin iş parçacığı güvenli hale getirmek için <xref:System.Windows.Media.Animation.Storyboard> nesneleri <xref:System.Windows.Freezable.Freeze%2A>gerekir. Veya alt zaman çizelgeleri dinamik kaynak başvuruları veya veri bağlama ifadeleri içeriyorsa <xref:System.Windows.Media.Animation.Storyboard> dondurulamıyor. Dondurma ve diğer <xref:System.Windows.Freezable> özellikleri hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Media.Animation.Storyboard> veya animasyon olayları için olay işleyicileri bildiremezsiniz.

Bir <xref:System.Windows.Controls.ControlTemplate>film şeridinin nasıl tanımlanacağını gösteren bir örnek için, bkz. [bir ControlTemplate 'de hareketlendirme](how-to-animate-in-a-controltemplate.md) örneği.

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Özellik değeri değiştiğinde animasyon ekleme

Stiller ve denetim şablonlarında, bir özellik değiştiğinde film şeridi başlatmak için tetikleyici nesnelerini kullanabilirsiniz. Örnekler için bkz. bir özellik değeri değiştiğinde ve [bir ControlTemplate 'de animasyon](how-to-animate-in-a-controltemplate.md) [uyguladığınızda animasyon tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md) .

Özellik <xref:System.Windows.Trigger> nesneleri tarafından uygulanan animasyonlar, <xref:System.Windows.EventTrigger> animasyonlarından veya <xref:System.Windows.Media.Animation.Storyboard> yöntemler kullanılarak başlatılan animasyonlardan daha karmaşık bir biçimde davranır.  Diğer <xref:System.Windows.Trigger> nesneleri tarafından tanımlanan animasyonlarla "iletiler", ancak <xref:System.Windows.EventTrigger> ve yöntemin tetiklediği animasyonlarla oluştur.

## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
