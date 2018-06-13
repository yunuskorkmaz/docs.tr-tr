---
title: 'Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 2407de5029007748de691a3020078b1241b02fd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561468"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="e17b2-102">Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetleme</span><span class="sxs-lookup"><span data-stu-id="e17b2-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="e17b2-103">Bu örnek kodu denetimi için kullanmayı gösterir bir <xref:System.Windows.Media.Animation.Storyboard> başladıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="e17b2-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="e17b2-104">Bir film şeridi denetlemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullanın <xref:System.Windows.Trigger> ve <xref:System.Windows.TriggerAction> nesneleri; Örneğin, bakın [bir film şeridi sonra başlar denetlemek için olay tetikleyicileri](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="e17b2-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="e17b2-105">Film şeridi başlatmak için kullandığınız kendi <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> hale getirmeyi ve film şeridi başlatır özellikleri film şeridi'nın animasyonları dağıtır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e17b2-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="e17b2-106">Film şeridi denetlenebilir yapmak için kullandığınız <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi ve belirtin **true** ikinci parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="e17b2-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="e17b2-107">Ardından, duraklatma, sürdürme, arama, durdurmak, hızlandırmak, veya film şeridi yavaş veya dolgu süresinin ilerletmek için film şeridi'nın etkileşimli yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e17b2-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="e17b2-108">Film şeridi'nın etkileşimli yöntemlerin listesi aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="e17b2-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
-   <span data-ttu-id="e17b2-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Film şeridi duraklatır.</span><span class="sxs-lookup"><span data-stu-id="e17b2-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="e17b2-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Duraklatılmış film şeridi sürdürür.</span><span class="sxs-lookup"><span data-stu-id="e17b2-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="e17b2-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Film şeridi'nın etkileşimli hızını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e17b2-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>  
  
-   <span data-ttu-id="e17b2-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Film şeridini belirtilen konuma götürür.</span><span class="sxs-lookup"><span data-stu-id="e17b2-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>  
  
-   <span data-ttu-id="e17b2-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Film şeridini belirtilen konuma götürür.</span><span class="sxs-lookup"><span data-stu-id="e17b2-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="e17b2-114">Farklı <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemi, bu işlem bir sonraki değer çizgilerinin önce işlenir.</span><span class="sxs-lookup"><span data-stu-id="e17b2-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
-   <span data-ttu-id="e17b2-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Varsa, film şeridi dolgu süresinin ilerler.</span><span class="sxs-lookup"><span data-stu-id="e17b2-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="e17b2-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Film şeridi durdurur.</span><span class="sxs-lookup"><span data-stu-id="e17b2-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="e17b2-117">Aşağıdaki örnekte, birkaç film şeridi yöntemi etkileşimli olarak film şeridi denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e17b2-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="e17b2-118">**Not:** olan tetikleyici kullanarak film şeridi denetlemeye yönelik bir örnek görmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [bir film şeridi sonra başlar denetlemek için olay tetikleyicileri kullanma](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="e17b2-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e17b2-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="e17b2-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e17b2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e17b2-120">See Also</span></span>  
 [<span data-ttu-id="e17b2-121">Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e17b2-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
