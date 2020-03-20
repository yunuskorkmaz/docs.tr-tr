---
title: 'Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186709"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="f2afa-102">Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="f2afa-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>

<span data-ttu-id="f2afa-103">Bu örnek, bir <xref:System.Windows.Media.Animation.Storyboard> başlatıldıktan sonra nasıl denetler gösterin.</span><span class="sxs-lookup"><span data-stu-id="f2afa-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="f2afa-104">Animasyonları <xref:System.Windows.Media.Animation.Storyboard> animasyonlarına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve <xref:System.Windows.Media.Animation.BeginStoryboard>özelliklerine dağıtan ve sonra film şeridini başlatan , kullanarak bir başlangıç yapmak için.</span><span class="sxs-lookup"><span data-stu-id="f2afa-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="f2afa-105">Özelliğini <xref:System.Windows.Media.Animation.BeginStoryboard> belirterek <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> bir ad verirseniz, onu denetlenebilir bir film şeridi haline getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2afa-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="f2afa-106">Daha sonra başladıktan sonra film şeridini etkileşimli olarak denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2afa-106">You can then interactively control the storyboard after it starts.</span></span>

<span data-ttu-id="f2afa-107">Bir film şeridini denetlemek <xref:System.Windows.EventTrigger> için nesnelerle birlikte aşağıdaki film şeridi eylemlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2afa-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>

- <span data-ttu-id="f2afa-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Film şeridini duraklatabilir.</span><span class="sxs-lookup"><span data-stu-id="f2afa-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>

- <span data-ttu-id="f2afa-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış bir film şeridini devam ettirer.</span><span class="sxs-lookup"><span data-stu-id="f2afa-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="f2afa-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Film şeridi hızını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f2afa-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>

- <span data-ttu-id="f2afa-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Eğer varsa, bir film şeridini dolum süresinin sonuna kadar ilerletir.</span><span class="sxs-lookup"><span data-stu-id="f2afa-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>

- <span data-ttu-id="f2afa-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Hikaye şeridini durdurur.</span><span class="sxs-lookup"><span data-stu-id="f2afa-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>

- <span data-ttu-id="f2afa-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Film şeridini kaldırır, kaynakları serbest çehresini serbest klar.</span><span class="sxs-lookup"><span data-stu-id="f2afa-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>

## <a name="example"></a><span data-ttu-id="f2afa-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2afa-114">Example</span></span>

<span data-ttu-id="f2afa-115">Aşağıdaki örnek, bir film şeridini etkileşimli olarak denetlemek için denetlenebilir film şeridi eylemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2afa-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="f2afa-116">Kodu kullanarak bir film şeridini denetleme örneğini görmek için, [Etkileşimli Yöntemleri Kullanmaya Başladıktan Sonra Bir Film Şeridini Denetleme](how-to-control-a-storyboard-after-it-starts.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f2afa-116">To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

<span data-ttu-id="f2afa-117">Ek örnekler için [Animasyon Örnek Galerisi'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)bakın.</span><span class="sxs-lookup"><span data-stu-id="f2afa-117">For additional examples, see the [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2afa-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2afa-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="f2afa-119">Görsel Taslağı Başladıktan Sonra Etkileşimli Yöntemlerini Kullanarak Denetleme</span><span class="sxs-lookup"><span data-stu-id="f2afa-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="f2afa-120">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="f2afa-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="f2afa-121">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f2afa-121">Storyboards Overview</span></span>](storyboards-overview.md)
