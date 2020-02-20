---
title: Animasyona Genel bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
ms.openlocfilehash: 00f01b63cdf9397fe25f28fff08767dfc3a83e69
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453123"
---
# <a name="animation-overview"></a>Animasyona Genel bakış

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] etkileyici kullanıcı arabirimleri ve çarpıcı belgeler oluşturmanıza olanak sağlayan güçlü bir grafik ve düzen özellikleri kümesi sağlar. Animasyon etkileyici bir kullanıcı arabirimini daha da etkileyici ve kullanılabilir hale getirebilirsiniz. Yalnızca bir arka plan rengi canlandırarak veya animasyonlu <xref:System.Windows.Media.Transform>uygulayarak, çarpıcı ekran geçişleri oluşturabilir veya yararlı görsel ipuçları sağlayabilirsiniz.

Bu genel bakış, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon ve zamanlama sistemine bir giriş sağlar. Film şeritleri kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nesnelerinin animasyonuna odaklanır.

<a name="introducinganimations"></a>

## <a name="introducing-animations"></a>Animasyonları tanıtma

Animasyon, her biri son verilerden biraz farklı olan bir dizi görüntüden hızlıca geçiş yaparak oluşturulan bir yanıdır. Bey, görüntü grubunu tek bir değişen sahne olarak beyin. Bu yanışta, her saniye çok sayıda fotoğraf veya kare kaydeden kameralar kullanılarak oluşturulur. Çerçeveler bir projektör tarafından geri yürütüldüğünde, hedef kitle bir hareketli resim görür.

Bir bilgisayardaki animasyon benzerdir. Örneğin, görünümün dışına çıkan bir dikdörtgen çizimi oluşturan bir program aşağıdaki gibi çalışabilir.

- Program bir zamanlayıcı oluşturur.

- Program, ne kadar süre geçtiğini görmek için zamanlayıcıyı ayarlanan aralıklarda denetler.

- Program zamanlayıcıyı her denetlediğinde, dikdörtgenin ne kadar süre geçtiğini temel alarak geçerli opaklık değerini hesaplar.

- Daha sonra program, dikdörtgeni yeni değerle güncelleştirir ve yeniden çizer.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]önce, Microsoft Windows geliştiricilerinin kendi zamanlama sistemlerini oluşturması ve yönetmesi veya özel özel kitaplıklar kullanması gerekiyordu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], yönetilen kod ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] aracılığıyla sunulan ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çerçevesiyle daha ayrıntılı bir şekilde tümleştirilmiş etkin bir zamanlama sistemi içerir. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon denetimleri ve diğer grafik nesnelerinin animasyonunu kolaylaştırır.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bir zamanlama sistemini yönetmek ve ekranı verimli bir şekilde yeniden çizmek için tüm arka planda çalışmayı işler. Bu etkileri sağlamak yerine, oluşturmak istediğiniz etkilere odaklanmanız için zamanlama sınıfları sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ayrıca, Özel animasyonlar oluşturmak için sınıflarınızın devraldığı animasyon temel sınıflarını açığa çıkararak kendi animasyonlarınızı oluşturmayı kolaylaştırır. Bu özel animasyonlar, standart animasyon sınıflarının birçok performans avantajı elde edebilir.

<a name="thewpftimingsystem"></a>

## <a name="wpf-property-animation-system"></a>WPF özelliği animasyon sistemi

Zamanlama sistemiyle ilgili birkaç önemli kavramı anladıysanız [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonların kullanımı daha kolay olabilir. En önemlileri, tek tek özelliklerine animasyon uygulayarak nesnelerin animasyonunu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Örneğin, bir çerçeve öğesini büyütmek için, <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerine animasyon uygularsınız. Bir nesneyi görünümden soluklaştırmak için, <xref:System.Windows.UIElement.Opacity%2A> özelliğine animasyon uygularsınız.

Bir özelliğin animasyon özelliklerine sahip olması için, aşağıdaki üç gereksinimi karşılaması gerekir:

- Bağımlılık özelliği olmalıdır.

- <xref:System.Windows.DependencyObject> devralan bir sınıfa ait olmalıdır ve <xref:System.Windows.Media.Animation.IAnimatable> arabirimini uygular.

- Kullanılabilir uyumlu bir animasyon türü olmalıdır. ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir tane sağlamıyorsa, kendi kendinizinkini oluşturabilirsiniz. Bkz. [Özel animasyonlara genel bakış](custom-animations-overview.md).)

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Media.Animation.IAnimatable> özellikleri olan çok sayıda nesne içeriyor. <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.TabControl>gibi denetimler ve ayrıca <xref:System.Windows.Controls.Panel> ve <xref:System.Windows.Shapes.Shape> nesneler <xref:System.Windows.DependencyObject>devralınır. Özelliklerinin çoğu bağımlılık özellikleridir.

