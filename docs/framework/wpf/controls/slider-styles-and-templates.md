---
title: "Kaydırıcı Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9ffbc5d2aa6e401dffb06f1695a5299a99ef90a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="d366b-102">Kaydırıcı Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d366b-102">Slider Styles and Templates</span></span>
<span data-ttu-id="d366b-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Slider> denetim.</span><span class="sxs-lookup"><span data-stu-id="d366b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="d366b-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="d366b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d366b-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d366b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="d366b-106">Kaydırıcı bölümleri</span><span class="sxs-lookup"><span data-stu-id="d366b-106">Slider Parts</span></span>  
 <span data-ttu-id="d366b-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Slider> denetim.</span><span class="sxs-lookup"><span data-stu-id="d366b-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="d366b-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="d366b-108">Part</span></span>|<span data-ttu-id="d366b-109">Tür</span><span class="sxs-lookup"><span data-stu-id="d366b-109">Type</span></span>|<span data-ttu-id="d366b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d366b-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d366b-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="d366b-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="d366b-112">Kapsayıcı konumunu gösterir öğesinin <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="d366b-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="d366b-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="d366b-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d366b-114">Seçim aralığı boyunca görüntüler öğesi <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="d366b-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="d366b-115">Seçim aralığı görülebilir yalnızca <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="d366b-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="d366b-116">Kaydırıcı durumları</span><span class="sxs-lookup"><span data-stu-id="d366b-116">Slider States</span></span>  
 <span data-ttu-id="d366b-117">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Slider> denetim.</span><span class="sxs-lookup"><span data-stu-id="d366b-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="d366b-118">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="d366b-118">VisualState Name</span></span>|<span data-ttu-id="d366b-119">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="d366b-119">VisualStateGroup Name</span></span>|<span data-ttu-id="d366b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d366b-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="d366b-121">Normal</span><span class="sxs-lookup"><span data-stu-id="d366b-121">Normal</span></span>|<span data-ttu-id="d366b-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d366b-122">CommonStates</span></span>|<span data-ttu-id="d366b-123">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="d366b-123">The default state.</span></span>|  
|<span data-ttu-id="d366b-124">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="d366b-124">MouseOver</span></span>|<span data-ttu-id="d366b-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d366b-125">CommonStates</span></span>|<span data-ttu-id="d366b-126">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="d366b-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="d366b-127">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="d366b-127">Disabled</span></span>|<span data-ttu-id="d366b-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d366b-128">CommonStates</span></span>|<span data-ttu-id="d366b-129">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d366b-129">The control is disabled.</span></span>|  
|<span data-ttu-id="d366b-130">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="d366b-130">Focused</span></span>|<span data-ttu-id="d366b-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d366b-131">FocusStates</span></span>|<span data-ttu-id="d366b-132">Denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d366b-132">The control has focus.</span></span>|  
|<span data-ttu-id="d366b-133">Odaksız</span><span class="sxs-lookup"><span data-stu-id="d366b-133">Unfocused</span></span>|<span data-ttu-id="d366b-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d366b-134">FocusStates</span></span>|<span data-ttu-id="d366b-135">Denetim odağı yok.</span><span class="sxs-lookup"><span data-stu-id="d366b-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="d366b-136">Geçerli</span><span class="sxs-lookup"><span data-stu-id="d366b-136">Valid</span></span>|<span data-ttu-id="d366b-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d366b-137">ValidationStates</span></span>|<span data-ttu-id="d366b-138">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="d366b-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d366b-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d366b-139">InvalidFocused</span></span>|<span data-ttu-id="d366b-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d366b-140">ValidationStates</span></span>|<span data-ttu-id="d366b-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d366b-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d366b-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d366b-142">InvalidUnfocused</span></span>|<span data-ttu-id="d366b-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d366b-143">ValidationStates</span></span>|<span data-ttu-id="d366b-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d366b-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="d366b-145">Kaydırıcı ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="d366b-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="d366b-146">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Slider> denetim.</span><span class="sxs-lookup"><span data-stu-id="d366b-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="d366b-147">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d366b-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d366b-148">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="d366b-148">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d366b-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d366b-149">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d366b-150">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d366b-150">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d366b-151">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d366b-151">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d366b-152">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d366b-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d366b-153">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d366b-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
