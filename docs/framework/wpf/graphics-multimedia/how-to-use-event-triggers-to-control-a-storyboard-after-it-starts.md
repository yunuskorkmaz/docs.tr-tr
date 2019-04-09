---
title: 'Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: d444349f8bc9236e1d15f484f35b1326c77e2425
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170657"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="c1c51-102">Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c1c51-102">How to: Use Event Triggers to Control a Storyboard After It Starts</span></span>
<span data-ttu-id="c1c51-103">Bu örnek nasıl denetleneceğini gösterir bir <xref:System.Windows.Media.Animation.Storyboard> başladıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="c1c51-103">This example shows how to control a <xref:System.Windows.Media.Animation.Storyboard> after it starts.</span></span> <span data-ttu-id="c1c51-104">Başlamak için bir <xref:System.Windows.Media.Animation.Storyboard> kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullanın <xref:System.Windows.Media.Animation.BeginStoryboard>, nesneleri ve özellikleri animasyon ve görsel Taslak'ı başlatır animasyonları dağıtır.</span><span class="sxs-lookup"><span data-stu-id="c1c51-104">To start a <xref:System.Windows.Media.Animation.Storyboard> by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Media.Animation.BeginStoryboard>, which distributes the animations to the objects and properties they animate and then starts the storyboard.</span></span> <span data-ttu-id="c1c51-105">Size, <xref:System.Windows.Media.Animation.BeginStoryboard> bir ad belirterek, <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> özelliği yaptığınız, denetlenebilir bir film şeridi.</span><span class="sxs-lookup"><span data-stu-id="c1c51-105">If you give <xref:System.Windows.Media.Animation.BeginStoryboard> a name by specifying its <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> property, you make it a controllable storyboard.</span></span> <span data-ttu-id="c1c51-106">Başladıktan sonra görsel taslak ardından etkileşimli olarak denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1c51-106">You can then interactively control the storyboard after it starts.</span></span>  
  
 <span data-ttu-id="c1c51-107">Aşağıdaki görsel taslak eylemleri ile birlikte kullanmak <xref:System.Windows.EventTrigger> bir film şeridini denetlemek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c1c51-107">Use the following storyboard actions together with <xref:System.Windows.EventTrigger> objects to control a storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard><span data-ttu-id="c1c51-108">: Film duraklatılır.</span><span class="sxs-lookup"><span data-stu-id="c1c51-108">: Pauses the storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard><span data-ttu-id="c1c51-109">: Duraklatılmış bir film şeridini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="c1c51-109">: Resumes a paused storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio><span data-ttu-id="c1c51-110">: Görsel taslak hızını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c1c51-110">: Changes the storyboard speed.</span></span>  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill><span data-ttu-id="c1c51-111">: Varsa, bir görsel taslak dolgu süresinin sonuna ilerler.</span><span class="sxs-lookup"><span data-stu-id="c1c51-111">: Advances a storyboard to the end of its fill period, if it has one.</span></span>  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard><span data-ttu-id="c1c51-112">: Görsel taslak durdurur.</span><span class="sxs-lookup"><span data-stu-id="c1c51-112">: Stops the storyboard.</span></span>  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard><span data-ttu-id="c1c51-113">: Kaynakları boşaltma, film şeridi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c1c51-113">: Removes the storyboard, freeing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1c51-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1c51-114">Example</span></span>  
 <span data-ttu-id="c1c51-115">Aşağıdaki örnek, etkileşimli bir film şeridini denetlemek için denetlenebilir film şeridi eylemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1c51-115">The following example uses controllable storyboard actions to interactively control a storyboard.</span></span>  
  
 <span data-ttu-id="c1c51-116">**Not:** Kod kullanarak bir film şeridini denetlemek için bir örnek görmek için bkz: [bir görsel taslak sonra onu başlatır kullanarak kendi etkileşimli yöntemlerini denetlemesine](how-to-control-a-storyboard-after-it-starts.md).</span><span class="sxs-lookup"><span data-stu-id="c1c51-116">**Note:** To see an example of controlling a storyboard by using code, see [Control a Storyboard After It Starts Using Its Interactive Methods](how-to-control-a-storyboard-after-it-starts.md).</span></span>  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 <span data-ttu-id="c1c51-117">Diğer örnekler için [animasyon örnek Galerisi](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="c1c51-117">For additional examples, see the [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c51-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1c51-118">See also</span></span>

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [<span data-ttu-id="c1c51-119">Görsel Taslağı Başladıktan Sonra Etkileşimli Yöntemlerini Kullanarak Denetleme</span><span class="sxs-lookup"><span data-stu-id="c1c51-119">Control a Storyboard After It Starts Using Its Interactive Methods</span></span>](how-to-control-a-storyboard-after-it-starts.md)
- [<span data-ttu-id="c1c51-120">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="c1c51-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="c1c51-121">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c1c51-121">Storyboards Overview</span></span>](storyboards-overview.md)
