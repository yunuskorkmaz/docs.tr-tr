---
title: Animasyona Genel bakış
description: Windows Presentation Foundation (WPF) ' de etkileyici ekran geçişleri veya canlı görsel ipuçları sayesinde etkileyici bir kullanıcı arabirimi daha da çarpıcı hale getirin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], animations
- animations [WPF], overview
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
ms.openlocfilehash: d761be0c95fb8aa7eb39cb26b57979185226b8fb
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853868"
---
# <a name="animation-overview"></a>Animasyona Genel bakış

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]etkileyici kullanıcı arabirimleri ve çekici belgeler oluşturmanızı sağlayan güçlü bir grafik ve düzen özellikleri kümesi sağlar. Animasyon etkileyici bir kullanıcı arabirimini daha da etkileyici ve kullanılabilir hale getirebilirsiniz. Yalnızca bir arka plan renginin animasyonunu yaparak veya animasyonlu bir animasyon uygulayarak <xref:System.Windows.Media.Transform> , çarpıcı ekran geçişleri oluşturabilir veya yararlı görsel yardımlar sağlayabilirsiniz.

Bu genel bakış, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon ve zamanlama sistemine bir giriş sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Film şeritleri kullanarak nesnelerin animasyonuna odaklanır.

<a name="introducinganimations"></a>

## <a name="introducing-animations"></a>Animasyonları tanıtma

Animasyon, her biri son verilerden biraz farklı olan bir dizi görüntüden hızlıca geçiş yaparak oluşturulan bir yanıdır. Bey, görüntü grubunu tek bir değişen sahne olarak beyin. Bu yanışta, her saniye çok sayıda fotoğraf veya kare kaydeden kameralar kullanılarak oluşturulur. Çerçeveler bir projektör tarafından geri yürütüldüğünde, hedef kitle bir hareketli resim görür.

Bir bilgisayardaki animasyon benzerdir. Örneğin, görünümün dışına çıkan bir dikdörtgen çizimi oluşturan bir program aşağıdaki gibi çalışabilir.

- Program bir zamanlayıcı oluşturur.

- Program, ne kadar süre geçtiğini görmek için zamanlayıcıyı ayarlanan aralıklarda denetler.

- Program zamanlayıcıyı her denetlediğinde, dikdörtgenin ne kadar süre geçtiğini temel alarak geçerli opaklık değerini hesaplar.

- Daha sonra program, dikdörtgeni yeni değerle güncelleştirir ve yeniden çizer.

Öncesinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , Microsoft Windows geliştiricilerinin kendi zamanlama sistemlerini oluşturması ve yönetmesi ya da özel özel kitaplıklar kullanması gerekiyordu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], yönetilen kod ile sunulan ve Framework 'e derinlemesine bir şekilde tümleştirilmiş olan etkili bir zamanlama sistemi içerir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]animasyon denetimleri ve diğer grafik nesnelerinin animasyonunu kolaylaştırır.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]bir zamanlama sisteminin yönetilmesi ve ekranı verimli bir şekilde çizmek için tüm arka planda çalışmayı işler. Bu etkileri sağlamak yerine, oluşturmak istediğiniz etkilere odaklanmanız için zamanlama sınıfları sağlar. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Ayrıca, Özel animasyonlar oluşturmak için sınıflarınızın devraldığı animasyon temel sınıflarını açığa çıkaran kendi animasyonlarınızı oluşturmayı kolaylaştırır. Bu özel animasyonlar, standart animasyon sınıflarının birçok performans avantajı elde edebilir.

<a name="thewpftimingsystem"></a>

## <a name="wpf-property-animation-system"></a>WPF özelliği animasyon sistemi

Zamanlama sistemiyle ilgili birkaç önemli kavramı anladıysanız, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyonların kullanımı daha kolay olabilir. En önemlileri, ' de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , tek tek özelliklerine animasyon uygulayarak nesneleri canlandırmaktır. Örneğin, bir çerçeve öğesini büyütmek için, <xref:System.Windows.FrameworkElement.Width%2A> ve özelliklerini canlandırırsınız <xref:System.Windows.FrameworkElement.Height%2A> . Bir nesneyi görünümden soluklaştırmak için, özelliği canlandırırsınız <xref:System.Windows.UIElement.Opacity%2A> .

Bir özelliğin animasyon özelliklerine sahip olması için, aşağıdaki üç gereksinimi karşılaması gerekir:

- Bağımlılık özelliği olmalıdır.

- Sınıfından devralan ve arabirimini uygulayan bir sınıfa ait olmalıdır <xref:System.Windows.DependencyObject> <xref:System.Windows.Media.Animation.IAnimatable> .

