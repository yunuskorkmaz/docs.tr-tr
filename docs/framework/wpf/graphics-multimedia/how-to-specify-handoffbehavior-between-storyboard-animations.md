---
title: 'Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: d7129d6a48bdf31dc4953bb450267ad3b38fdd17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083887"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a><span data-ttu-id="9d5e0-102">Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme</span><span class="sxs-lookup"><span data-stu-id="9d5e0-102">How to: Specify HandoffBehavior Between Storyboard Animations</span></span>
<span data-ttu-id="9d5e0-103">Bu örnekte, görsel taslak animasyonları arasında iletim davranışı belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9d5e0-103">This example shows how to specify handoff behavior between storyboard animations.</span></span> <span data-ttu-id="9d5e0-104"><xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Özelliği <xref:System.Windows.Media.Animation.BeginStoryboard> belirtir nasıl yeni bir özellik için zaten uygulanmış olan tüm mevcut vm'lere etkileşim.</span><span class="sxs-lookup"><span data-stu-id="9d5e0-104">The <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> property of <xref:System.Windows.Media.Animation.BeginStoryboard> specifies how new animations interact with any existing ones that are already applied to a property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d5e0-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d5e0-105">Example</span></span>  
 <span data-ttu-id="9d5e0-106">Aşağıdaki örnek, fare imleci üzerine getirdiğinde büyütün ve işaretçiyi hemen taşır, daha küçük olur iki düğme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d5e0-106">The following example creates two buttons that enlarge when the mouse cursor moves over them and become smaller when the cursor moves away.</span></span> <span data-ttu-id="9d5e0-107">Bir düğmenin üzerine fare imleci hızlı bir şekilde kaldırmak, ilk tamamlanmadan önce ikinci animasyonun uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9d5e0-107">If you mouse over a button and then quickly remove the cursor, the second animation will be applied before the first one is finished.</span></span> <span data-ttu-id="9d5e0-108">Bu arasındaki farkı gördüğünüz gibi üst üste iki animasyon <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> değerlerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> ve <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span><span class="sxs-lookup"><span data-stu-id="9d5e0-108">It is when two animations overlap like this that you can see the difference between the <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> values of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> and <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>.</span></span> <span data-ttu-id="9d5e0-109">Değerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> değerini animasyonlar arasında daha sorunsuz bir geçiş neden örtüşen animasyonlar birleştirir <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> hemen önceki çakışan animasyonu değiştirmek yeni animasyonu neden olur.</span><span class="sxs-lookup"><span data-stu-id="9d5e0-109">A value of <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> combines the overlapping animations causing a smoother transition between animations while a value of <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> causes the new animation to immediately replace the earlier overlapping animation.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9d5e0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d5e0-110">See also</span></span>

- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [<span data-ttu-id="9d5e0-111">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="9d5e0-111">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="9d5e0-112">Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9d5e0-112">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
