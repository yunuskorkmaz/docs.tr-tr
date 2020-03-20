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
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="52c21-102">Nasıl yapılır: Etkin Döneminin Sonuna Gelen Zaman Çizelgesi için FillBehavior Belirtme</span><span class="sxs-lookup"><span data-stu-id="52c21-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="52c21-103">Bu örnek, animasyonlu <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> bir özelliğin etkin olmayan <xref:System.Windows.Media.Animation.Timeline> için nasıl belirtilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="52c21-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52c21-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="52c21-104">Example</span></span>  
 <span data-ttu-id="52c21-105">Animasyonlu <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> olmadığında, yani etkin olmadığında ancak üst <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline> öğesi etkin veya bekleme süresinin içinde yken animasyonlu bir özelliğin değerine ne olacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="52c21-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="52c21-106">Örneğin, animasyon özelliği animasyon sona erdikten sonra bitiş değerinde mi kalır yoksa animasyon başlamadan önceki değerine geri mi döner?</span><span class="sxs-lookup"><span data-stu-id="52c21-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="52c21-107">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimation> iki dikdörtgenin <xref:System.Windows.FrameworkElement.Width%2A> animasyonu için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="52c21-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="52c21-108">Her dikdörtgen farklı <xref:System.Windows.Media.Animation.Timeline> bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="52c21-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="52c21-109">Bir <xref:System.Windows.Media.Animation.Timeline> ayarlı bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.Stop>var , dikdörtgenin genişliği <xref:System.Windows.Media.Animation.Timeline> sona erdiğinde animasyonsuz değerine geri dönmek için neden olur.</span><span class="sxs-lookup"><span data-stu-id="52c21-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="52c21-110">Diğer <xref:System.Windows.Media.Animation.Timeline> bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>var , hangi genişlik <xref:System.Windows.Media.Animation.Timeline> sona erdiğinde son değeri kalmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="52c21-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="52c21-111">Tam örnek için [Animasyon Örnek Galerisi'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)bakın.</span><span class="sxs-lookup"><span data-stu-id="52c21-111">For the complete sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c21-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52c21-112">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="52c21-113">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="52c21-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="52c21-114">Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="52c21-114">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