- Kullanılabilir uyumlu bir animasyon türü olmalıdır. ( [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Bir tane sağlamıyorsa, kendi kendinizinkini oluşturabilirsiniz. Bkz. [Özel animasyonlara genel bakış](custom-animations-overview.md).)

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]özellikleri olan çok sayıda nesne içerir <xref:System.Windows.Media.Animation.IAnimatable> . Ve gibi denetimler <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.TabControl> Ayrıca, ve <xref:System.Windows.Controls.Panel> de <xref:System.Windows.Shapes.Shape> nesneleri öğesinden devralınır <xref:System.Windows.DependencyObject> . Özelliklerinin çoğu bağımlılık özellikleridir.

Animasyonları, stiller ve denetim şablonlarına dahil neredeyse her yerde kullanabilirsiniz. Animasyonların görsel olması gerekmez; Bu bölümde açıklanan ölçütlere uyduklarında, Kullanıcı arabiriminin parçası olmayan nesnelere animasyon uygulayabilirsiniz.

<a name="storyboardwalkthrough"></a>

## <a name="example-make-an-element-fade-in-and-out-of-view"></a>Örnek: bir öğeyi Soluklaştırın ve görünümün dışında yapma

Bu örnek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , bir bağımlılık özelliğinin değerine animasyon uygulamak için animasyonun nasıl kullanılacağını gösterir. <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Double> Öğesinin özelliğine animasyon uygulamak için değer üreten bir animasyon türü olan bir kullanır <xref:System.Windows.UIElement.Opacity%2A> <xref:System.Windows.Shapes.Rectangle> . Sonuç olarak, <xref:System.Windows.Shapes.Rectangle> belirme ve görünümün dışına çıkar.

Örneğin ilk bölümü bir <xref:System.Windows.Shapes.Rectangle> öğesi oluşturur. Aşağıdaki adımlar bir animasyon oluşturmayı ve dikdörtgenin özelliğine nasıl uygulanacağını gösterir <xref:System.Windows.UIElement.Opacity%2A> .

Aşağıda, <xref:System.Windows.Shapes.Rectangle> XAML içinde bir öğesinin nasıl oluşturulacağı gösterilmektedir <xref:System.Windows.Controls.StackPanel> .

[!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]

Aşağıda, <xref:System.Windows.Shapes.Rectangle> içindeki bir öğenin nasıl oluşturulacağı gösterilmektedir <xref:System.Windows.Controls.StackPanel> .

[!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
[!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]

<a name="opacity_animation_step1"></a>

### <a name="part-1-create-a-doubleanimation"></a>1. kısım: DoubleAnimation oluşturma

Bir öğeyi soluklaştırın ve görünümün dışında yapmanın bir yolu, özelliğin animasyonunu kullanmaktır <xref:System.Windows.UIElement.Opacity%2A> . <xref:System.Windows.UIElement.Opacity%2A>Özelliği türünde olduğundan <xref:System.Double> , Double değerleri üreten bir animasyon gerekir. <xref:System.Windows.Media.Animation.DoubleAnimation>, Bu tür bir animasyondur. <xref:System.Windows.Media.Animation.DoubleAnimation>İki Double değeri arasında bir geçiş oluşturur. Başlangıç değerini belirtmek için, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini ayarlarsınız. Bitiş değerini belirtmek için, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini ayarlarsınız.

1. Opaklık değeri `1.0` nesnenin tamamen opak olmasını sağlar ve opaklık değeri `0.0` tamamen görünmez hale gelir. ' Den ' e geçiş yapmak `1.0` için `0.0` , <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> özelliğini `1.0` ve <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> özelliğini olarak ayarlayın `0.0` . Aşağıda, XAML içinde nasıl oluşturulacağı gösterilmektedir <xref:System.Windows.Media.Animation.DoubleAnimation> .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]

    Aşağıda bir kod içinde nasıl oluşturulacağı gösterilmektedir <xref:System.Windows.Media.Animation.DoubleAnimation> .

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]

2. Ardından, bir belirtmeniz gerekir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> . <xref:System.Windows.Media.Animation.Timeline.Duration%2A>Bir animasyon, başlangıç değerinden hedef değerine gitmek için geçen süreyi belirtir. Aşağıda, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> xaml 'de beş saniyelik olarak nasıl ayarlanacağı gösterilmektedir.

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]

    Aşağıda, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> kodda beş saniyelik olarak nasıl ayarlanacağı gösterilmektedir.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]

