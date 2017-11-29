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
ms.openlocfilehash: 475607381f16d7b42f26f12809a11d5eaf4e74bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="de775-102">ProgressBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="de775-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="de775-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="de775-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="de775-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="de775-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="de775-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="de775-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="de775-106">ProgressBar bölümleri</span><span class="sxs-lookup"><span data-stu-id="de775-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="de775-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="de775-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="de775-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="de775-108">Part</span></span>|<span data-ttu-id="de775-109">Tür</span><span class="sxs-lookup"><span data-stu-id="de775-109">Type</span></span>|<span data-ttu-id="de775-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de775-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="de775-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="de775-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="de775-112">İlerleme durumunu gösteren nesne.</span><span class="sxs-lookup"><span data-stu-id="de775-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="de775-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="de775-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="de775-114">İlerleme göstergesi yolunu tanımlayan nesnesi.</span><span class="sxs-lookup"><span data-stu-id="de775-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="de775-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="de775-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="de775-116">İlerleme çubuğu embellishes bir nesne.</span><span class="sxs-lookup"><span data-stu-id="de775-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="de775-117">ProgressBar durumları</span><span class="sxs-lookup"><span data-stu-id="de775-117">ProgressBar States</span></span>  
 <span data-ttu-id="de775-118">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="de775-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="de775-119">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="de775-119">VisualState Name</span></span>|<span data-ttu-id="de775-120">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="de775-120">VisualStateGroup Name</span></span>|<span data-ttu-id="de775-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de775-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="de775-122">Belirli</span><span class="sxs-lookup"><span data-stu-id="de775-122">Determinate</span></span>|<span data-ttu-id="de775-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="de775-123">CommonStates</span></span>|<span data-ttu-id="de775-124"><xref:System.Windows.Controls.ProgressBar>temel ilerleme raporları <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="de775-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="de775-125">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="de775-125">Indeterminate</span></span>|<span data-ttu-id="de775-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="de775-126">CommonStates</span></span>|<span data-ttu-id="de775-127"><xref:System.Windows.Controls.ProgressBar>Yinelenen bir desen ile genel ilerleme durumunu raporlar.</span><span class="sxs-lookup"><span data-stu-id="de775-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="de775-128">Geçerli</span><span class="sxs-lookup"><span data-stu-id="de775-128">Valid</span></span>|<span data-ttu-id="de775-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="de775-129">ValidationStates</span></span>|<span data-ttu-id="de775-130">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="de775-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="de775-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="de775-131">InvalidFocused</span></span>|<span data-ttu-id="de775-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="de775-132">ValidationStates</span></span>|<span data-ttu-id="de775-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="de775-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="de775-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="de775-134">InvalidUnfocused</span></span>|<span data-ttu-id="de775-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="de775-135">ValidationStates</span></span>|<span data-ttu-id="de775-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="de775-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="de775-137">ProgressBar ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="de775-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="de775-138">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ProgressBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="de775-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="de775-139">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="de775-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="de775-140">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="de775-140">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de775-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de775-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="de775-142">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="de775-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="de775-143">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="de775-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="de775-144">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="de775-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="de775-145">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="de775-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
