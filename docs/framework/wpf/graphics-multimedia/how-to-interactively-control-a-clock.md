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
ms.openlocfilehash: 05989b6a03e03fb5723a70c9c36d5e32f9117049
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186595"
---
# <a name="how-to-interactively-control-a-clock"></a><span data-ttu-id="9a3d3-102">Nasıl yapılır: Etkileşimli Olarak Saat Denetimi</span><span class="sxs-lookup"><span data-stu-id="9a3d3-102">How to: Interactively Control a Clock</span></span>
<span data-ttu-id="9a3d3-103">A <xref:System.Windows.Media.Animation.Clock> nesnenin <xref:System.Windows.Media.Animation.ClockController> özelliği etkileşimli olarak başlatın, duraklatma, sürdürme, arama, dolgu süresinin ilerletme ve saati olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a3d3-103">A <xref:System.Windows.Media.Animation.Clock> object's <xref:System.Windows.Media.Animation.ClockController> property enables you to interactively start, pause, resume, seek, advance the clock to its fill period, and stop the clock.</span></span> <span data-ttu-id="9a3d3-104">Yalnızca kök saatin zamanlama ağacının etkileşimli olarak denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="9a3d3-104">Only the root clock of a timing tree can be interactively controlled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a3d3-105">Etkileşimli olarak doğrudan saatlerle çalışmanızı gerektirmeyen denetim animasyonlar farklı yöntemleri vardır: film şeridi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a3d3-105">There are other ways to interactively control animations that don't require you to work directly with clocks: you can also use Storyboards.</span></span> <span data-ttu-id="9a3d3-106">Görsel Taslaklar işaretleme ve kod desteklenir.</span><span class="sxs-lookup"><span data-stu-id="9a3d3-106">Storyboards are supported in both markup and code.</span></span> <span data-ttu-id="9a3d3-107">Bir örnek için bkz. [görsel taslak kullanarak özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md) veya [animasyona genel bakış](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9a3d3-107">For an example, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md) or the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="9a3d3-108">Aşağıdaki örnekte, çeşitli düğmeler, etkileşimli bir animasyon saat denetimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a3d3-108">In the following example, several buttons are used to interactively control an animation clock.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a3d3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a3d3-109">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="9a3d3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a3d3-110">See also</span></span>

- [<span data-ttu-id="9a3d3-111">Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="9a3d3-111">Animate a Property by Using a Storyboard</span></span>](how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="9a3d3-112">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="9a3d3-112">Animation Overview</span></span>](animation-overview.md)
