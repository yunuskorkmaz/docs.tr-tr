---
title: Görsel Taslaklara Genel Bakış
desription: Organize and apply animations in storyboards. Use property-targeting syntax and combine timelines in Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 50f45953da3801bf73016c09b78a6a1b54878bc0
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853645"
---
# <a name="storyboards-overview"></a>Görsel Taslaklara Genel Bakış

Bu konu <xref:System.Windows.Media.Animation.Storyboard> , animasyonları düzenlemek ve uygulamak için nesneleri nasıl kullanacağınızı gösterir. Nesneleri etkileşimli olarak nasıl işleyebileceğinizi <xref:System.Windows.Media.Animation.Storyboard> ve dolaylı Özellik hedefleme söz dizimini açıklar.

## <a name="prerequisites"></a>Önkoşullar

Bu konuyu anlamak için, farklı animasyon türleri ve bunların temel özellikleri hakkında bilgi sahibi olmanız gerekir. Animasyona giriş için bkz. [animasyona genel bakış](animation-overview.md). Ayrıca ekli özelliklerin nasıl kullanılacağını da bilmeniz gerekir. Ekli Özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>Görsel taslak nedir?

Animasyonlar, zaman çizelgesinin yalnızca faydalı türü değildir. Diğer zaman çizelgesi sınıfları, zaman çizelgesi kümelerini düzenlemenize ve özellikleri zaman çizelgelerini uygulamanıza yardımcı olmak için sağlanır. Kapsayıcı zaman çizelgeleri sınıfından türetilir <xref:System.Windows.Media.Animation.TimelineGroup> ve <xref:System.Windows.Media.Animation.ParallelTimeline> ve içerir <xref:System.Windows.Media.Animation.Storyboard> .

<xref:System.Windows.Media.Animation.Storyboard>, İçerdiği zaman çizelgeleri için hedefleme bilgilerini sağlayan bir kapsayıcı zaman çizelgesi türüdür. Görsel taslak <xref:System.Windows.Media.Animation.Timeline> , diğer kapsayıcı zaman çizelgeleri ve animasyonları dahil olmak üzere herhangi bir tür içerebilir. <xref:System.Windows.Media.Animation.Storyboard>nesneler, çeşitli nesne ve özellikleri etkileyen zaman çizelgelerini tek bir zaman çizelgesi ağacında birleştirerek karmaşık zamanlama davranışlarını düzenlemenizi ve denetlemenizi kolaylaştırır. Örneğin, bu üç şeyi yapan bir düğme istediğinizi varsayalım.

- Kullanıcı düğmeyi seçtiğinde büyüt ve rengi değiştir.

- , Öğesini daraltın ve sonra tıklandığı zaman özgün boyutuna büyüt.

- Devre dışı bırakıldığında, yüzde 50 opaklık ve daraltma.

Bu durumda, aynı nesneye uygulanan birden fazla animasyon kümesi vardır ve düğmenin durumuna bağlı olarak farklı zamanlarda yürütmek istersiniz. <xref:System.Windows.Media.Animation.Storyboard>nesneler, animasyonları düzenlemenizi ve gruplar halinde bir veya daha fazla nesneye uygulamanızı sağlar.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Film şeridini nerede kullanabilirsiniz?

<xref:System.Windows.Media.Animation.Storyboard>, Animatable sınıflarının bağımlılık özelliklerine animasyon uygulamak için kullanılabilir (bir sınıf canlandırılacak olan nedir hakkında daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md)). Ancak, görsel taslak oluşturma bir çerçeve düzeyi özellik olduğundan, nesnesi bir veya ' a ait olmalıdır <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> .

Örneğin, <xref:System.Windows.Media.Animation.Storyboard> aşağıdakileri yapmak için bir kullanabilirsiniz:

- Bir <xref:System.Windows.Media.SolidColorBrush> düğmenin (türü) arka planını boyayan bir (Framework olmayan öğe) animasyonu <xref:System.Windows.FrameworkElement>

- Bir ( <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.GeometryDrawing> ) () kullanılarak görüntülenen (Framework olmayan öğe) dolgusunu boyayan bir (Framework olmayan öğe) animasyonu <xref:System.Windows.Controls.Image> <xref:System.Windows.FrameworkElement> .

