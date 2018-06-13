---
title: 'Nasıl yapılır: Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 498aefa16b8a76262c01965b8992ef9a94b7ce28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560071"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a><span data-ttu-id="ce290-102">Nasıl yapılır: Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme</span><span class="sxs-lookup"><span data-stu-id="ce290-102">How to: Specify Whether a Timeline Automatically Reverses</span></span>
<span data-ttu-id="ce290-103">Bir zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği, ileriye doğru yineleme tamamlandıktan sonra geriye doğru çalar olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="ce290-103">A timeline's <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property determines whether it plays in reverse after it completes a forward iteration.</span></span> <span data-ttu-id="ce290-104">Aşağıdaki örnek, birkaç animasyon ile aynı süre ve hedef değerleri, ancak farklı gösterir <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ce290-104">The following example shows several animations with identical duration and target values, but with different <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> settings.</span></span> <span data-ttu-id="ce290-105">Göstermek için nasıl <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği ile farklı davranan <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ayarları, bazı animasyonları yinelenecek şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ce290-105">To demonstrate how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property behaves with different <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> settings, some animations are set to repeat.</span></span> <span data-ttu-id="ce290-106">Son animasyon gösterir nasıl <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği iç içe geçmiş zaman çizelgelerini üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="ce290-106">The last animation shows how the <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> property works on nested timelines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce290-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce290-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
