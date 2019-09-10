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
ms.openlocfilehash: 4d5a5ee3f1fcbd09fad9e25773d0e508209e1492
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855844"
---
# <a name="storyboards-overview"></a>Görsel Taslaklara Genel Bakış

Bu konu, animasyonları düzenlemek ve <xref:System.Windows.Media.Animation.Storyboard> uygulamak için nesneleri nasıl kullanacağınızı gösterir. Nesneleri etkileşimli olarak nasıl işleyebileceğinizi <xref:System.Windows.Media.Animation.Storyboard> ve dolaylı Özellik hedefleme söz dizimini açıklar.

## <a name="prerequisites"></a>Önkoşullar

Bu konuyu anlamak için, farklı animasyon türleri ve bunların temel özellikleri hakkında bilgi sahibi olmanız gerekir. Animasyona giriş için bkz. [animasyona genel bakış](animation-overview.md). Ayrıca ekli özelliklerin nasıl kullanılacağını da bilmeniz gerekir. Ekli Özellikler hakkında daha fazla bilgi için bkz. [ekli özelliklere genel bakış](../advanced/attached-properties-overview.md).

<a name="whatisatimeline"></a>

## <a name="what-is-a-storyboard"></a>Görsel taslak nedir?

Animasyonlar, zaman çizelgesinin yalnızca faydalı türü değildir. Diğer zaman çizelgesi sınıfları, zaman çizelgesi kümelerini düzenlemenize ve özellikleri zaman çizelgelerini uygulamanıza yardımcı olmak için sağlanır. Kapsayıcı zaman çizelgeleri <xref:System.Windows.Media.Animation.TimelineGroup> sınıfından türetilir ve ve <xref:System.Windows.Media.Animation.Storyboard>içerir <xref:System.Windows.Media.Animation.ParallelTimeline> .

<xref:System.Windows.Media.Animation.Storyboard> , İçerdiği zaman çizelgeleri için hedefleme bilgilerini sağlayan bir kapsayıcı zaman çizelgesi türüdür. Görsel taslak <xref:System.Windows.Media.Animation.Timeline>, diğer kapsayıcı zaman çizelgeleri ve animasyonları dahil olmak üzere herhangi bir tür içerebilir. <xref:System.Windows.Media.Animation.Storyboard>nesneler, çeşitli nesne ve özellikleri etkileyen zaman çizelgelerini tek bir zaman çizelgesi ağacında birleştirerek karmaşık zamanlama davranışlarını düzenlemenizi ve denetlemenizi kolaylaştırır. Örneğin, bu üç şeyi yapan bir düğme istediğinizi varsayalım.

- Kullanıcı düğmeyi seçtiğinde büyüt ve rengi değiştir.

- , Öğesini daraltın ve sonra tıklandığı zaman özgün boyutuna büyüt.

- Devre dışı bırakıldığında, yüzde 50 opaklık ve daraltma.

Bu durumda, aynı nesneye uygulanan birden fazla animasyon kümesi vardır ve düğmenin durumuna bağlı olarak farklı zamanlarda yürütmek istersiniz. <xref:System.Windows.Media.Animation.Storyboard>nesneler, animasyonları düzenlemenizi ve gruplar halinde bir veya daha fazla nesneye uygulamanızı sağlar.

<a name="wherecanyouuseastoryboard"></a>

## <a name="where-can-you-use-a-storyboard"></a>Film şeridini nerede kullanabilirsiniz?

, Animatable sınıflarının bağımlılık özelliklerine animasyon uygulamak için kullanılabilir (bir sınıf canlandırılacak olan nedir hakkında daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md)). <xref:System.Windows.Media.Animation.Storyboard> Ancak, görsel taslak oluşturma bir çerçeve düzeyi özellik olduğundan, nesnesi bir <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>' a ait olmalıdır.

Örneğin, aşağıdakileri yapmak için bir <xref:System.Windows.Media.Animation.Storyboard> kullanabilirsiniz:

- Bir düğmenin <xref:System.Windows.Media.SolidColorBrush> ( <xref:System.Windows.FrameworkElement>türü) arka planını boyayan bir (Framework olmayan öğe) animasyonu

- Bir ( <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.FrameworkElement>) () kullanılarak <xref:System.Windows.Controls.Image> görüntülenen (Framework olmayan öğe) dolgusunu <xref:System.Windows.Media.GeometryDrawing> boyayan bir (Framework olmayan öğe) animasyonu.

- Kod içinde, adını ile <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.FrameworkElement> kayıtlıolan<xref:System.Windows.Media.SolidColorBrush> bir sınıf tarafından tanımlanan bir sınıf tarafından animasyon uygulayın. <xref:System.Windows.FrameworkElement>

Ancak, <xref:System.Windows.Media.Animation.Storyboard> adını bir <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> 'a<xref:System.Windows.FrameworkContentElement>kaydetmeyen veya ya da ' nin birözelliğiniayarlamakiçinkullanılmamış<xref:System.Windows.FrameworkElement> olan bir öğesine animasyon uygulamak için kullanamazsınız.

<a name="applyanimationswithastoryboard"></a>

## <a name="how-to-apply-animations-with-a-storyboard"></a>Görsel taslağa sahip animasyonları uygulama

Animasyonları düzenlemek ve <xref:System.Windows.Media.Animation.Storyboard> uygulamak üzere kullanmak için, animasyonları alt öğe zaman çizelgeleri <xref:System.Windows.Media.Animation.Storyboard>olarak eklersiniz. <xref:System.Windows.Media.Animation.Storyboard> Sınıfı <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> ve ekli<xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> özellikleri sağlar. Bu özellikleri bir animasyon üzerinde, hedef nesnesini ve özelliğini belirtmek için ayarlarsınız.

Animasyonlarına animasyon uygulamak için bir tetikleyici eylemi veya bir <xref:System.Windows.Media.Animation.Storyboard> yöntemi kullanmaya başlayabilirsiniz. İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.EventTrigger>,, veya <xref:System.Windows.Media.Animation.BeginStoryboard> içerenbir<xref:System.Windows.Trigger>nesnesikullanırsınız. <xref:System.Windows.DataTrigger> Kodda, <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemini de kullanabilirsiniz.

Aşağıdaki tabloda, her <xref:System.Windows.Media.Animation.Storyboard> BEGIN tekniğinin desteklendiği farklı konumlar gösterilmektedir: örnek başına, stil, denetim şablonu ve veri şablonu. "Örnek başına" bir animasyon veya görsel taslağı, bir stil, denetim şablonu veya veri şablonu yerine doğrudan nesnenin örneklerine uygulama tekniği anlamına gelir.