Animasyonları, stiller ve denetim şablonlarına dahil neredeyse her yerde kullanabilirsiniz. Animasyonların görsel olması gerekmez; Bu bölümde açıklanan ölçütlere uyduklarında, Kullanıcı arabiriminin parçası olmayan nesnelere animasyon uygulayabilirsiniz.

<a name="storyboardwalkthrough"></a>

## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Örnek: bir öğeyi Soluklaştırın ve görünümün dışında yapma

Bu örnek, bir bağımlılık özelliğinin değerine animasyon eklemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonun nasıl kullanılacağını gösterir. Bir <xref:System.Windows.Shapes.Rectangle><xref:System.Windows.UIElement.Opacity%2A> özelliğine animasyon uygulamak için <xref:System.Double> değerleri üreten bir animasyon türü olan <xref:System.Windows.Media.Animation.DoubleAnimation>kullanır. Sonuç olarak, <xref:System.Windows.Shapes.Rectangle> görünümden çıkar ve görünümden çıkar.

Örneğin ilk bölümü bir <xref:System.Windows.Shapes.Rectangle> öğesi oluşturur. Aşağıdaki adımlar bir animasyon oluşturmayı ve dikdörtgenin <xref:System.Windows.UIElement.Opacity%2A> özelliğine nasıl uygulanacağını gösterir.

Aşağıda, XAML 'de <xref:System.Windows.Controls.StackPanel> bir <xref:System.Windows.Shapes.Rectangle> öğesinin nasıl oluşturulacağı gösterilmektedir.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]

Aşağıda, koddaki bir <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Shapes.Rectangle> öğesinin nasıl oluşturulacağı gösterilmektedir.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]

<a name="opacity_animation_step1"></a>

### <a name="part-1-create-a-doubleanimation"></a>1\. kısım: DoubleAnimation oluşturma

Bir öğeyi soluklaştırın ve görünümün dışında yapmanın bir yolu <xref:System.Windows.UIElement.Opacity%2A> özelliğine animasyon kullanmaktır. <xref:System.Windows.UIElement.Opacity%2A> özelliği <xref:System.Double>türünde olduğundan, çift değerler üreten bir animasyonunuz olmalıdır. <xref:System.Windows.Media.Animation.DoubleAnimation> bir animasyondur. <xref:System.Windows.Media.Animation.DoubleAnimation> iki Double değeri arasında bir geçiş oluşturur. Başlangıç değerini belirtmek için, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini ayarlarsınız. Bitiş değerini belirtmek için, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini ayarlarsınız.

1. `1.0` opaklık değeri nesneyi tamamen opak hale getirir ve `0.0` opaklık değeri tamamen görünmez hale gelir. `1.0` 'den `0.0` animasyon geçişi yapmak için <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini `1.0` ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini `0.0`olarak ayarlarsınız. Aşağıda, XAML 'de <xref:System.Windows.Media.Animation.DoubleAnimation> oluşturma gösterilmektedir.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]

    Aşağıda, kodda <xref:System.Windows.Media.Animation.DoubleAnimation> oluşturma gösterilmektedir.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]

2. Daha sonra, bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A>belirtmeniz gerekir. Bir animasyonun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> başlangıç değerinden hedef değerine ne kadar süreceğine ilişkin süreyi belirtir. Aşağıda, XAML 'de <xref:System.Windows.Media.Animation.Timeline.Duration%2A> beş saniyeye ayarlama gösterilmiştir.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]

    Aşağıda, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> kodda beş saniyeye nasıl ayarlanacağı gösterilmiştir.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]

3. Önceki kod, `1.0` ile `0.0`arasında geçiş yapan bir animasyon gösterdi. Bu, hedef öğenin tamamen opak ve tamamen görünmez olarak zayıflamasına neden olur. Öğe geçtikten sonra öğeyi görünüme geri dönerek getirmek için animasyonun <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliğini `true`olarak ayarlayın. Animasyonun süresiz olarak tekrarlanması için <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>olarak ayarlayın. Aşağıda, XAML 'de <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ve <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliklerinin nasıl ayarlanacağı gösterilmektedir.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]

    Aşağıda, koddaki <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ve <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliklerinin nasıl ayarlanacağı gösterilmektedir.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]

<a name="opacity_animation_step2"></a>

