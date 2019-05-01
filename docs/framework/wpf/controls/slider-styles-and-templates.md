---
title: Kaydırıcı Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
ms.openlocfilehash: 385a69ad2bd17ae4c51437245915109aad446bdf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970982"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="badcb-102">Kaydırıcı Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="badcb-102">Slider Styles and Templates</span></span>
<span data-ttu-id="badcb-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Slider> denetimi.</span><span class="sxs-lookup"><span data-stu-id="badcb-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="badcb-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="badcb-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="badcb-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="badcb-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="badcb-106">Kaydırıcı bölümleri</span><span class="sxs-lookup"><span data-stu-id="badcb-106">Slider Parts</span></span>  
 <span data-ttu-id="badcb-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Slider> denetimi.</span><span class="sxs-lookup"><span data-stu-id="badcb-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="badcb-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="badcb-108">Part</span></span>|<span data-ttu-id="badcb-109">Tür</span><span class="sxs-lookup"><span data-stu-id="badcb-109">Type</span></span>|<span data-ttu-id="badcb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="badcb-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="badcb-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="badcb-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="badcb-112">Kapsayıcı konumunu gösteren bir öğe için <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="badcb-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="badcb-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="badcb-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="badcb-114">Bir seçim aralığını boyunca görüntüler öğesi <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="badcb-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="badcb-115">Seçenek aralığındaki görünür olup yalnızca <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="badcb-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="badcb-116">Kaydırıcı durumları</span><span class="sxs-lookup"><span data-stu-id="badcb-116">Slider States</span></span>  
 <span data-ttu-id="badcb-117">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Slider> denetimi.</span><span class="sxs-lookup"><span data-stu-id="badcb-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="badcb-118">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="badcb-118">VisualState Name</span></span>|<span data-ttu-id="badcb-119">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="badcb-119">VisualStateGroup Name</span></span>|<span data-ttu-id="badcb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="badcb-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="badcb-121">Normal</span><span class="sxs-lookup"><span data-stu-id="badcb-121">Normal</span></span>|<span data-ttu-id="badcb-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="badcb-122">CommonStates</span></span>|<span data-ttu-id="badcb-123">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="badcb-123">The default state.</span></span>|  
|<span data-ttu-id="badcb-124">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="badcb-124">MouseOver</span></span>|<span data-ttu-id="badcb-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="badcb-125">CommonStates</span></span>|<span data-ttu-id="badcb-126">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="badcb-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="badcb-127">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="badcb-127">Disabled</span></span>|<span data-ttu-id="badcb-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="badcb-128">CommonStates</span></span>|<span data-ttu-id="badcb-129">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="badcb-129">The control is disabled.</span></span>|  
|<span data-ttu-id="badcb-130">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="badcb-130">Focused</span></span>|<span data-ttu-id="badcb-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="badcb-131">FocusStates</span></span>|<span data-ttu-id="badcb-132">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="badcb-132">The control has focus.</span></span>|  
|<span data-ttu-id="badcb-133">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="badcb-133">Unfocused</span></span>|<span data-ttu-id="badcb-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="badcb-134">FocusStates</span></span>|<span data-ttu-id="badcb-135">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="badcb-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="badcb-136">Geçerli</span><span class="sxs-lookup"><span data-stu-id="badcb-136">Valid</span></span>|<span data-ttu-id="badcb-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="badcb-137">ValidationStates</span></span>|<span data-ttu-id="badcb-138">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="badcb-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="badcb-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="badcb-139">InvalidFocused</span></span>|<span data-ttu-id="badcb-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="badcb-140">ValidationStates</span></span>|<span data-ttu-id="badcb-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="badcb-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="badcb-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="badcb-142">InvalidUnfocused</span></span>|<span data-ttu-id="badcb-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="badcb-143">ValidationStates</span></span>|<span data-ttu-id="badcb-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="badcb-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="badcb-145">Kaydırıcı ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="badcb-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="badcb-146">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Slider> denetimi.</span><span class="sxs-lookup"><span data-stu-id="badcb-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="badcb-147">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="badcb-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="badcb-148">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="badcb-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="badcb-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="badcb-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="badcb-150">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="badcb-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="badcb-151">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="badcb-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="badcb-152">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="badcb-152">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="badcb-153">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="badcb-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
