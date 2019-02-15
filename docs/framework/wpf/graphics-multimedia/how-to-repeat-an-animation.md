---
title: 'Nasıl yapılır: Animasyonu Yineleme'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 358400c07ec2e96401d95929cbdd22784db630f9
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305148"
---
# <a name="how-to-repeat-an-animation"></a>Nasıl yapılır: Animasyonu Yineleme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> bir animasyonun yineleme davranışını denetlemek için.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> animasyon yineler basit süresinin kaç kez denetler. Kullanarak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, belirtebilirsiniz bir <xref:System.Windows.Media.Animation.Timeline> bir belirli sayıda yineler (yineleme sayısı) veya belirli bir süre için. Her iki durumda da animasyon istenen sayı veya süresini doldurmak için gereken sayıda başına ve sonuna çalıştırır gider.  
  
 Varsayılan olarak, bir yineleme sayısını bir kez yürütmek ve Yineleme 1.0 zaman çizelgeleri sahiptir. Ancak ayarlarsanız <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> için <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, zaman çizelgesi süresiz olarak tekrarlar.  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> bir animasyonun yineleme davranışını denetlemek için özellik. Örnek canlandırır <xref:System.Windows.FrameworkElement.Width%2A> beş farklı türde bir yineleme davranışı kullanarak her bir dikdörtgen dikdörtgenin özelliği.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Tam bir örnek için bkz. [animasyon zamanlama davranışı örneği](https://go.microsoft.com/fwlink/?LinkID=159970).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)
- [Animasyon ve zamanlama ile ilgili nasıl yapılır konuları](animation-and-timing-how-to-topics.md)
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Animasyon zamanlama davranışı örneği](https://go.microsoft.com/fwlink/?LinkID=159970)