3. Önceki kod, ' dan ' a geçiş yapan bir animasyon gösterdi `1.0` `0.0` . Bu, hedef öğenin tamamen opak ve tamamen görünmez hale gelmesine neden olur. Öğe geçtikten sonra öğeyi görünüme geri dönerek yapmak için <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> animasyonun özelliğini olarak ayarlayın `true` . Animasyonun süresiz olarak tekrarlanması için <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliğini olarak ayarlayın <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A> . Aşağıda, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> xaml 'de ve özelliklerinin nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]

    Aşağıda, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> koddaki ve özelliklerinin nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> .

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]

<a name="opacity_animation_step2"></a>

### <a name="part-2-create-a-storyboard"></a>2. Bölüm: görsel taslak oluşturma

Bir nesneye animasyon uygulamak için bir oluşturur <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> animasyon eklenecek nesne ve özelliği belirtmek için ve ekli özellikleri kullanırsınız.

1. <xref:System.Windows.Media.Animation.Storyboard>' İ oluşturun ve animasyonu alt öğesi olarak ekleyin. Aşağıda, XAML 'de nasıl oluşturulacağı gösterilmektedir <xref:System.Windows.Media.Animation.Storyboard> .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]

    <xref:System.Windows.Media.Animation.Storyboard>İçinde kod oluşturmak için <xref:System.Windows.Media.Animation.Storyboard> sınıf düzeyinde bir değişken bildirin.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]

    Ardından öğesini başlatın <xref:System.Windows.Media.Animation.Storyboard> ve animasyonu alt öğesi olarak ekleyin.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]

2. , <xref:System.Windows.Media.Animation.Storyboard> Animasyonun nereye uygulanacağını bilmelidir. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>Canlandırılacak nesneyi belirtmek için iliştirilmiş özelliğini kullanın. Aşağıda, ' nin hedef adının XAML 'de nasıl ayarlanacağı gösterilmiştir <xref:System.Windows.Media.Animation.DoubleAnimation> `MyRectangle` .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]

    Aşağıda, ' nin hedef adının kodda olarak nasıl ayarlanacağı gösterilmiştir <xref:System.Windows.Media.Animation.DoubleAnimation> `MyRectangle` .

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]

3. <xref:System.Windows.Media.Animation.Storyboard.TargetProperty>Animasyon uygulanacak özelliği belirtmek için iliştirilmiş özelliğini kullanın. Aşağıda animasyonun <xref:System.Windows.UIElement.Opacity%2A> xaml içindeki özelliğini hedeflemek için nasıl yapılandırıldığı gösterilmiştir <xref:System.Windows.Shapes.Rectangle> .

    [!code-xaml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]

    Aşağıda, animasyonun <xref:System.Windows.UIElement.Opacity%2A> kod içindeki özelliğini hedeflemek üzere nasıl yapılandırıldığı gösterilmiştir <xref:System.Windows.Shapes.Rectangle> .

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]

Sözdizimi ve ek örnekler hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> bkz. görsel taslaklara [genel bakış](storyboards-overview.md).

<a name="opacity_animation_step3"></a>

### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>Bölüm 3 (XAML): görsel taslağı bir tetikleyici ile Ilişkilendirme

' In uygulanması ve başlatılması en kolay yolu <xref:System.Windows.Media.Animation.Storyboard> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir olay tetikleyicisi kullanmaktır. Bu bölümde, <xref:System.Windows.Media.Animation.Storyboard> ' nın xaml 'de bir tetikleyiciyle ilişkilendirilmesi gösterilmektedir.

1. Bir <xref:System.Windows.Media.Animation.BeginStoryboard> nesne oluşturun ve görsel taslağınızı onunla ilişkilendirin. <xref:System.Windows.Media.Animation.BeginStoryboard>, <xref:System.Windows.TriggerAction> Uygulanan ve Başlatan bir türüdür <xref:System.Windows.Media.Animation.Storyboard> .

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]

2. Oluşturun <xref:System.Windows.EventTrigger> ve <xref:System.Windows.Media.Animation.BeginStoryboard> koleksiyonuna ekleyin <xref:System.Windows.EventTrigger.Actions%2A> . <xref:System.Windows.EventTrigger.RoutedEvent%2A>Öğesinin özelliğini <xref:System.Windows.EventTrigger> başlatmak istediğiniz yönlendirilmiş olay olarak ayarlayın <xref:System.Windows.Media.Animation.Storyboard> . (Yönlendirilmiş olaylar hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](../advanced/routed-events-overview.md).)

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]

3. Öğesini <xref:System.Windows.EventTrigger> <xref:System.Windows.FrameworkElement.Triggers%2A> dikdörtgenin koleksiyonuna ekleyin.

    [!code-xaml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]

