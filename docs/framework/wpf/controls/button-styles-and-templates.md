---
title: Düğme Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: ec64c7c2051b12cba01135054a90e54864b7386a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116343"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="b56db-102">Düğme Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="b56db-102">Button Styles and Templates</span></span>
<span data-ttu-id="b56db-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b56db-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="b56db-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="b56db-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b56db-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="b56db-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="b56db-106">Düğme bölümleri</span><span class="sxs-lookup"><span data-stu-id="b56db-106">Button Parts</span></span>  
 <span data-ttu-id="b56db-107"><xref:System.Windows.Controls.Button> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="b56db-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="b56db-108">Düğme durumları</span><span class="sxs-lookup"><span data-stu-id="b56db-108">Button States</span></span>  
 <span data-ttu-id="b56db-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b56db-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="b56db-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="b56db-110">VisualState Name</span></span>|<span data-ttu-id="b56db-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="b56db-111">VisualStateGroup Name</span></span>|<span data-ttu-id="b56db-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b56db-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b56db-113">Normal</span><span class="sxs-lookup"><span data-stu-id="b56db-113">Normal</span></span>|<span data-ttu-id="b56db-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b56db-114">CommonStates</span></span>|<span data-ttu-id="b56db-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="b56db-115">The default state.</span></span>|  
|<span data-ttu-id="b56db-116">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="b56db-116">MouseOver</span></span>|<span data-ttu-id="b56db-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b56db-117">CommonStates</span></span>|<span data-ttu-id="b56db-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b56db-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="b56db-119">Basılan</span><span class="sxs-lookup"><span data-stu-id="b56db-119">Pressed</span></span>|<span data-ttu-id="b56db-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b56db-120">CommonStates</span></span>|<span data-ttu-id="b56db-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="b56db-121">The control is pressed.</span></span>|  
|<span data-ttu-id="b56db-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="b56db-122">Disabled</span></span>|<span data-ttu-id="b56db-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b56db-123">CommonStates</span></span>|<span data-ttu-id="b56db-124">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="b56db-124">The control is disabled.</span></span>|  
|<span data-ttu-id="b56db-125">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="b56db-125">Focused</span></span>|<span data-ttu-id="b56db-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="b56db-126">FocusStates</span></span>|<span data-ttu-id="b56db-127">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="b56db-127">The control has focus.</span></span>|  
|<span data-ttu-id="b56db-128">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="b56db-128">Unfocused</span></span>|<span data-ttu-id="b56db-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="b56db-129">FocusStates</span></span>|<span data-ttu-id="b56db-130">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b56db-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="b56db-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="b56db-131">Valid</span></span>|<span data-ttu-id="b56db-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b56db-132">ValidationStates</span></span>|<span data-ttu-id="b56db-133">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="b56db-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b56db-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b56db-134">InvalidFocused</span></span>|<span data-ttu-id="b56db-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b56db-135">ValidationStates</span></span>|<span data-ttu-id="b56db-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` ve Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="b56db-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="b56db-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b56db-137">InvalidUnfocused</span></span>|<span data-ttu-id="b56db-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b56db-138">ValidationStates</span></span>|<span data-ttu-id="b56db-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` ve Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b56db-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="b56db-140">ControlTemplate Örneği düğmesi</span><span class="sxs-lookup"><span data-stu-id="b56db-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="b56db-141">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b56db-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="b56db-142">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="b56db-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b56db-143">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="b56db-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56db-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b56db-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b56db-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="b56db-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b56db-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b56db-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b56db-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b56db-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="b56db-148">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b56db-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
