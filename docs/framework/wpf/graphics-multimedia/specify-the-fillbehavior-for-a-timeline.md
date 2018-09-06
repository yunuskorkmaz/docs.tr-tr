---
title: 'Nasıl yapılır: Etkin Döneminin Sonuna Gelen Zaman Çizelgesi için FillBehavior Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: c88deeb679a3e8f2027d6bb2e817edc1ade5926d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748031"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="46197-102">Nasıl yapılır: Etkin Döneminin Sonuna Gelen Zaman Çizelgesi için FillBehavior Belirtme</span><span class="sxs-lookup"><span data-stu-id="46197-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="46197-103">Bu örnek nasıl belirtileceğini gösterir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> için etkin olmayan <xref:System.Windows.Media.Animation.Timeline> animasyonlu bir özelliği.</span><span class="sxs-lookup"><span data-stu-id="46197-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46197-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="46197-104">Example</span></span>  
 <span data-ttu-id="46197-105"><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> yok edilirken animasyonlu bir özelliğin değerini ne olacağını belirler, diğer bir deyişle, ne zaman animasyonlu <xref:System.Windows.Media.Animation.Timeline> üst etkin değil <xref:System.Windows.Media.Animation.Timeline> içinde etkin veya dönem.</span><span class="sxs-lookup"><span data-stu-id="46197-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="46197-106">Örneğin, bir animasyonlu özelliği sonuna kalır yoksa animasyon sona erer veya mevcut sonra değer animasyon başlamadan önceki değerine geri dönmek?</span><span class="sxs-lookup"><span data-stu-id="46197-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="46197-107">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon uygulamak için <xref:System.Windows.FrameworkElement.Width%2A> iki dikdörtgenlerin.</span><span class="sxs-lookup"><span data-stu-id="46197-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="46197-108">Her dikdörtgenin farklı bir kullanan <xref:System.Windows.Media.Animation.Timeline> nesne.</span><span class="sxs-lookup"><span data-stu-id="46197-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="46197-109">Bir <xref:System.Windows.Media.Animation.Timeline> sahip bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> ayarlanmış <xref:System.Windows.Media.Animation.FillBehavior.Stop>, geri kendi hareketli olmayan için dikdörtgenin genişliğini neden değeri <xref:System.Windows.Media.Animation.Timeline> sona erer.</span><span class="sxs-lookup"><span data-stu-id="46197-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="46197-110">Diğer <xref:System.Windows.Media.Animation.Timeline> sahip bir <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, genişliğin sonuna kalmasına neden değeri <xref:System.Windows.Media.Animation.Timeline> sona erer.</span><span class="sxs-lookup"><span data-stu-id="46197-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="46197-111">Tam bir örnek için bkz. [animasyon örnek Galerisi](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="46197-111">For the complete sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46197-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46197-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [<span data-ttu-id="46197-113">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="46197-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="46197-114">Animasyon ve zamanlama</span><span class="sxs-lookup"><span data-stu-id="46197-114">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="46197-115">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="46197-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
