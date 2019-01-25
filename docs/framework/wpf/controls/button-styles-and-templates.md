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
ms.openlocfilehash: af9ea902cba2c8be0fbee621297af3198bbec150
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620480"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="53638-102">Düğme Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="53638-102">Button Styles and Templates</span></span>
<span data-ttu-id="53638-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="53638-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="53638-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="53638-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="53638-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="53638-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="53638-106">Düğme bölümleri</span><span class="sxs-lookup"><span data-stu-id="53638-106">Button Parts</span></span>  
 <span data-ttu-id="53638-107"><xref:System.Windows.Controls.Button> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="53638-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="53638-108">Düğme durumları</span><span class="sxs-lookup"><span data-stu-id="53638-108">Button States</span></span>  
 <span data-ttu-id="53638-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="53638-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="53638-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="53638-110">VisualState Name</span></span>|<span data-ttu-id="53638-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="53638-111">VisualStateGroup Name</span></span>|<span data-ttu-id="53638-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53638-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="53638-113">Normal</span><span class="sxs-lookup"><span data-stu-id="53638-113">Normal</span></span>|<span data-ttu-id="53638-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="53638-114">CommonStates</span></span>|<span data-ttu-id="53638-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="53638-115">The default state.</span></span>|  
|<span data-ttu-id="53638-116">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="53638-116">MouseOver</span></span>|<span data-ttu-id="53638-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="53638-117">CommonStates</span></span>|<span data-ttu-id="53638-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="53638-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="53638-119">Basılan</span><span class="sxs-lookup"><span data-stu-id="53638-119">Pressed</span></span>|<span data-ttu-id="53638-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="53638-120">CommonStates</span></span>|<span data-ttu-id="53638-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="53638-121">The control is pressed.</span></span>|  
|<span data-ttu-id="53638-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="53638-122">Disabled</span></span>|<span data-ttu-id="53638-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="53638-123">CommonStates</span></span>|<span data-ttu-id="53638-124">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="53638-124">The control is disabled.</span></span>|  
|<span data-ttu-id="53638-125">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="53638-125">Focused</span></span>|<span data-ttu-id="53638-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="53638-126">FocusStates</span></span>|<span data-ttu-id="53638-127">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="53638-127">The control has focus.</span></span>|  
|<span data-ttu-id="53638-128">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="53638-128">Unfocused</span></span>|<span data-ttu-id="53638-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="53638-129">FocusStates</span></span>|<span data-ttu-id="53638-130">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="53638-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="53638-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="53638-131">Valid</span></span>|<span data-ttu-id="53638-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="53638-132">ValidationStates</span></span>|<span data-ttu-id="53638-133">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="53638-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="53638-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="53638-134">InvalidFocused</span></span>|<span data-ttu-id="53638-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="53638-135">ValidationStates</span></span>|<span data-ttu-id="53638-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` ve Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="53638-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="53638-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="53638-137">InvalidUnfocused</span></span>|<span data-ttu-id="53638-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="53638-138">ValidationStates</span></span>|<span data-ttu-id="53638-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` ve Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="53638-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="53638-140">ControlTemplate Örneği düğmesi</span><span class="sxs-lookup"><span data-stu-id="53638-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="53638-141">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Button> denetimi.</span><span class="sxs-lookup"><span data-stu-id="53638-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="53638-142">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="53638-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="53638-143">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="53638-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53638-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53638-144">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="53638-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="53638-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="53638-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="53638-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="53638-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="53638-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="53638-148">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="53638-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
