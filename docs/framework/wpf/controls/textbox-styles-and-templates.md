---
title: TextBox Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 41e390c261836909240cc146a48729d48c4a410e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283696"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="78e0a-102">TextBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="78e0a-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="78e0a-103">Bu konuda <xref:System.Windows.Controls.TextBox> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78e0a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="78e0a-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78e0a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="78e0a-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="78e0a-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="78e0a-106">Metin kutusu parçaları</span><span class="sxs-lookup"><span data-stu-id="78e0a-106">TextBox Parts</span></span>  
 <span data-ttu-id="78e0a-107">Aşağıdaki tabloda <xref:System.Windows.Controls.TextBox> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="78e0a-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="78e0a-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="78e0a-108">Part</span></span>|<span data-ttu-id="78e0a-109">Type</span><span class="sxs-lookup"><span data-stu-id="78e0a-109">Type</span></span>|<span data-ttu-id="78e0a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78e0a-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="78e0a-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="78e0a-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="78e0a-112"><xref:System.Windows.FrameworkElement>içerebilen görsel öğe.</span><span class="sxs-lookup"><span data-stu-id="78e0a-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="78e0a-113"><xref:System.Windows.Controls.TextBox> metni bu öğede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="78e0a-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="78e0a-114">Metin kutusu durumları</span><span class="sxs-lookup"><span data-stu-id="78e0a-114">TextBox States</span></span>  
 <span data-ttu-id="78e0a-115">Aşağıdaki tabloda <xref:System.Windows.Controls.TextBox> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="78e0a-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="78e0a-116">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="78e0a-116">VisualState Name</span></span>|<span data-ttu-id="78e0a-117">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="78e0a-117">VisualStateGroup Name</span></span>|<span data-ttu-id="78e0a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78e0a-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="78e0a-119">Normal</span><span class="sxs-lookup"><span data-stu-id="78e0a-119">Normal</span></span>|<span data-ttu-id="78e0a-120">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="78e0a-120">CommonStates</span></span>|<span data-ttu-id="78e0a-121">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="78e0a-121">The default state.</span></span>|  
|<span data-ttu-id="78e0a-122">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="78e0a-122">MouseOver</span></span>|<span data-ttu-id="78e0a-123">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="78e0a-123">CommonStates</span></span>|<span data-ttu-id="78e0a-124">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="78e0a-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="78e0a-125">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="78e0a-125">Disabled</span></span>|<span data-ttu-id="78e0a-126">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="78e0a-126">CommonStates</span></span>|<span data-ttu-id="78e0a-127">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="78e0a-127">The control is disabled.</span></span>|  
|<span data-ttu-id="78e0a-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="78e0a-128">ReadOnly</span></span>|<span data-ttu-id="78e0a-129">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="78e0a-129">CommonStates</span></span>|<span data-ttu-id="78e0a-130">Kullanıcı <xref:System.Windows.Controls.TextBox>metni değiştiremiyor.</span><span class="sxs-lookup"><span data-stu-id="78e0a-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="78e0a-131">Diğinize</span><span class="sxs-lookup"><span data-stu-id="78e0a-131">Focused</span></span>|<span data-ttu-id="78e0a-132">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="78e0a-132">FocusStates</span></span>|<span data-ttu-id="78e0a-133">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="78e0a-133">The control has focus.</span></span>|  
|<span data-ttu-id="78e0a-134">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="78e0a-134">Unfocused</span></span>|<span data-ttu-id="78e0a-135">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="78e0a-135">FocusStates</span></span>|<span data-ttu-id="78e0a-136">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="78e0a-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="78e0a-137">Geçerli</span><span class="sxs-lookup"><span data-stu-id="78e0a-137">Valid</span></span>|<span data-ttu-id="78e0a-138">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="78e0a-138">ValidationStates</span></span>|<span data-ttu-id="78e0a-139">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="78e0a-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="78e0a-140">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="78e0a-140">InvalidFocused</span></span>|<span data-ttu-id="78e0a-141">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="78e0a-141">ValidationStates</span></span>|<span data-ttu-id="78e0a-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="78e0a-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="78e0a-143">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="78e0a-143">InvalidUnfocused</span></span>|<span data-ttu-id="78e0a-144">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="78e0a-144">ValidationStates</span></span>|<span data-ttu-id="78e0a-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="78e0a-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="78e0a-146">TextBox ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="78e0a-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="78e0a-147">Aşağıdaki örnek, <xref:System.Windows.Controls.TextBox> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="78e0a-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="78e0a-148">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78e0a-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="78e0a-149">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="78e0a-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e0a-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78e0a-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="78e0a-151">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="78e0a-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="78e0a-152">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="78e0a-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="78e0a-153">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="78e0a-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="78e0a-154">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="78e0a-154">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
