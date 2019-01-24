---
title: 'Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: 01c652e170e27da0be9b1ab5f7659d7089aee6f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677763"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="a9b21-102">Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme</span><span class="sxs-lookup"><span data-stu-id="a9b21-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="a9b21-103">Bu örnekte, görsel taslak animasyonları arasında iletim davranışı belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a9b21-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="a9b21-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Özelliği <xref:System.Windows.Media.Animation.BeginStoryboard> belirtir nasıl yeni bir özellik için zaten uygulanmış olan tüm mevcut vm'lere etkileşim.</span><span class="sxs-lookup"><span data-stu-id="a9b21-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9b21-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9b21-105">Example</span></span>  
 <span data-ttu-id="a9b21-106">Aşağıdaki örnek, fare imleci üzerine getirdiğinde büyütün ve işaretçiyi hemen taşır, daha küçük olur iki düğme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a9b21-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="a9b21-107">Bir düğmenin üzerine fare imleci hızlı bir şekilde kaldırmak, ilk tamamlanmadan önce ikinci animasyonun uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a9b21-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="a9b21-108">Bu arasındaki farkı gördüğünüz gibi üst üste iki animasyon <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> değerlerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> ve <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="a9b21-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="a9b21-109">Değerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> değerini animasyonlar arasında daha sorunsuz bir geçiş neden örtüşen animasyonlar birleştirir <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> hemen önceki çakışan animasyonu değiştirmek yeni animasyonu neden olur.</span><span class="sxs-lookup"><span data-stu-id="a9b21-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a9b21-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9b21-110">See also</span></span>
- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [<span data-ttu-id="a9b21-111">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="a9b21-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="a9b21-112">Animasyon ve zamanlama</span><span class="sxs-lookup"><span data-stu-id="a9b21-112">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="a9b21-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a9b21-113">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
