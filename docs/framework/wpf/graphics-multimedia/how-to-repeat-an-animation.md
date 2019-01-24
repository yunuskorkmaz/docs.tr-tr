---
title: 'Nasıl yapılır: Animasyonu Yineleme'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 213fca0796840ae87035be4f474cfdf4648460a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609650"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="b1db5-102">Nasıl yapılır: Animasyonu Yineleme</span><span class="sxs-lookup"><span data-stu-id="b1db5-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="b1db5-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> bir animasyonun yineleme davranışını denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="b1db5-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1db5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1db5-104">Example</span></span>  
 <span data-ttu-id="b1db5-105"><xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> animasyon yineler basit süresinin kaç kez denetler.</span><span class="sxs-lookup"><span data-stu-id="b1db5-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="b1db5-106">Kullanarak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, belirtebilirsiniz bir <xref:System.Windows.Media.Animation.Timeline> bir belirli sayıda yineler (yineleme sayısı) veya belirli bir süre için.</span><span class="sxs-lookup"><span data-stu-id="b1db5-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="b1db5-107">Her iki durumda da animasyon istenen sayı veya süresini doldurmak için gereken sayıda başına ve sonuna çalıştırır gider.</span><span class="sxs-lookup"><span data-stu-id="b1db5-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="b1db5-108">Varsayılan olarak, bir yineleme sayısını bir kez yürütmek ve Yineleme 1.0 zaman çizelgeleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b1db5-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="b1db5-109">Ancak ayarlarsanız <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> için <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, zaman çizelgesi süresiz olarak tekrarlar.</span><span class="sxs-lookup"><span data-stu-id="b1db5-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="b1db5-110">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> bir animasyonun yineleme davranışını denetlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="b1db5-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="b1db5-111">Örnek canlandırır <xref:System.Windows.FrameworkElement.Width%2A> beş farklı türde bir yineleme davranışı kullanarak her bir dikdörtgen dikdörtgenin özelliği.</span><span class="sxs-lookup"><span data-stu-id="b1db5-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="b1db5-112">Tam bir örnek için bkz. [animasyon zamanlama davranışı örneği](https://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="b1db5-112">For the complete sample, see [Animation Timing Behavior Sample](https://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1db5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1db5-113">See also</span></span>
- [<span data-ttu-id="b1db5-114">Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme</span><span class="sxs-lookup"><span data-stu-id="b1db5-114">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="b1db5-115">Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="b1db5-115">Specify Whether a Timeline Automatically Reverses</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="b1db5-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b1db5-116">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="b1db5-117">Animasyon ve zamanlama</span><span class="sxs-lookup"><span data-stu-id="b1db5-117">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="b1db5-118">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="b1db5-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="b1db5-119">Animasyon zamanlama davranışı örneği</span><span class="sxs-lookup"><span data-stu-id="b1db5-119">Animation Timing Behavior Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159970)
