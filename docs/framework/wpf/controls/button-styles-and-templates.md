---
title: Düğme Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: ef9f85848ebdda9dc4ae15d0f54847eacd46e24d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283575"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="f7e73-102">Düğme Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="f7e73-102">Button Styles and Templates</span></span>
<span data-ttu-id="f7e73-103">Bu konuda <xref:System.Windows.Controls.Button> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7e73-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="f7e73-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7e73-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f7e73-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="f7e73-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="f7e73-106">Düğme bölümleri</span><span class="sxs-lookup"><span data-stu-id="f7e73-106">Button Parts</span></span>  
 <span data-ttu-id="f7e73-107"><xref:System.Windows.Controls.Button> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="f7e73-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="f7e73-108">Düğme durumları</span><span class="sxs-lookup"><span data-stu-id="f7e73-108">Button States</span></span>  
 <span data-ttu-id="f7e73-109">Aşağıdaki tabloda <xref:System.Windows.Controls.Button> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="f7e73-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="f7e73-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="f7e73-110">VisualState Name</span></span>|<span data-ttu-id="f7e73-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="f7e73-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f7e73-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7e73-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f7e73-113">Normal</span><span class="sxs-lookup"><span data-stu-id="f7e73-113">Normal</span></span>|<span data-ttu-id="f7e73-114">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="f7e73-114">CommonStates</span></span>|<span data-ttu-id="f7e73-115">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="f7e73-115">The default state.</span></span>|  
|<span data-ttu-id="f7e73-116">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="f7e73-116">MouseOver</span></span>|<span data-ttu-id="f7e73-117">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="f7e73-117">CommonStates</span></span>|<span data-ttu-id="f7e73-118">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f7e73-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f7e73-119">Basılan</span><span class="sxs-lookup"><span data-stu-id="f7e73-119">Pressed</span></span>|<span data-ttu-id="f7e73-120">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="f7e73-120">CommonStates</span></span>|<span data-ttu-id="f7e73-121">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="f7e73-121">The control is pressed.</span></span>|  
|<span data-ttu-id="f7e73-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="f7e73-122">Disabled</span></span>|<span data-ttu-id="f7e73-123">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="f7e73-123">CommonStates</span></span>|<span data-ttu-id="f7e73-124">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f7e73-124">The control is disabled.</span></span>|  
|<span data-ttu-id="f7e73-125">Diğinize</span><span class="sxs-lookup"><span data-stu-id="f7e73-125">Focused</span></span>|<span data-ttu-id="f7e73-126">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="f7e73-126">FocusStates</span></span>|<span data-ttu-id="f7e73-127">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7e73-127">The control has focus.</span></span>|  
|<span data-ttu-id="f7e73-128">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="f7e73-128">Unfocused</span></span>|<span data-ttu-id="f7e73-129">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="f7e73-129">FocusStates</span></span>|<span data-ttu-id="f7e73-130">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="f7e73-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="f7e73-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="f7e73-131">Valid</span></span>|<span data-ttu-id="f7e73-132">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="f7e73-132">ValidationStates</span></span>|<span data-ttu-id="f7e73-133">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7e73-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f7e73-134">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="f7e73-134">InvalidFocused</span></span>|<span data-ttu-id="f7e73-135">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="f7e73-135">ValidationStates</span></span>|<span data-ttu-id="f7e73-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `true` ve denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7e73-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="f7e73-137">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="f7e73-137">InvalidUnfocused</span></span>|<span data-ttu-id="f7e73-138">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="f7e73-138">ValidationStates</span></span>|<span data-ttu-id="f7e73-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `true` ve denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f7e73-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="f7e73-140">Düğme ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="f7e73-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="f7e73-141">Aşağıdaki örnek, <xref:System.Windows.Controls.Button> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7e73-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="f7e73-142">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f7e73-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f7e73-143">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f7e73-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e73-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7e73-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f7e73-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="f7e73-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f7e73-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="f7e73-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f7e73-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7e73-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f7e73-148">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7e73-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
