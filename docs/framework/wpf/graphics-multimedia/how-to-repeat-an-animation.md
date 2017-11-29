---
title: "Nasıl yapılır: Animasyonu Yineleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2f942771e01c2b7fae989f73779672edb8ba2f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="9fd59-102">Nasıl yapılır: Animasyonu Yineleme</span><span class="sxs-lookup"><span data-stu-id="9fd59-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="9fd59-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> animasyonun yineleme davranışını denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="9fd59-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fd59-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fd59-104">Example</span></span>  
 <span data-ttu-id="9fd59-105"><xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Özelliği bir <xref:System.Windows.Media.Animation.Timeline> animasyonun yineler basit süresinin kaç kez denetler.</span><span class="sxs-lookup"><span data-stu-id="9fd59-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="9fd59-106">Kullanarak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, belirtebilirsiniz bir <xref:System.Windows.Media.Animation.Timeline> bir belirli sayıda yineler (yineleme sayısı) veya belirli bir süre için.</span><span class="sxs-lookup"><span data-stu-id="9fd59-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="9fd59-107">Her iki durumda da animasyon, istenen sayı veya süresini doldurmak için gereken sayıda başına sonuna çalıştırır gider.</span><span class="sxs-lookup"><span data-stu-id="9fd59-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="9fd59-108">Varsayılan olarak, bunlar bir kez oynayacağı ve yineleniyor mu anlamına gelir 1.0 yineleme sayısını zaman çizelgelerini sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9fd59-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="9fd59-109">Ancak, ayarlarsanız <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> özelliği bir <xref:System.Windows.Media.Animation.Timeline> için <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, zaman çizelgesi süresiz olarak tekrarlar.</span><span class="sxs-lookup"><span data-stu-id="9fd59-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="9fd59-110">Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> animasyonun yineleme davranışını denetlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="9fd59-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="9fd59-111">Örnek canlandırır <xref:System.Windows.FrameworkElement.Width%2A> her dikdörtgen farklı tür yineleme davranışı kullanarak beş dikdörtgenin özelliği.</span><span class="sxs-lookup"><span data-stu-id="9fd59-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="9fd59-112">Tam bir örnek için bkz: [animasyon zamanlama davranışı örneği](http://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="9fd59-112">For the complete sample, see [Animation Timing Behavior Sample](http://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd59-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fd59-113">See Also</span></span>  
 [<span data-ttu-id="9fd59-114">Yineleme döngüsü sırasında animasyon değerlerini accumulate</span><span class="sxs-lookup"><span data-stu-id="9fd59-114">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [<span data-ttu-id="9fd59-115">Bir zaman çizelgesi otomatik olarak ters çevrilip çevrilmeyeceğini belirleme</span><span class="sxs-lookup"><span data-stu-id="9fd59-115">Specify Whether a Timeline Automatically Reverses</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [<span data-ttu-id="9fd59-116">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9fd59-116">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [<span data-ttu-id="9fd59-117">Animasyon ve zamanlama</span><span class="sxs-lookup"><span data-stu-id="9fd59-117">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="9fd59-118">Animasyon genel bakış</span><span class="sxs-lookup"><span data-stu-id="9fd59-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="9fd59-119">Animasyon zamanlama davranışı örneği</span><span class="sxs-lookup"><span data-stu-id="9fd59-119">Animation Timing Behavior Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159970)
