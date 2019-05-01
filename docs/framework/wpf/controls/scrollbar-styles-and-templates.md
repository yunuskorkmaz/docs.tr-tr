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
ms.openlocfilehash: 22b2206067302f621a94a1e9abca1607792b3393
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052891"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="f3613-102">ScrollBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="f3613-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="f3613-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f3613-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="f3613-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="f3613-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f3613-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f3613-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="f3613-106">Kaydırma çubuğu bölümleri</span><span class="sxs-lookup"><span data-stu-id="f3613-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="f3613-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f3613-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="f3613-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="f3613-108">Part</span></span>|<span data-ttu-id="f3613-109">Tür</span><span class="sxs-lookup"><span data-stu-id="f3613-109">Type</span></span>|<span data-ttu-id="f3613-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3613-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f3613-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="f3613-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="f3613-112">Kapsayıcı konumunu gösteren bir öğe için <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="f3613-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="f3613-113">Kaydırma çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="f3613-113">ScrollBar States</span></span>  
 <span data-ttu-id="f3613-114">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f3613-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="f3613-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="f3613-115">VisualState Name</span></span>|<span data-ttu-id="f3613-116">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="f3613-116">VisualStateGroup Name</span></span>|<span data-ttu-id="f3613-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3613-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f3613-118">Normal</span><span class="sxs-lookup"><span data-stu-id="f3613-118">Normal</span></span>|<span data-ttu-id="f3613-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3613-119">CommonStates</span></span>|<span data-ttu-id="f3613-120">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="f3613-120">The default state.</span></span>|  
|<span data-ttu-id="f3613-121">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="f3613-121">MouseOver</span></span>|<span data-ttu-id="f3613-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3613-122">CommonStates</span></span>|<span data-ttu-id="f3613-123">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f3613-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f3613-124">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="f3613-124">Disabled</span></span>|<span data-ttu-id="f3613-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3613-125">CommonStates</span></span>|<span data-ttu-id="f3613-126">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f3613-126">The control is disabled.</span></span>|  
|<span data-ttu-id="f3613-127">Geçerli</span><span class="sxs-lookup"><span data-stu-id="f3613-127">Valid</span></span>|<span data-ttu-id="f3613-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3613-128">ValidationStates</span></span>|<span data-ttu-id="f3613-129">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="f3613-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f3613-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f3613-130">InvalidFocused</span></span>|<span data-ttu-id="f3613-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3613-131">ValidationStates</span></span>|<span data-ttu-id="f3613-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="f3613-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f3613-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f3613-133">InvalidUnfocused</span></span>|<span data-ttu-id="f3613-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3613-134">ValidationStates</span></span>|<span data-ttu-id="f3613-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f3613-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="f3613-136">Kaydırma çubuğu ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="f3613-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="f3613-137">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="f3613-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="f3613-138">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3613-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f3613-139">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f3613-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3613-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3613-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f3613-141">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="f3613-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f3613-142">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f3613-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f3613-143">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f3613-143">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="f3613-144">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f3613-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
