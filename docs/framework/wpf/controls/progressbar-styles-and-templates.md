---
title: ProgressBar Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: f948cf2b4f4cd2a4cb73b0cd5fc754240c850b83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770532"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="d77e7-102">ProgressBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d77e7-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="d77e7-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.ProgressBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d77e7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="d77e7-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d77e7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d77e7-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d77e7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="d77e7-106">ProgressBar bölümleri</span><span class="sxs-lookup"><span data-stu-id="d77e7-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="d77e7-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.ProgressBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d77e7-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="d77e7-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="d77e7-108">Part</span></span>|<span data-ttu-id="d77e7-109">Tür</span><span class="sxs-lookup"><span data-stu-id="d77e7-109">Type</span></span>|<span data-ttu-id="d77e7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d77e7-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d77e7-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="d77e7-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d77e7-112">İlerleme durumunu gösteren nesne.</span><span class="sxs-lookup"><span data-stu-id="d77e7-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="d77e7-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="d77e7-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d77e7-114">İlerleme göstergesi yolunu tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="d77e7-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="d77e7-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="d77e7-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d77e7-116">İlerleme çubuğu embellishes bir nesne.</span><span class="sxs-lookup"><span data-stu-id="d77e7-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="d77e7-117">ProgressBar durumları</span><span class="sxs-lookup"><span data-stu-id="d77e7-117">ProgressBar States</span></span>  
 <span data-ttu-id="d77e7-118">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.ProgressBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d77e7-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="d77e7-119">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="d77e7-119">VisualState Name</span></span>|<span data-ttu-id="d77e7-120">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="d77e7-120">VisualStateGroup Name</span></span>|<span data-ttu-id="d77e7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d77e7-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="d77e7-122">Kararlı</span><span class="sxs-lookup"><span data-stu-id="d77e7-122">Determinate</span></span>|<span data-ttu-id="d77e7-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d77e7-123">CommonStates</span></span>|<span data-ttu-id="d77e7-124"><xref:System.Windows.Controls.ProgressBar> göre ilerleme raporlarınızı <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d77e7-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="d77e7-125">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="d77e7-125">Indeterminate</span></span>|<span data-ttu-id="d77e7-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d77e7-126">CommonStates</span></span>|<span data-ttu-id="d77e7-127"><xref:System.Windows.Controls.ProgressBar> Yinelenen bir desen ile genel ilerlemeyi raporlar.</span><span class="sxs-lookup"><span data-stu-id="d77e7-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="d77e7-128">Geçerli</span><span class="sxs-lookup"><span data-stu-id="d77e7-128">Valid</span></span>|<span data-ttu-id="d77e7-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d77e7-129">ValidationStates</span></span>|<span data-ttu-id="d77e7-130">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="d77e7-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d77e7-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d77e7-131">InvalidFocused</span></span>|<span data-ttu-id="d77e7-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d77e7-132">ValidationStates</span></span>|<span data-ttu-id="d77e7-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d77e7-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d77e7-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d77e7-134">InvalidUnfocused</span></span>|<span data-ttu-id="d77e7-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d77e7-135">ValidationStates</span></span>|<span data-ttu-id="d77e7-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d77e7-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="d77e7-137">ProgressBar ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="d77e7-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="d77e7-138">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ProgressBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d77e7-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="d77e7-139">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d77e7-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d77e7-140">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d77e7-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77e7-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d77e7-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d77e7-142">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d77e7-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d77e7-143">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d77e7-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d77e7-144">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d77e7-144">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="d77e7-145">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d77e7-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