|Görsel taslak kullanılarak başlatıldı...|Örnek başına|Stil|Denetim şablonu|Veri şablonu|Örnek|
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir<xref:System.Windows.EventTrigger>|Evet|Evet|Evet|Evet|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir özellik<xref:System.Windows.Trigger>|Hayır|Evet|Evet|Evet|[Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md)|
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir<xref:System.Windows.DataTrigger>|Hayır|Evet|Evet|Evet|[Nasıl yapılır: Veri değiştiğinde animasyon tetikleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>yöntemidir|Evet|Hayır|Hayır|Hayır|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|

Aşağıdaki <xref:System.Windows.Media.Animation.Storyboard> örnek, <xref:System.Windows.Shapes.Rectangle> öğesini boyamak için bir öğesi <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush>vebir öğesine animasyon uygulamak için bir kullanır. <xref:System.Windows.Shapes.Rectangle>

[!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]

[!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]

Aşağıdaki bölümlerde <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> Ekli Özellikler daha ayrıntılı olarak açıklanır.

<a name="targetingelementsandfreezables"></a>

## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>Framework öğelerini, Framework Içerik öğelerini ve Freezable nesneleri hedefleme

Önceki bölümde, bir animasyonun hedefini bulması için hedefin adı ve animasyon uygulanacak özelliği bilmeleri gerekir. Animasyon uygulanacak özelliği belirtmek düz bir işlemdir: yalnızca animasyon eklenecek <xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType> özelliğin adıyla birlikte ayarlanır.  Animasyon üzerinde <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> özelliğini ayarlayarak, özelliğini hareketlendirmek istediğiniz nesnenin adını belirtirsiniz.

<xref:System.Windows.Setter.TargetName%2A> Özelliğin çalışması için, hedeflenen nesne bir ada sahip olmalıdır. Bir <xref:System.Windows.FrameworkElement> veyaiçine[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir adı atamak<xref:System.Windows.Freezable> , bir nesneye ad atamaktan farklıdır. <xref:System.Windows.FrameworkContentElement>

Framework öğeleri <xref:System.Windows.FrameworkElement> sınıfından kalıtımla alan sınıflardır. Çerçeve <xref:System.Windows.Window>öğelerinin örnekleri <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Shapes.Rectangle>, ,,veiçerir.<xref:System.Windows.Controls.Button> Temelde tüm pencereler, paneller ve denetimler öğelerdir. Framework içerik öğeleri <xref:System.Windows.FrameworkContentElement> sınıfından kalıtımla alan sınıflardır. Framework içerik öğelerinin örnekleri ve <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Documents.Paragraph>içerir. Bir türün çerçeve öğesi veya çerçeve içerik öğesi olup olmadığından emin değilseniz, bir ad özelliğine sahip olup olmadığını denetleyin. Bu, büyük olasılıkla bir çerçeve öğesi ya da çerçeve içerik öğesidir. Emin olmak için, tür sayfasının devralma hiyerarşisi bölümünü kontrol edin.

' De [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir çerçeve öğesi veya çerçeve içerik öğesi hedeflemesini etkinleştirmek için, <xref:System.Windows.FrameworkElement.Name%2A> özelliğini ayarlarsınız. Kodda, öğesini <xref:System.Windows.NameScope>oluşturduğunuz öğesiyle öğe adını kaydetmek için <xref:System.Windows.NameScope.RegisterName%2A> yöntemini de kullanmanız gerekir.

Yukarıdaki örnekten alınan aşağıdaki örnek, bir türü olan `MyRectangle` <xref:System.Windows.FrameworkElement>bir <xref:System.Windows.Shapes.Rectangle>adı atar.

[!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]

[!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]

Bir ada sahip olduktan sonra, bu öğenin bir özelliğine animasyon uygulayabilirsiniz.

[!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]

[!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]

<xref:System.Windows.Freezable>türler, <xref:System.Windows.Freezable> sınıfından kalıtımla alan sınıflardır. <xref:System.Windows.Freezable> , Ve<xref:System.Windows.Media.RotateTransform>ekleme örnekleri. <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.GradientStop>

' Deki <xref:System.Windows.Freezable> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir animasyon tarafından hedeflemesini etkinleştirmek için, [x:Name yönergesini](../../xaml-services/x-name-directive.md) bir ad atamak için kullanırsınız. Kodda, adını <xref:System.Windows.NameScope>oluşturduğunuz öğesi ile <xref:System.Windows.NameScope.RegisterName%2A> kaydetmek için yöntemini kullanırsınız.

Aşağıdaki örnek bir <xref:System.Windows.Freezable> nesnesine bir ad atar.

[!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]

[!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]

Nesne daha sonra bir animasyon tarafından hedeflenebilir.

[!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]

[!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]

<xref:System.Windows.Media.Animation.Storyboard>nesneler, <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> özelliği çözümlemek için ad kapsamlarını kullanır. WPF ad kapsamları hakkında daha fazla bilgi için bkz. [WPF xaml namescopes](../advanced/wpf-xaml-namescopes.md). <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Özellik atlanırsa, animasyon tanımlanan öğeyi veya stiller söz konusu olduğunda stilli öğeyi hedefler.

Bazen bir <xref:System.Windows.Freezable> nesneye bir ad atanamaz. Örneğin, bir <xref:System.Windows.Freezable> kaynak olarak bildirilirse veya bir stilde Özellik değeri ayarlamak için kullanılırsa, buna bir ad verilemez. Bir adı olmadığı için doğrudan hedeflenemez, ancak dolaylı olarak hedeflenebilir. Aşağıdaki bölümlerde dolaylı hedefleme kullanımı açıklanır.

<a name="pathsyntaxforchangeable"></a>

## <a name="indirect-targeting"></a>Dolaylı hedefleme

Bir <xref:System.Windows.Freezable> animasyon tarafından doğrudan hedeflenemez, örneğin, <xref:System.Windows.Freezable> kaynak olarak bildirildiği veya bir stilde Özellik değeri ayarlamak için kullanılan durumlar vardır. Bu durumlarda, doğrudan hedeflendiremeseniz bile, <xref:System.Windows.Freezable> nesneye animasyon uygulayabilirsiniz. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Özelliğini öğesinin adıyla <xref:System.Windows.Freezable>ayarlamak yerine, bu bileşene <xref:System.Windows.Freezable> "ait olduğu" öğesinin adını verirsiniz. Örneğin, dikdörtgen bir <xref:System.Windows.Media.SolidColorBrush> öğenin ' ı <xref:System.Windows.Shapes.Shape.Fill%2A> ayarlamak için kullanılan bir dikdörtgene aittir. Fırçaya animasyon uygulamak için, animasyonu <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> bir çerçeve öğesi veya çerçeve içeriği öğesinin özelliği ile başlayan özellikler zinciri ile, <xref:System.Windows.Freezable> animasyon için <xref:System.Windows.Freezable> özelliği ile ayarlamak için kullanılan bir özellik zinciri ile ayarlarsınız.

[!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]

[!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]

<xref:System.Windows.Freezable> Dondurulmuşsa, bir kopyanın yapıldığını ve bu kopyanın canlandırılabileceğini unutmayın. Bu durumda, özgün nesne gerçekten canlandırılmış <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> olmadığından özgün nesnenin özelliği `false`Return olmaya devam eder. Kopyalama hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).

Ayrıca, dolaylı Özellik hedefleme kullanılırken mevcut olmayan nesneleri hedeflemek mümkün olduğunu unutmayın. Örneğin, belirli bir düğmenin bir <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Media.SolidColorBrush> ile ayarlandığını varsayabilir ve söz konusu düğmenin arka planını ayarlamak için kullanılan olgu <xref:System.Windows.Media.LinearGradientBrush> ' ın rengine animasyon çalıştırmayı deneyebilirsiniz. Bu durumlarda, hiçbir özel durum oluşturulmaz; özelliğin<xref:System.Windows.Media.SolidColorBrush.Color%2A> değişikliklere tepki vermediğinden animasyon, görünür bir etkiye <xref:System.Windows.Media.LinearGradientBrush> sahip olamaz.

Aşağıdaki bölümlerde, dolaylı Özellik hedefleme sözdizimi daha ayrıntılı olarak açıklanır.

<a name="xamlsyntaxchangeableproperty"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>XAML 'de Freezable 'ın bir özelliğini dolaylı olarak hedefleme

İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Freezable 'ın bir özelliğini hedeflemek için aşağıdaki sözdizimini kullanın.

| |
|-|
|*ElementPropertyName* `.` *FreezablePropertyName*|

Where

- *ElementPropertyName* , öğesini ayarlamak için kullanılan <xref:System.Windows.FrameworkElement> özelliğidir <xref:System.Windows.Freezable> ve

- *FreezablePropertyName* , canlandırılacak öğesinin <xref:System.Windows.Freezable> özelliğidir.

Aşağıdaki kod, dikdörtgen bir öğenin kümesini ayarlamak <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Shapes.Shape.Fill%2A> için <xref:System.Windows.Media.SolidColorBrush> kullanılan öğesinin nasıl hareketlendirileceğini gösterir.

[!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]

Bazen bir koleksiyon veya dizide bulunan bir Freezable 'ı hedefleyebilirsiniz.

Bir koleksiyonda bulunan bir Freezable 'ı hedeflemek için aşağıdaki yol söz dizimini kullanın.

| |
|-|
|*ElementPropertyName* CollectionIndex *FreezablePropertyName* `.Children[` `].`|

Burada *CollectionIndex* nesnesinin veya koleksiyonundaki nesnenin dizinidir.

Örneğin, bir dikdörtgenin <xref:System.Windows.Media.TransformGroup> <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine bir kaynak uygulandığını ve içerdiği dönüşümlerden birine animasyon eklemek istediğinizi varsayalım.

[!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]

Aşağıdaki kod, önceki örnekte <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> gösterilen öğesinin özelliğinin nasıl hareketlendirileceğini gösterir.

[!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]

<a name="targetingpropertyofchangeableincode"></a>

### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>Kod içinde Freezable 'ın bir özelliğini dolaylı olarak hedefleme

Kod ' de bir <xref:System.Windows.PropertyPath> nesne oluşturun. Oluştururken <xref:System.Windows.PropertyPath>, <xref:System.Windows.PropertyPath.Path%2A> ve belirtirsiniz.<xref:System.Windows.PropertyPath.PathParameters%2A>

Oluşturmak <xref:System.Windows.PropertyPath.PathParameters%2A>için, bağımlılık özelliği tanımlayıcı alanlarının bir listesini <xref:System.Windows.DependencyProperty> içeren türünde bir dizi oluşturun. İlk tanımlayıcı alanı, ayarlamak için kullanılan <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.Freezable> özelliğine yöneliktir. Next Identifier alanı, <xref:System.Windows.Freezable> to hedefinin özelliğini temsil eder. Bunu <xref:System.Windows.Freezable> <xref:System.Windows.FrameworkElement> nesnesine bağlayan özelliklerin zinciri olarak düşünün.

Aşağıda, bir dikdörtgen öğesinin kümesini ayarlamak <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Shapes.Shape.Fill%2A> için kullanılan bir <xref:System.Windows.Media.SolidColorBrush> bağımlılık özelliği zinciri örneği verilmiştir.

[!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]

Ayrıca bir <xref:System.Windows.PropertyPath.Path%2A>belirtmeniz gerekir. , Nasıl yorumlayacağını belirten bir <xref:System.String>. <xref:System.Windows.PropertyPath.PathParameters%2A> <xref:System.Windows.PropertyPath.Path%2A> <xref:System.Windows.PropertyPath.Path%2A> Aşağıdaki sözdizimini kullanır.

| |
|-|
|`(`*OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex*`)`|

Where

- *OwnerPropertyArrayIndex* , ' ın ayarlamak için <xref:System.Windows.DependencyProperty> kullanılan <xref:System.Windows.FrameworkElement> nesnenin özelliğinin <xref:System.Windows.Freezable> tanımlayıcısını içeren dizinin dizinidir ve

- *FreezablePropertyArrayIndex* , hedeflenecek özelliğin tanımlayıcısını <xref:System.Windows.DependencyProperty> içeren dizinin dizinidir.

Aşağıdaki örnek, önceki örnekte <xref:System.Windows.PropertyPath.Path%2A> <xref:System.Windows.PropertyPath.PathParameters%2A> tanımlanan öğesine eşlik eden öğesini gösterir.

[!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]

Aşağıdaki örnek, bir dikdörtgen öğesini ayarlamak <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Shapes.Shape.Fill%2A> için <xref:System.Windows.Media.SolidColorBrush> kullanılan öğesinin animasyonunu yapmak için önceki örneklerde bulunan kodu birleştirir.

[!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]

Bazen bir koleksiyon veya dizide bulunan bir Freezable 'ı hedefleyebilirsiniz. Örneğin, bir dikdörtgenin <xref:System.Windows.Media.TransformGroup> <xref:System.Windows.UIElement.RenderTransform%2A> özelliğine bir kaynak uygulandığını ve içerdiği dönüşümlerden birine animasyon eklemek istediğinizi varsayalım.

[!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]

Bir koleksiyonda bulunan <xref:System.Windows.Freezable> bir hedefi hedeflemek için aşağıdaki yol söz dizimini kullanın.

| |
|-|
|`(`*OwnerPropertyArrayIndex* `)` `[` `].(` Collectionchildrenpropertyarrayındex CollectionIndex FreezablePropertyArrayIndex `).(``)`|

Burada *CollectionIndex* nesnesinin veya koleksiyonundaki nesnenin dizinidir.

<xref:System.Windows.Media.RotateTransform.Angle%2A> İçindeki <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.PropertyPath.PathParameters%2A>ikinci dönüşüm olan öğesinin özelliğini hedeflemek için aşağıdaki <xref:System.Windows.PropertyPath.Path%2A> ve kullanın. <xref:System.Windows.Media.TransformGroup>

[!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]

Aşağıdaki örnek, içindeki içindeki içindeki <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.TransformGroup>öğesinin animasyon için tüm kodu gösterir.

[!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]

### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>Başlangıç noktası olarak Freezable ile dolaylı olarak hedefleme

<xref:System.Windows.Freezable> Önceki bölümlerde, bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement> ile başlayıp bir <xref:System.Windows.Freezable> alt özelliğe bir özellik zinciri oluşturarak bir, dolaylı olarak nasıl hedeflenecek anlatılmıştır. Bir <xref:System.Windows.Freezable> başlangıç noktası olarak da kullanabilirsiniz ve kendi <xref:System.Windows.Freezable> alt özelliklerinden birini dolaylı olarak hedefleyin. Dolaylı hedefleme için başlangıç noktası olarak kullanıldığında <xref:System.Windows.Freezable> bir ek kısıtlama geçerlidir: Başlangıç <xref:System.Windows.Freezable> ve her <xref:System.Windows.Freezable> ikisi arasındaki ve dolaylı olarak hedeflenen alt özelliği dondurulmuş olmamalıdır.

<a name="controllable_storyboards"></a>

## <a name="interactively-controlling-a-storyboard-in-xaml"></a>XAML 'de görsel taslağı etkileşimli olarak denetleme

İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir görsel taslak başlatmak için bir <xref:System.Windows.Media.Animation.BeginStoryboard> tetikleyici eylemi kullanırsınız. <xref:System.Windows.Media.Animation.BeginStoryboard>animasyonları, canlandırdıkları nesnelere ve özelliklere dağıtır ve film şeridini başlatır. (Bu işlem hakkındaki ayrıntılar için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).) <xref:System.Windows.Media.Animation.BeginStoryboard> Kendi<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> özelliğini belirterek bir ad verirseniz, denetlenebilir bir görsel taslak yaparsınız. Daha sonra film şeridini başladıktan sonra etkileşimli bir şekilde denetleyebilirsiniz. Bir film şeridini denetlemek için olay tetikleyicilerle birlikte kullandığınız denetlenebilir görsel taslak eylemlerinin bir listesi aşağıda verilmiştir.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Film şeridini duraklatır.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış bir film şeridini sürdürür.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Görsel taslağın hızını değiştirir.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Bir film şeridini, varsa, kendi Fill döneminin sonuna ilerletir.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Film şeridini sonlandırır.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Görsel Taslağı kaldırır.