<a name="opacity_animation_step3code"></a>

### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>Bölüm 3 (kod): görsel taslağı bir olay Işleyicisiyle Ilişkilendirme

Bir kod içinde uygulamanın en kolay yolu bir <xref:System.Windows.Media.Animation.Storyboard> olay işleyicisi kullanmaktır. Bu bölümde, <xref:System.Windows.Media.Animation.Storyboard> ' nin kodda bir olay işleyicisi ile ilişkilendirilmesi gösterilmektedir.

1. <xref:System.Windows.FrameworkElement.Loaded>Dikdörtgenin olayına kaydolun.

    [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
    [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]

2. Olay işleyicisini bildirin. Olay işleyicisinde, <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> film şeridini uygulamak için yöntemini kullanın.

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

Animasyonlar özellik değerleri oluşturduğundan farklı özellik türleri için farklı animasyon türleri mevcuttur. Bir öğenin özelliği gibi bir özelliğine animasyon uygulamak için, <xref:System.Double> <xref:System.Windows.FrameworkElement.Width%2A> değer üreten bir animasyon kullanın <xref:System.Double> . Alan bir özelliği hareketlendirmek için <xref:System.Windows.Point> , değerler üreten bir animasyon kullanın ve bu <xref:System.Windows.Point> şekilde devam edin. Farklı özellik türlerinin sayısı nedeniyle, ad alanında birkaç animasyon sınıfı vardır <xref:System.Windows.Media.Animation> . Neyse ki, aralarında ayrım yapmayı kolaylaştıran bir katı adlandırma kuralına uyar:

- \<*Type*>Animasyon

  "From/to/by" veya "temel" animasyon olarak bilinen, bu, başlangıç ve hedef değerleri arasında veya başlangıç değerine bir de bir konum değeri eklenerek canlandırılır.

  - Başlangıç değerini belirtmek için animasyonun from özelliğini ayarlayın.

  - Bir bitiş değeri belirtmek için animasyonun To özelliğini ayarlayın.

  - Bir fark değeri belirtmek için animasyonun by özelliğini ayarlayın.

  Bu genel bakışta örnekler bu animasyonları kullanır, çünkü bu en basit kullanım kolayıdır. From/To/By animasyonları, From/To/By animasyonlara genel bakış bölümünde ayrıntılı olarak açıklanmıştır.

- \<*Type*>Sınıflarından

  Anahtar çerçeve animasyonları, herhangi bir sayıda hedef değer belirtebileceğiniz ve hatta enterpolasyon yöntemini denetleyebildiğinden, From/To/By animasyonlarından daha güçlüdür. Bazı türler yalnızca anahtar çerçeve animasyonlarına animasyon eklenebilir. Anahtar çerçeve animasyonları, [anahtar çerçeve animasyonlarında genel bakış](key-frame-animations-overview.md)bölümünde ayrıntılı olarak açıklanmıştır.

- \<*Type*>AnimationUsingPath

  Yol animasyonları, animasyon değerlerini oluşturmak için geometrik yol kullanmanıza olanak sağlar.

- \<*Type*>Birinden

  Özet sınıf, uyguladığınızda, bir \<*Type*> değeri hareketlendirir. Bu sınıf, \<*Type*> Animation ve AnimationUsingKeyFrames sınıfları için temel sınıf olarak hizmet verir \<*Type*> . Yalnızca kendi özel animasyonlarınızı oluşturmak istiyorsanız bu sınıflarla doğrudan uğraşmanız gerekir. Aksi takdirde, bir \<*Type*> animasyon veya ana kare \<*Type*> animasyonu kullanın.

Çoğu durumda, \<*Type*> ve gibi animasyon sınıflarını kullanmak isteyeceksiniz <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Animation.ColorAnimation> .

Aşağıdaki tabloda birkaç ortak animasyon türü ve bunların kullanıldıkları bazı özellikler gösterilmektedir.

|Özellik türü|Karşılık gelen temel (From/To/By) animasyonu|Karşılık gelen anahtar çerçeve animasyonu|Karşılık gelen yol animasyonu|Kullanım örneği|
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Hiçbiri|<xref:System.Windows.Media.SolidColorBrush.Color%2A>Bir <xref:System.Windows.Media.SolidColorBrush> veya ' a animasyon ekleyin <xref:System.Windows.Media.GradientStop> .|
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|' A <xref:System.Windows.FrameworkElement.Width%2A> veya ' <xref:System.Windows.Controls.DockPanel> a animasyon ekleyin <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.Button> .|
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|Konumuna animasyon ekleyin <xref:System.Windows.Media.EllipseGeometry.Center%2A> <xref:System.Windows.Media.EllipseGeometry> .|
|<xref:System.String>|Hiçbiri|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Hiçbiri|' A <xref:System.Windows.Controls.TextBlock.Text%2A> veya ' <xref:System.Windows.Controls.TextBlock> a animasyon ekleyin <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Button> .|

<a name="animationsaretimelines"></a>

### <a name="animations-are-timelines"></a>Animasyonlar zaman çizelgelerinizi

Tüm animasyon türleri <xref:System.Windows.Media.Animation.Timeline> sınıftan devralınır; bu nedenle tüm animasyonlar, zaman çizelgelerinin özelleşmiş türleridir. Bir <xref:System.Windows.Media.Animation.Timeline> zaman kesimini tanımlar. Bir zaman çizelgesinin *zamanlama davranışlarını* belirtebilirsiniz: <xref:System.Windows.Media.Animation.Timeline.Duration%2A> Bu sürenin kaç kez tekrarlandığını ve hatta ne kadar hızlı zaman ilerlediğini belirtir.

Bir animasyon bir olduğundan <xref:System.Windows.Media.Animation.Timeline> , bir zaman kesimini de temsil eder. Bir animasyon, belirtilen zaman segmentinden (veya) ilerledikçe çıkış değerlerini de hesaplar <xref:System.Windows.Media.Animation.Timeline.Duration%2A> . Animasyon ilerledikçe veya "oynatılır", ilişkili olduğu özelliği günceller.

Sık kullanılan üç zamanlama özelliği <xref:System.Windows.Media.Animation.Timeline.Duration%2A> , <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ve ' dir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> .

#### <a name="the-duration-property"></a>Duration özelliği

Daha önce belirtildiği gibi, bir zaman çizelgesi bir zaman kesimini temsil eder. Bu segmentin uzunluğu, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> genellikle bir değer kullanılarak belirtilen zaman çizelgesi tarafından belirlenir <xref:System.Windows.Duration.TimeSpan%2A> . Bir zaman çizelgesi süresinin sonuna ulaştığında bir yinelemeyi tamamlamıştır.

Bir animasyon, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> geçerli değerini öğrenmek için özelliğini kullanır. <xref:System.Windows.Media.Animation.Timeline.Duration%2A>Animasyon için bir değer belirtmezseniz, varsayılan değer olan 1 saniye kullanır.

Aşağıdaki sözdizimi, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] özelliği için öznitelik sözdiziminin basitleştirilmiş bir sürümünü gösterir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> .