### <a name="part-2-create-a-storyboard"></a>2\. Bölüm: görsel taslak oluşturma

Bir nesneye animasyon uygulamak için bir <xref:System.Windows.Media.Animation.Storyboard> oluşturup <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> iliştirilmiş özellikleri kullanarak canlandırılacak nesne ve özelliği belirtin.

1. <xref:System.Windows.Media.Animation.Storyboard> oluşturun ve animasyonu alt öğesi olarak ekleyin. Aşağıda, <xref:System.Windows.Media.Animation.Storyboard> XAML 'de nasıl oluşturacağınız gösterilmektedir.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]

    Kodda <xref:System.Windows.Media.Animation.Storyboard> oluşturmak için sınıf düzeyinde bir <xref:System.Windows.Media.Animation.Storyboard> değişkeni bildirin.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]

    Sonra <xref:System.Windows.Media.Animation.Storyboard> başlatın ve animasyonu alt öğesi olarak ekleyin.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]

2. <xref:System.Windows.Media.Animation.Storyboard> animasyonun nereye uygulanacağını bilmelidir. Canlandırılacak nesneyi belirtmek için <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType> ekli özelliğini kullanın. Aşağıda, <xref:System.Windows.Media.Animation.DoubleAnimation> hedef adının XAML içinde `MyRectangle` olarak nasıl ayarlanacağı gösterilmiştir.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]

    Aşağıda, <xref:System.Windows.Media.Animation.DoubleAnimation> hedef adının koddaki `MyRectangle` olarak nasıl ayarlanacağı gösterilmiştir.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]

3. Canlandırılacak özelliği belirtmek için <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> ekli özelliğini kullanın. Aşağıda, animasyonun XAML içindeki <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.UIElement.Opacity%2A> özelliğini hedeflemek için nasıl yapılandırıldığı gösterilmiştir.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]

    Aşağıda, animasyonun, koddaki <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.UIElement.Opacity%2A> özelliğini hedeflemek için nasıl yapılandırıldığı gösterilmiştir.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]

<xref:System.Windows.Media.Animation.Storyboard.TargetProperty> sözdizimi hakkında daha fazla bilgi edinmek ve ek örnekler için bkz. [Görsel Taslaklara Genel Bakış](storyboards-overview.md).

<a name="opacity_animation_step3"></a>

### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Bölüm 3 (XAML): görsel taslağı bir tetikleyici ile Ilişkilendirme

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Media.Animation.Storyboard> uygulama ve başlatmanın en kolay yolu bir olay tetikleyicisi kullanmaktır. Bu bölümde, <xref:System.Windows.Media.Animation.Storyboard> XAML 'deki bir tetikleyiciyle nasıl ilişkilendireceğiniz gösterilmektedir.

1. <xref:System.Windows.Media.Animation.BeginStoryboard> nesnesi oluşturun ve görsel taslağınızı onunla ilişkilendirin. <xref:System.Windows.Media.Animation.BeginStoryboard>, bir <xref:System.Windows.Media.Animation.Storyboard>uygulayan ve Başlatan bir <xref:System.Windows.TriggerAction> türüdür.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]

2. Bir <xref:System.Windows.EventTrigger> oluşturun ve <xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.EventTrigger.Actions%2A> koleksiyonuna ekleyin. <xref:System.Windows.EventTrigger> <xref:System.Windows.EventTrigger.RoutedEvent%2A> özelliğini <xref:System.Windows.Media.Animation.Storyboard>başlatmak istediğiniz yönlendirilmiş olay olarak ayarlayın. (Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](../advanced/routed-events-overview.md).)

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]

3. <xref:System.Windows.EventTrigger> dikdörtgenin <xref:System.Windows.FrameworkElement.Triggers%2A> koleksiyonuna ekleyin.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]

<a name="opacity_animation_step3code"></a>

### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Bölüm 3 (kod): görsel taslağı bir olay Işleyicisiyle Ilişkilendirme

Kodda <xref:System.Windows.Media.Animation.Storyboard> uygulama ve başlatmanın en kolay yolu bir olay işleyicisi kullanmaktır. Bu bölümde, <xref:System.Windows.Media.Animation.Storyboard> koddaki olay işleyicisiyle nasıl ilişkilendireceğiniz gösterilmektedir.

1. Dikdörtgenin <xref:System.Windows.FrameworkElement.Loaded> olayına kaydolun.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]

2. Olay işleyicisini bildirin. Olay işleyicisinde, film şeridini uygulamak için <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemini kullanın.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]

### <a name="complete-example"></a>Tam Örnek

