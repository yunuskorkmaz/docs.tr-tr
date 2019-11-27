---
title: ToggleButton Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: a4c449a561017659db7f54fd3cdb8964742650de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283668"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="1c276-102">ToggleButton Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="1c276-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="1c276-103">Bu konuda <xref:System.Windows.Controls.Primitives.ToggleButton> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c276-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="1c276-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c276-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1c276-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="1c276-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="1c276-106">ToggleButton bölüm</span><span class="sxs-lookup"><span data-stu-id="1c276-106">ToggleButton Parts</span></span>

<span data-ttu-id="1c276-107"><xref:System.Windows.Controls.Primitives.ToggleButton> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="1c276-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="1c276-108">ToggleButton durumları</span><span class="sxs-lookup"><span data-stu-id="1c276-108">ToggleButton States</span></span>

<span data-ttu-id="1c276-109">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="1c276-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="1c276-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="1c276-110">VisualState Name</span></span>|<span data-ttu-id="1c276-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="1c276-111">VisualStateGroup Name</span></span>|<span data-ttu-id="1c276-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c276-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="1c276-113">Normal</span><span class="sxs-lookup"><span data-stu-id="1c276-113">Normal</span></span>|<span data-ttu-id="1c276-114">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="1c276-114">CommonStates</span></span>|<span data-ttu-id="1c276-115">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="1c276-115">The default state.</span></span>|
|<span data-ttu-id="1c276-116">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="1c276-116">MouseOver</span></span>|<span data-ttu-id="1c276-117">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="1c276-117">CommonStates</span></span>|<span data-ttu-id="1c276-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1c276-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="1c276-119">Basılan</span><span class="sxs-lookup"><span data-stu-id="1c276-119">Pressed</span></span>|<span data-ttu-id="1c276-120">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="1c276-120">CommonStates</span></span>|<span data-ttu-id="1c276-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="1c276-121">The control is pressed.</span></span>|
|<span data-ttu-id="1c276-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="1c276-122">Disabled</span></span>|<span data-ttu-id="1c276-123">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="1c276-123">CommonStates</span></span>|<span data-ttu-id="1c276-124">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="1c276-124">The control is disabled.</span></span>|
|<span data-ttu-id="1c276-125">Diğinize</span><span class="sxs-lookup"><span data-stu-id="1c276-125">Focused</span></span>|<span data-ttu-id="1c276-126">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="1c276-126">FocusStates</span></span>|<span data-ttu-id="1c276-127">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1c276-127">The control has focus.</span></span>|
|<span data-ttu-id="1c276-128">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="1c276-128">Unfocused</span></span>|<span data-ttu-id="1c276-129">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="1c276-129">FocusStates</span></span>|<span data-ttu-id="1c276-130">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="1c276-130">The control does not have focus.</span></span>|
|<span data-ttu-id="1c276-131">İşaretli</span><span class="sxs-lookup"><span data-stu-id="1c276-131">Checked</span></span>|<span data-ttu-id="1c276-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="1c276-132">CheckStates</span></span>|<span data-ttu-id="1c276-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `true`.</span><span class="sxs-lookup"><span data-stu-id="1c276-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="1c276-134">Olmayan</span><span class="sxs-lookup"><span data-stu-id="1c276-134">Unchecked</span></span>|<span data-ttu-id="1c276-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="1c276-135">CheckStates</span></span>|<span data-ttu-id="1c276-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `false`.</span><span class="sxs-lookup"><span data-stu-id="1c276-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="1c276-137">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="1c276-137">Indeterminate</span></span>|<span data-ttu-id="1c276-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="1c276-138">CheckStates</span></span>|<span data-ttu-id="1c276-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> `true`ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`.</span><span class="sxs-lookup"><span data-stu-id="1c276-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="1c276-140">Geçerli</span><span class="sxs-lookup"><span data-stu-id="1c276-140">Valid</span></span>|<span data-ttu-id="1c276-141">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="1c276-141">ValidationStates</span></span>|<span data-ttu-id="1c276-142">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c276-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="1c276-143">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="1c276-143">InvalidFocused</span></span>|<span data-ttu-id="1c276-144">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="1c276-144">ValidationStates</span></span>|<span data-ttu-id="1c276-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="1c276-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="1c276-146">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="1c276-146">InvalidUnfocused</span></span>|<span data-ttu-id="1c276-147">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="1c276-147">ValidationStates</span></span>|<span data-ttu-id="1c276-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="1c276-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="1c276-149">Denetim şablonunuzda belirsiz görsel durumu yoksa, denetlenmeyen görsel durum varsayılan görsel durum olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1c276-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="1c276-150">ToggleButton ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="1c276-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="1c276-151">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.ToggleButton> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c276-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="1c276-152">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c276-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="1c276-153">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="1c276-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c276-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c276-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="1c276-155">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="1c276-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="1c276-156">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="1c276-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="1c276-157">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c276-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="1c276-158">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c276-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