*saat* `:` *dakika* `:` *saniyeler*

Aşağıdaki tabloda çeşitli <xref:System.Windows.Duration> Ayarlar ve sonuçta elde edilen değerler gösterilmektedir.

|Ayar|Sonuç değeri|
|-------------|---------------------|
|0:0: 5,5|5,5 saniye.|
|0:30:5,5|30 dakika ve 5,5 saniye.|
|1:30:5,5|1 saat, 30 dakika ve 5,5 saniye.|

Bir kod içinde belirtmenin bir yolu, <xref:System.Windows.Duration> <xref:System.TimeSpan.FromSeconds%2A> oluşturmak için yöntemini kullanmak <xref:System.TimeSpan> ve ardından kullanarak yeni bir yapı bildirmektir <xref:System.Windows.Duration> <xref:System.TimeSpan> .

Değerler ve tüm sözdizimi hakkında daha fazla bilgi için <xref:System.Windows.Duration> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , yapısına bakın <xref:System.Windows.Duration> .

#### <a name="autoreverse"></a>AutoReverse

<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>Özelliği, bir zaman çizelgesinin sonuna ulaştıktan sonra geriye doğru yürütülüp yürütülmeyeceğini belirtir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> . Bu animasyon özelliğini olarak ayarlarsanız `true` , bir animasyon onun sonuna ulaştıktan sonra ters döner ve onun <xref:System.Windows.Media.Animation.Timeline.Duration%2A> bitiş değerinden başlangıç değerine geri döner. Varsayılan olarak, bu özellik `false` .

#### <a name="repeatbehavior"></a>RepeatBehavior

<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>Özelliği, bir zaman çizelgesinin kaç kez oynatılacağını belirtir. Varsayılan olarak, zaman çizelgeleri yineleme sayısına sahiptir; `1.0` Bu, bir kez oynadıkları ve hiç yinelenmediği anlamına gelir.

Bu özellikler ve diğerleri hakkında daha fazla bilgi için bkz. [Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md).

<a name="applyanimationstoproperty"></a>

