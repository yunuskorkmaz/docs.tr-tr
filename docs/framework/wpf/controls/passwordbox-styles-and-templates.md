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
ms.openlocfilehash: 4ba90182468466773644c7375059f0cc01675b33
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283459"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="e0718-102">PasswordBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="e0718-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="e0718-103">Bu konuda <xref:System.Windows.Controls.PasswordBox> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0718-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="e0718-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0718-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e0718-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="e0718-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="e0718-106">PasswordBox bölümleri</span><span class="sxs-lookup"><span data-stu-id="e0718-106">PasswordBox Parts</span></span>

<span data-ttu-id="e0718-107">Aşağıdaki tabloda <xref:System.Windows.Controls.PasswordBox> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0718-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="e0718-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="e0718-108">Part</span></span>|<span data-ttu-id="e0718-109">Type</span><span class="sxs-lookup"><span data-stu-id="e0718-109">Type</span></span>|<span data-ttu-id="e0718-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0718-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="e0718-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="e0718-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="e0718-112"><xref:System.Windows.FrameworkElement>içerebilen görsel öğe.</span><span class="sxs-lookup"><span data-stu-id="e0718-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="e0718-113"><xref:System.Windows.Controls.PasswordBox> metni bu öğede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e0718-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="e0718-114">PasswordBox durumları</span><span class="sxs-lookup"><span data-stu-id="e0718-114">PasswordBox States</span></span>

<span data-ttu-id="e0718-115">Aşağıdaki tabloda <xref:System.Windows.Controls.PasswordBox> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0718-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="e0718-116">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="e0718-116">VisualState Name</span></span>|<span data-ttu-id="e0718-117">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="e0718-117">VisualStateGroup Name</span></span>|<span data-ttu-id="e0718-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0718-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="e0718-119">Normal</span><span class="sxs-lookup"><span data-stu-id="e0718-119">Normal</span></span>|<span data-ttu-id="e0718-120">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="e0718-120">CommonStates</span></span>|<span data-ttu-id="e0718-121">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="e0718-121">The default state.</span></span>|
|<span data-ttu-id="e0718-122">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="e0718-122">MouseOver</span></span>|<span data-ttu-id="e0718-123">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="e0718-123">CommonStates</span></span>|<span data-ttu-id="e0718-124">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e0718-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="e0718-125">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="e0718-125">Disabled</span></span>|<span data-ttu-id="e0718-126">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="e0718-126">CommonStates</span></span>|<span data-ttu-id="e0718-127">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e0718-127">The control is disabled.</span></span>|
|<span data-ttu-id="e0718-128">Diğinize</span><span class="sxs-lookup"><span data-stu-id="e0718-128">Focused</span></span>|<span data-ttu-id="e0718-129">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="e0718-129">FocusStates</span></span>|<span data-ttu-id="e0718-130">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e0718-130">The control has focus.</span></span>|
|<span data-ttu-id="e0718-131">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="e0718-131">Unfocused</span></span>|<span data-ttu-id="e0718-132">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="e0718-132">FocusStates</span></span>|<span data-ttu-id="e0718-133">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="e0718-133">The control does not have focus.</span></span>|
|<span data-ttu-id="e0718-134">Geçerli</span><span class="sxs-lookup"><span data-stu-id="e0718-134">Valid</span></span>|<span data-ttu-id="e0718-135">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="e0718-135">ValidationStates</span></span>|<span data-ttu-id="e0718-136">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0718-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="e0718-137">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="e0718-137">InvalidFocused</span></span>|<span data-ttu-id="e0718-138">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="e0718-138">ValidationStates</span></span>|<span data-ttu-id="e0718-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="e0718-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="e0718-140">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="e0718-140">InvalidUnfocused</span></span>|<span data-ttu-id="e0718-141">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="e0718-141">ValidationStates</span></span>|<span data-ttu-id="e0718-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="e0718-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="e0718-143">PasswordBox ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="e0718-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="e0718-144">Aşağıdaki örnek, <xref:System.Windows.Controls.PasswordBox> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0718-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="e0718-145">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0718-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="e0718-146">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="e0718-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0718-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0718-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e0718-148">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="e0718-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="e0718-149">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e0718-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="e0718-150">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0718-150">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="e0718-151">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0718-151">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