Aşağıda, XAML 'de görünümü aşağı ve dışına çıkan bir dikdörtgenin nasıl oluşturulacağı gösterilmektedir.

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]

Aşağıda, kodda görünüm ve görünümün dışında bir dikdörtgen oluşturma gösterilmektedir.

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]

<a name="animationtypes"></a>

## <a name="animation-types"></a>Animasyon türleri

Animasyonlar özellik değerleri oluşturduğundan farklı özellik türleri için farklı animasyon türleri mevcuttur. Bir öğenin <xref:System.Windows.FrameworkElement.Width%2A> özelliği gibi <xref:System.Double>alan bir özelliğe animasyon uygulamak için <xref:System.Double> değerler üreten bir animasyon kullanın. <xref:System.Windows.Point>alan bir özelliğe animasyon uygulamak için <xref:System.Windows.Point> değerleri üreten bir animasyon kullanın ve bu şekilde devam edin. Farklı özellik türlerinin sayısı nedeniyle <xref:System.Windows.Media.Animation> ad alanında birkaç animasyon sınıfı vardır. Neyse ki, aralarında ayrım yapmayı kolaylaştıran bir katı adlandırma kuralına uyar:

- \<*türü*> animasyonu

  "From/to/by" veya "temel" animasyon olarak bilinen, bu, başlangıç ve hedef değerleri arasında veya başlangıç değerine bir de bir konum değeri eklenerek canlandırılır.

  - Başlangıç değerini belirtmek için animasyonun from özelliğini ayarlayın.

  - Bir bitiş değeri belirtmek için animasyonun To özelliğini ayarlayın.

  - Bir fark değeri belirtmek için animasyonun by özelliğini ayarlayın.

  Bu genel bakışta örnekler bu animasyonları kullanır, çünkü bu en basit kullanım kolayıdır. From/To/By animasyonları, From/To/By animasyonlara genel bakış bölümünde ayrıntılı olarak açıklanmıştır.

- \<> AnimationUsingKeyFrames *türü*

  Anahtar çerçeve animasyonları, herhangi bir sayıda hedef değer belirtebileceğiniz ve hatta enterpolasyon yöntemini denetleyebildiğinden, From/To/By animasyonlarından daha güçlüdür. Bazı türler yalnızca anahtar çerçeve animasyonlarına animasyon eklenebilir. Anahtar çerçeve animasyonları, [anahtar çerçeve animasyonlarında genel bakış](key-frame-animations-overview.md)bölümünde ayrıntılı olarak açıklanmıştır.

- \<*türü*> AnimationUsingPath

  Yol animasyonları, animasyon değerlerini oluşturmak için geometrik yol kullanmanıza olanak sağlar.

- \<*türü*> AnimationBase

  Özet sınıf, uygulamayı uyguladığınızda \<*tür*> değerini hareketlendirir. Bu sınıf, \<*türü*> animasyon ve \<*türü*> AnimationUsingKeyFrames sınıfları için temel sınıf olarak hizmet verir. Yalnızca kendi özel animasyonlarınızı oluşturmak istiyorsanız bu sınıflarla doğrudan uğraşmanız gerekir. Aksi takdirde, bir \<*türü*> animasyon veya anahtar kare\<> animasyon *yazın*.

Çoğu durumda, <xref:System.Windows.Media.Animation.DoubleAnimation> ve <xref:System.Windows.Media.Animation.ColorAnimation>gibi \<*türü*> animasyon sınıflarını kullanmak isteyeceksiniz.

Aşağıdaki tabloda birkaç ortak animasyon türü ve bunların kullanıldıkları bazı özellikler gösterilmektedir.

|Özellik türü|Karşılık gelen temel (From/To/By) animasyonu|Karşılık gelen anahtar çerçeve animasyonu|Karşılık gelen yol animasyonu|Kullanım örneği|
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Yok.|Bir <xref:System.Windows.Media.SolidColorBrush> veya <xref:System.Windows.Media.GradientStop><xref:System.Windows.Media.SolidColorBrush.Color%2A> canlandırın.|
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Bir <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.FrameworkElement.Width%2A> veya <xref:System.Windows.Controls.Button><xref:System.Windows.FrameworkElement.Height%2A> canlandırın.|
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Bir <xref:System.Windows.Media.EllipseGeometry><xref:System.Windows.Media.EllipseGeometry.Center%2A> konumuna animasyon ekleyin.|
|<xref:System.String>|Yok.|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Yok.|Bir <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBlock.Text%2A> veya <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ContentControl.Content%2A> canlandırın.|

<a name="animationsaretimelines"></a>

### <a name="animations-are-timelines"></a>Animasyonlar zaman çizelgelerinizi

