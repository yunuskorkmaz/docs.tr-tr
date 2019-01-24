---
title: 'Nasıl yapılır: Etkin Döneminin Sonuna Gelen Zaman Çizelgesi için FillBehavior Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 6745cf5d57a341068e93784d5487f21e34f8a64a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530114"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Nasıl yapılır: Etkin Döneminin Sonuna Gelen Zaman Çizelgesi için FillBehavior Belirtme
Bu örnek nasıl belirtileceğini gösterir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> için etkin olmayan <xref:System.Windows.Media.Animation.Timeline> animasyonlu bir özelliği.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> yok edilirken animasyonlu bir özelliğin değerini ne olacağını belirler, diğer bir deyişle, ne zaman animasyonlu <xref:System.Windows.Media.Animation.Timeline> üst etkin değil <xref:System.Windows.Media.Animation.Timeline> içinde etkin veya dönem. Örneğin, bir animasyonlu özelliği sonuna kalır yoksa animasyon sona erer veya mevcut sonra değer animasyon başlamadan önceki değerine geri dönmek?  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon uygulamak için <xref:System.Windows.FrameworkElement.Width%2A> iki dikdörtgenlerin. Her dikdörtgenin farklı bir kullanan <xref:System.Windows.Media.Animation.Timeline> nesne.  
  
 Bir <xref:System.Windows.Media.Animation.Timeline> sahip bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> ayarlanmış <xref:System.Windows.Media.Animation.FillBehavior.Stop>, geri kendi hareketli olmayan için dikdörtgenin genişliğini neden değeri <xref:System.Windows.Media.Animation.Timeline> sona erer. Diğer <xref:System.Windows.Media.Animation.Timeline> sahip bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, genişliğin sonuna kalmasına neden değeri <xref:System.Windows.Media.Animation.Timeline> sona erer.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Tam bir örnek için bkz. [animasyon örnek Galerisi](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Animasyon ve zamanlama](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