- Kod içinde, <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.FrameworkElement> <xref:System.Windows.Media.SolidColorBrush> adını ile kayıtlı olan bir sınıf tarafından tanımlanan bir sınıf tarafından animasyon uygulayın <xref:System.Windows.FrameworkElement> .

Ancak, <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.SolidColorBrush> adını bir veya ' a kaydetmeyen veya ya da <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> ' nin bir özelliğini ayarlamak için kullanılmamış olan bir öğesine animasyon uygulamak için kullanamazsınız <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> .

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Görsel taslağa sahip animasyonları uygulama

<xref:System.Windows.Media.Animation.Storyboard>Animasyonları düzenlemek ve uygulamak üzere kullanmak için, animasyonları alt öğe zaman çizelgeleri olarak eklersiniz <xref:System.Windows.Media.Animation.Storyboard> . <xref:System.Windows.Media.Animation.Storyboard>Sınıfı <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> ekli özellikleri sağlar. Bu özellikleri bir animasyon üzerinde, hedef nesnesini ve özelliğini belirtmek için ayarlarsınız.

Animasyonlarına animasyon uygulamak için <xref:System.Windows.Media.Animation.Storyboard> bir tetikleyici eylemi veya bir yöntemi kullanmaya başlayabilirsiniz. İçinde,, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Media.Animation.BeginStoryboard> veya içeren bir nesnesi kullanırsınız <xref:System.Windows.EventTrigger> <xref:System.Windows.Trigger> <xref:System.Windows.DataTrigger> . Kodda, yöntemini de kullanabilirsiniz <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> .

Aşağıdaki tabloda <xref:System.Windows.Media.Animation.Storyboard> , her BEGIN tekniğinin desteklendiği farklı konumlar gösterilmektedir: örnek başına, stil, denetim şablonu ve veri şablonu. "Örnek başına" bir animasyon veya görsel taslağı, bir stil, denetim şablonu veya veri şablonu yerine doğrudan nesnenin örneklerine uygulama tekniği anlamına gelir.

