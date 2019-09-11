---
title: 'Nasıl yapılır: Görsel Taslağı başladıktan sonra denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855870"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="4a7f3-102">Nasıl yapılır: Görsel Taslağı başladıktan sonra denetleme</span><span class="sxs-lookup"><span data-stu-id="4a7f3-102">How to: Control a Storyboard After It Starts</span></span>

<span data-ttu-id="4a7f3-103">Bu örnek, başlatıldıktan sonra bir <xref:System.Windows.Media.Animation.Storyboard> nasıl kontrol etmek için kodun nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="4a7f3-104">İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir film şeridini denetlemek için ve <xref:System.Windows.Trigger> <xref:System.Windows.TriggerAction> nesneleri kullanın; bir örnek için bkz. [bir film şeridini başladıktan sonra denetlemek için olay tetikleyicilerini kullanma](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="4a7f3-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

<span data-ttu-id="4a7f3-105">Görsel Taslağı başlatmak için, film şeridinin animasyonlarını <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> canlandırdıkları özelliklere dağıtan ve film şeridini Başlatan yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>

<span data-ttu-id="4a7f3-106">Bir film şeridini denetlenebilir yapmak için <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemini kullanın ve ikinci parametre olarak **true değerini** belirtin.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="4a7f3-107">Daha sonra görsel taslağın etkileşimli yöntemlerini kullanarak film şeridini duraklatabilir, sürdürebilir, arayabilir, durdurabilir, hızlandıramaz veya yavaşlatabilir ya da bunu kendi Fill dönemine ilerletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="4a7f3-108">Görsel taslağın etkileşimli yöntemlerinin bir listesi aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4a7f3-108">The following is a list of the storyboard's interactive methods:</span></span>

- <span data-ttu-id="4a7f3-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Film şeridini duraklatır.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>

- <span data-ttu-id="4a7f3-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Duraklatılmış bir film şeridini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="4a7f3-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Görsel taslağın etkileşimli hızını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>

- <span data-ttu-id="4a7f3-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Film şeridini belirtilen konumu arar.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>

- <span data-ttu-id="4a7f3-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Görsel Taslağı belirtilen konuma arar.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="4a7f3-114"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A> Yönteminden farklı olarak, bu işlem sonraki Tick 'ten önce işlenir.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>

- <span data-ttu-id="4a7f3-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Film şeridini, varsa, kendi Fill dönemine ilerletir.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>

- <span data-ttu-id="4a7f3-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Film şeridini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>

<span data-ttu-id="4a7f3-117">Aşağıdaki örnekte, bir görsel taslağı etkileşimli olarak denetlemek için çeşitli görsel taslak yöntemleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="4a7f3-118">İle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Tetikleyicileri kullanarak bir film şeridini denetlemeye ilişkin bir örnek görmek için bkz. [bir film şeridini başladıktan sonra denetlemek için olay tetikleyicilerini kullanma](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="4a7f3-118">To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

## <a name="example"></a><span data-ttu-id="4a7f3-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a7f3-119">Example</span></span>

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a><span data-ttu-id="4a7f3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a7f3-120">See also</span></span>

- [<span data-ttu-id="4a7f3-121">Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="4a7f3-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