Tüm animasyon türleri <xref:System.Windows.Media.Animation.Timeline> sınıfından devralınır; Bu nedenle, tüm animasyonlar zaman çizelgelerinin özelleşmiş türleridir. Bir zaman kesimini tanımlar <xref:System.Windows.Media.Animation.Timeline>. Bir zaman çizelgesinin *zamanlama davranışlarını* belirtebilirsiniz: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, kaç kez tekrarlandığını ve hatta ne kadar hızlı zaman ilerledikçe.

Animasyon bir <xref:System.Windows.Media.Animation.Timeline>olduğundan, bir zaman kesimini de temsil eder. Ayrıca, bir animasyon, belirtilen zaman segmentinden (veya <xref:System.Windows.Media.Animation.Timeline.Duration%2A>) ilerledikçe çıkış değerlerini de hesaplar. Animasyon ilerledikçe veya "oynatılır", ilişkili olduğu özelliği günceller.

Sık kullanılan üç zamanlama özelliği <xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>ve <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>.

#### <a name="the-duration-property"></a>Duration özelliği

Daha önce belirtildiği gibi, bir zaman çizelgesi bir zaman kesimini temsil eder. Bu segmentin uzunluğu, genellikle bir <xref:System.Windows.Duration.TimeSpan%2A> değeri kullanılarak belirtilen zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.Duration%2A> belirlenir. Bir zaman çizelgesi süresinin sonuna ulaştığında bir yinelemeyi tamamlamıştır.

Bir animasyon, geçerli değerini öğrenmek için <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliğini kullanır. Bir animasyon için <xref:System.Windows.Media.Animation.Timeline.Duration%2A> değeri belirtmezseniz, varsayılan değer olan 1 saniye kullanır.

Aşağıdaki sözdizimi, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği için [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] öznitelik sözdiziminin basitleştirilmiş bir sürümünü gösterir.

*saat* `:` *dakika* `:` *saniye*

Aşağıdaki tabloda bazı <xref:System.Windows.Duration> ayarları ve sonuçta elde edilen değerler gösterilmektedir.

|Ayar|Sonuç değeri|
|-------------|---------------------|
|0:0:5.5|5,5 saniye.|
|0:30:5.5|30 dakika ve 5,5 saniye.|
|1:30:5.5|1 saat, 30 dakika ve 5,5 saniye.|

Kodda <xref:System.Windows.Duration> belirtmenin bir yolu, bir <xref:System.TimeSpan>oluşturmak için <xref:System.TimeSpan.FromSeconds%2A> metodunu kullanmak ve ardından bu <xref:System.TimeSpan>kullanarak yeni bir <xref:System.Windows.Duration> yapısı bildirmektir.