|Görsel taslak kullanılarak başlatıldı...|Örnek başına|Stil|Denetim şablonu|Veri şablonu|Örnek|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir<xref:System.Windows.EventTrigger>|Yes|Yes|Yes|Yes|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir özellik<xref:System.Windows.Trigger>|No|Yes|Yes|Yes|[Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir<xref:System.Windows.DataTrigger>|No|Yes|Yes|Yes|[Nasıl yapılır: veri değiştiğinde animasyon tetikleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi|Evet|Hayır|Hayır|Hayır|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|

Aşağıdaki örnek, <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Shapes.Rectangle> öğesini boyamak için bir öğesi ve bir öğesine animasyon uygulamak için bir kullanır <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Shapes.Rectangle> .

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

Aşağıdaki bölümlerde <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> Ekli Özellikler daha ayrıntılı olarak açıklanır.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Framework öğelerini, Framework Içerik öğelerini ve Freezable nesneleri hedefleme

Önceki bölümde, bir animasyonun hedefini bulması için hedefin adı ve animasyon uygulanacak özelliği bilmeleri gerekir. Animasyon uygulanacak özelliği belirtmek düz bir işlemdir: yalnızca <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> animasyon eklenecek özelliğin adıyla birlikte ayarlanır.  Animasyon üzerinde özelliğini ayarlayarak, özelliğini hareketlendirmek istediğiniz nesnenin adını belirtirsiniz <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> .

<xref:System.Windows.Setter.TargetName%2A>Özelliğin çalışması için, hedeflenen nesne bir ada sahip olmalıdır. Bir veya içine bir adı atamak <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> , bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nesneye ad atamaktan farklıdır <xref:System.Windows.Freezable> .

Framework öğeleri sınıfından kalıtımla alan sınıflardır <xref:System.Windows.FrameworkElement> . Çerçeve öğelerinin örnekleri,, <xref:System.Windows.Window> , <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Button> ve içerir <xref:System.Windows.Shapes.Rectangle> . Temelde tüm pencereler, paneller ve denetimler öğelerdir. Framework içerik öğeleri sınıfından kalıtımla alan sınıflardır <xref:System.Windows.FrameworkContentElement> . Framework içerik öğelerinin örnekleri ve içerir <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.Paragraph> . Bir türün çerçeve öğesi veya çerçeve içerik öğesi olup olmadığından emin değilseniz, bir ad özelliğine sahip olup olmadığını denetleyin. Bu, büyük olasılıkla bir çerçeve öğesi ya da çerçeve içerik öğesidir. Emin olmak için, tür sayfasının devralma hiyerarşisi bölümünü kontrol edin.

' De bir çerçeve öğesi veya çerçeve içerik öğesi hedeflemesini etkinleştirmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , <xref:System.Windows.FrameworkElement.Name%2A> özelliğini ayarlarsınız. Kodda, <xref:System.Windows.NameScope.RegisterName%2A> öğesini oluşturduğunuz öğesiyle öğe adını kaydetmek için yöntemini de kullanmanız gerekir <xref:System.Windows.NameScope> .

Yukarıdaki örnekten alınan aşağıdaki örnek, bir `MyRectangle` türü olan bir adı atar <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.FrameworkElement> .

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Bir ada sahip olduktan sonra, bu öğenin bir özelliğine animasyon uygulayabilirsiniz.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable>türler, sınıfından kalıtımla alan sınıflardır <xref:System.Windows.Freezable> . <xref:System.Windows.Freezable> <xref:System.Windows.Media.SolidColorBrush> , Ve ekleme örnekleri <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.GradientStop> .

' Deki bir animasyon tarafından hedeflemesini etkinleştirmek için <xref:System.Windows.Freezable> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , [x:Name yönergesini](../../../desktop-wpf/xaml-services/xname-directive.md) bir ad atamak için kullanırsınız. Kodda, <xref:System.Windows.NameScope.RegisterName%2A> adını oluşturduğunuz öğesi ile kaydetmek için yöntemini kullanırsınız <xref:System.Windows.NameScope> .

Aşağıdaki örnek bir nesnesine bir ad atar <xref:System.Windows.Freezable> .

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

Nesne daha sonra bir animasyon tarafından hedeflenebilir.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard>nesneler, özelliği çözümlemek için ad kapsamlarını kullanır <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> . WPF ad kapsamları hakkında daha fazla bilgi için bkz. [WPF xaml namescopes](../advanced/wpf-xaml-namescopes.md). <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>Özellik atlanırsa, animasyon tanımlanan öğeyi veya stiller söz konusu olduğunda stilli öğeyi hedefler.

Bazen bir nesneye bir ad atanamaz <xref:System.Windows.Freezable> . Örneğin, bir <xref:System.Windows.Freezable> kaynak olarak bildirilirse veya bir stilde Özellik değeri ayarlamak için kullanılırsa, buna bir ad verilemez. Bir adı olmadığı için doğrudan hedeflenemez, ancak dolaylı olarak hedeflenebilir. Aşağıdaki bölümlerde dolaylı hedefleme kullanımı açıklanır.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Dolaylı hedefleme

Bir <xref:System.Windows.Freezable> animasyon tarafından doğrudan hedeflenemez, örneğin, <xref:System.Windows.Freezable> kaynak olarak bildirildiği veya bir stilde Özellik değeri ayarlamak için kullanılan durumlar vardır. Bu durumlarda, doğrudan hedeflendiremeseniz bile, nesneye animasyon uygulayabilirsiniz <xref:System.Windows.Freezable> . Özelliğini öğesinin adıyla ayarlamak yerine, <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> <xref:System.Windows.Freezable> bu bileşene <xref:System.Windows.Freezable> "ait olduğu" öğesinin adını verirsiniz. Örneğin, dikdörtgen bir <xref:System.Windows.Media.SolidColorBrush> öğenin ' ı ayarlamak için kullanılan bir dikdörtgene <xref:System.Windows.Shapes.Shape.Fill%2A> aittir. Fırçaya animasyon uygulamak için, animasyonu <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> bir çerçeve öğesi veya çerçeve içeriği öğesinin özelliği ile başlayan özellikler zinciri ile, animasyon <xref:System.Windows.Freezable> için özelliği ile ayarlamak için kullanılan bir özellik zinciri ile ayarlarsınız <xref:System.Windows.Freezable> .

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

<xref:System.Windows.Freezable>Dondurulmuşsa, bir kopyanın yapıldığını ve bu kopyanın canlandırılabileceğini unutmayın. Bu durumda, özgün nesne <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> gerçekten canlandırılmış olmadığından özgün nesnenin özelliği Return olmaya devam eder `false` . Kopyalama hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).

Ayrıca, dolaylı Özellik hedefleme kullanılırken mevcut olmayan nesneleri hedeflemek mümkün olduğunu unutmayın. Örneğin, <xref:System.Windows.Controls.Control.Background%2A> belirli bir düğmenin bir ile ayarlandığını varsayabilir ve söz konusu <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.LinearGradientBrush> düğmenin arka planını ayarlamak için kullanılan olgu ' ın rengine animasyon çalıştırmayı deneyebilirsiniz. Bu durumlarda, hiçbir özel durum oluşturulmaz; özelliğin değişikliklere tepki vermediğinden animasyon, görünür bir etkiye sahip olamaz <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.SolidColorBrush.Color%2A> .

Aşağıdaki bölümlerde, dolaylı Özellik hedefleme sözdizimi daha ayrıntılı olarak açıklanır.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>XAML 'de Freezable 'ın bir özelliğini dolaylı olarak hedefleme

İçinde Freezable 'ın bir özelliğini hedeflemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aşağıdaki sözdizimini kullanın.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Konum

- *ElementPropertyName* , <xref:System.Windows.FrameworkElement> <xref:System.Windows.Freezable> öğesini ayarlamak için kullanılan özelliğidir ve

- *FreezablePropertyName* , canlandırılacak öğesinin özelliğidir <xref:System.Windows.Freezable> .

Aşağıdaki kod, <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> dikdörtgen bir öğenin kümesini ayarlamak için kullanılan öğesinin nasıl hareketlendirileceğini gösterir <xref:System.Windows.Shapes.Shape.Fill%2A> .

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Bazen bir koleksiyon veya dizide bulunan bir Freezable 'ı hedefleyebilirsiniz.

Bir koleksiyonda bulunan bir Freezable 'ı hedeflemek için aşağıdaki yol söz dizimini kullanın.

| |
|-|
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|

Burada *CollectionIndex* nesnesinin veya koleksiyonundaki nesnenin dizinidir.

Örneğin, bir dikdörtgenin <xref:System.Windows.Media.TransformGroup> özelliğine bir kaynak uygulandığını <xref:System.Windows.UIElement.RenderTransform%2A> ve içerdiği dönüşümlerden birine animasyon eklemek istediğinizi varsayalım.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

Aşağıdaki kod, <xref:System.Windows.Media.RotateTransform.Angle%2A> Önceki örnekte gösterilen öğesinin özelliğinin nasıl hareketlendirileceğini gösterir <xref:System.Windows.Media.RotateTransform> .

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Kod içinde Freezable 'ın bir özelliğini dolaylı olarak hedefleme

Kod ' de bir nesne oluşturun <xref:System.Windows.PropertyPath> . Oluştururken, <xref:System.Windows.PropertyPath> <xref:System.Windows.PropertyPath.Path%2A> ve belirtirsiniz <xref:System.Windows.PropertyPath.PathParameters%2A> .

Oluşturmak için <xref:System.Windows.PropertyPath.PathParameters%2A> , <xref:System.Windows.DependencyProperty> bağımlılık özelliği tanımlayıcı alanlarının bir listesini içeren türünde bir dizi oluşturun. İlk tanımlayıcı alanı, <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.Freezable> ayarlamak için kullanılan veya özelliğine yöneliktir. Next Identifier alanı, to hedefinin özelliğini temsil eder <xref:System.Windows.Freezable> . Bunu nesnesine bağlayan özelliklerin zinciri olarak düşünün <xref:System.Windows.Freezable> <xref:System.Windows.FrameworkElement> .

Aşağıda, bir <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> dikdörtgen öğesinin kümesini ayarlamak için kullanılan bir bağımlılık özelliği zinciri örneği verilmiştir <xref:System.Windows.Shapes.Shape.Fill%2A> .

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Ayrıca bir belirtmeniz gerekir <xref:System.Windows.PropertyPath.Path%2A> . <xref:System.Windows.PropertyPath.Path%2A> <xref:System.String> , <xref:System.Windows.PropertyPath.Path%2A> Nasıl yorumlayacağını belirten bir <xref:System.Windows.PropertyPath.PathParameters%2A> . Aşağıdaki sözdizimini kullanır.

| |
|-|
|`(`*OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex*`)`|

Konum

- *OwnerPropertyArrayIndex* , <xref:System.Windows.DependencyProperty> <xref:System.Windows.FrameworkElement> ' ın ayarlamak için kullanılan nesnenin özelliğinin tanımlayıcısını içeren dizinin dizinidir <xref:System.Windows.Freezable> ve

- *FreezablePropertyArrayIndex* , <xref:System.Windows.DependencyProperty> hedeflenecek özelliğin tanımlayıcısını içeren dizinin dizinidir.

Aşağıdaki örnek, <xref:System.Windows.PropertyPath.Path%2A> Önceki örnekte tanımlanan öğesine eşlik eden öğesini gösterir <xref:System.Windows.PropertyPath.PathParameters%2A> .

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

Aşağıdaki örnek, <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> bir dikdörtgen öğesini ayarlamak için kullanılan öğesinin animasyonunu yapmak için önceki örneklerde bulunan kodu birleştirir <xref:System.Windows.Shapes.Shape.Fill%2A> .

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Bazen bir koleksiyon veya dizide bulunan bir Freezable 'ı hedefleyebilirsiniz. Örneğin, bir dikdörtgenin <xref:System.Windows.Media.TransformGroup> özelliğine bir kaynak uygulandığını <xref:System.Windows.UIElement.RenderTransform%2A> ve içerdiği dönüşümlerden birine animasyon eklemek istediğinizi varsayalım.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Bir koleksiyonda bulunan bir hedefi hedeflemek için <xref:System.Windows.Freezable> aşağıdaki yol söz dizimini kullanın.

| |
|-|
|`(`*OwnerPropertyArrayIndex* `).(` *Collectionchildrenpropertyarrayındex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex*`)`|

Burada *CollectionIndex* nesnesinin veya koleksiyonundaki nesnenin dizinidir.

<xref:System.Windows.Media.RotateTransform.Angle%2A>İçindeki ikinci dönüşüm olan öğesinin özelliğini hedeflemek için <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.TransformGroup> aşağıdaki <xref:System.Windows.PropertyPath.Path%2A> ve kullanın <xref:System.Windows.PropertyPath.PathParameters%2A> .

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

Aşağıdaki örnek, <xref:System.Windows.Media.RotateTransform.Angle%2A> içindeki içindeki içindeki öğesinin animasyon için tüm kodu gösterir <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.TransformGroup> .

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Başlangıç noktası olarak Freezable ile dolaylı olarak hedefleme

Önceki bölümlerde, bir <xref:System.Windows.Freezable> veya ile başlayıp bir <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> alt özelliğe bir özellik zinciri oluşturarak bir, dolaylı olarak nasıl hedeflenecek anlatılmıştır <xref:System.Windows.Freezable> . Bir <xref:System.Windows.Freezable> Başlangıç noktası olarak da kullanabilirsiniz ve kendi alt özelliklerinden birini dolaylı olarak hedefleyin <xref:System.Windows.Freezable> . <xref:System.Windows.Freezable>Dolaylı hedefleme için başlangıç noktası olarak kullanıldığında bir ek kısıtlama geçerlidir: Başlangıç <xref:System.Windows.Freezable> ve her ikisi <xref:System.Windows.Freezable> arasındaki ve dolaylı olarak hedeflenen alt özelliği dondurulmuş olmamalıdır.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>XAML 'de görsel taslağı etkileşimli olarak denetleme

İçinde bir görsel taslak başlatmak için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bir <xref:System.Windows.Media.Animation.BeginStoryboard> tetikleyici eylemi kullanırsınız. <xref:System.Windows.Media.Animation.BeginStoryboard>animasyonları, canlandırdıkları nesnelere ve özelliklere dağıtır ve film şeridini başlatır. (Bu işlem hakkındaki ayrıntılar için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).) <xref:System.Windows.Media.Animation.BeginStoryboard>Kendi özelliğini belirterek bir ad verirseniz <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> , denetlenebilir bir görsel taslak yaparsınız. Daha sonra film şeridini başladıktan sonra etkileşimli bir şekilde denetleyebilirsiniz. Bir film şeridini denetlemek için olay tetikleyicilerle birlikte kullandığınız denetlenebilir görsel taslak eylemlerinin bir listesi aşağıda verilmiştir.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Film şeridini duraklatır.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış bir film şeridini sürdürür.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Görsel taslak hızını değiştirir.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Bir film şeridini, varsa, kendi Fill döneminin sonuna ilerletir.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Görsel taslağı sonlandırır.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Görsel taslağı kaldırır.

