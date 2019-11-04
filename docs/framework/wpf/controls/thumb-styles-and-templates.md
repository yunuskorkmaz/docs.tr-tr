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
ms.openlocfilehash: c2114a02016db96d898a394b6892b6d3042d81ff
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458244"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="ccc2e-102">Parmak Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="ccc2e-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="ccc2e-103">Bu konuda <xref:System.Windows.Controls.Primitives.Thumb> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="ccc2e-104">Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ccc2e-105">Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="ccc2e-106">Parmak parçaları</span><span class="sxs-lookup"><span data-stu-id="ccc2e-106">Thumb Parts</span></span>

<span data-ttu-id="ccc2e-107"><xref:System.Windows.Controls.Primitives.Thumb> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="ccc2e-108">Parmak izi durumları</span><span class="sxs-lookup"><span data-stu-id="ccc2e-108">Thumb States</span></span>

<span data-ttu-id="ccc2e-109">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.Thumb> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="ccc2e-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="ccc2e-110">VisualState Name</span></span>|<span data-ttu-id="ccc2e-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="ccc2e-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ccc2e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccc2e-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="ccc2e-113">Olağan</span><span class="sxs-lookup"><span data-stu-id="ccc2e-113">Normal</span></span>|<span data-ttu-id="ccc2e-114">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="ccc2e-114">CommonStates</span></span>|<span data-ttu-id="ccc2e-115">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-115">The default state.</span></span>|
|<span data-ttu-id="ccc2e-116">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="ccc2e-116">MouseOver</span></span>|<span data-ttu-id="ccc2e-117">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="ccc2e-117">CommonStates</span></span>|<span data-ttu-id="ccc2e-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="ccc2e-119">Basılması</span><span class="sxs-lookup"><span data-stu-id="ccc2e-119">Pressed</span></span>|<span data-ttu-id="ccc2e-120">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="ccc2e-120">CommonStates</span></span>|<span data-ttu-id="ccc2e-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-121">The control is pressed.</span></span>|
|<span data-ttu-id="ccc2e-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="ccc2e-122">Disabled</span></span>|<span data-ttu-id="ccc2e-123">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="ccc2e-123">CommonStates</span></span>|<span data-ttu-id="ccc2e-124">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-124">The control is disabled.</span></span>|
|<span data-ttu-id="ccc2e-125">Diğinize</span><span class="sxs-lookup"><span data-stu-id="ccc2e-125">Focused</span></span>|<span data-ttu-id="ccc2e-126">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="ccc2e-126">FocusStates</span></span>|<span data-ttu-id="ccc2e-127">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-127">The control has focus.</span></span>|
|<span data-ttu-id="ccc2e-128">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="ccc2e-128">Unfocused</span></span>|<span data-ttu-id="ccc2e-129">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="ccc2e-129">FocusStates</span></span>|<span data-ttu-id="ccc2e-130">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-130">The control does not have focus.</span></span>|
|<span data-ttu-id="ccc2e-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="ccc2e-131">Valid</span></span>|<span data-ttu-id="ccc2e-132">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="ccc2e-132">ValidationStates</span></span>|<span data-ttu-id="ccc2e-133">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="ccc2e-134">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="ccc2e-134">InvalidFocused</span></span>|<span data-ttu-id="ccc2e-135">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="ccc2e-135">ValidationStates</span></span>|<span data-ttu-id="ccc2e-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="ccc2e-137">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="ccc2e-137">InvalidUnfocused</span></span>|<span data-ttu-id="ccc2e-138">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="ccc2e-138">ValidationStates</span></span>|<span data-ttu-id="ccc2e-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="ccc2e-140">Thumb ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="ccc2e-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="ccc2e-141">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.Thumb> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="ccc2e-142">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="ccc2e-143">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="ccc2e-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ccc2e-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="ccc2e-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ccc2e-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ccc2e-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ccc2e-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ccc2e-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ccc2e-148">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ccc2e-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
