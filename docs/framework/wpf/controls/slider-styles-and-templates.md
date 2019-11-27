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
ms.openlocfilehash: f533142d5ba202bd4aaf628487eaaa2a18a535d0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283380"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="f5f3c-102">Kaydırıcı Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="f5f3c-102">Slider Styles and Templates</span></span>
<span data-ttu-id="f5f3c-103">Bu konuda <xref:System.Windows.Controls.Slider> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="f5f3c-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f5f3c-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="f5f3c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="f5f3c-106">Kaydırıcı bölümleri</span><span class="sxs-lookup"><span data-stu-id="f5f3c-106">Slider Parts</span></span>  
 <span data-ttu-id="f5f3c-107">Aşağıdaki tabloda <xref:System.Windows.Controls.Slider> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="f5f3c-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="f5f3c-108">Part</span></span>|<span data-ttu-id="f5f3c-109">Tür</span><span class="sxs-lookup"><span data-stu-id="f5f3c-109">Type</span></span>|<span data-ttu-id="f5f3c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5f3c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f5f3c-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="f5f3c-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="f5f3c-112"><xref:System.Windows.Controls.Slider>konumunu gösteren öğe için kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="f5f3c-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="f5f3c-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="f5f3c-114"><xref:System.Windows.Controls.Slider>üzerinde bir seçim aralığı görüntüleyen öğe.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="f5f3c-115">Seçim aralığı yalnızca <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> özelliği `true`görünür.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="f5f3c-116">Kaydırıcı durumları</span><span class="sxs-lookup"><span data-stu-id="f5f3c-116">Slider States</span></span>  
 <span data-ttu-id="f5f3c-117">Aşağıdaki tabloda <xref:System.Windows.Controls.Slider> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="f5f3c-118">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="f5f3c-118">VisualState Name</span></span>|<span data-ttu-id="f5f3c-119">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="f5f3c-119">VisualStateGroup Name</span></span>|<span data-ttu-id="f5f3c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5f3c-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f5f3c-121">Normal</span><span class="sxs-lookup"><span data-stu-id="f5f3c-121">Normal</span></span>|<span data-ttu-id="f5f3c-122">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="f5f3c-122">CommonStates</span></span>|<span data-ttu-id="f5f3c-123">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-123">The default state.</span></span>|  
|<span data-ttu-id="f5f3c-124">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="f5f3c-124">MouseOver</span></span>|<span data-ttu-id="f5f3c-125">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="f5f3c-125">CommonStates</span></span>|<span data-ttu-id="f5f3c-126">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f5f3c-127">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="f5f3c-127">Disabled</span></span>|<span data-ttu-id="f5f3c-128">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="f5f3c-128">CommonStates</span></span>|<span data-ttu-id="f5f3c-129">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-129">The control is disabled.</span></span>|  
|<span data-ttu-id="f5f3c-130">Diğinize</span><span class="sxs-lookup"><span data-stu-id="f5f3c-130">Focused</span></span>|<span data-ttu-id="f5f3c-131">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="f5f3c-131">FocusStates</span></span>|<span data-ttu-id="f5f3c-132">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-132">The control has focus.</span></span>|  
|<span data-ttu-id="f5f3c-133">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="f5f3c-133">Unfocused</span></span>|<span data-ttu-id="f5f3c-134">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="f5f3c-134">FocusStates</span></span>|<span data-ttu-id="f5f3c-135">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="f5f3c-136">Geçerli</span><span class="sxs-lookup"><span data-stu-id="f5f3c-136">Valid</span></span>|<span data-ttu-id="f5f3c-137">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="f5f3c-137">ValidationStates</span></span>|<span data-ttu-id="f5f3c-138">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f5f3c-139">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="f5f3c-139">InvalidFocused</span></span>|<span data-ttu-id="f5f3c-140">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="f5f3c-140">ValidationStates</span></span>|<span data-ttu-id="f5f3c-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f5f3c-142">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="f5f3c-142">InvalidUnfocused</span></span>|<span data-ttu-id="f5f3c-143">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="f5f3c-143">ValidationStates</span></span>|<span data-ttu-id="f5f3c-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="f5f3c-145">Slider ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="f5f3c-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="f5f3c-146">Aşağıdaki örnek, <xref:System.Windows.Controls.Slider> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="f5f3c-147">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f5f3c-148">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f5f3c-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5f3c-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5f3c-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f5f3c-150">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="f5f3c-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f5f3c-151">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f5f3c-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f5f3c-152">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5f3c-152">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f5f3c-153">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5f3c-153">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