Aşağıdaki örnekte, denetlenebilir görsel taslak eylemleri görsel taslağı etkileşimli olarak denetlemek için kullanılır.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Kod kullanarak görsel taslağı etkileşimli olarak denetleme

Önceki örneklerde tetikleyici eylemleri kullanılarak nasıl animasyon ekleneceği gösterilmekte. Kodda, sınıfın etkileşimli yöntemlerini kullanarak bir görsel taslağı da denetleyebilirsiniz <xref:System.Windows.Media.Animation.Storyboard> . Uygulamasının <xref:System.Windows.Media.Animation.Storyboard> kodda etkileşimli hale getirilme için, görsel taslak yönteminin uygun aşırı yüklemesini kullanmanız <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> ve `true` denetlenebilir hale getirmek için belirtmeniz gerekir. <xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>Daha fazla bilgi için sayfasına bakın.

Aşağıdaki listede, başlatıldıktan sonra bir işlemi işlemek için kullanılabilecek yöntemler gösterilmektedir <xref:System.Windows.Media.Animation.Storyboard> :

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

Bu yöntemleri kullanmanın avantajı, <xref:System.Windows.Trigger> veya nesneleri oluşturmanız gerekmez <xref:System.Windows.TriggerAction> ; yalnızca işlemek istediğiniz denetlenebilir öğesine bir başvuruya ihtiyacınız vardır <xref:System.Windows.Media.Animation.Storyboard> .