Aşağıdaki örnekte, denetlenebilir görsel taslak eylemleri görsel taslağı etkileşimli olarak denetlemek için kullanılır.

[!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]

<a name="controllable_storyboards_procedural"></a>

## <a name="interactively-controlling-a-storyboard-by-using-code"></a>Kod kullanarak görsel taslağı etkileşimli olarak denetleme

Önceki örneklerde tetikleyici eylemleri kullanılarak nasıl animasyon ekleneceği gösterilmekte. Kodda, <xref:System.Windows.Media.Animation.Storyboard> sınıfın etkileşimli yöntemlerini kullanarak bir görsel taslağı da denetleyebilirsiniz. Uygulamasının kodda etkileşimli hale getirilme için, <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> görsel taslak yönteminin uygun aşırı yüklemesini kullanmanız ve denetlenebilir hale getirmek için belirtmeniz `true` gerekir. <xref:System.Windows.Media.Animation.Storyboard> Daha fazla bilgi için sayfasınabakın.<xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>

Aşağıdaki listede, başlatıldıktan sonra bir <xref:System.Windows.Media.Animation.Storyboard> işlemi işlemek için kullanılabilecek yöntemler gösterilmektedir:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>

- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>

Bu yöntemleri kullanmanın avantajı, veya <xref:System.Windows.Trigger> <xref:System.Windows.TriggerAction> nesneleri oluşturmanız gerekmez; yalnızca işlemek istediğiniz denetlenebilir <xref:System.Windows.Media.Animation.Storyboard> öğesine bir başvuruya ihtiyacınız vardır.

