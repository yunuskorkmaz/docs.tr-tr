---
title: PasswordBox Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 7783330dd56ec5b2759e783a6935761eb3587978
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770649"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="d1c1b-102">PasswordBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d1c1b-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="d1c1b-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.PasswordBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="d1c1b-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d1c1b-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d1c1b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="d1c1b-106">PasswordBox bölümleri</span><span class="sxs-lookup"><span data-stu-id="d1c1b-106">PasswordBox Parts</span></span>

<span data-ttu-id="d1c1b-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.PasswordBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="d1c1b-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="d1c1b-108">Part</span></span>|<span data-ttu-id="d1c1b-109">Tür</span><span class="sxs-lookup"><span data-stu-id="d1c1b-109">Type</span></span>|<span data-ttu-id="d1c1b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1c1b-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="d1c1b-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="d1c1b-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="d1c1b-112">İçeren bir görsel öğe bir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="d1c1b-113">Metnin <xref:System.Windows.Controls.PasswordBox> bu öğe görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="d1c1b-114">PasswordBox durumları</span><span class="sxs-lookup"><span data-stu-id="d1c1b-114">PasswordBox States</span></span>

<span data-ttu-id="d1c1b-115">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.PasswordBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="d1c1b-116">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="d1c1b-116">VisualState Name</span></span>|<span data-ttu-id="d1c1b-117">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="d1c1b-117">VisualStateGroup Name</span></span>|<span data-ttu-id="d1c1b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1c1b-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="d1c1b-119">Normal</span><span class="sxs-lookup"><span data-stu-id="d1c1b-119">Normal</span></span>|<span data-ttu-id="d1c1b-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d1c1b-120">CommonStates</span></span>|<span data-ttu-id="d1c1b-121">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-121">The default state.</span></span>|
|<span data-ttu-id="d1c1b-122">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="d1c1b-122">MouseOver</span></span>|<span data-ttu-id="d1c1b-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d1c1b-123">CommonStates</span></span>|<span data-ttu-id="d1c1b-124">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="d1c1b-125">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="d1c1b-125">Disabled</span></span>|<span data-ttu-id="d1c1b-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d1c1b-126">CommonStates</span></span>|<span data-ttu-id="d1c1b-127">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-127">The control is disabled.</span></span>|
|<span data-ttu-id="d1c1b-128">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="d1c1b-128">Focused</span></span>|<span data-ttu-id="d1c1b-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d1c1b-129">FocusStates</span></span>|<span data-ttu-id="d1c1b-130">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-130">The control has focus.</span></span>|
|<span data-ttu-id="d1c1b-131">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="d1c1b-131">Unfocused</span></span>|<span data-ttu-id="d1c1b-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d1c1b-132">FocusStates</span></span>|<span data-ttu-id="d1c1b-133">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-133">The control does not have focus.</span></span>|
|<span data-ttu-id="d1c1b-134">Geçerli</span><span class="sxs-lookup"><span data-stu-id="d1c1b-134">Valid</span></span>|<span data-ttu-id="d1c1b-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1c1b-135">ValidationStates</span></span>|<span data-ttu-id="d1c1b-136">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="d1c1b-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d1c1b-137">InvalidFocused</span></span>|<span data-ttu-id="d1c1b-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1c1b-138">ValidationStates</span></span>|<span data-ttu-id="d1c1b-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="d1c1b-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d1c1b-140">InvalidUnfocused</span></span>|<span data-ttu-id="d1c1b-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d1c1b-141">ValidationStates</span></span>|<span data-ttu-id="d1c1b-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="d1c1b-143">PasswordBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="d1c1b-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="d1c1b-144">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.PasswordBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="d1c1b-145">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="d1c1b-146">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d1c1b-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1c1b-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1c1b-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d1c1b-148">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d1c1b-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d1c1b-149">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d1c1b-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d1c1b-150">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1c1b-150">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="d1c1b-151">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d1c1b-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