> [!NOTE]
> Bir üzerinde gerçekleştirilen tüm etkileşimli eylemler <xref:System.Windows.Media.Animation.Clock> ve bu nedenle bir <xref:System.Windows.Media.Animation.Storyboard> sonraki render 'in kısa süre önce gerçekleştirilecek olan zamanlama altyapısının bir sonraki Tick 'i üzerinde gerçekleşecektir. Örneğin, <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> bir animasyondaki başka bir noktaya geçmek için yöntemini kullanırsanız, özellik değeri anında değişmez; bunun yerine, değer zamanlama altyapısının bir sonraki değerinde değişir.

Aşağıdaki örnekte, sınıfının etkileşimli yöntemleri kullanılarak animasyonların nasıl uygulanacağı ve kontrol edileceği gösterilmektedir <xref:System.Windows.Media.Animation.Storyboard> .

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Bir Stile Animasyon Ekleme

<xref:System.Windows.Media.Animation.Storyboard>' De animasyonları tanımlamak için nesneleri kullanabilirsiniz <xref:System.Windows.Style> . <xref:System.Windows.Media.Animation.Storyboard>Bir içinde ile hareketlendirmek <xref:System.Windows.Style> <xref:System.Windows.Media.Animation.Storyboard> , aşağıdaki üç özel durum dışında başka bir yerde kullanılmasına benzerdir:

