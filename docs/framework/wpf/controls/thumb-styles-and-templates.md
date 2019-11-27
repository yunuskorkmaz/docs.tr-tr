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
ms.openlocfilehash: 0d0d88e3b527beacfa5f879027e696aa75b18147
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283689"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="21014-102">Parmak Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="21014-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="21014-103">Bu konuda <xref:System.Windows.Controls.Primitives.Thumb> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21014-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="21014-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21014-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="21014-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="21014-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="21014-106">Parmak parçaları</span><span class="sxs-lookup"><span data-stu-id="21014-106">Thumb Parts</span></span>

<span data-ttu-id="21014-107"><xref:System.Windows.Controls.Primitives.Thumb> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="21014-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="21014-108">Parmak izi durumları</span><span class="sxs-lookup"><span data-stu-id="21014-108">Thumb States</span></span>

<span data-ttu-id="21014-109">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.Thumb> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="21014-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="21014-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="21014-110">VisualState Name</span></span>|<span data-ttu-id="21014-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="21014-111">VisualStateGroup Name</span></span>|<span data-ttu-id="21014-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21014-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="21014-113">Normal</span><span class="sxs-lookup"><span data-stu-id="21014-113">Normal</span></span>|<span data-ttu-id="21014-114">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="21014-114">CommonStates</span></span>|<span data-ttu-id="21014-115">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="21014-115">The default state.</span></span>|
|<span data-ttu-id="21014-116">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="21014-116">MouseOver</span></span>|<span data-ttu-id="21014-117">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="21014-117">CommonStates</span></span>|<span data-ttu-id="21014-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="21014-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="21014-119">Basılan</span><span class="sxs-lookup"><span data-stu-id="21014-119">Pressed</span></span>|<span data-ttu-id="21014-120">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="21014-120">CommonStates</span></span>|<span data-ttu-id="21014-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="21014-121">The control is pressed.</span></span>|
|<span data-ttu-id="21014-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="21014-122">Disabled</span></span>|<span data-ttu-id="21014-123">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="21014-123">CommonStates</span></span>|<span data-ttu-id="21014-124">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="21014-124">The control is disabled.</span></span>|
|<span data-ttu-id="21014-125">Diğinize</span><span class="sxs-lookup"><span data-stu-id="21014-125">Focused</span></span>|<span data-ttu-id="21014-126">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="21014-126">FocusStates</span></span>|<span data-ttu-id="21014-127">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="21014-127">The control has focus.</span></span>|
|<span data-ttu-id="21014-128">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="21014-128">Unfocused</span></span>|<span data-ttu-id="21014-129">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="21014-129">FocusStates</span></span>|<span data-ttu-id="21014-130">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="21014-130">The control does not have focus.</span></span>|
|<span data-ttu-id="21014-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="21014-131">Valid</span></span>|<span data-ttu-id="21014-132">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="21014-132">ValidationStates</span></span>|<span data-ttu-id="21014-133">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="21014-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="21014-134">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="21014-134">InvalidFocused</span></span>|<span data-ttu-id="21014-135">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="21014-135">ValidationStates</span></span>|<span data-ttu-id="21014-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="21014-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="21014-137">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="21014-137">InvalidUnfocused</span></span>|<span data-ttu-id="21014-138">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="21014-138">ValidationStates</span></span>|<span data-ttu-id="21014-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="21014-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="21014-140">Thumb ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="21014-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="21014-141">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.Thumb> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21014-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="21014-142">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21014-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="21014-143">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="21014-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="21014-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21014-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="21014-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="21014-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="21014-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="21014-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="21014-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="21014-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="21014-148">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="21014-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
