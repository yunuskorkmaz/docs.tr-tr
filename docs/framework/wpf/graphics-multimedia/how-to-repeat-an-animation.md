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
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="30b29-102">Nasıl yapılır: Animasyonu Yineleme</span><span class="sxs-lookup"><span data-stu-id="30b29-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="30b29-103">Bu örnek, bir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> animasyonun <xref:System.Windows.Media.Animation.Timeline> yinelenen davranışını denetlemek için a özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="30b29-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30b29-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="30b29-104">Example</span></span>  
 <span data-ttu-id="30b29-105">Bir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> animasyonun basit süresini kaç kez yinelemeyi denetimleri özelliği.</span><span class="sxs-lookup"><span data-stu-id="30b29-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="30b29-106">Kullanarak, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>belirli bir sayıda <xref:System.Windows.Media.Animation.Timeline> (yineleme sayısı) veya belirli bir süre için bir yineleme nin tekrarladığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30b29-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="30b29-107">Her iki durumda da, animasyon istenen sayıyı veya süreyi doldurmak için ihtiyaç duyduğu sayıda baştan uç çalıştırmadan geçer.</span><span class="sxs-lookup"><span data-stu-id="30b29-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="30b29-108">Varsayılan olarak, zaman çizelgeleri 1.0 tekrar sayısına sahiptir, bu da bir kez oynadıkları ve yineledikleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="30b29-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="30b29-109">Ancak, bir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> özelliği <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>ayarlarsanız, zaman çizelgesi süresiz olarak yinelenir.</span><span class="sxs-lookup"><span data-stu-id="30b29-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="30b29-110">Aşağıdaki örnek, bir animasyonun <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> yinelenen davranışını denetlemek için özelliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="30b29-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="30b29-111">Örnek, farklı bir <xref:System.Windows.FrameworkElement.Width%2A> yineleme davranışı türünü kullanarak her dikdörtgenle birlikte beş dikdörtgenin özelliğini animasyona dizer.</span><span class="sxs-lookup"><span data-stu-id="30b29-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="30b29-112">Tam örnek için [Animasyon Zamanlama Davranışı Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)bakın.</span><span class="sxs-lookup"><span data-stu-id="30b29-112">For the complete sample, see [Animation Timing Behavior Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b29-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30b29-113">See also</span></span>

- [<span data-ttu-id="30b29-114">Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme</span><span class="sxs-lookup"><span data-stu-id="30b29-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="30b29-115">Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="30b29-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="30b29-116">Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="30b29-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="30b29-117">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="30b29-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="30b29-118">Animasyon Zamanlama Davranış Örneği</span><span class="sxs-lookup"><span data-stu-id="30b29-118">Animation Timing Behavior Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