- Bir belirtmeniz gerekmez <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ; <xref:System.Windows.Media.Animation.Storyboard> her zaman, uygulandığı öğeyi hedefler <xref:System.Windows.Style> . Nesneleri hedeflemek için <xref:System.Windows.Freezable> dolaylı hedefleme kullanmanız gerekir. Dolaylı hedefleme hakkında daha fazla bilgi için, bkz. [dolaylı hedefleme](#pathsyntaxforchangeable) bölümü.

- <xref:System.Windows.EventTrigger.SourceName%2A>Veya için bir için belirtemezsiniz <xref:System.Windows.EventTrigger> <xref:System.Windows.Trigger> .

- Özellik değerlerini ayarlamak veya animasyon uygulamak için dinamik kaynak başvurularını veya veri bağlama ifadelerini kullanamazsınız <xref:System.Windows.Media.Animation.Storyboard> . Bunun nedeni, içindeki her şeyin <xref:System.Windows.Style> iş parçacığı açısından güvenli olması ve zamanlama sisteminin <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> iş parçacığı açısından güvenli hale getirmek için nesneler olması gerekir. <xref:System.Windows.Media.Animation.Storyboard>Ya da alt zaman çizelgeleri dinamik kaynak başvuruları veya veri bağlama ifadeleri içeriyorsa, A dondurulamıyor. Dondurma ve diğer özellikler hakkında daha fazla bilgi için <xref:System.Windows.Freezable> bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]' De, veya animasyon olayları için olay işleyicileri bildiremezsiniz <xref:System.Windows.Media.Animation.Storyboard> .

