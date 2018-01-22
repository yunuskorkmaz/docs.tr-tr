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
ms.workload: dotnet
ms.openlocfilehash: 9d11c559679b67c22eeed87893bf2e362084034c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="93ba2-102">Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme</span><span class="sxs-lookup"><span data-stu-id="93ba2-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="93ba2-103">Bu örnek film şeridi animasyonları arasında iletim davranışı belirtmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="93ba2-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="93ba2-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Özelliği <xref:System.Windows.Media.Animation.BeginStoryboard> nasıl yeni bir animasyon belirtir bir özelliğe uygulanmış olan tüm varolanları etkileşim.</span><span class="sxs-lookup"><span data-stu-id="93ba2-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93ba2-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="93ba2-105">Example</span></span>  
 <span data-ttu-id="93ba2-106">Aşağıdaki örnek, fare imleci üzerine getirdiğinde büyütün ve imleci hemen taşındığında küçültülüyor iki düğme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93ba2-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="93ba2-107">Düğme üzerinde fare imleci hızlı bir şekilde kaldırmak, ikinci animasyon ilki bitmeden önce uygulanır.</span><span class="sxs-lookup"><span data-stu-id="93ba2-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="93ba2-108">Üst üste iki animasyon arasındaki farkı görebilirsiniz şuna benzer tutulduğunda <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> değerlerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> ve <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="93ba2-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="93ba2-109">Değerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> değerini sırasında bir animasyon arasında sorunsuz bir geçiş neden olan örtüşen animasyonları birleştirir <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> yeni animasyonun önceki çakışan animasyonu hemen değiştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="93ba2-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="93ba2-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93ba2-110">See Also</span></span>  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [<span data-ttu-id="93ba2-111">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="93ba2-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="93ba2-112">Animasyon ve zamanlama</span><span class="sxs-lookup"><span data-stu-id="93ba2-112">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="93ba2-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="93ba2-113">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
