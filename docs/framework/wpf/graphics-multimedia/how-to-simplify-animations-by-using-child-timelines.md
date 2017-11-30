---
title: "Nasıl yapılır: Alt Öğe Zaman Çizelgelerini Kullanarak Animasyonları Basitleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: daa4caac0046293e8b86a773bfffd46cf30e835b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a><span data-ttu-id="5fe0f-102">Nasıl yapılır: Alt Öğe Zaman Çizelgelerini Kullanarak Animasyonları Basitleştirme</span><span class="sxs-lookup"><span data-stu-id="5fe0f-102">How to: Simplify Animations by Using Child Timelines</span></span>
<span data-ttu-id="5fe0f-103">Bu örnek alt kullanarak animasyonları basitleştirme gösterilmektedir <xref:System.Windows.Media.Animation.ParallelTimeline> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-103">This example shows how to simplify animations by using child <xref:System.Windows.Media.Animation.ParallelTimeline> objects.</span></span> <span data-ttu-id="5fe0f-104">A <xref:System.Windows.Media.Animation.Storyboard> bir tür <xref:System.Windows.Media.Animation.Timeline> içerdiği zaman çizelgeleri için hedefleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-104">A <xref:System.Windows.Media.Animation.Storyboard> is a type of <xref:System.Windows.Media.Animation.Timeline> that provides targeting information for the timelines it contains.</span></span> <span data-ttu-id="5fe0f-105">Kullanım bir <xref:System.Windows.Media.Animation.Storyboard> nesne ve özellik bilgileri de dahil olmak üzere, zaman çizelgesi hedeflemesi bilgilerini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-105">Use a <xref:System.Windows.Media.Animation.Storyboard> to provide timeline targeting information, including object and property information.</span></span>  
  
 <span data-ttu-id="5fe0f-106">Bir animasyon başlamak için bir veya daha fazla kullanın <xref:System.Windows.Media.Animation.ParallelTimeline> nesneleri iç içe alt öğeleri olarak bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-106">To begin an animation, use one or more <xref:System.Windows.Media.Animation.ParallelTimeline> objects as nested child elements of a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="5fe0f-107">Bunlar <xref:System.Windows.Media.Animation.ParallelTimeline> nesneleri diğer animasyonları içerebilir ve bu nedenle, karmaşık bir animasyon zamanlama sıralarında daha iyi yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-107">These <xref:System.Windows.Media.Animation.ParallelTimeline> objects can contain other animations and therefore, can better encapsulate the timing sequences in complex animations.</span></span> <span data-ttu-id="5fe0f-108">Örneğin, animasyonu yapıyorsanız bir <xref:System.Windows.Controls.TextBlock> ve aynı çeşitli şekillerde <xref:System.Windows.Media.Animation.Storyboard>, animasyonlarını ayırabilirsiniz <xref:System.Windows.Controls.TextBlock> ve her bir ayrı koyma şekiller <xref:System.Windows.Media.Animation.ParallelTimeline>.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-108">For example, if you are animating a <xref:System.Windows.Controls.TextBlock> and several shapes in the same <xref:System.Windows.Media.Animation.Storyboard>, you can separate the animations for the <xref:System.Windows.Controls.TextBlock> and the shapes, putting each into a separate <xref:System.Windows.Media.Animation.ParallelTimeline>.</span></span> <span data-ttu-id="5fe0f-109">Çünkü her <xref:System.Windows.Media.Animation.ParallelTimeline> kendi <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> ve tüm alt öğeleri <xref:System.Windows.Media.Animation.ParallelTimeline> bu göreli başlamak <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, zamanlama daha iyi kapsüllenir.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-109">Because each <xref:System.Windows.Media.Animation.ParallelTimeline> has its own <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> and all child elements of the <xref:System.Windows.Media.Animation.ParallelTimeline> begin relative to this <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, timing is better encapsulated.</span></span>  
  
 <span data-ttu-id="5fe0f-110">Aşağıdaki örnekte iki parça metin canlandırır (<xref:System.Windows.Controls.TextBlock> nesneler) gelen aynı içinde <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-110">The following example animates two pieces of text (<xref:System.Windows.Controls.TextBlock> objects) from within the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="5fe0f-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> birindeki animasyonları yalıtır <xref:System.Windows.Controls.TextBlock> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> encapsulates the animations of one of the <xref:System.Windows.Controls.TextBlock> objects.</span></span>  
  
 <span data-ttu-id="5fe0f-112">**Performans Not:** geçirebilmenize karşın <xref:System.Windows.Media.Animation.Storyboard> zaman çizelgelerini birbirlerine iç <xref:System.Windows.Media.Animation.ParallelTimeline>lar daha az ek yük gerektirdiğinden, iç içe geçme daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-112">**Performance Note:** Although you can nest <xref:System.Windows.Media.Animation.Storyboard> timelines inside each other, <xref:System.Windows.Media.Animation.ParallelTimeline>s are more suitable for nesting because they require less overhead.</span></span> <span data-ttu-id="5fe0f-113">( <xref:System.Windows.Media.Animation.Storyboard> Sınıfının devraldığı <xref:System.Windows.Media.Animation.ParallelTimeline> sınıfı.)</span><span class="sxs-lookup"><span data-stu-id="5fe0f-113">(The <xref:System.Windows.Media.Animation.Storyboard> class inherits from the <xref:System.Windows.Media.Animation.ParallelTimeline> class.)</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fe0f-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fe0f-114">Example</span></span>  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5fe0f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fe0f-115">See Also</span></span>  
 [<span data-ttu-id="5fe0f-116">Animasyon genel bakış</span><span class="sxs-lookup"><span data-stu-id="5fe0f-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="5fe0f-117">Film şeridi animasyonları arasında HandoffBehavior belirtin</span><span class="sxs-lookup"><span data-stu-id="5fe0f-117">Specify HandoffBehavior Between Storyboard Animations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
