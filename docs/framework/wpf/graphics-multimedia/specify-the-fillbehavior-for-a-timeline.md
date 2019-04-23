---
title: 'Nasıl yapılır: Etkin Döneminin Sonuna Gelen Zaman Çizelgesi için FillBehavior Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 9f03c5b8d4585c32e0a9f119649dd15a23523033
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091134"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Nasıl yapılır: Etkin Döneminin Sonuna Gelen Zaman Çizelgesi için FillBehavior Belirtme
Bu örnek nasıl belirtileceğini gösterir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> için etkin olmayan <xref:System.Windows.Media.Animation.Timeline> animasyonlu bir özelliği.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> yok edilirken animasyonlu bir özelliğin değerini ne olacağını belirler, diğer bir deyişle, ne zaman animasyonlu <xref:System.Windows.Media.Animation.Timeline> üst etkin değil <xref:System.Windows.Media.Animation.Timeline> içinde etkin veya dönem. Örneğin, bir animasyonlu özelliği sonuna kalır yoksa animasyon sona erer veya mevcut sonra değer animasyon başlamadan önceki değerine geri dönmek?  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon uygulamak için <xref:System.Windows.FrameworkElement.Width%2A> iki dikdörtgenlerin. Her dikdörtgenin farklı bir kullanan <xref:System.Windows.Media.Animation.Timeline> nesne.  
  
 Bir <xref:System.Windows.Media.Animation.Timeline> sahip bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> ayarlanmış <xref:System.Windows.Media.Animation.FillBehavior.Stop>, geri kendi hareketli olmayan için dikdörtgenin genişliğini neden değeri <xref:System.Windows.Media.Animation.Timeline> sona erer. Diğer <xref:System.Windows.Media.Animation.Timeline> sahip bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, genişliğin sonuna kalmasına neden değeri <xref:System.Windows.Media.Animation.Timeline> sona erer.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Tam bir örnek için bkz. [animasyon örnek Galerisi](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon ve zamanlama ile ilgili nasıl yapılır konuları](animation-and-timing-how-to-topics.md)
