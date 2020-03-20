---
title: Özellik Animasyon Tekniklerine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
ms.openlocfilehash: 0b4bf6d4963f32ad83f762fce73c805197ff9c9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181839"
---
# <a name="property-animation-techniques-overview"></a>Özellik Animasyon Tekniklerine Genel Bakış
Bu konu animasyon özellikleri için farklı yaklaşımları açıklar: film panoları, yerel animasyonlar, saatler ve kare başına animasyonlar.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için, [Animasyona Genel Bakış'ta](animation-overview.md)açıklanan temel animasyon özelliklerine aşina olmalısınız.  
  
<a name="summary"></a>
## <a name="different-ways-to-animate"></a>Animasyon için Farklı Yollar  
 Özellikleri animating için birçok farklı senaryo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olduğundan, anaimating özellikleri için çeşitli yaklaşımlar sağlar.  
  
 Her yaklaşım için aşağıdaki tablo, örnek başına, stillerde, denetim şablonlarında veya veri şablonlarında kullanılıp kullanılamayacağı nı gösterir; kullanılıp kullanılamayacağı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; ve yaklaşımın animasyonu etkileşimli olarak kontrol etmenizi sağlar mı?  "Örnek Başına" bir animasyon veya film şeridini stil, denetim şablonu veya veri şablonu yerine doğrudan bir nesnenin örneklerine uygulama tekniğini ifade eder.  
  
|Animasyon tekniği|Senaryolar|XAML'yi destekler|Etkileşimli olarak kontrol edilebilir|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Storyboard animasyon|Örnek başına, <xref:System.Windows.Style> <xref:System.Windows.Controls.ControlTemplate>,<xref:System.Windows.DataTemplate>|Evet|Evet|  
|Yerel animasyon|Örnek başına|Hayır|Hayır|  
|Saat animasyonu|Örnek başına|Hayır|Evet|  
|Kare başına animasyon|Örnek başına|Hayır|Yok|  
  
<a name="storyboard_animations"></a>
## <a name="storyboard-animations"></a>Storyboard Animasyonlar  
 Animasyonlarınızı <xref:System.Windows.Media.Animation.Storyboard> tanımlamak ve uygulamak istediğinizde bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]animasyon kullanın, animasyonlarınızı başladıktan sonra etkileşimle kontrol edin, karmaşık <xref:System.Windows.Style>bir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.DataTemplate>animasyon ağacı oluşturun veya bir animasyonda animasyon uyguluyorsunuz. Bir nesnenin <xref:System.Windows.Media.Animation.Storyboard>bir <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>veya bir veya . Daha fazla bilgi için [Storyboards Genel Bakış'a](storyboards-overview.md)bakın.  
  
 A, <xref:System.Windows.Media.Animation.Storyboard> içerdiği animasyonlar <xref:System.Windows.Media.Animation.Timeline> için hedefleme bilgileri sağlayan özel bir kapsayıcı türüdür. Bir <xref:System.Windows.Media.Animation.Storyboard>ile animasyon için, aşağıdaki üç adımı tamamlarsınız.  
  
1. Bir <xref:System.Windows.Media.Animation.Storyboard> veya daha fazla animasyon bildirin.  
  
2. Her <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> animasyonun hedef nesnesini ve özelliğini belirtmek için ekli ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> ekteki özellikleri kullanın.  
  
3. (Yalnızca kod) A <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>için bir tanımlayın. Nesnelerin adlarını bu <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>animasyon adamak için kaydolun.  
  
4. <xref:System.Windows.Media.Animation.Storyboard>Başlayın.  
  
 Başlangıç, <xref:System.Windows.Media.Animation.Storyboard> animasyonları animasyonlarına uygular ve başlatın. Bir <xref:System.Windows.Media.Animation.Storyboard>başlatmak için iki yol vardır: <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> <xref:System.Windows.Media.Animation.Storyboard> sınıf tarafından sağlanan yöntemi kullanabilirsiniz, ya da bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem kullanabilirsiniz. Bu eylemi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] canlandırmanın tek yolu bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem kullanmaktır. Bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem, bir <xref:System.Windows.EventTrigger>özellik <xref:System.Windows.Trigger>veya bir <xref:System.Windows.DataTrigger>.  
  
 Aşağıdaki tablo, her <xref:System.Windows.Media.Animation.Storyboard> başlangıç tekniğinin desteklendiği farklı yerleri gösterir: örnek başına stil, denetim şablonu ve veri şablonu.  
  
