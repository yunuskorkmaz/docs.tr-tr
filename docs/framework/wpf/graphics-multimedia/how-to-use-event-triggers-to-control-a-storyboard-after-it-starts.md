---
title: 'Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: f31b1233f00147fdccde5e0816fa4839ae33d549
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183544"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="5eaa6-102">Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="5eaa6-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="5eaa6-103">Bu örnek nasıl denetleneceğini gösterir bir <xref:System.Windows.Media.Animation.Storyboard> başladıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="5eaa6-104">Başlamak için bir <xref:System.Windows.Media.Animation.Storyboard> kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullanın <xref:System.Windows.Media.Animation.BeginStoryboard>, nesneleri ve özellikleri animasyon ve görsel Taslak'ı başlatır animasyonları dağıtır.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="5eaa6-105">Size, <xref:System.Windows.Media.Animation.BeginStoryboard> bir ad belirterek, <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> özelliği yaptığınız, denetlenebilir bir film şeridi.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="5eaa6-106">Başladıktan sonra görsel taslak ardından etkileşimli olarak denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="5eaa6-107">Aşağıdaki görsel taslak eylemleri ile birlikte kullanmak <xref:System.Windows.EventTrigger> bir film şeridini denetlemek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <span data-ttu-id="5eaa6-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Film duraklatılır.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-108"><xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses the storyboard.</span></span>  
  
-   <span data-ttu-id="5eaa6-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış bir film şeridini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-109"><xref:System.Windows.Media.Animation.ResumeStoryboard>: Resumes a paused storyboard.</span></span>  
  
-   <span data-ttu-id="5eaa6-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Film şeridi hızını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-110"><xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Changes the storyboard speed.</span></span>  
  
-   <span data-ttu-id="5eaa6-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Bir görsel taslak dolgu süresinin sonuna varsa ilerler.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-111"><xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <span data-ttu-id="5eaa6-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Film şeridi durdurur.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-112"><xref:System.Windows.Media.Animation.StopStoryboard>: Stops the storyboard.</span></span>  
  
-   <span data-ttu-id="5eaa6-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Kaynakları boşaltma, film şeridini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-113"><xref:System.Windows.Media.Animation.RemoveStoryboard>: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5eaa6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5eaa6-114">Example</span></span>  
 <span data-ttu-id="5eaa6-115">Aşağıdaki örnek, etkileşimli bir film şeridini denetlemek için denetlenebilir film şeridi eylemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="5eaa6-116">**Not:** kod kullanarak bir film şeridini denetlemek için bir örnek görmek için bkz: [bir görsel taslak sonra onu başlatır kullanarak kendi etkileşimli yöntemlerini denetlemesine](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="5eaa6-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="5eaa6-117">Diğer örnekler için [animasyon örnek Galerisi](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="5eaa6-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eaa6-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5eaa6-118">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>  
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>  
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>  
 <xref:System.Windows.Media.Animation.PauseStoryboard>  
 <xref:System.Windows.Media.Animation.StopStoryboard>  
 <xref:System.Windows.Media.Animation.SeekStoryboard>  
 [<span data-ttu-id="5eaa6-119">Görsel Taslağı Başladıktan Sonra Etkileşimli Yöntemlerini Kullanarak Denetleme</span><span class="sxs-lookup"><span data-stu-id="5eaa6-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)  
 [<span data-ttu-id="5eaa6-120">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="5eaa6-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="5eaa6-121">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5eaa6-121">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
