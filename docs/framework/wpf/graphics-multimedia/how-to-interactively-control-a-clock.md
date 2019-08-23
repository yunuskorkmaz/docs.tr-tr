---
title: 'Nasıl yapılır: Etkileşimli Olarak Saat Denetimi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 2d18f395974750a6b85458f636a27f6101e7978f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951341"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="1b928-102">Nasıl yapılır: Etkileşimli Olarak Saat Denetimi</span><span class="sxs-lookup"><span data-stu-id="1b928-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="1b928-103"><xref:System.Windows.Media.Animation.Clock> Bir<xref:System.Windows.Media.Animation.ClockController> nesnenin özelliği, etkileşimli olarak başlamasını, duraklatmanızı, devam ettirmenizi, arama süresini dolduracak ve saati durdurmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b928-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="1b928-104">Yalnızca bir zamanlama ağacının kök saati etkileşimli olarak denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="1b928-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1b928-105">Doğrudan saatlerle çalışmanıza gerek olmayan animasyonları etkileşimli olarak denetleyebilmeniz için başka yollar vardır: film şeritleri de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b928-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="1b928-106">Görsel Taslaklar hem biçimlendirme hem de kodda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1b928-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="1b928-107">Bir örnek için bkz. görsel taslak veya [animasyona genel bakış](animation-overview.md) [kullanarak bir özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md) .</span><span class="sxs-lookup"><span data-stu-id="1b928-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="1b928-108">Aşağıdaki örnekte, bir animasyon saatini etkileşimli olarak denetlemek için birkaç düğme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b928-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b928-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1b928-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="1b928-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b928-110">See also</span></span>

- [<span data-ttu-id="1b928-111">Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="1b928-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="1b928-112">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="1b928-112">Animation Overview</span></span>](animation-overview.md)
