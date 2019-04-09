---
title: 'Nasıl yapılır: Görsel taslağı başladıktan sonra denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 107391386dfbb718f9436d9a039b08439fbc3279
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161492"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="d121f-102">Nasıl yapılır: Görsel taslağı başladıktan sonra denetleme</span><span class="sxs-lookup"><span data-stu-id="d121f-102">How to: Control a Storyboard After It Starts</span></span>
<span data-ttu-id="d121f-103">Bu örnek kod denetimine kullanmayı gösterir bir <xref:System.Windows.Media.Animation.Storyboard> başlatıldıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="d121f-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="d121f-104">İçinde bir film şeridini denetlemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullanın <xref:System.Windows.Trigger> ve <xref:System.Windows.TriggerAction> nesneleri; Örneğin, bkz [bir film şeridini denetlemek için olay tetikleyicilerini](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="d121f-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 <span data-ttu-id="d121f-105">Görsel taslağı'nı başlatmak için kullandığınız kendi <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi şeridinin animasyonları özelliklerine animasyon ve görsel taslak başlar dağıtır.</span><span class="sxs-lookup"><span data-stu-id="d121f-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>  
  
 <span data-ttu-id="d121f-106">Bir film şeridi denetlenebilir yapmak için kullanmanız <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi belirtin **true** ikinci parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="d121f-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="d121f-107">Ardından, duraklatma, sürdürme, arama, Durdur, hızlandırmak, veya film şeridini yavaşlatma veya dolgu süresinin ilerleyin şeridinin etkileşimli yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d121f-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="d121f-108">Görsel Taslak'ın etkileşimli yöntemlerin listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d121f-108">The following is a list of the storyboard's interactive methods:</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A><span data-ttu-id="d121f-109">: Film duraklatılır.</span><span class="sxs-lookup"><span data-stu-id="d121f-109">: Pauses the storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A><span data-ttu-id="d121f-110">: Duraklatılmış bir film şeridini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="d121f-110">: Resumes a paused storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A><span data-ttu-id="d121f-111">: Şeridinin etkileşimli hızını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d121f-111">: Sets the storyboard's interactive speed.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A><span data-ttu-id="d121f-112">: Görsel taslak belirtilen konumda arar.</span><span class="sxs-lookup"><span data-stu-id="d121f-112">: Seeks the storyboard the specified location.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A><span data-ttu-id="d121f-113">: Belirtilen konum film şeridini götürür.</span><span class="sxs-lookup"><span data-stu-id="d121f-113">: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="d121f-114">Farklı <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemi, bu işlem, sonraki değer çizgisi önce işlenir.</span><span class="sxs-lookup"><span data-stu-id="d121f-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A><span data-ttu-id="d121f-115">: Varsa film şeridini dolgu süresinin ilerler.</span><span class="sxs-lookup"><span data-stu-id="d121f-115">: Advances the storyboard to its fill period, if it has one.</span></span>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A><span data-ttu-id="d121f-116">: Görsel taslak durdurur.</span><span class="sxs-lookup"><span data-stu-id="d121f-116">: Stops the storyboard.</span></span>  
  
 <span data-ttu-id="d121f-117">Aşağıdaki örnekte, birkaç film şeridi yöntemi, etkileşimli bir film şeridini denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d121f-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="d121f-118">**Not:** Tetikleyicilerle kullanma film şeridini denetlemek için bir örnek görmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [bir film şeridini denetlemek için olay tetikleyicileri kullanma](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="d121f-118">**Note:** To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d121f-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d121f-119">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d121f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d121f-120">See also</span></span>

- [<span data-ttu-id="d121f-121">Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="d121f-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