<xref:System.Windows.Duration> değerleri ve tüm [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sözdizimi hakkında daha fazla bilgi için <xref:System.Windows.Duration> yapısına bakın.

#### <a name="autoreverse"></a>AutoReverse

<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği, bir zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.Duration%2A>sonuna ulaştıktan sonra geri yürütülüp yürütülmeyeceğini belirtir. Bu animasyon özelliğini `true`olarak ayarlarsanız, bir animasyon onun <xref:System.Windows.Media.Animation.Timeline.Duration%2A>sonuna ulaştıktan sonra ters döner ve onun bitiş değerinden başlangıç değerine doğru oynamaya başlar. Varsayılan olarak, bu özellik `false`.

#### <a name="repeatbehavior"></a>RepeatBehavior

<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği, bir zaman çizelgesinin kaç kez oynatılacağını belirtir. Varsayılan olarak, zaman çizelgeleri `1.0`yineleme sayısına sahiptir, bu, bir kez oynadıkları ve hiç yinelenmediği anlamına gelir.

Bu özellikler ve diğerleri hakkında daha fazla bilgi için bkz. [Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md).

<a name="applyanimationstoproperty"></a>

## <a name="applying-an-animation-to-a-property"></a>Bir özelliğe animasyon uygulama

Önceki bölümlerde farklı animasyon türleri ve bunların zamanlama özellikleri açıklanır. Bu bölüm, animasyonunu hareketlendirmek istediğiniz özelliğe nasıl uygulayacağınızı gösterir. <xref:System.Windows.Media.Animation.Storyboard> nesneler, özelliklere animasyon uygulamak için bir yol sağlar. <xref:System.Windows.Media.Animation.Storyboard>, içerdiği animasyonlar için hedefleme bilgilerini sağlayan bir *kapsayıcı zaman çizelgesi* ' dir.

### <a name="targeting-objects-and-properties"></a>Nesneleri ve özellikleri hedefleme

<xref:System.Windows.Media.Animation.Storyboard> sınıfı, <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> ekli özellikleri sağlar. Bu özellikleri bir animasyon üzerinde ayarlayarak, animasyona nelerin hareketlendirileceğini söylemiş olursunuz. Ancak, bir animasyon bir nesneyi hedeflebilmeniz için, nesneye genellikle bir ad verilmelidir.

Bir <xref:System.Windows.FrameworkElement> ad atamak <xref:System.Windows.Freezable> nesnesine bir ad atamaya göre farklılık gösterir. Çoğu denetim ve panel çerçeve öğeleridir; Ancak, fırçalar, dönüşümler ve geometriler gibi çoğu tamamen grafik nesnesi Freezable nesnelerdir. Bir türün <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.Freezable>olup olmadığından emin değilseniz, başvuru belgelerinin **devralma hiyerarşisi** bölümüne bakın.

- Bir animasyon hedefi <xref:System.Windows.FrameworkElement> yapmak için, <xref:System.Windows.FrameworkElement.Name%2A> özelliğini ayarlayarak buna bir ad verirsiniz. Kod içinde, öğe adını ait olduğu sayfayla birlikte kaydetmek için <xref:System.Windows.FrameworkElement.RegisterName%2A> yöntemini de kullanmanız gerekir.

- <xref:System.Windows.Freezable> nesnesini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]animasyon hedefi yapmak için, [X:Name yönergesini](../../../desktop-wpf/xaml-services/xname-directive.md) bir ad atamak için kullanırsınız. Kodda, nesne ait olduğu sayfaya kaydetmek için <xref:System.Windows.FrameworkElement.RegisterName%2A> yöntemini kullanırsınız.

Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ve koddaki bir öğe adlandırmayla ilgili bir örnek sağlar. Adlandırma ve hedefleme hakkında daha ayrıntılı bilgi için bkz. görsel taslaklara [genel bakış](storyboards-overview.md).

### <a name="applying-and-starting-storyboards"></a>Film şeritleri uygulanıyor ve başlatılıyor

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir film şeridini başlatmak için, bunu bir <xref:System.Windows.EventTrigger>ilişkilendirirsiniz. <xref:System.Windows.EventTrigger>, belirtilen bir olay gerçekleştiğinde gerçekleştirilecek eylemleri açıklayan bir nesnedir. Bu eylemlerden biri, görsel taslağınızı başlatmak için kullandığınız <xref:System.Windows.Media.Animation.BeginStoryboard> eylem olabilir. Olay Tetikleyicileri, uygulamanızın belirli bir olaya nasıl yanıt vereceğini belirtmenizi sağladığından olay işleyicileri kavramıyla benzerdir. Olay işleyicilerinin aksine, olay tetikleyicileri [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]içinde tam olarak açıklanabilir. başka kod gerekmez.

Kodda bir <xref:System.Windows.Media.Animation.Storyboard> başlatmak için bir <xref:System.Windows.EventTrigger> kullanabilir veya <xref:System.Windows.Media.Animation.Storyboard> sınıfının <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemini kullanabilirsiniz.

<a name="controllingstoryboards"></a>

## <a name="interactively-control-a-storyboard"></a>Görsel Taslağı etkileşimli olarak denetleme

Önceki örnekte, bir olay gerçekleştiğinde <xref:System.Windows.Media.Animation.Storyboard> nasıl başlatılacağı gösterildi. <xref:System.Windows.Media.Animation.Storyboard> başladıktan sonra etkileşimli bir şekilde denetleyebilirsiniz: Bu işlemi duraklatabilir, sürdürebilir, durdurabilir, Fill dönemine ilerletebilirsiniz, arayabilir ve <xref:System.Windows.Media.Animation.Storyboard>kaldırabilirsiniz. Daha fazla bilgi ve bir <xref:System.Windows.Media.Animation.Storyboard>etkileşimli olarak nasıl kontrol edilecek bir örnek için bkz. görsel taslaklara [genel bakış](storyboards-overview.md).

<a name="fillbehaviorsection"></a>

## <a name="what-happens-after-an-animation-ends"></a>Bir animasyon bittikten sonra ne olur?

<xref:System.Windows.Media.Animation.FillBehavior> özelliği, zaman çizelgesinin sona erdiğinde nasıl davranacağını belirtir. Varsayılan olarak, bir zaman çizelgesi sona erdiğinde <xref:System.Windows.Media.Animation.ClockState.Filling> başlar. <xref:System.Windows.Media.Animation.ClockState.Filling> bir animasyon, son çıkış değerini barındırır.

