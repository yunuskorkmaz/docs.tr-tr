---
title: 'Nasıl yapılır: Animasyonu Yineleme'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: a098c912289f59f8be48edeec0f066b7f94b9fda
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354013"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="1faa6-102">Nasıl yapılır: Animasyonu Yineleme</span><span class="sxs-lookup"><span data-stu-id="1faa6-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="1faa6-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> bir animasyonun yineleme davranışını denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="1faa6-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1faa6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1faa6-104">Example</span></span>  
 <span data-ttu-id="1faa6-105"><xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> animasyon yineler basit süresinin kaç kez denetler.</span><span class="sxs-lookup"><span data-stu-id="1faa6-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="1faa6-106">Kullanarak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, belirtebilirsiniz bir <xref:System.Windows.Media.Animation.Timeline> bir belirli sayıda yineler (yineleme sayısı) veya belirli bir süre için.</span><span class="sxs-lookup"><span data-stu-id="1faa6-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="1faa6-107">Her iki durumda da animasyon istenen sayı veya süresini doldurmak için gereken sayıda başına ve sonuna çalıştırır gider.</span><span class="sxs-lookup"><span data-stu-id="1faa6-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="1faa6-108">Varsayılan olarak, bir yineleme sayısını bir kez yürütmek ve Yineleme 1.0 zaman çizelgeleri sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1faa6-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="1faa6-109">Ancak ayarlarsanız <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> için <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, zaman çizelgesi süresiz olarak tekrarlar.</span><span class="sxs-lookup"><span data-stu-id="1faa6-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="1faa6-110">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> bir animasyonun yineleme davranışını denetlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="1faa6-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="1faa6-111">Örnek canlandırır <xref:System.Windows.FrameworkElement.Width%2A> beş farklı türde bir yineleme davranışı kullanarak her bir dikdörtgen dikdörtgenin özelliği.</span><span class="sxs-lookup"><span data-stu-id="1faa6-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="1faa6-112">Tam bir örnek için bkz. [animasyon zamanlama davranışı örneği](https://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="1faa6-112">For the complete sample, see [Animation Timing Behavior Sample](https://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1faa6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1faa6-113">See also</span></span>
- [<span data-ttu-id="1faa6-114">Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme</span><span class="sxs-lookup"><span data-stu-id="1faa6-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="1faa6-115">Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="1faa6-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="1faa6-116">Animasyon ve zamanlama ile ilgili nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="1faa6-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="1faa6-117">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="1faa6-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="1faa6-118">Animasyon zamanlama davranışı örneği</span><span class="sxs-lookup"><span data-stu-id="1faa6-118">Animation Timing Behavior Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159970)
