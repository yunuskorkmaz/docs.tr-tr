---
title: 'Nasıl yapılır: Etkin Döneminin Sonuna Gelen Zaman Çizelgesi için FillBehavior Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141179"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Nasıl yapılır: Etkin Döneminin Sonuna Gelen Zaman Çizelgesi için FillBehavior Belirtme
Bu örnek, animasyonlu <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> bir özelliğin etkin olmayan <xref:System.Windows.Media.Animation.Timeline> için nasıl belirtilir gösterir.  
  
## <a name="example"></a>Örnek  
 Animasyonlu <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> olmadığında, yani etkin olmadığında ancak üst <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline> öğesi etkin veya bekleme süresinin içinde yken animasyonlu bir özelliğin değerine ne olacağını belirler. Örneğin, animasyon özelliği animasyon sona erdikten sonra bitiş değerinde mi kalır yoksa animasyon başlamadan önceki değerine geri mi döner?  
  
 Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimation> iki dikdörtgenin <xref:System.Windows.FrameworkElement.Width%2A> animasyonu için a kullanır. Her dikdörtgen farklı <xref:System.Windows.Media.Animation.Timeline> bir nesne kullanır.  
  
 Bir <xref:System.Windows.Media.Animation.Timeline> ayarlı bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.Stop>var , dikdörtgenin genişliği <xref:System.Windows.Media.Animation.Timeline> sona erdiğinde animasyonsuz değerine geri dönmek için neden olur. Diğer <xref:System.Windows.Media.Animation.Timeline> bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>var , hangi genişlik <xref:System.Windows.Media.Animation.Timeline> sona erdiğinde son değeri kalmasına neden olur.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Tam örnek için [Animasyon Örnek Galerisi'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)