## <a name="applying-an-animation-to-a-property"></a>Bir özelliğe animasyon uygulama

Önceki bölümlerde farklı animasyon türleri ve bunların zamanlama özellikleri açıklanır. Bu bölüm, animasyonunu hareketlendirmek istediğiniz özelliğe nasıl uygulayacağınızı gösterir. <xref:System.Windows.Media.Animation.Storyboard>nesneler, özelliklere animasyon uygulamak için bir yol sağlar. , <xref:System.Windows.Media.Animation.Storyboard> İçerdiği animasyonlar için hedefleme bilgilerini sağlayan bir *kapsayıcı zaman çizelgesi* olur.

### <a name="targeting-objects-and-properties"></a>Nesneleri ve özellikleri hedefleme

<xref:System.Windows.Media.Animation.Storyboard>Sınıfı <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> ekli özellikleri sağlar. Bu özellikleri bir animasyon üzerinde ayarlayarak, animasyona nelerin hareketlendirileceğini söylemiş olursunuz. Ancak, bir animasyon bir nesneyi hedeflebilmeniz için, nesneye genellikle bir ad verilmelidir.

Bir adın bir nesneye atanması <xref:System.Windows.FrameworkElement> farklı bir ada atanmasından farklıdır <xref:System.Windows.Freezable> . Çoğu denetim ve panel çerçeve öğeleridir; Ancak, fırçalar, dönüşümler ve geometriler gibi çoğu tamamen grafik nesnesi Freezable nesnelerdir. Bir türün bir veya için olup olmadığından emin değilseniz <xref:System.Windows.FrameworkElement> <xref:System.Windows.Freezable> , başvuru belgelerinin **devralma hiyerarşisi** bölümüne bakın.

- <xref:System.Windows.FrameworkElement>Bir animasyon hedefi oluşturmak için, özelliğini ayarlayarak bir ad verirsiniz <xref:System.Windows.FrameworkElement.Name%2A> . Kodda, <xref:System.Windows.FrameworkElement.RegisterName%2A> öğe adını ait olduğu sayfayla birlikte kaydetmek için yöntemini de kullanmalısınız.

- Bir <xref:System.Windows.Freezable> nesneyi ' de bir animasyon hedefi yapmak için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , [x:Name yönergesini](../../../desktop-wpf/xaml-services/xname-directive.md) bir ad atamak için kullanırsınız. Kod içinde, <xref:System.Windows.FrameworkElement.RegisterName%2A> nesneyi ait olduğu sayfayla kaydetmek için yalnızca yöntemini kullanırsınız.

Aşağıdaki bölümlerde, ve kodunda bir öğe adlandırma örneği sağlanmaktadır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Adlandırma ve hedefleme hakkında daha ayrıntılı bilgi için bkz. görsel taslaklara [genel bakış](storyboards-overview.md).

### <a name="applying-and-starting-storyboards"></a>Film şeritleri uygulanıyor ve başlatılıyor

' De bir film şeridi başlatmak için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bunu bir ile ilişkilendirirsiniz <xref:System.Windows.EventTrigger> . <xref:System.Windows.EventTrigger>, Belirtilen bir olay gerçekleştiğinde gerçekleştirilecek eylemleri açıklayan bir nesnedir. Bu eylemlerden biri <xref:System.Windows.Media.Animation.BeginStoryboard> , görsel taslağınızı başlatmak için kullandığınız bir eylem olabilir. Olay Tetikleyicileri, uygulamanızın belirli bir olaya nasıl yanıt vereceğini belirtmenizi sağladığından olay işleyicileri kavramıyla benzerdir. Olay işleyicilerinin aksine, Olay Tetikleyicileri içinde tam olarak açıklanabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ; başka kod gerekmez.

Bir <xref:System.Windows.Media.Animation.Storyboard> kod içinde başlatmak için, <xref:System.Windows.EventTrigger> veya <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> sınıfının yöntemini kullanabilirsiniz <xref:System.Windows.Media.Animation.Storyboard> .

<a name="controllingstoryboards"></a>

## <a name="interactively-control-a-storyboard"></a>Görsel Taslağı etkileşimli olarak denetleme

Önceki örnek bir olay gerçekleştiğinde nasıl başlatılacağını gösterdi <xref:System.Windows.Media.Animation.Storyboard> . Başladıktan sonra etkileşimli bir şekilde denetleyebilirsiniz <xref:System.Windows.Media.Animation.Storyboard> : duraklatıp devam edebilir, durdurabilir, Fill dönemine ilerletebilirsiniz, arayabilir ve kaldırabilirsiniz <xref:System.Windows.Media.Animation.Storyboard> . Daha fazla bilgi ve bir örneğini etkileşimli olarak nasıl denet, gösteren bir örnek için <xref:System.Windows.Media.Animation.Storyboard> bkz. görsel taslaklara [genel bakış](storyboards-overview.md).