|Storyboard kullanmaya başladı ...|Örnek başına|Stil|Denetim şablonu|Veri şablonu|Örnek|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir<xref:System.Windows.EventTrigger>|Evet|Evet|Evet|Evet|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir özellik<xref:System.Windows.Trigger>|Hayır|Evet|Evet|Evet|[Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir<xref:System.Windows.DataTrigger>|Hayır|Evet|Evet|Evet|[Nasıl kullanılır: Veri Değiştiğinde Animasyonu Tetikleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi|Evet|Hayır|Hayır|Hayır|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Nesneler hakkında <xref:System.Windows.Media.Animation.Storyboard> daha fazla bilgi için [Storyboards Genel Bakış'a](storyboards-overview.md)bakın.  
  
## <a name="local-animations"></a>Yerel Animasyonlar  
 Yerel animasyonlar, herhangi <xref:System.Windows.Media.Animation.Animatable> bir nesnenin bağımlılık özelliğini canlandırmak için kullanışlı bir yol sağlar. Bir tesise tek bir animasyon uygulamak istediğinizde ve animasyon başladıktan sonra etkileşimli olarak denetlemeniz gerekmezken yerel animasyonları kullanın. <xref:System.Windows.Media.Animation.Storyboard> Animasyonun aksine, yerel animasyon bir <xref:System.Windows.FrameworkElement> veya bir <xref:System.Windows.FrameworkContentElement>nesneyle ilişkili olmayan bir nesneyi canlandırabilir. Ayrıca, bu tür animasyonlar <xref:System.Windows.NameScope> için bir tanımlamanız da gerek yoktur.  
  
 Yerel animasyonlar yalnızca kod olarak kullanılabilir ve stiller, denetim şablonları veya veri şablonlarında tanımlanamaz. Yerel animasyon başlatıldıktan sonra etkileşimli olarak denetlenemez.  
  
 Yerel bir animasyon kullanarak animasyon yapmak için aşağıdaki adımları tamamlayın.  
  
1. Bir <xref:System.Windows.Media.Animation.AnimationTimeline> nesne oluşturun.  
  
2. Belirttiğiniz <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> özelliğe uygulamak <xref:System.Windows.Media.Animation.AnimationTimeline> için animasyon yapmak istediğiniz nesnenin yöntemini kullanın.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Saat Animasyonları  
 Nesneleri, a <xref:System.Windows.Media.MediaPlayer.Clock%2A> <xref:System.Windows.Media.Animation.Storyboard> kullanmadan animasyon yapmak istediğinizde ve karmaşık zamanlama ağaçları oluşturmak istediğinizde veya animasyonları başladıktan sonra etkileşimli olarak denetlemek istediğinizde kullanın. Herhangi <xref:System.Windows.Media.Animation.Animatable> bir nesnenin bağımlılık özelliğini canlandırmak için Saat nesnelerini kullanabilirsiniz.  
  
 Nesneleri doğrudan <xref:System.Windows.Media.Animation.Clock> stilleri, denetim şablonlarını veya veri şablonlarını canlandırmak için kullanamazsınız. (Animasyon ve zamanlama sistemi <xref:System.Windows.Media.Animation.Clock> aslında stilleri, denetim şablonları ve veri şablonları animasyon nesneleri kullanır, <xref:System.Windows.Media.Animation.Clock> ancak bir <xref:System.Windows.Media.Animation.Storyboard>sizin için bu nesneleri oluşturması gerekir . Nesneler ve <xref:System.Windows.Media.Animation.Clock> nesneler arasındaki <xref:System.Windows.Media.Animation.Storyboard> ilişki hakkında daha fazla bilgi için Animasyon ve Zamanlama Sistemine Genel [Bakış'a](animation-and-timing-system-overview.md)bakın .)  
  
 Bir özelliğe <xref:System.Windows.Media.Animation.Clock> tek bir uygulama için aşağıdaki adımları tamamlarsınız.  
  
1. Bir <xref:System.Windows.Media.Animation.AnimationTimeline> nesne oluşturun.  
  
2. Bir <xref:System.Windows.Media.Animation.AnimationClock> <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> oluşturmak <xref:System.Windows.Media.Animation.AnimationTimeline> için yöntemini kullanın.  
  
3. Belirttiğiniz <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> özelliğe uygulamak için animasyon yapmak istediğiniz <xref:System.Windows.Media.Animation.AnimationClock> nesnenin yöntemini kullanın.  
  
 Aşağıdaki örnek, bir tanenin <xref:System.Windows.Media.Animation.AnimationClock> nasıl oluşturulacağı ve iki benzer özelleğe nasıl uygulanacağı gösterilmektedir.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Zamanlama ağacı oluşturmak ve özelliklerini canlandırmak için aşağıdaki adımları tamamlarsınız.  
  
1. Zamanlama <xref:System.Windows.Media.Animation.ParallelTimeline> <xref:System.Windows.Media.Animation.AnimationTimeline> ağacını oluşturmak için kullanın ve nesneler.  
  
2. <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> <xref:System.Windows.Media.Animation.ClockGroup>Bir <xref:System.Windows.Media.Animation.ParallelTimeline> .  
  
3. Üzerinden iterate <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> <xref:System.Windows.Media.Animation.ClockGroup> ve alt <xref:System.Windows.Media.Animation.Clock> nesneleri uygulayın. Her <xref:System.Windows.Media.Animation.AnimationClock> çocuk için, <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> belirttiğiniz özelliğe uygulamak için animasyon yapmak <xref:System.Windows.Media.Animation.AnimationClock> istediğiniz nesnenin yöntemini kullanın  
  
 Saat nesneleri hakkında daha fazla bilgi için [Animasyon ve Zamanlama Sistemine Genel Bakış'a](animation-and-timing-system-overview.md)bakın.  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Kare Başına Animasyon: Animasyon ve Zamanlama Sistemini Atlayın  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Animasyon sistemini tamamen atlamanız gerektiğinde bu yaklaşımı kullanın. Bu yaklaşım için bir senaryo, animasyondaki her adımın nesnelerin son nesne etkileşimkümesine göre yeniden hesaplanmasını gerektirdiği fizik animasyonlarıdır.  
  
 Kare başına animasyonlar stilleri, denetim şablonları veya veri şablonları içinde tanımlanamaz.  
  
 Kare kare animasyonyapmak için, animasyon yapmak <xref:System.Windows.Media.CompositionTarget.Rendering> istediğiniz nesneleri içeren nesnenin olayı için kaydolursunuz. Bu olay işleyicisi yöntemi çerçeve başına bir kez çağrılır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Görsel ağaçtaki kalıcı görüntüleme verilerini kompozisyon ağacının karşısındaki her zaman, olay işleyicisi yönteminiz çağrılır.  
  
 Olay işleyicinizde, animasyon efektiniz için gereken hesaplamaları gerçekleştirin ve bu değerlerle canlandırmak istediğiniz nesnelerin özelliklerini ayarlayın.  
  
 Geçerli çerçeve için sunu saatini elde <xref:System.EventArgs> etmek için, bu <xref:System.Windows.Media.RenderingEventArgs>olayla ilişkili <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> olan oyuncu, geçerli çerçevenin oluşturma süresini elde etmek için kullanabileceğiniz bir özellik sağlayan olarak dökümlenebilir.  
  
 Daha fazla bilgi <xref:System.Windows.Media.CompositionTarget.Rendering> için sayfaya bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Bağımlılık Özelliklerine Genel Bakış](../advanced/dependency-properties-overview.md)
