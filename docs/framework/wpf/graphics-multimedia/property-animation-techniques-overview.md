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
ms.openlocfilehash: ebee350f69b5c5e4f9d38c452b9c87bf003528ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317915"
---
# <a name="property-animation-techniques-overview"></a>Özellik Animasyon Tekniklerine Genel Bakış
Bu konuda özellikleri farklı yaklaşım açıklanmaktadır: görsel Taslaklar, yerel animasyonları, saatler ve başına-çerçeve animasyonlara.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuda anlamak için açıklanan temel animasyon özellikleri hakkında bilgi sahibi olmalısınız [animasyona genel bakış](animation-overview.md).  
  
<a name="summary"></a>   
## <a name="different-ways-to-animate"></a>Farklı yolları animasyon ekleme  
 Özellikler animasyon için birçok farklı senaryo olduğundan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerine animasyon ekleme için çeşitli yaklaşımlar sağlar.  
  
 Her bir yaklaşım için aşağıdaki tabloda, çözümlenmeyeceğini gösteren örnek başına, stiller, denetim şablonları veya veri şablonları; kullanılan Bunu kullanılabilir olup olmadığını [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; ve bir yaklaşım olup animasyon etkileşimli bir şekilde denetlemenizi sağlar.  "Örnek başına" animasyon veya görsel taslak örneklerine doğrudan bir stil, denetim şablonu veya veri şablonu değil, bir nesnenin uygulama tekniği anlamına gelir.  
  
|Animasyon yöntemi|Senaryolar|XAML destekler|Etkileşimli olarak denetlenebilir|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Animasyon film şeridi|Örnek başına, <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, <xref:System.Windows.DataTemplate>|Evet|Evet|  
|Yerel animasyon|Örnek başına|Hayır|Hayır|  
|Saat animasyonu|Örnek başına|Hayır|Evet|  
|Çerçeve başına animasyonu|Örnek başına|Hayır|Yok|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>Görsel taslak animasyonları  
 Kullanım bir <xref:System.Windows.Media.Animation.Storyboard> tanımlamak ve içinde animasyon uygulamak istediğinizde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], etkileşimli olarak sonra Başlat, karmaşık bir ağaç animasyon oluşturmak veya içinde animasyon ekleme animasyonlarınızı denetleyen bir <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> veya <xref:System.Windows.DataTemplate>. Göre animasyonlu hale getirilmesini bir nesne için bir <xref:System.Windows.Media.Animation.Storyboard>, olmalıdır bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, veya ayarlanacak kullanılmalıdır bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Daha fazla ayrıntı için [görsel taslaklara genel bakış](storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> kapsayıcı özel bir tür <xref:System.Windows.Media.Animation.Timeline> içerdiği animasyon için hedefleme bilgileri sağlar. İle animasyon uygulamak için bir <xref:System.Windows.Media.Animation.Storyboard>, aşağıdaki üç adımı tamamlayın.  
  
1. Bildirme bir <xref:System.Windows.Media.Animation.Storyboard> ve bir veya daha fazla animasyonları.  
  
2. Kullanım <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> hedef nesne belirtmek için özellikleri ve özellik animasyonun bağlı.  
  
3. (Yalnızca kod) Tanımlayan bir <xref:System.Windows.NameScope> için bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. İle animasyon uygulamak için nesnelerin adlarını kaydetmeleri <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>.  
  
4. Başlamak <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Başlayan bir <xref:System.Windows.Media.Animation.Storyboard> bunlar animasyon özelliklerine animasyon uygular ve bunları başlatır. Başlamak için iki yolu vardır bir <xref:System.Windows.Media.Animation.Storyboard>: kullanabilirsiniz <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi tarafından sağlanan <xref:System.Windows.Media.Animation.Storyboard> sınıfı veya kullanabileceğiniz bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem. İçinde animasyon uygulamak için tek yolu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmaktır bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem. A <xref:System.Windows.Media.Animation.BeginStoryboard> eylemi kullanılabilir bir <xref:System.Windows.EventTrigger>, özellik <xref:System.Windows.Trigger>, veya bir <xref:System.Windows.DataTrigger>.  
  
 Aşağıdaki tabloda farklı yerlere gösterilmektedir. burada her <xref:System.Windows.Media.Animation.Storyboard> başlamak teknik desteklenir: örnek başına, stil, denetim şablonu ve veri şablonu.  
  
|Görsel taslak kullanarak başladı...|Örnek başına|Stil|Denetim şablonu|Veri şablonu|Örnek|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve <xref:System.Windows.EventTrigger>|Evet|Evet|Evet|Evet|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve bir özelliği <xref:System.Windows.Trigger>|Hayır|Evet|Evet|Evet|[Özellik Değeri Değiştiğinde bir Animasyonu Tetikleme](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> ve <xref:System.Windows.DataTrigger>|Hayır|Evet|Evet|Evet|[Nasıl yapılır: Veriler değiştiğinde bir animasyonu tetikleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> Yöntemi|Evet|Hayır|Hayır|Hayır|[Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Storyboard> nesneleri bkz [görsel taslaklara genel bakış](storyboards-overview.md).  
  
## <a name="local-animations"></a>Yerel animasyon  
 Yerel animasyon herhangi bir bağımlılık özelliği için kullanışlı bir yol sağlayan <xref:System.Windows.Media.Animation.Animatable> nesne. Yerel animasyon başladıktan sonra etkileşimli animasyon denetimi gerekmez ve özellik tek bir animasyon uygulamak istediğiniz kullanın. Farklı bir <xref:System.Windows.Media.Animation.Storyboard> animasyon, yerel bir animasyon animasyon ekleme ile ilişkili olmayan bir nesne bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Ayrıca tanımlamak zorunda olmadığınızı bir <xref:System.Windows.NameScope> bu tür bir animasyon için.  
  
 Yerel animasyon yalnızca kod içinde kullanılabilir ve stiller, denetim şablonları veya veri şablonları tanımlanamaz. Başladıktan sonra yerel animasyon etkileşimli olarak kontrol edilemez.  
  
 Yerel animasyon kullanarak animasyon uygulamak için aşağıdaki adımları tamamlayın.  
  
1. Oluşturma bir <xref:System.Windows.Media.Animation.AnimationTimeline> nesne.  
  
2. Kullanım <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> uygulamak için animasyon uygulamak istediğiniz nesneye yöntemi <xref:System.Windows.Media.Animation.AnimationTimeline> belirttiğiniz özelliğine.  
  
 Aşağıdaki örnekte, genişlik ve arka plan rengini animasyon ekleme işlemi gösterilmektedir bir <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Saat animasyonları  
 Kullanım <xref:System.Windows.Media.MediaPlayer.Clock%2A> nesneleri kullanmadan animasyon uygulamak istediğinizde bir <xref:System.Windows.Media.Animation.Storyboard> ve karmaşık zamanlama ağaçları oluşturmak veya başladıktan sonra animasyonları etkileşimli olarak denetlemek istiyorsanız. Saat nesneleri herhangi bir bağımlılık özelliği için kullanabileceğiniz <xref:System.Windows.Media.Animation.Animatable> nesne.  
  
 Kullanamazsınız <xref:System.Windows.Media.Animation.Clock> nesneleri doğrudan stillerde, animasyon uygulamak için denetim şablonları veya veri şablonları. (Animasyon ve zamanlama sistemi gerçekten kullandığınız <xref:System.Windows.Media.Animation.Clock> stiller, denetim şablonları ve veri şablonları ancak bu animasyon uygulamak için nesneleri oluşturmalıdır <xref:System.Windows.Media.Animation.Clock> nesneler için sizden bir <xref:System.Windows.Media.Animation.Storyboard>. Arasındaki ilişki hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Storyboard> nesneleri ve <xref:System.Windows.Media.Animation.Clock> nesneleri bkz [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).)  
  
 Tek bir uygulamaya <xref:System.Windows.Media.Animation.Clock> bir özellik için aşağıdaki adımları tamamlayın.  
  
1. Oluşturma bir <xref:System.Windows.Media.Animation.AnimationTimeline> nesne.  
  
2. Kullanım <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> yöntemi <xref:System.Windows.Media.Animation.AnimationTimeline> oluşturmak için bir <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3. Kullanım <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> uygulamak için animasyon uygulamak istediğiniz nesneye yöntemi <xref:System.Windows.Media.Animation.AnimationClock> belirttiğiniz özelliğine.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Media.Animation.AnimationClock> ve iki benzer özellikleri için geçerlidir.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Bir zamanlama ağacını oluşturmak ve Canlandır özellikleri kullanmak için aşağıdaki adımları tamamlayın.  
  
1. Kullanım <xref:System.Windows.Media.Animation.ParallelTimeline> ve <xref:System.Windows.Media.Animation.AnimationTimeline> Zamanlama ağacını oluşturmak için nesne.  
  
2. Kullanım <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> kök <xref:System.Windows.Media.Animation.ParallelTimeline> oluşturmak için bir <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3. Yinelemek <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> , <xref:System.Windows.Media.Animation.ClockGroup> ve kendi alt uygulama <xref:System.Windows.Media.Animation.Clock> nesneleri. Her <xref:System.Windows.Media.Animation.AnimationClock> alt, kullanım <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> uygulamak için animasyon uygulamak istediğiniz nesneye yöntemi <xref:System.Windows.Media.Animation.AnimationClock> belirttiğiniz özelliğine  
  
 Saat nesneleri hakkında daha fazla bilgi için bkz. [animasyon ve zamanlama sistemine genel bakış](animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Çerçeve başına animasyonu: Animasyon ve zamanlama sistemine atlama  
 Tamamen atlamak gerektiğinde bu yaklaşımı kullanın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon sistemi. Bu yaklaşıma bir senaryo fizik animasyonları, burada her adımda animasyon nesnelerin son nesne etkileşimlerini kümesine göre yeniden hesaplanmasını gerektirmesidir.  
  
 Çerçeve başına animasyon, stiller, denetim şablonları veya veri şablonları içinde tanımlanamaz.  
  
 Kare kare animasyon uygulamak için kayıt <xref:System.Windows.Media.CompositionTarget.Rendering> olayı animasyon uygulamak istediğiniz nesneleri içeren nesne. Bu olay işleyicisi yöntemi, çerçeve başına bir kez çağrılır. Her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sıraladığında kalıcı işleme verileri arasında görsel ağaç kompozisyon ağacı, olay işleyicisi yönteminiz için çağrılır.  
  
 Olay işleyicisinde, hesaplamaları, animasyon efekti için gerekli olan ve bu değerleri ile animasyon uygulamak istediğiniz nesnelerin özelliklerini ayarlayın gerçekleştirin.  
  
 Geçerli çerçevenin sunu zamanını almak için <xref:System.EventArgs> bununla ilişkili olay olarak yayımlanabilir <xref:System.Windows.Media.RenderingEventArgs>, sağlayan bir <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> geçerli çerçeve elde etmek için kullanabileceğiniz özellik işleme süresini.  
  
 Daha fazla bilgi için <xref:System.Windows.Media.CompositionTarget.Rendering> sayfası.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Animasyon ve Zamanlama Sistemine Genel Bakış](animation-and-timing-system-overview.md)
- [Bağımlılık Özelliklerine Genel Bakış](../advanced/dependency-properties-overview.md)
