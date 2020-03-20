---
title: 'Nasıl yapılır: Animasyonu Yineleme'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141555"
---
# <a name="how-to-repeat-an-animation"></a>Nasıl yapılır: Animasyonu Yineleme
Bu örnek, bir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> animasyonun <xref:System.Windows.Media.Animation.Timeline> yinelenen davranışını denetlemek için a özelliğinin nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> animasyonun basit süresini kaç kez yinelemeyi denetimleri özelliği. Kullanarak, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>belirli bir sayıda <xref:System.Windows.Media.Animation.Timeline> (yineleme sayısı) veya belirli bir süre için bir yineleme nin tekrarladığını belirtebilirsiniz. Her iki durumda da, animasyon istenen sayıyı veya süreyi doldurmak için ihtiyaç duyduğu sayıda baştan uç çalıştırmadan geçer.  
  
 Varsayılan olarak, zaman çizelgeleri 1.0 tekrar sayısına sahiptir, bu da bir kez oynadıkları ve yineledikleri anlamına gelir. Ancak, bir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> özelliği <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>ayarlarsanız, zaman çizelgesi süresiz olarak yinelenir.  
  
 Aşağıdaki örnek, bir animasyonun <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> yinelenen davranışını denetlemek için özelliğin nasıl kullanılacağını gösterir. Örnek, farklı bir <xref:System.Windows.FrameworkElement.Width%2A> yineleme davranışı türünü kullanarak her dikdörtgenle birlikte beş dikdörtgenin özelliğini animasyona dizer.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Tam örnek için [Animasyon Zamanlama Davranışı Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon Zamanlama Davranış Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
