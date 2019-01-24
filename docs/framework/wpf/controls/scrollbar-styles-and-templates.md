---
title: ScrollBar Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: d38173cad01e0f2d17cd53be102e0b8afd75d608
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642980"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="f24a6-102">ScrollBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="f24a6-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="f24a6-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f24a6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="f24a6-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="f24a6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f24a6-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f24a6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="f24a6-106">Kaydırma çubuğu bölümleri</span><span class="sxs-lookup"><span data-stu-id="f24a6-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="f24a6-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f24a6-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="f24a6-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="f24a6-108">Part</span></span>|<span data-ttu-id="f24a6-109">Tür</span><span class="sxs-lookup"><span data-stu-id="f24a6-109">Type</span></span>|<span data-ttu-id="f24a6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f24a6-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f24a6-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="f24a6-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="f24a6-112">Kapsayıcı konumunu gösteren bir öğe için <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="f24a6-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="f24a6-113">Kaydırma çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="f24a6-113">ScrollBar States</span></span>  
 <span data-ttu-id="f24a6-114">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f24a6-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="f24a6-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="f24a6-115">VisualState Name</span></span>|<span data-ttu-id="f24a6-116">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="f24a6-116">VisualStateGroup Name</span></span>|<span data-ttu-id="f24a6-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f24a6-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f24a6-118">Normal</span><span class="sxs-lookup"><span data-stu-id="f24a6-118">Normal</span></span>|<span data-ttu-id="f24a6-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f24a6-119">CommonStates</span></span>|<span data-ttu-id="f24a6-120">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="f24a6-120">The default state.</span></span>|  
|<span data-ttu-id="f24a6-121">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="f24a6-121">MouseOver</span></span>|<span data-ttu-id="f24a6-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f24a6-122">CommonStates</span></span>|<span data-ttu-id="f24a6-123">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f24a6-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f24a6-124">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="f24a6-124">Disabled</span></span>|<span data-ttu-id="f24a6-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f24a6-125">CommonStates</span></span>|<span data-ttu-id="f24a6-126">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f24a6-126">The control is disabled.</span></span>|  
|<span data-ttu-id="f24a6-127">Geçerli</span><span class="sxs-lookup"><span data-stu-id="f24a6-127">Valid</span></span>|<span data-ttu-id="f24a6-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f24a6-128">ValidationStates</span></span>|<span data-ttu-id="f24a6-129">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="f24a6-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f24a6-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f24a6-130">InvalidFocused</span></span>|<span data-ttu-id="f24a6-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f24a6-131">ValidationStates</span></span>|<span data-ttu-id="f24a6-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="f24a6-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f24a6-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f24a6-133">InvalidUnfocused</span></span>|<span data-ttu-id="f24a6-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f24a6-134">ValidationStates</span></span>|<span data-ttu-id="f24a6-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f24a6-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="f24a6-136">Kaydırma çubuğu ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="f24a6-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="f24a6-137">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f24a6-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="f24a6-138">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f24a6-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f24a6-139">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f24a6-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f24a6-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f24a6-140">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f24a6-141">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="f24a6-141">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="f24a6-142">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f24a6-142">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="f24a6-143">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f24a6-143">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="f24a6-144">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f24a6-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