<a name="fillbehaviorsection"></a>

## <a name="what-happens-after-an-animation-ends"></a>Bir animasyon bittikten sonra ne olur?

<xref:System.Windows.Media.Animation.FillBehavior>Özelliği, bir zaman çizelgesinin sona erdiğinde nasıl davranacağını belirtir. Varsayılan olarak, bir zaman çizelgesi <xref:System.Windows.Media.Animation.ClockState.Filling> sona erdiğinde başlar. <xref:System.Windows.Media.Animation.ClockState.Filling>Son çıkış değerini tutan bir animasyon.

<xref:System.Windows.Media.Animation.DoubleAnimation>Önceki örnekteki, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği olarak ayarlandığı için sonlanmıyor <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A> . Aşağıdaki örnek, benzer bir animasyon kullanarak bir dikdörtgeni hareketlendirir. Önceki örneğin aksine, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> Bu animasyonun ve özellikleri varsayılan değerlerinde bırakılır. Bu nedenle, animasyon beş saniye boyunca 1 ile 0 arasında ilerlerler ve sonra duraklar.

[!code-xaml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]

[!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
[!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]

<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>Varsayılan değerinden değişmediğinden, <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd> Bu, animasyon son değerini, 0, sona erdiğinde tutar. Bu nedenle, <xref:System.Windows.UIElement.Opacity%2A> bir animasyon bittikten sonra dikdörtgenin 0 ' da kalması gerekir. <xref:System.Windows.UIElement.Opacity%2A>Dikdörtgenin bir değerini başka bir değere ayarlarsanız, animasyon özelliği hala etkilediği için kodunuzun etkisi olmaz gibi görünür <xref:System.Windows.UIElement.Opacity%2A> .

Kodda animasyonlu bir özelliğin denetimini yeniden kazanmak için bir yol <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanmak ve parametresi için null değeri belirtmektir <xref:System.Windows.Media.Animation.AnimationTimeline> . Daha fazla bilgi ve bir örnek için bkz. [Görsel Taslakla animasyon uygulandıktan sonra özelliği ayarlama](how-to-set-a-property-after-animating-it-with-a-storyboard.md).

Ya da animasyonu olan bir özellik değerinin <xref:System.Windows.Media.Animation.ClockState.Active> <xref:System.Windows.Media.Animation.ClockState.Filling> etkin olmadığından, özellik değerinin değişebileceğini unutmayın. Daha fazla bilgi için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).

<a name="databindingAndAnimatingAnimationsSection"></a>

## <a name="data-binding-and-animating-animations"></a>Veri bağlama ve animasyonları hareketlendirme

Animasyon özelliklerinin çoğu veri veya animasyonlu olabilir; Örneğin, <xref:System.Windows.Media.Animation.Timeline.Duration%2A> bir öğesinin özelliğine animasyon uygulayabilirsiniz <xref:System.Windows.Media.Animation.DoubleAnimation> . Ancak, zamanlama sisteminin çalışma biçimi nedeniyle, veri bağlantılı veya animasyonlu animasyonlar diğer veri bağlantılı veya animasyonlu nesneler gibi davranmaz. Davranışlarını anlamak için bir özelliği bir animasyon uygulamak için ne anlama geldiğini anlamanıza yardımcı olur.

Bir dikdörtgenin nasıl hareketlendirileceğini gösteren önceki bölümde yer alan örneğe bakın <xref:System.Windows.UIElement.Opacity%2A> . Önceki örnekteki dikdörtgen yüklendiğinde, olay tetikleyicisi uygular <xref:System.Windows.Media.Animation.Storyboard> . Zamanlama sistemi, ve animasyonunun bir kopyasını oluşturur <xref:System.Windows.Media.Animation.Storyboard> . Bu kopyalar dondurulur (salt okunurdur) ve <xref:System.Windows.Media.Animation.Clock> nesneler bunlardan oluşturulur. Bu saatler, hedeflenen özellikleri hareketlendirmek için gerçek çalışmalara sahiptir.

Zamanlama sistemi için bir saat oluşturur ve, ve <xref:System.Windows.Media.Animation.DoubleAnimation> tarafından belirtilen nesnesine ve özelliğine uygular <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> <xref:System.Windows.Media.Animation.DoubleAnimation> . Bu durumda, zamanlama sistemi, <xref:System.Windows.UIElement.Opacity%2A> "MyRectangle" adlı nesnenin özelliğine saati uygular.