Önceki örnekteki <xref:System.Windows.Media.Animation.DoubleAnimation> bitmediği için <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>olarak ayarlanmıştır. Aşağıdaki örnek, benzer bir animasyon kullanarak bir dikdörtgeni hareketlendirir. Önceki örneğin aksine, bu animasyonun <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ve <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özellikleri varsayılan değerlerinde bırakılır. Bu nedenle, animasyon beş saniye boyunca 1 ile 0 arasında ilerlerler ve sonra duraklar.

[!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]

[!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
[!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]

<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>, <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>varsayılan değerinden değişmediğinden, animasyon son değerini, 0, sona erdiğinde tutar. Bu nedenle, dikdörtgenin <xref:System.Windows.UIElement.Opacity%2A>, animasyon bittikten sonra 0 ' da kalır. Dikdörtgenin <xref:System.Windows.UIElement.Opacity%2A> başka bir değere ayarlarsanız, animasyon hala <xref:System.Windows.UIElement.Opacity%2A> özelliğini etkilediği için kodunuzun hiçbir etkisi olmaz.

Kodda animasyonlu bir özelliğin denetimini yeniden kazanmak için bir yol <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanmaktır ve <xref:System.Windows.Media.Animation.AnimationTimeline> parametresi için null değerini belirtmelidir. Daha fazla bilgi ve bir örnek için bkz. [Görsel Taslakla animasyon uygulandıktan sonra özelliği ayarlama](how-to-set-a-property-after-animating-it-with-a-storyboard.md).

Bir <xref:System.Windows.Media.Animation.ClockState.Active> veya <xref:System.Windows.Media.Animation.ClockState.Filling> animasyonuna sahip bir özellik değeri ayarlamanın hiçbir etkisi olmamasına rağmen, özellik değeri değişir. Daha fazla bilgi için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).

<a name="databindingAndAnimatingAnimationsSection"></a>

## <a name="data-binding-and-animating-animations"></a>Veri bağlama ve animasyonları hareketlendirme

Animasyon özelliklerinin çoğu veri veya animasyonlu olabilir; Örneğin, bir <xref:System.Windows.Media.Animation.DoubleAnimation><xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliğine animasyon uygulayabilirsiniz. Ancak, zamanlama sisteminin çalışma biçimi nedeniyle, veri bağlantılı veya animasyonlu animasyonlar diğer veri bağlantılı veya animasyonlu nesneler gibi davranmaz. Davranışlarını anlamak için bir özelliği bir animasyon uygulamak için ne anlama geldiğini anlamanıza yardımcı olur.

Bir dikdörtgenin <xref:System.Windows.UIElement.Opacity%2A> animasyonunu gösteren önceki bölümde yer alan örneğe bakın. Önceki örnekteki dikdörtgen yüklendiğinde, olay tetikleyicisi <xref:System.Windows.Media.Animation.Storyboard>uygular. Zamanlama sistemi, <xref:System.Windows.Media.Animation.Storyboard> ve animasyonunun bir kopyasını oluşturur. Bu kopyalar dondurulur (salt okunurdur) ve <xref:System.Windows.Media.Animation.Clock> nesneler bunlardan oluşturulur. Bu saatler, hedeflenen özellikleri hareketlendirmek için gerçek çalışmalara sahiptir.

Zamanlama sistemi <xref:System.Windows.Media.Animation.DoubleAnimation> için bir saat oluşturur ve <xref:System.Windows.Media.Animation.DoubleAnimation><xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> tarafından belirtilen nesne ve özelliğe uygular. Bu durumda, zamanlama sistemi, "MyRectangle" adlı nesnenin <xref:System.Windows.UIElement.Opacity%2A> özelliğine saati uygular.

<xref:System.Windows.Media.Animation.Storyboard>için saat de oluşturulsa da, saat herhangi bir özelliğe uygulanmaz. Amacı, <xref:System.Windows.Media.Animation.DoubleAnimation>için oluşturulan saatin alt saatini denetsağlamaktır.

Bir animasyonun veri bağlamayı veya animasyon değişikliklerini yansıtması için, saatinin yeniden oluşturulması gerekir. Saatler sizin için otomatik olarak yeniden oluşturulmaz. Bir animasyonun değişiklikleri yansıtması için, film şeridini bir <xref:System.Windows.Media.Animation.BeginStoryboard> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi kullanarak yeniden uygulayın. Bu yöntemlerden birini kullandığınızda animasyon yeniden başlatılır. Kod içinde, görsel taslağı önceki konumuna geri kaydırmak için <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemini kullanabilirsiniz.

