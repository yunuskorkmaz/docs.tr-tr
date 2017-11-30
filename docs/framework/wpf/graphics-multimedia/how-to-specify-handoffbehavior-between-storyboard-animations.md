---
title: "Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 323ea563aec7bc7ad0abec2372e3af977c7e38eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="b1f08-102">Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme</span><span class="sxs-lookup"><span data-stu-id="b1f08-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="b1f08-103">Bu örnek film şeridi animasyonları arasında iletim davranışı belirtmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f08-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="b1f08-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Özelliği <xref:System.Windows.Media.Animation.BeginStoryboard> nasıl yeni bir animasyon belirtir bir özelliğe uygulanmış olan tüm varolanları etkileşim.</span><span class="sxs-lookup"><span data-stu-id="b1f08-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1f08-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1f08-105">Example</span></span>  
 <span data-ttu-id="b1f08-106">Aşağıdaki örnek, fare imleci üzerine getirdiğinde büyütün ve imleci hemen taşındığında küçültülüyor iki düğme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1f08-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="b1f08-107">Düğme üzerinde fare imleci hızlı bir şekilde kaldırmak, ikinci animasyon ilki bitmeden önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b1f08-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="b1f08-108">Üst üste iki animasyon arasındaki farkı görebilirsiniz şuna benzer tutulduğunda <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> değerlerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> ve <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="b1f08-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="b1f08-109">Değerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> değerini sırasında bir animasyon arasında sorunsuz bir geçiş neden olan örtüşen animasyonları birleştirir <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> yeni animasyonun önceki çakışan animasyonu hemen değiştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="b1f08-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b1f08-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1f08-110">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [<span data-ttu-id="b1f08-111">Animasyon genel bakış</span><span class="sxs-lookup"><span data-stu-id="b1f08-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="b1f08-112">Animasyon ve zamanlama</span><span class="sxs-lookup"><span data-stu-id="b1f08-112">Animation and Timing</span></span>](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="b1f08-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b1f08-113">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
