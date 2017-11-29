---
title: "Özellik Animasyon Tekniklerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a8c196ea15617b13abe8311f8501ab32fd320c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="property-animation-techniques-overview"></a>Özellik Animasyon Tekniklerine Genel Bakış
Bu konu özellikleri için farklı yaklaşımlara açıklar: film şeritleri, yerel animasyonları, saatler ve çerçeve başına animasyonları.  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Önkoşullar  
 Bu konuyu anlamak için açıklanan temel animasyon özellikleri hakkında bilgi sahibi olmalısınız [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
<a name="summary"></a>   
## <a name="different-ways-to-animate"></a>Animasyon için farklı yollar  
 Özellikleri, birçok farklı senaryolar olduğundan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri animasyon için çeşitli yaklaşımlar sağlar.  
  
 Her bir yaklaşım aşağıdaki tabloda, olup olamayacağını gösterir örnek başına, stiller, denetim şablonları veya veri şablonları; kullanılan Bu, kullanılabilir olup olmadığını [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; ve bir yaklaşım mı etkileşimli olarak animasyon denetlemenize olanak verir.  "Örnek" animasyon veya film şeridi örneklerine doğrudan stil, denetim şablonu veya veri şablonu yerine bir nesne uygulama tekniği anlamına gelir.  
  
|Animasyon tekniği|Senaryolar|XAML'i destekler|Etkileşimli olarak denetlenebilir|  
|-------------------------|---------------|-------------------|--------------------------------|  
|Film şeridi animasyon|Örnek başına, <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>,<xref:System.Windows.DataTemplate>|Evet|Evet|  
|Yerel animasyon|Örnek başına|Hayır|Hayır|  
|Saat animasyonu|Örnek başına|Hayır|Evet|  
|Çerçeve başına animasyon|Örnek başına|Hayır|Yok|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>Film şeridi animasyonları  
 Kullanım bir <xref:System.Windows.Media.Animation.Storyboard> tanımlamak ve, animasyonları uygulamak istediğinizde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], etkileşimli olarak bunlar başlatma, karmaşık bir ağacı animasyonların oluşturmak veya içinde animasyon sonra animasyonların bir <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> veya <xref:System.Windows.DataTemplate>. Tarafından animasyonlu için bir nesne için bir <xref:System.Windows.Media.Animation.Storyboard>, olması gerektiğini bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, ayarlamak için kullanılan gerekir veya bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Daha fazla ayrıntı için bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 A <xref:System.Windows.Media.Animation.Storyboard> kapsayıcı özel bir tür <xref:System.Windows.Media.Animation.Timeline> içerdiği animasyonları için hedefleme bilgileri sağlar. İle animasyon eklemek için bir <xref:System.Windows.Media.Animation.Storyboard>, aşağıdaki üç adımı tamamlayın.  
  
1.  Bildirme bir <xref:System.Windows.Media.Animation.Storyboard> ve bir veya daha fazla animasyonları.  
  
2.  Kullanım <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> ve <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> hedef nesne belirtmek için özellikleri ve her animasyonun özellik bağlı.  
  
3.  (Yalnızca kodu) Tanımlayan bir <xref:System.Windows.NameScope> için bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Nesne ile animasyon adlarını kaydetme <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>.  
  
4.  Begin <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Başlayan bir <xref:System.Windows.Media.Animation.Storyboard> animasyonları bunlar animasyon özellikler uygular ve bunları başlatır. Başlamak için iki yolla bir <xref:System.Windows.Media.Animation.Storyboard>: kullanabileceğiniz <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi tarafından sağlanan <xref:System.Windows.Media.Animation.Storyboard> sınıfı veya kullanabilirsiniz bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem. Tek yolu, animasyon [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kullanmaktır bir <xref:System.Windows.Media.Animation.BeginStoryboard> eylem. A <xref:System.Windows.Media.Animation.BeginStoryboard> eylem kullanılabilir bir <xref:System.Windows.EventTrigger>, özellik <xref:System.Windows.Trigger>, veya bir <xref:System.Windows.DataTrigger>.  
  
 Aşağıdaki tabloda farklı yerlerde gösterilmektedir burada her <xref:System.Windows.Media.Animation.Storyboard> başlamak teknik desteklenir: örnek başına, stil, denetim şablonu ve veri şablonu.  
  
|Şeridi başlatılır kullanarak...|Örnek başına|Stil|Denetim şablonu|Veri şablonu|Örnek|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir<xref:System.Windows.EventTrigger>|Evet|Evet|Evet|Evet|[Film şeridi kullanarak bir özelliği animasyon ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve bir özelliği<xref:System.Windows.Trigger>|Hayır|Evet|Evet|Evet|[Bir özellik değeri değiştiğinde animasyon tetikleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>ve<xref:System.Windows.DataTrigger>|Hayır|Evet|Evet|Evet|[Nasıl yapılır: veriler değiştiğinde animasyon tetikleme](http://msdn.microsoft.com/en-us/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>yöntemi|Evet|Hayır|Hayır|Hayır|[Film şeridi kullanarak bir özelliği animasyon ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 Hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Storyboard> nesneleri bkz [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
## <a name="local-animations"></a>Yerel animasyonları  
 Yerel animasyonları herhangi bir bağımlılık özelliği için kullanışlı bir yol sunar <xref:System.Windows.Media.Animation.Animatable> nesnesi. Yerel animasyonları başladıktan sonra animasyonun etkileşimli olarak denetlemek gerek yoktur ve bir özelliğe tek animasyon uygulamak istediğinizde kullanın. Farklı bir <xref:System.Windows.Media.Animation.Storyboard> animasyon, yerel bir animasyon animasyon ile ilişkili olmayan bir nesne bir <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>. Tanımlamanız gerekmez bir <xref:System.Windows.NameScope> bu tür bir animasyon için.  
  
 Yerel animasyonları kodda yalnızca kullanılabilir ve stiller, denetim şablonları veya veri şablonlarında tanımlanamaz. Başladıktan sonra yerel bir animasyon etkileşimli olarak denetlenemez.  
  
 Yerel bir animasyon kullanarak animasyon eklemek için aşağıdaki adımları tamamlayın.  
  
1.  Oluşturma bir <xref:System.Windows.Media.Animation.AnimationTimeline> nesnesi.  
  
2.  Kullanım <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> uygulamak için animasyon eklemek istediğiniz nesnesinin yöntemi <xref:System.Windows.Media.Animation.AnimationTimeline> belirttiğiniz özelliğine.  
  
 Aşağıdaki örnek genişlik ve arka plan rengi animasyon gösterilmektedir bir <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>Saat animasyonları  
 Kullanım <xref:System.Windows.Media.MediaPlayer.Clock%2A> nesneleri kullanmadan animasyon uygulamak istediğinizde bir <xref:System.Windows.Media.Animation.Storyboard> ve karmaşık zamanlama ağaçları oluşturmak veya başladıktan sonra animasyonları etkileşimli olarak denetlemek istediğinizde. Saat nesneleri herhangi bir bağımlılık özelliği için kullanabileceğiniz <xref:System.Windows.Media.Animation.Animatable> nesnesi.  
  
 Kullanamazsınız <xref:System.Windows.Media.Animation.Clock> nesneleri doğrudan stillerde, animasyon denetimini şablonları veya veri şablonları. (Animasyon ve zamanlama sistemi gerçekten kullandığınız <xref:System.Windows.Media.Animation.Clock> stiller, denetim şablonları ve veri şablonları, ancak bunu animasyon nesnelere oluşturmalıdır <xref:System.Windows.Media.Animation.Clock> nesneler için sizden bir <xref:System.Windows.Media.Animation.Storyboard>. Arasındaki ilişki hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Storyboard> nesneleri ve <xref:System.Windows.Media.Animation.Clock> nesneleri bkz [animasyon ve zamanlama sistem genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).)  
  
 Tek bir uygulamak için <xref:System.Windows.Media.Animation.Clock> bir özellik için aşağıdaki adımları tamamlayın.  
  
1.  Oluşturma bir <xref:System.Windows.Media.Animation.AnimationTimeline> nesnesi.  
  
2.  Kullanım <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> yöntemi <xref:System.Windows.Media.Animation.AnimationTimeline> oluşturmak için bir <xref:System.Windows.Media.Animation.AnimationClock>.  
  
3.  Kullanım <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> uygulamak için animasyon eklemek istediğiniz nesnesinin yöntemi <xref:System.Windows.Media.Animation.AnimationClock> belirttiğiniz özelliğine.  
  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.Animation.AnimationClock> ve iki benzer özellikleri için geçerlidir.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Zamanlama ağacı oluşturmak ve animasyon olarak oluşturmak özellikleri kullanmak için aşağıdaki adımları tamamlayın.  
  
1.  Kullanım <xref:System.Windows.Media.Animation.ParallelTimeline> ve <xref:System.Windows.Media.Animation.AnimationTimeline> Zamanlama ağacını oluşturmak için nesneleri.  
  
2.  Kullanım <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> kök <xref:System.Windows.Media.Animation.ParallelTimeline> oluşturmak için bir <xref:System.Windows.Media.Animation.ClockGroup>.  
  
3.  Yinelemek <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> , <xref:System.Windows.Media.Animation.ClockGroup> ve kendi alt geçerli <xref:System.Windows.Media.Animation.Clock> nesneleri. Her <xref:System.Windows.Media.Animation.AnimationClock> alt, kullanım <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> uygulamak için animasyon eklemek istediğiniz nesnesinin yöntemi <xref:System.Windows.Media.Animation.AnimationClock> belirttiğiniz özelliğine  
  
 Saat nesneleri hakkında daha fazla bilgi için bkz: [animasyon ve zamanlama sistem genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md).  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>Çerçeve başına animasyon: animasyon ve zamanlama sistemini atlama  
 Tamamen atlamak istediğinizde bu yaklaşımı kullanın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] animasyon sistemi. Bu yaklaşım için bir senaryo fizik animasyonları burada animasyonun her adımda nesne etkileşimlerin son kümesini temel alınarak yeniden hesaplanacaktır nesnelere gerektirmesidir.  
  
 Çerçeve başına animasyonları stiller, denetim şablonları veya veri şablonları içinde tanımlanamaz.  
  
 Kare kare animasyon için için kayıt <xref:System.Windows.Media.CompositionTarget.Rendering> hale getirmeyi istediğiniz nesneleri içeren nesneyi olay. Bu olay işleyicisi yöntemi çerçeve başına bir kez çağrılır. Her [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sıraladığında verilerini kalıcı işleme arasında görsel ağaç birleşim ağacında, olay işleyicisi yöntemi için çağrılır.  
  
 Olay işleyicinizi ne olursa olsun hesaplamalar animasyon efekti için gerekli olan ve bu değerlerle animasyon eklemek istediğiniz nesnelerin özelliklerini ayarlayın gerçekleştirin.  
  
 Geçerli çerçevenin sunu zamanını elde etmek için <xref:System.EventArgs> bu ile ilişkili olay şeklinde dönüştürülür <xref:System.Windows.Media.RenderingEventArgs>, sağlayan bir <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> geçerli çerçeve elde etmek için kullanabileceğiniz özelliği işleme süresini.  
  
 Daha fazla bilgi için bkz: <xref:System.Windows.Media.CompositionTarget.Rendering> sayfası.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Animasyon ve zamanlama sistemi özeti](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [Bağımlılık özelliklerine genel bakış](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