Bir stil içinde bir film şeridinin nasıl tanımlanacağını gösteren bir örnek için, [bir stil örneğine animasyon ekleme](how-to-animate-in-a-style.md) bölümüne bakın.

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>ControlTemplate İçinde Animasyon Ekleme

<xref:System.Windows.Media.Animation.Storyboard>' De animasyonları tanımlamak için nesneleri kullanabilirsiniz <xref:System.Windows.Controls.ControlTemplate> . <xref:System.Windows.Media.Animation.Storyboard>Bir içinde ile hareketlendirmek <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Media.Animation.Storyboard> , aşağıdaki iki özel durum dışında başka bir yerde kullanılmasına benzerdir:

- <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>Yalnızca öğesinin alt nesnelerine başvurabilir <xref:System.Windows.Controls.ControlTemplate> . <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>Belirtilmemişse, animasyon uygulanan öğesini hedefler <xref:System.Windows.Controls.ControlTemplate> .

- <xref:System.Windows.EventTrigger.SourceName%2A>Veya için için, <xref:System.Windows.EventTrigger> <xref:System.Windows.Trigger> yalnızca öğesinin alt nesnelerine başvurabilir <xref:System.Windows.Controls.ControlTemplate> .

- Özellik değerlerini ayarlamak veya animasyon uygulamak için dinamik kaynak başvurularını veya veri bağlama ifadelerini kullanamazsınız <xref:System.Windows.Media.Animation.Storyboard> . Bunun nedeni, içindeki her şeyin <xref:System.Windows.Controls.ControlTemplate> iş parçacığı açısından güvenli olması ve zamanlama sisteminin <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> iş parçacığı açısından güvenli hale getirmek için nesneler olması gerekir. <xref:System.Windows.Media.Animation.Storyboard>Ya da alt zaman çizelgeleri dinamik kaynak başvuruları veya veri bağlama ifadeleri içeriyorsa, A dondurulamıyor. Dondurma ve diğer özellikler hakkında daha fazla bilgi için <xref:System.Windows.Freezable> bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).

- [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]' De, veya animasyon olayları için olay işleyicileri bildiremezsiniz <xref:System.Windows.Media.Animation.Storyboard> .

İçindeki bir film şeridini nasıl tanımlayacağınızı gösteren bir örnek için <xref:System.Windows.Controls.ControlTemplate> , bkz. [bir ControlTemplate 'de hareketlendirme](how-to-animate-in-a-controltemplate.md) örneği.

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Özellik değeri değiştiğinde animasyon ekleme

Stiller ve denetim şablonlarında, bir özellik değiştiğinde film şeridi başlatmak için tetikleyici nesnelerini kullanabilirsiniz. Örnekler için bkz. bir özellik değeri değiştiğinde ve [bir ControlTemplate 'de animasyon](how-to-animate-in-a-controltemplate.md) [uyguladığınızda animasyon tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md) .

Özellik nesneleri tarafından uygulanan animasyonlar <xref:System.Windows.Trigger> , <xref:System.Windows.EventTrigger> animasyonlar veya animasyonlar kullanılarak başlatılan animasyonlardan daha karmaşık bir biçimde davranır <xref:System.Windows.Media.Animation.Storyboard> .  Diğer nesneler tarafından tanımlanan animasyonlarla birlikte "iletiler" <xref:System.Windows.Trigger> , ancak <xref:System.Windows.EventTrigger> ve yöntemin tetiklediği animasyonlar ile oluşturma.

## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
