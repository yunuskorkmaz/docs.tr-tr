---
title: 'Nasıl yapılır: Animasyonu Yineleme'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: b2281805b62d6d4e639524d9a0959b392006d003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-repeat-an-animation"></a>Nasıl yapılır: Animasyonu Yineleme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> animasyonun yineleme davranışını denetlemek için.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> animasyonun yineler basit süresinin kaç kez denetler. Kullanarak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, belirtebilirsiniz bir <xref:System.Windows.Media.Animation.Timeline> bir belirli sayıda yineler (yineleme sayısı) veya belirli bir süre için. Her iki durumda da animasyon, istenen sayı veya süresini doldurmak için gereken sayıda başına sonuna çalıştırır gider.  
  
 Varsayılan olarak, bunlar bir kez oynayacağı ve yineleniyor mu anlamına gelir 1.0 yineleme sayısını zaman çizelgelerini sahiptir. Ancak, ayarlarsanız <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> için <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, zaman çizelgesi süresiz olarak tekrarlar.  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> animasyonun yineleme davranışını denetlemek için özellik. Örnek canlandırır <xref:System.Windows.FrameworkElement.Width%2A> her dikdörtgen farklı tür yineleme davranışı kullanarak beş dikdörtgenin özelliği.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Tam bir örnek için bkz: [animasyon zamanlama davranışı örneği](http://go.microsoft.com/fwlink/?LinkID=159970).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Animasyon ve zamanlama](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animasyon zamanlama davranışı örneği](http://go.microsoft.com/fwlink/?LinkID=159970)