İçin bir saat de oluşturulsa da, <xref:System.Windows.Media.Animation.Storyboard> saat herhangi bir özelliğe uygulanmaz. Amacı, için oluşturulan saat olan alt saatini denetme amaçlıdır <xref:System.Windows.Media.Animation.DoubleAnimation> .

Bir animasyonun veri bağlamayı veya animasyon değişikliklerini yansıtması için, saatinin yeniden oluşturulması gerekir. Saatler sizin için otomatik olarak yeniden oluşturulmaz. Bir animasyonun değişiklikleri yansıtmasını sağlamak için, veya metodunu kullanarak film şeridini yeniden uygulayın <xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> . Bu yöntemlerden birini kullandığınızda animasyon yeniden başlatılır. Kod içinde, <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> Görsel Taslağı önceki konumuna geri kaydırmak için yöntemini kullanabilirsiniz.

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
|[Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)|Zamanlama sisteminin, ve sınıflarını nasıl kullandığını açıklar <xref:System.Windows.Media.Animation.Timeline> ve <xref:System.Windows.Media.Animation.Clock> Bu da animasyonları oluşturmanızı sağlar.|
|[Animasyon İpuçları ve Püf Noktaları](animation-tips-and-tricks.md)|Performans gibi animasyonlarla ilgili sorunları çözmek için faydalı ipuçları listeler.|
|[Özel Animasyonlara Genel Bakış](custom-animations-overview.md)|Animasyon sisteminin anahtar çerçeveler, animasyon sınıfları veya kare başına geri çağırmalar ile nasıl genişletileceğini açıklar.|
|[Gelen/İçin/Göre Animasyonlarına Genel Bakış](from-to-by-animations-overview.md)|İki değer arasında geçiş yapan bir animasyonun nasıl oluşturulacağını açıklar.|
|[Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)|Enterpolasyon yöntemini denetleme özelliği de dahil olmak üzere birden çok hedef değeri olan bir animasyonun nasıl oluşturulacağını açıklar.|
|[Kolaylaştırıcı İşlevler](easing-functions.md)|Sıçramalar gibi gerçekçi davranışları almak için animasyonlarınızın matematiksel formüllerin nasıl uygulanacağını açıklar.|
|[Yol Animasyonlarına Genel Bakış](path-animations-overview.md)|Bir nesnenin karmaşık bir yol üzerinde nasıl taşınacağını veya döndürüleceğini açıklar.|
|[Özellik Animasyon Tekniklerine Genel Bakış](property-animation-techniques-overview.md)|Görsel taslak, yerel animasyon, saat ve çerçeve başına animasyonları kullanarak özellik animasyonlarını açıklar.|
|[Görsel Taslaklara Genel Bakış](storyboards-overview.md)|Karmaşık animasyonlar oluşturmak için birden çok zaman çizelgesi ile film şeritlerinin nasıl kullanılacağını açıklar.|
|[Zamanlama Davranışlarına Genel Bakış](timing-behaviors-overview.md)|<xref:System.Windows.Media.Animation.Timeline>Animasyonlarda kullanılan türleri ve özellikleri açıklar.|
|[Zamanlama Olaylarına Genel Bakış](timing-events-overview.md)|<xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Clock> Başlangıç, duraklatma, devam etmeyi, atla veya Durdur gibi zaman çizelgesindeki noktalarda kod yürütmek için ve nesnelerinde kullanılabilir olayları açıklar.|
|[Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)|Uygulamanızda animasyon ve zaman çizelgelerini kullanmaya yönelik kod örnekleri içerir.|
|[Saatler ile İlgili Nasıl Yapılır Konuları](clocks-how-to-topics.md)|Uygulamanızda nesnesini kullanmak için kod örnekleri içerir <xref:System.Windows.Media.Animation.Clock> .|
|[Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)|Uygulamanızda anahtar çerçeve animasyonlarını kullanmaya yönelik kod örnekleri içerir.|
|[Yol Animasyonu ile İlgili Nasıl Yapılır Konuları](path-animation-how-to-topics.md)|Uygulamanızdaki yol animasyonlarını kullanmaya yönelik kod örnekleri içerir.|

<a name="reference"></a>

## <a name="reference"></a>Başvuru

- <xref:System.Windows.Media.Animation.Timeline>

- <xref:System.Windows.Media.Animation.Storyboard>

- <xref:System.Windows.Media.Animation.BeginStoryboard>

- <xref:System.Windows.Media.Animation.Clock>
