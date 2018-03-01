---
title: "Nasıl yapılır: Görsel Taslakla Özelliğe Animasyon Ekledikten Sonra Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3ffc534549f5b114a07f09326be72c1968d178a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>Nasıl yapılır: Görsel Taslakla Özelliğe Animasyon Ekledikten Sonra Ayarlama
Bazı durumlarda, animasyon sonra bir özelliğin değerini değiştiremezsiniz görünebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.Storyboard> rengini animasyon uygulamak için kullanılan bir <xref:System.Windows.Media.SolidColorBrush>. Düğme tıklatıldığında film şeridi tetiklenir. <xref:System.Windows.Media.Animation.Timeline.Completed> Olayı program bilgilendirecek işlenir zaman <xref:System.Windows.Media.Animation.ColorAnimation> tamamlar.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>Örnek  
 Sonra <xref:System.Windows.Media.Animation.ColorAnimation> tamamlar, mavi ve fırça rengini değiştirmek için program girişimleri.  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 Önceki kod herhangi bir şey yapmanızı görünmüyor: değeri olan fırça sarı olarak kalır verdiği <xref:System.Windows.Media.Animation.ColorAnimation> fırça animasyonlu. Temel alınan özellik değeri (Temel) gerçekte mavi olarak değiştirilir. Ancak, etkin veya geçerli, değer sarı olarak kalır çünkü <xref:System.Windows.Media.Animation.ColorAnimation> hala temel değeri geçersiz kılma. Temel değerin yeniden etkili değer olmasını istiyorsanız, animasyonun özelliği etkilemesini durdurmanız gerekir. Film şeridi animasyonları ile bunun için üç yolu vardır:  
  
-   Animasyonun ayarlamak <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği<xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   Tüm film şeridi kaldırın.  
  
-   Animasyonun tek tek özelliğinden kaldırın.  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>Animasyonun FillBehavior özelliğini durdurmaya ayarlayın  
 Ayarlayarak <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> için <xref:System.Windows.Media.Animation.FillBehavior.Stop>, etkin süresinin sonuna ulaştıktan sonra hedef özelliği etkilemeyi durdurmak için animasyon söyleyin.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>Tüm film şeridi Kaldır  
 Kullanarak bir <xref:System.Windows.Media.Animation.RemoveStoryboard> tetikleyici veya <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> yöntemi, hedef özellikleri etkilemeyi durdurmak için film şeridi animasyonları söyleyin. Bu yaklaşım ve ayar arasındaki farkı <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliktir film şeridi kaldırabilirsiniz, dilediğiniz zaman, while <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> özelliği yalnızca bir etkisi animasyon etkin süresinin sonuna ulaştığında.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>Animasyonun bir bireysel özellikten kaldırın  
 Animasyonun bir özelliği etkilemesini durdurmak için başka bir teknik kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> hareketli nesnesinin yöntemi. Özelliğin ilk parametre olarak belirtin ve `null` ikinci olarak.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 Bu teknik film şeridi olmayan animasyon için de çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Özellik Animasyon Tekniklerine Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
