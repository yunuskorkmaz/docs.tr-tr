---
title: RepeatButton stilleri ve şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 86f212326bc707e4b07b8cab8d9a95d4f6ef8920
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57507318"
---
# <a name="repeatbutton-styles-and-templates"></a><span data-ttu-id="96649-102">RepeatButton stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="96649-102">RepeatButton Styles and Templates</span></span>

<span data-ttu-id="96649-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="96649-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="96649-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="96649-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="96649-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="96649-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="repeatbutton-parts"></a><span data-ttu-id="96649-106">RepeatButton bölümleri</span><span class="sxs-lookup"><span data-stu-id="96649-106">RepeatButton Parts</span></span>

<span data-ttu-id="96649-107"><xref:System.Windows.Controls.Primitives.RepeatButton> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="96649-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>

## <a name="repeatbutton-states"></a><span data-ttu-id="96649-108">RepeatButton durumları</span><span class="sxs-lookup"><span data-stu-id="96649-108">RepeatButton States</span></span>

<span data-ttu-id="96649-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="96649-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

|<span data-ttu-id="96649-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="96649-110">VisualState Name</span></span>|<span data-ttu-id="96649-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="96649-111">VisualStateGroup Name</span></span>|<span data-ttu-id="96649-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96649-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="96649-113">Normal</span><span class="sxs-lookup"><span data-stu-id="96649-113">Normal</span></span>|<span data-ttu-id="96649-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="96649-114">CommonStates</span></span>|<span data-ttu-id="96649-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="96649-115">The default state.</span></span>|
|<span data-ttu-id="96649-116">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="96649-116">MouseOver</span></span>|<span data-ttu-id="96649-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="96649-117">CommonStates</span></span>|<span data-ttu-id="96649-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="96649-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="96649-119">Basılan</span><span class="sxs-lookup"><span data-stu-id="96649-119">Pressed</span></span>|<span data-ttu-id="96649-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="96649-120">CommonStates</span></span>|<span data-ttu-id="96649-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="96649-121">The control is pressed.</span></span>|
|<span data-ttu-id="96649-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="96649-122">Disabled</span></span>|<span data-ttu-id="96649-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="96649-123">CommonStates</span></span>|<span data-ttu-id="96649-124">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="96649-124">The control is disabled.</span></span>|
|<span data-ttu-id="96649-125">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="96649-125">Focused</span></span>|<span data-ttu-id="96649-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="96649-126">FocusStates</span></span>|<span data-ttu-id="96649-127">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="96649-127">The control has focus.</span></span>|
|<span data-ttu-id="96649-128">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="96649-128">Unfocused</span></span>|<span data-ttu-id="96649-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="96649-129">FocusStates</span></span>|<span data-ttu-id="96649-130">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="96649-130">The control does not have focus.</span></span>|
|<span data-ttu-id="96649-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="96649-131">Valid</span></span>|<span data-ttu-id="96649-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="96649-132">ValidationStates</span></span>|<span data-ttu-id="96649-133">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="96649-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="96649-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="96649-134">InvalidFocused</span></span>|<span data-ttu-id="96649-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="96649-135">ValidationStates</span></span>|<span data-ttu-id="96649-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="96649-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="96649-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="96649-137">InvalidUnfocused</span></span>|<span data-ttu-id="96649-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="96649-138">ValidationStates</span></span>|<span data-ttu-id="96649-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="96649-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="96649-140">RepeatButton ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="96649-140">RepeatButton ControlTemplate Example</span></span>

<span data-ttu-id="96649-141">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="96649-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

<span data-ttu-id="96649-142">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="96649-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="96649-143">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="96649-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="96649-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96649-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="96649-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="96649-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="96649-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="96649-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="96649-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="96649-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="96649-148">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="96649-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