> [!NOTE]
> Bir <xref:System.Windows.Media.Animation.Clock>üzerinde gerçekleştirilen tüm etkileşimli eylemler ve bu nedenle bir sonraki render <xref:System.Windows.Media.Animation.Storyboard> 'in kısa süre önce gerçekleştirilecek olan zamanlama altyapısının bir sonraki Tick 'i üzerinde gerçekleşecektir. Örneğin, bir animasyondaki başka bir <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> noktaya geçmek için yöntemini kullanırsanız, özellik değeri anında değişmez; bunun yerine, değer zamanlama altyapısının bir sonraki değerinde değişir.

Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Storyboard> sınıfının etkileşimli yöntemleri kullanılarak animasyonların nasıl uygulanacağı ve kontrol edileceği gösterilmektedir.

[!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
[!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]

<a name="usingstoryboardsinstyles"></a>

## <a name="animate-in-a-style"></a>Bir Stile Animasyon Ekleme

' De animasyonları <xref:System.Windows.Media.Animation.Storyboard> tanımlamak için nesneleri kullanabilirsiniz. <xref:System.Windows.Style> <xref:System.Windows.Media.Animation.Storyboard> Bir <xref:System.Windows.Media.Animation.Storyboard> içindeilehareketlendirmek,aşağıdakiüçözeldurumdışındabaşkabiryerdekullanılmasınabenzerdir:<xref:System.Windows.Style>

- Bir <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>belirtmeniz gerekmez <xref:System.Windows.Media.Animation.Storyboard> ; her zaman, uygulandığı öğeyi <xref:System.Windows.Style> hedefler. Nesneleri hedeflemek <xref:System.Windows.Freezable> için dolaylı hedefleme kullanmanız gerekir. Dolaylı hedefleme hakkında daha fazla bilgi için, bkz. [dolaylı hedefleme](#pathsyntaxforchangeable) bölümü.

- Veya içinbir<xref:System.Windows.EventTrigger.SourceName%2A> için belirtemezsiniz. <xref:System.Windows.Trigger> <xref:System.Windows.EventTrigger>

- Özellik değerlerini ayarlamak <xref:System.Windows.Media.Animation.Storyboard> veya animasyon uygulamak için dinamik kaynak başvurularını veya veri bağlama ifadelerini kullanamazsınız. Bunun nedeni, içindeki <xref:System.Windows.Style> her şeyin iş parçacığı açısından güvenli olması ve zamanlama sisteminin iş parçacığı açısından güvenli hale getirmek için nesneler olması <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> gerekir. Ya <xref:System.Windows.Media.Animation.Storyboard> da alt zaman çizelgeleri dinamik kaynak başvuruları veya veri bağlama ifadeleri içeriyorsa, A dondurulamıyor. Dondurma ve diğer <xref:System.Windows.Freezable> özellikler hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).

- ' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]De, veya animasyon olayları için <xref:System.Windows.Media.Animation.Storyboard> olay işleyicileri bildiremezsiniz.

Bir stil içinde bir film şeridinin nasıl tanımlanacağını gösteren bir örnek için, [bir stil örneğine animasyon ekleme](how-to-animate-in-a-style.md) bölümüne bakın.

<a name="defineAStoryboardInAControlTemplateSection"></a>

## <a name="animate-in-a-controltemplate"></a>ControlTemplate İçinde Animasyon Ekleme

' De animasyonları <xref:System.Windows.Media.Animation.Storyboard> tanımlamak için nesneleri kullanabilirsiniz. <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Media.Animation.Storyboard> Bir <xref:System.Windows.Media.Animation.Storyboard> içindeilehareketlendirmek,aşağıdakiikiözeldurumdışındabaşkabiryerdekullanılmasınabenzerdir:<xref:System.Windows.Controls.ControlTemplate>

- Yalnızca öğesinin alt nesnelerine başvurabilir. <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> Belirtilmemişse, animasyon uygulanan öğesini <xref:System.Windows.Controls.ControlTemplate> hedefler. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>

- Veya<xref:System.Windows.EventTrigger> içiniçin<xref:System.Windows.EventTrigger.SourceName%2A> , yalnızca öğesinin<xref:System.Windows.Controls.ControlTemplate>alt nesnelerine başvurabilir. <xref:System.Windows.Trigger>

- Özellik değerlerini ayarlamak <xref:System.Windows.Media.Animation.Storyboard> veya animasyon uygulamak için dinamik kaynak başvurularını veya veri bağlama ifadelerini kullanamazsınız. Bunun nedeni, içindeki <xref:System.Windows.Controls.ControlTemplate> her şeyin iş parçacığı açısından güvenli olması ve zamanlama sisteminin iş parçacığı açısından güvenli hale getirmek için nesneler olması <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> gerekir. Ya <xref:System.Windows.Media.Animation.Storyboard> da alt zaman çizelgeleri dinamik kaynak başvuruları veya veri bağlama ifadeleri içeriyorsa, A dondurulamıyor. Dondurma ve diğer <xref:System.Windows.Freezable> özellikler hakkında daha fazla bilgi için bkz. [Freezable nesnelerine genel bakış](../advanced/freezable-objects-overview.md).

- ' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]De, veya animasyon olayları için <xref:System.Windows.Media.Animation.Storyboard> olay işleyicileri bildiremezsiniz.

İçindeki <xref:System.Windows.Controls.ControlTemplate>bir film şeridini nasıl tanımlayacağınızı gösteren bir örnek için, bkz. [bir ControlTemplate 'de hareketlendirme](how-to-animate-in-a-controltemplate.md) örneği.

<a name="animateWhenAPropertyValueChanges"></a>

## <a name="animate-when-a-property-value-changes"></a>Özellik değeri değiştiğinde animasyon ekleme

Stiller ve denetim şablonlarında, bir özellik değiştiğinde film şeridi başlatmak için tetikleyici nesnelerini kullanabilirsiniz. Örnekler için bkz. bir özellik değeri değiştiğinde ve [bir ControlTemplate 'de animasyon](how-to-animate-in-a-controltemplate.md) [uyguladığınızda animasyon tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md) .

Özellik <xref:System.Windows.Trigger> nesneleri tarafından uygulanan animasyonlar, animasyonlar veya animasyonlar kullanılarak <xref:System.Windows.Media.Animation.Storyboard> başlatılan animasyonlardan <xref:System.Windows.EventTrigger> daha karmaşık bir biçimde davranır.  Diğer <xref:System.Windows.Trigger> nesneler tarafından tanımlanan animasyonlarla birlikte "iletiler", ancak <xref:System.Windows.EventTrigger> ve yöntemin tetiklediği animasyonlar ile oluşturma.

## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)
- [Freezable Nesnelerine Genel Bakış](../advanced/freezable-objects-overview.md)
