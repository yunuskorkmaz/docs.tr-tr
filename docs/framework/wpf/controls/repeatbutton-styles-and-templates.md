---
title: RepeatButton Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 8585e98536fd908daa11f21da395cab44924d612
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283422"
---
# <a name="repeatbutton-styles-and-templates"></a><span data-ttu-id="42f78-102">RepeatButton Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="42f78-102">RepeatButton Styles and Templates</span></span>

<span data-ttu-id="42f78-103">Bu konuda <xref:System.Windows.Controls.Primitives.RepeatButton> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42f78-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span> <span data-ttu-id="42f78-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42f78-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="42f78-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="42f78-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="repeatbutton-parts"></a><span data-ttu-id="42f78-106">RepeatButton bölümleri</span><span class="sxs-lookup"><span data-stu-id="42f78-106">RepeatButton Parts</span></span>

<span data-ttu-id="42f78-107"><xref:System.Windows.Controls.Primitives.RepeatButton> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="42f78-107">The <xref:System.Windows.Controls.Primitives.RepeatButton> control does not have any named parts.</span></span>

## <a name="repeatbutton-states"></a><span data-ttu-id="42f78-108">RepeatButton durumları</span><span class="sxs-lookup"><span data-stu-id="42f78-108">RepeatButton States</span></span>

<span data-ttu-id="42f78-109">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="42f78-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

|<span data-ttu-id="42f78-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="42f78-110">VisualState Name</span></span>|<span data-ttu-id="42f78-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="42f78-111">VisualStateGroup Name</span></span>|<span data-ttu-id="42f78-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42f78-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="42f78-113">Normal</span><span class="sxs-lookup"><span data-stu-id="42f78-113">Normal</span></span>|<span data-ttu-id="42f78-114">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="42f78-114">CommonStates</span></span>|<span data-ttu-id="42f78-115">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="42f78-115">The default state.</span></span>|
|<span data-ttu-id="42f78-116">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="42f78-116">MouseOver</span></span>|<span data-ttu-id="42f78-117">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="42f78-117">CommonStates</span></span>|<span data-ttu-id="42f78-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="42f78-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="42f78-119">Basılan</span><span class="sxs-lookup"><span data-stu-id="42f78-119">Pressed</span></span>|<span data-ttu-id="42f78-120">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="42f78-120">CommonStates</span></span>|<span data-ttu-id="42f78-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="42f78-121">The control is pressed.</span></span>|
|<span data-ttu-id="42f78-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="42f78-122">Disabled</span></span>|<span data-ttu-id="42f78-123">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="42f78-123">CommonStates</span></span>|<span data-ttu-id="42f78-124">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="42f78-124">The control is disabled.</span></span>|
|<span data-ttu-id="42f78-125">Diğinize</span><span class="sxs-lookup"><span data-stu-id="42f78-125">Focused</span></span>|<span data-ttu-id="42f78-126">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="42f78-126">FocusStates</span></span>|<span data-ttu-id="42f78-127">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="42f78-127">The control has focus.</span></span>|
|<span data-ttu-id="42f78-128">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="42f78-128">Unfocused</span></span>|<span data-ttu-id="42f78-129">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="42f78-129">FocusStates</span></span>|<span data-ttu-id="42f78-130">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="42f78-130">The control does not have focus.</span></span>|
|<span data-ttu-id="42f78-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="42f78-131">Valid</span></span>|<span data-ttu-id="42f78-132">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="42f78-132">ValidationStates</span></span>|<span data-ttu-id="42f78-133">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="42f78-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="42f78-134">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="42f78-134">InvalidFocused</span></span>|<span data-ttu-id="42f78-135">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="42f78-135">ValidationStates</span></span>|<span data-ttu-id="42f78-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="42f78-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="42f78-137">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="42f78-137">InvalidUnfocused</span></span>|<span data-ttu-id="42f78-138">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="42f78-138">ValidationStates</span></span>|<span data-ttu-id="42f78-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="42f78-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="repeatbutton-controltemplate-example"></a><span data-ttu-id="42f78-140">RepeatButton ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="42f78-140">RepeatButton ControlTemplate Example</span></span>

<span data-ttu-id="42f78-141">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="42f78-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.RepeatButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

<span data-ttu-id="42f78-142">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42f78-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="42f78-143">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="42f78-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="42f78-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42f78-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="42f78-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="42f78-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="42f78-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="42f78-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="42f78-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="42f78-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="42f78-148">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="42f78-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
