---
title: Düğme Stilleri ve Şablonları
description: Windows Presentation Foundation Button denetimi için stiller ve şablonlar hakkında bilgi edinin. Denetime benzersiz bir görünüm sağlamak için ControlTemplate 'i değiştirin.
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 11509adeef397f26eb040e6e98d0edb333b2515f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166261"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="9c601-104">Düğme Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="9c601-104">Button Styles and Templates</span></span>
<span data-ttu-id="9c601-105">Bu konuda, denetimin stilleri ve şablonları açıklanmaktadır <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="9c601-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="9c601-106"><xref:System.Windows.Controls.ControlTemplate>Denetim için benzersiz bir görünüm sağlamak üzere varsayılan ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c601-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9c601-107">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="9c601-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="9c601-108">Düğme bölümleri</span><span class="sxs-lookup"><span data-stu-id="9c601-108">Button Parts</span></span>  
 <span data-ttu-id="9c601-109"><xref:System.Windows.Controls.Button>Denetimde hiçbir adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="9c601-109">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="9c601-110">Düğme durumları</span><span class="sxs-lookup"><span data-stu-id="9c601-110">Button States</span></span>  
 <span data-ttu-id="9c601-111">Aşağıdaki tabloda denetim için görsel durumlar listelenmektedir <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="9c601-111">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="9c601-112">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="9c601-112">VisualState Name</span></span>|<span data-ttu-id="9c601-113">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="9c601-113">VisualStateGroup Name</span></span>|<span data-ttu-id="9c601-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c601-114">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="9c601-115">Normal</span><span class="sxs-lookup"><span data-stu-id="9c601-115">Normal</span></span>|<span data-ttu-id="9c601-116">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="9c601-116">CommonStates</span></span>|<span data-ttu-id="9c601-117">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="9c601-117">The default state.</span></span>|  
|<span data-ttu-id="9c601-118">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="9c601-118">MouseOver</span></span>|<span data-ttu-id="9c601-119">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="9c601-119">CommonStates</span></span>|<span data-ttu-id="9c601-120">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9c601-120">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="9c601-121">Pressed</span><span class="sxs-lookup"><span data-stu-id="9c601-121">Pressed</span></span>|<span data-ttu-id="9c601-122">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="9c601-122">CommonStates</span></span>|<span data-ttu-id="9c601-123">Denetime basıldığında.</span><span class="sxs-lookup"><span data-stu-id="9c601-123">The control is pressed.</span></span>|  
|<span data-ttu-id="9c601-124">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="9c601-124">Disabled</span></span>|<span data-ttu-id="9c601-125">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="9c601-125">CommonStates</span></span>|<span data-ttu-id="9c601-126">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9c601-126">The control is disabled.</span></span>|  
|<span data-ttu-id="9c601-127">Odaklı</span><span class="sxs-lookup"><span data-stu-id="9c601-127">Focused</span></span>|<span data-ttu-id="9c601-128">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="9c601-128">FocusStates</span></span>|<span data-ttu-id="9c601-129">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9c601-129">The control has focus.</span></span>|  
|<span data-ttu-id="9c601-130">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="9c601-130">Unfocused</span></span>|<span data-ttu-id="9c601-131">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="9c601-131">FocusStates</span></span>|<span data-ttu-id="9c601-132">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="9c601-132">The control does not have focus.</span></span>|  
|<span data-ttu-id="9c601-133">Geçerli</span><span class="sxs-lookup"><span data-stu-id="9c601-133">Valid</span></span>|<span data-ttu-id="9c601-134">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="9c601-134">ValidationStates</span></span>|<span data-ttu-id="9c601-135">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği kullanır `false` .</span><span class="sxs-lookup"><span data-stu-id="9c601-135">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="9c601-136">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="9c601-136">InvalidFocused</span></span>|<span data-ttu-id="9c601-137">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="9c601-137">ValidationStates</span></span>|<span data-ttu-id="9c601-138"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özelliği `true` ve denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9c601-138">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="9c601-139">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="9c601-139">InvalidUnfocused</span></span>|<span data-ttu-id="9c601-140">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="9c601-140">ValidationStates</span></span>|<span data-ttu-id="9c601-141"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özelliği `true` ve denetim odağa sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="9c601-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="9c601-142">Düğme ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="9c601-142">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="9c601-143">Aşağıdaki örnek, denetimi için nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="9c601-143">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="9c601-144">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9c601-144">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="9c601-145">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="9c601-145">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c601-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c601-146">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="9c601-147">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="9c601-147">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="9c601-148">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="9c601-148">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="9c601-149">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c601-149">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="9c601-150">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="9c601-150">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