Veri bağlantılı animasyon örneği için bkz. [Anahtar eğri animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations). Animasyon ve zamanlama sisteminin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).

<a name="otherWaysToAnimateSection"></a>

## <a name="other-ways-to-animate"></a>Animasyon almanın diğer yolları

Bu genel bakışdaki örneklerde film şeritleri kullanılarak nasıl animasyon ekleneceği gösterilmektedir. Kodu kullandığınızda, birkaç farklı yolla animasyon uygulayabilirsiniz. Daha fazla bilgi için bkz. [animasyon tekniklerine genel bakış](property-animation-techniques-overview.md).

<a name="animation_samples"></a>

## <a name="animation-samples"></a>Animasyon örnekleri

Aşağıdaki örnekler uygulamalarınıza animasyon eklemeye başlamanıza yardımcı olabilir.

- [From, to ve By animasyon hedefi değerleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)

  Farklı From/To/By ayarlarını gösterir.

- [Animasyon Zamanlama davranışı örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)

  Animasyonun zamanlama davranışını denetleyebilmeniz için farklı yollar gösterir. Bu örnek ayrıca bir animasyonun hedef değerini veri bağlama şeklini gösterir.

<a name="related_topics"></a>

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)|Zamanlama sisteminin <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Clock> sınıflarını nasıl kullandığını açıklar. Bu, animasyonlar oluşturmanıza olanak tanır.|
|[Animasyon İpuçları ve Püf Noktaları](animation-tips-and-tricks.md)|Performans gibi animasyonlarla ilgili sorunları çözmek için faydalı ipuçları listeler.|
|[Özel Animasyonlara Genel Bakış](custom-animations-overview.md)|Animasyon sisteminin anahtar çerçeveler, animasyon sınıfları veya kare başına geri çağırmalar ile nasıl genişletileceğini açıklar.|
|[Gelen/İçin/Göre Animasyonlarına Genel Bakış](from-to-by-animations-overview.md)|İki değer arasında geçiş yapan bir animasyonun nasıl oluşturulacağını açıklar.|
|[Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)|Enterpolasyon yöntemini denetleme özelliği de dahil olmak üzere birden çok hedef değeri olan bir animasyonun nasıl oluşturulacağını açıklar.|
|[Hızlandırma İşlevleri](easing-functions.md)|Sıçramalar gibi gerçekçi davranışları almak için animasyonlarınızın matematiksel formüllerin nasıl uygulanacağını açıklar.|
|[Yol Animasyonlarına Genel Bakış](path-animations-overview.md)|Bir nesnenin karmaşık bir yol üzerinde nasıl taşınacağını veya döndürüleceğini açıklar.|
|[Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)|Görsel taslak, yerel animasyon, saat ve çerçeve başına animasyonları kullanarak özellik animasyonlarını açıklar.|
|[Görsel Taslaklara Genel Bakış](storyboards-overview.md)|Karmaşık animasyonlar oluşturmak için birden çok zaman çizelgesi ile film şeritlerinin nasıl kullanılacağını açıklar.|
|[Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md)|Animasyonlarda kullanılan <xref:System.Windows.Media.Animation.Timeline> türlerini ve özelliklerini açıklar.|
|[Zamanlama Olaylarına Genel Bakış](timing-events-overview.md)|<xref:System.Windows.Media.Animation.Timeline> için kullanılabilir olayları ve zaman çizelgesinde, başlatma, duraklatma, devam etmeyi, atla veya Durdur gibi bir noktada kod yürütmeye yönelik <xref:System.Windows.Media.Animation.Clock> nesneleri açıklar.|
|[Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)|Uygulamanızda animasyon ve zaman çizelgelerini kullanmaya yönelik kod örnekleri içerir.|
|[Saatler ile İlgili Nasıl Yapılır Konuları](clocks-how-to-topics.md)|Uygulamanızda <xref:System.Windows.Media.Animation.Clock> nesnesini kullanmaya yönelik kod örnekleri içerir.|
|[Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)|Uygulamanızda anahtar çerçeve animasyonlarını kullanmaya yönelik kod örnekleri içerir.|
|[Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)|Uygulamanızdaki yol animasyonlarını kullanmaya yönelik kod örnekleri içerir.|

<a name="reference"></a>

## <a name="reference"></a>Başvuru

- <xref:System.Windows.Media.Animation.Timeline>

- <xref:System.Windows.Media.Animation.Storyboard>

- <xref:System.Windows.Media.Animation.BeginStoryboard>

- <xref:System.Windows.Media.Animation.Clock>
