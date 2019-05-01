---
title: Parmak Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: b7fc595f0c592d42f118c6b5542edf93716c2fca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790786"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="45517-102">Parmak Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="45517-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="45517-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Primitives.Thumb> denetimi.</span><span class="sxs-lookup"><span data-stu-id="45517-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="45517-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="45517-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="45517-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="45517-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="45517-106">Thumb bölümleri</span><span class="sxs-lookup"><span data-stu-id="45517-106">Thumb Parts</span></span>

<span data-ttu-id="45517-107"><xref:System.Windows.Controls.Primitives.Thumb> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="45517-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="45517-108">Thumb durumları</span><span class="sxs-lookup"><span data-stu-id="45517-108">Thumb States</span></span>

<span data-ttu-id="45517-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.Thumb> denetimi.</span><span class="sxs-lookup"><span data-stu-id="45517-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="45517-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="45517-110">VisualState Name</span></span>|<span data-ttu-id="45517-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="45517-111">VisualStateGroup Name</span></span>|<span data-ttu-id="45517-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45517-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="45517-113">Normal</span><span class="sxs-lookup"><span data-stu-id="45517-113">Normal</span></span>|<span data-ttu-id="45517-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="45517-114">CommonStates</span></span>|<span data-ttu-id="45517-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="45517-115">The default state.</span></span>|
|<span data-ttu-id="45517-116">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="45517-116">MouseOver</span></span>|<span data-ttu-id="45517-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="45517-117">CommonStates</span></span>|<span data-ttu-id="45517-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="45517-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="45517-119">Basılan</span><span class="sxs-lookup"><span data-stu-id="45517-119">Pressed</span></span>|<span data-ttu-id="45517-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="45517-120">CommonStates</span></span>|<span data-ttu-id="45517-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="45517-121">The control is pressed.</span></span>|
|<span data-ttu-id="45517-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="45517-122">Disabled</span></span>|<span data-ttu-id="45517-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="45517-123">CommonStates</span></span>|<span data-ttu-id="45517-124">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="45517-124">The control is disabled.</span></span>|
|<span data-ttu-id="45517-125">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="45517-125">Focused</span></span>|<span data-ttu-id="45517-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="45517-126">FocusStates</span></span>|<span data-ttu-id="45517-127">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="45517-127">The control has focus.</span></span>|
|<span data-ttu-id="45517-128">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="45517-128">Unfocused</span></span>|<span data-ttu-id="45517-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="45517-129">FocusStates</span></span>|<span data-ttu-id="45517-130">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="45517-130">The control does not have focus.</span></span>|
|<span data-ttu-id="45517-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="45517-131">Valid</span></span>|<span data-ttu-id="45517-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="45517-132">ValidationStates</span></span>|<span data-ttu-id="45517-133">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="45517-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="45517-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="45517-134">InvalidFocused</span></span>|<span data-ttu-id="45517-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="45517-135">ValidationStates</span></span>|<span data-ttu-id="45517-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="45517-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="45517-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="45517-137">InvalidUnfocused</span></span>|<span data-ttu-id="45517-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="45517-138">ValidationStates</span></span>|<span data-ttu-id="45517-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="45517-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="45517-140">Thumb ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="45517-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="45517-141">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.Thumb> denetimi.</span><span class="sxs-lookup"><span data-stu-id="45517-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="45517-142">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="45517-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="45517-143">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="45517-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="45517-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45517-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="45517-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="45517-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="45517-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="45517-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="45517-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="45517-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="45517-148">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="45517-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
