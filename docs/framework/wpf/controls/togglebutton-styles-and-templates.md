---
title: ToggleButton stilleri ve şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: 46fd7d07c3904ee752ae3f467f65af4b0c031c84
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57507294"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="e4f32-102">ToggleButton stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="e4f32-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="e4f32-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e4f32-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="e4f32-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="e4f32-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e4f32-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e4f32-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="e4f32-106">ToggleButton bölümleri</span><span class="sxs-lookup"><span data-stu-id="e4f32-106">ToggleButton Parts</span></span>

<span data-ttu-id="e4f32-107"><xref:System.Windows.Controls.Primitives.ToggleButton> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="e4f32-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="e4f32-108">ToggleButton durumları</span><span class="sxs-lookup"><span data-stu-id="e4f32-108">ToggleButton States</span></span>

<span data-ttu-id="e4f32-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e4f32-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="e4f32-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="e4f32-110">VisualState Name</span></span>|<span data-ttu-id="e4f32-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="e4f32-111">VisualStateGroup Name</span></span>|<span data-ttu-id="e4f32-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4f32-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="e4f32-113">Normal</span><span class="sxs-lookup"><span data-stu-id="e4f32-113">Normal</span></span>|<span data-ttu-id="e4f32-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-114">CommonStates</span></span>|<span data-ttu-id="e4f32-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="e4f32-115">The default state.</span></span>|
|<span data-ttu-id="e4f32-116">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="e4f32-116">MouseOver</span></span>|<span data-ttu-id="e4f32-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-117">CommonStates</span></span>|<span data-ttu-id="e4f32-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e4f32-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="e4f32-119">Basılan</span><span class="sxs-lookup"><span data-stu-id="e4f32-119">Pressed</span></span>|<span data-ttu-id="e4f32-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-120">CommonStates</span></span>|<span data-ttu-id="e4f32-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="e4f32-121">The control is pressed.</span></span>|
|<span data-ttu-id="e4f32-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="e4f32-122">Disabled</span></span>|<span data-ttu-id="e4f32-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-123">CommonStates</span></span>|<span data-ttu-id="e4f32-124">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e4f32-124">The control is disabled.</span></span>|
|<span data-ttu-id="e4f32-125">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="e4f32-125">Focused</span></span>|<span data-ttu-id="e4f32-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-126">FocusStates</span></span>|<span data-ttu-id="e4f32-127">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="e4f32-127">The control has focus.</span></span>|
|<span data-ttu-id="e4f32-128">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="e4f32-128">Unfocused</span></span>|<span data-ttu-id="e4f32-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-129">FocusStates</span></span>|<span data-ttu-id="e4f32-130">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e4f32-130">The control does not have focus.</span></span>|
|<span data-ttu-id="e4f32-131">İşaretli</span><span class="sxs-lookup"><span data-stu-id="e4f32-131">Checked</span></span>|<span data-ttu-id="e4f32-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-132">CheckStates</span></span>|<span data-ttu-id="e4f32-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> olan `true`.</span><span class="sxs-lookup"><span data-stu-id="e4f32-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="e4f32-134">Denetlenmeyen</span><span class="sxs-lookup"><span data-stu-id="e4f32-134">Unchecked</span></span>|<span data-ttu-id="e4f32-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-135">CheckStates</span></span>|<span data-ttu-id="e4f32-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> olan `false`.</span><span class="sxs-lookup"><span data-stu-id="e4f32-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="e4f32-137">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="e4f32-137">Indeterminate</span></span>|<span data-ttu-id="e4f32-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-138">CheckStates</span></span>|<span data-ttu-id="e4f32-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> olan `true`, ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> olduğu `null`.</span><span class="sxs-lookup"><span data-stu-id="e4f32-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="e4f32-140">Geçerli</span><span class="sxs-lookup"><span data-stu-id="e4f32-140">Valid</span></span>|<span data-ttu-id="e4f32-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-141">ValidationStates</span></span>|<span data-ttu-id="e4f32-142">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="e4f32-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="e4f32-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e4f32-143">InvalidFocused</span></span>|<span data-ttu-id="e4f32-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-144">ValidationStates</span></span>|<span data-ttu-id="e4f32-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="e4f32-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="e4f32-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e4f32-146">InvalidUnfocused</span></span>|<span data-ttu-id="e4f32-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e4f32-147">ValidationStates</span></span>|<span data-ttu-id="e4f32-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e4f32-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="e4f32-149">Belirsiz görsel durum denetimi şablonunuzda yoksa denetlenmeyen görsel durum varsayılan görsel durum kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4f32-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="e4f32-150">ToggleButton ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="e4f32-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="e4f32-151">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e4f32-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="e4f32-152">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4f32-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="e4f32-153">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="e4f32-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="e4f32-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4f32-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e4f32-155">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="e4f32-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e4f32-156">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e4f32-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e4f32-157">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e4f32-157">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="e4f32-158">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e4f32-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
