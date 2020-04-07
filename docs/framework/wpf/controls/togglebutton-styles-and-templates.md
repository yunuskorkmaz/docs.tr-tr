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
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805917"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="be9a1-102">ToggleButton Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="be9a1-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="be9a1-103">Bu <xref:System.Windows.Controls.Primitives.ToggleButton> konu, denetim in stilleri ve şablonlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="be9a1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="be9a1-104">Denetime benzersiz <xref:System.Windows.Controls.ControlTemplate> bir görünüm kazandırmak için varsayılanı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be9a1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="be9a1-105">Daha fazla bilgi [için](../../../desktop-wpf/themes/how-to-create-apply-template.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="be9a1-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="be9a1-106">Düğme Parçaları</span><span class="sxs-lookup"><span data-stu-id="be9a1-106">ToggleButton Parts</span></span>

<span data-ttu-id="be9a1-107">Denetimde <xref:System.Windows.Controls.Primitives.ToggleButton> herhangi bir adlandırılmış parça yok.</span><span class="sxs-lookup"><span data-stu-id="be9a1-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="be9a1-108">ToggleButton Durumları</span><span class="sxs-lookup"><span data-stu-id="be9a1-108">ToggleButton States</span></span>

<span data-ttu-id="be9a1-109">Aşağıdaki <xref:System.Windows.Controls.Primitives.ToggleButton> tabloda denetim için görsel durumları listeler.</span><span class="sxs-lookup"><span data-stu-id="be9a1-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="be9a1-110">VisualState Adı</span><span class="sxs-lookup"><span data-stu-id="be9a1-110">VisualState Name</span></span>|<span data-ttu-id="be9a1-111">VisualStateGroup Adı</span><span class="sxs-lookup"><span data-stu-id="be9a1-111">VisualStateGroup Name</span></span>|<span data-ttu-id="be9a1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be9a1-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="be9a1-113">Normal</span><span class="sxs-lookup"><span data-stu-id="be9a1-113">Normal</span></span>|<span data-ttu-id="be9a1-114">Commonstates</span><span class="sxs-lookup"><span data-stu-id="be9a1-114">CommonStates</span></span>|<span data-ttu-id="be9a1-115">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="be9a1-115">The default state.</span></span>|
|<span data-ttu-id="be9a1-116">Mouseover</span><span class="sxs-lookup"><span data-stu-id="be9a1-116">MouseOver</span></span>|<span data-ttu-id="be9a1-117">Commonstates</span><span class="sxs-lookup"><span data-stu-id="be9a1-117">CommonStates</span></span>|<span data-ttu-id="be9a1-118">Fare işaretçisi denetimin üzerine konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="be9a1-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="be9a1-119">Pressed</span><span class="sxs-lookup"><span data-stu-id="be9a1-119">Pressed</span></span>|<span data-ttu-id="be9a1-120">Commonstates</span><span class="sxs-lookup"><span data-stu-id="be9a1-120">CommonStates</span></span>|<span data-ttu-id="be9a1-121">Kontrol basılı.</span><span class="sxs-lookup"><span data-stu-id="be9a1-121">The control is pressed.</span></span>|
|<span data-ttu-id="be9a1-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="be9a1-122">Disabled</span></span>|<span data-ttu-id="be9a1-123">Commonstates</span><span class="sxs-lookup"><span data-stu-id="be9a1-123">CommonStates</span></span>|<span data-ttu-id="be9a1-124">Denetim devre dışı.</span><span class="sxs-lookup"><span data-stu-id="be9a1-124">The control is disabled.</span></span>|
|<span data-ttu-id="be9a1-125">Odaklı</span><span class="sxs-lookup"><span data-stu-id="be9a1-125">Focused</span></span>|<span data-ttu-id="be9a1-126">Odak Devletler</span><span class="sxs-lookup"><span data-stu-id="be9a1-126">FocusStates</span></span>|<span data-ttu-id="be9a1-127">Kontrol odak noktası.</span><span class="sxs-lookup"><span data-stu-id="be9a1-127">The control has focus.</span></span>|
|<span data-ttu-id="be9a1-128">Odaklanmamış</span><span class="sxs-lookup"><span data-stu-id="be9a1-128">Unfocused</span></span>|<span data-ttu-id="be9a1-129">Odak Devletler</span><span class="sxs-lookup"><span data-stu-id="be9a1-129">FocusStates</span></span>|<span data-ttu-id="be9a1-130">Denetimin odak noktası yok.</span><span class="sxs-lookup"><span data-stu-id="be9a1-130">The control does not have focus.</span></span>|
|<span data-ttu-id="be9a1-131">İşaretli</span><span class="sxs-lookup"><span data-stu-id="be9a1-131">Checked</span></span>|<span data-ttu-id="be9a1-132">Çek Durumları</span><span class="sxs-lookup"><span data-stu-id="be9a1-132">CheckStates</span></span>|<span data-ttu-id="be9a1-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>`true`.</span><span class="sxs-lookup"><span data-stu-id="be9a1-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="be9a1-134">Denetlenme -yen</span><span class="sxs-lookup"><span data-stu-id="be9a1-134">Unchecked</span></span>|<span data-ttu-id="be9a1-135">Çek Durumları</span><span class="sxs-lookup"><span data-stu-id="be9a1-135">CheckStates</span></span>|<span data-ttu-id="be9a1-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>`false`.</span><span class="sxs-lookup"><span data-stu-id="be9a1-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="be9a1-137">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="be9a1-137">Indeterminate</span></span>|<span data-ttu-id="be9a1-138">Çek Durumları</span><span class="sxs-lookup"><span data-stu-id="be9a1-138">CheckStates</span></span>|<span data-ttu-id="be9a1-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>' `true`dir <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> `null`ve .</span><span class="sxs-lookup"><span data-stu-id="be9a1-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="be9a1-140">Geçerli</span><span class="sxs-lookup"><span data-stu-id="be9a1-140">Valid</span></span>|<span data-ttu-id="be9a1-141">Doğrulama Durumları</span><span class="sxs-lookup"><span data-stu-id="be9a1-141">ValidationStates</span></span>|<span data-ttu-id="be9a1-142">Denetim <xref:System.Windows.Controls.Validation> sınıfı kullanır ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli `false`özellik.</span><span class="sxs-lookup"><span data-stu-id="be9a1-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="be9a1-143">GeçersizOdaklanmış</span><span class="sxs-lookup"><span data-stu-id="be9a1-143">InvalidFocused</span></span>|<span data-ttu-id="be9a1-144">Doğrulama Durumları</span><span class="sxs-lookup"><span data-stu-id="be9a1-144">ValidationStates</span></span>|<span data-ttu-id="be9a1-145">Ekli <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> özellik ve `true` denetim odak vardır.</span><span class="sxs-lookup"><span data-stu-id="be9a1-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|
|<span data-ttu-id="be9a1-146">Geçersiz Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="be9a1-146">InvalidUnfocused</span></span>|<span data-ttu-id="be9a1-147">Doğrulama Durumları</span><span class="sxs-lookup"><span data-stu-id="be9a1-147">ValidationStates</span></span>|<span data-ttu-id="be9a1-148">Ekli <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> özellik ve `true` denetim odak yok.</span><span class="sxs-lookup"><span data-stu-id="be9a1-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="be9a1-149">Denetim şablonunuzda Belirsiz görsel durum yoksa, denetlenmemiş görsel durum varsayılan görsel durum olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be9a1-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="be9a1-150">Düğme DenetimiŞablon Örneği</span><span class="sxs-lookup"><span data-stu-id="be9a1-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="be9a1-151">Aşağıdaki örnek, denetim için <xref:System.Windows.Controls.ControlTemplate> a'nın <xref:System.Windows.Controls.Primitives.ToggleButton> nasıl tanımlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be9a1-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="be9a1-152">Önceki örnekte aşağıdaki kaynaklardan biri veya birkaçı kullanır.</span><span class="sxs-lookup"><span data-stu-id="be9a1-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="be9a1-153">Tam örnek için [ControlTemplates Örnek ile Şekillendirme'ye](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)bakın.</span><span class="sxs-lookup"><span data-stu-id="be9a1-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="be9a1-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be9a1-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="be9a1-155">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="be9a1-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="be9a1-156">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="be9a1-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="be9a1-157">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="be9a1-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="be9a1-158">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="be9a1-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
