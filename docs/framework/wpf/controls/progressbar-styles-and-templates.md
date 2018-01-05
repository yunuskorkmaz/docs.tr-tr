---
title: "ProgressBar Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6809ce2f51af8a1baf535afa8fe80f4e5b5f53e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="d8f00-102">ProgressBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d8f00-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="d8f00-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="d8f00-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="d8f00-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="d8f00-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d8f00-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d8f00-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="d8f00-106">ProgressBar bölümleri</span><span class="sxs-lookup"><span data-stu-id="d8f00-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="d8f00-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="d8f00-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="d8f00-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="d8f00-108">Part</span></span>|<span data-ttu-id="d8f00-109">Tür</span><span class="sxs-lookup"><span data-stu-id="d8f00-109">Type</span></span>|<span data-ttu-id="d8f00-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8f00-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d8f00-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="d8f00-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d8f00-112">İlerleme durumunu gösteren nesne.</span><span class="sxs-lookup"><span data-stu-id="d8f00-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="d8f00-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="d8f00-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d8f00-114">İlerleme göstergesi yolunu tanımlayan nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d8f00-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="d8f00-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="d8f00-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d8f00-116">İlerleme çubuğu embellishes bir nesne.</span><span class="sxs-lookup"><span data-stu-id="d8f00-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="d8f00-117">ProgressBar durumları</span><span class="sxs-lookup"><span data-stu-id="d8f00-117">ProgressBar States</span></span>  
 <span data-ttu-id="d8f00-118">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="d8f00-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="d8f00-119">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="d8f00-119">VisualState Name</span></span>|<span data-ttu-id="d8f00-120">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="d8f00-120">VisualStateGroup Name</span></span>|<span data-ttu-id="d8f00-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8f00-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="d8f00-122">Belirli</span><span class="sxs-lookup"><span data-stu-id="d8f00-122">Determinate</span></span>|<span data-ttu-id="d8f00-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d8f00-123">CommonStates</span></span>|<span data-ttu-id="d8f00-124"><xref:System.Windows.Controls.ProgressBar>temel ilerleme raporları <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8f00-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="d8f00-125">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="d8f00-125">Indeterminate</span></span>|<span data-ttu-id="d8f00-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d8f00-126">CommonStates</span></span>|<span data-ttu-id="d8f00-127"><xref:System.Windows.Controls.ProgressBar>Yinelenen bir desen ile genel ilerleme durumunu raporlar.</span><span class="sxs-lookup"><span data-stu-id="d8f00-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="d8f00-128">Geçerli</span><span class="sxs-lookup"><span data-stu-id="d8f00-128">Valid</span></span>|<span data-ttu-id="d8f00-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d8f00-129">ValidationStates</span></span>|<span data-ttu-id="d8f00-130">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="d8f00-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d8f00-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d8f00-131">InvalidFocused</span></span>|<span data-ttu-id="d8f00-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d8f00-132">ValidationStates</span></span>|<span data-ttu-id="d8f00-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d8f00-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d8f00-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d8f00-134">InvalidUnfocused</span></span>|<span data-ttu-id="d8f00-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d8f00-135">ValidationStates</span></span>|<span data-ttu-id="d8f00-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d8f00-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="d8f00-137">ProgressBar ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="d8f00-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="d8f00-138">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="d8f00-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="d8f00-139">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8f00-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d8f00-140">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="d8f00-140">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f00-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8f00-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d8f00-142">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d8f00-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d8f00-143">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d8f00-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d8f00-144">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d8f00-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d8f00-145">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d8f00-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
