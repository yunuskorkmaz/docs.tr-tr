---
title: TextBox Stilleri ve Şablonları
description: Windows Presentation Foundation TextBox denetimi için stiller ve şablonlar hakkında bilgi edinin. Denetime benzersiz bir görünüm sağlamak için ControlTemplate 'i değiştirin.
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164734"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="cc242-104">TextBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="cc242-104">TextBox Styles and Templates</span></span>
<span data-ttu-id="cc242-105">Bu konuda, denetimin stilleri ve şablonları açıklanmaktadır <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="cc242-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="cc242-106"><xref:System.Windows.Controls.ControlTemplate>Denetim için benzersiz bir görünüm sağlamak üzere varsayılan ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc242-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="cc242-107">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="cc242-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="cc242-108">Metin kutusu parçaları</span><span class="sxs-lookup"><span data-stu-id="cc242-108">TextBox Parts</span></span>  
 <span data-ttu-id="cc242-109">Aşağıdaki tabloda, denetimin adlandırılmış parçaları listelenmektedir <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="cc242-109">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="cc242-110">Bölüm</span><span class="sxs-lookup"><span data-stu-id="cc242-110">Part</span></span>|<span data-ttu-id="cc242-111">Tür</span><span class="sxs-lookup"><span data-stu-id="cc242-111">Type</span></span>|<span data-ttu-id="cc242-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc242-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="cc242-113">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="cc242-113">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="cc242-114">İçeren bir görsel öğe <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="cc242-114">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="cc242-115"><xref:System.Windows.Controls.TextBox>Öğesinin metni bu öğede görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cc242-115">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="cc242-116">Metin kutusu durumları</span><span class="sxs-lookup"><span data-stu-id="cc242-116">TextBox States</span></span>  
 <span data-ttu-id="cc242-117">Aşağıdaki tabloda denetim için görsel durumlar listelenmektedir <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="cc242-117">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="cc242-118">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="cc242-118">VisualState Name</span></span>|<span data-ttu-id="cc242-119">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="cc242-119">VisualStateGroup Name</span></span>|<span data-ttu-id="cc242-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc242-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="cc242-121">Normal</span><span class="sxs-lookup"><span data-stu-id="cc242-121">Normal</span></span>|<span data-ttu-id="cc242-122">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="cc242-122">CommonStates</span></span>|<span data-ttu-id="cc242-123">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="cc242-123">The default state.</span></span>|  
|<span data-ttu-id="cc242-124">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="cc242-124">MouseOver</span></span>|<span data-ttu-id="cc242-125">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="cc242-125">CommonStates</span></span>|<span data-ttu-id="cc242-126">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cc242-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="cc242-127">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="cc242-127">Disabled</span></span>|<span data-ttu-id="cc242-128">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="cc242-128">CommonStates</span></span>|<span data-ttu-id="cc242-129">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="cc242-129">The control is disabled.</span></span>|  
|<span data-ttu-id="cc242-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="cc242-130">ReadOnly</span></span>|<span data-ttu-id="cc242-131">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="cc242-131">CommonStates</span></span>|<span data-ttu-id="cc242-132">Kullanıcı içindeki metni değiştiremiyor <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="cc242-132">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="cc242-133">Odaklı</span><span class="sxs-lookup"><span data-stu-id="cc242-133">Focused</span></span>|<span data-ttu-id="cc242-134">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="cc242-134">FocusStates</span></span>|<span data-ttu-id="cc242-135">Denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cc242-135">The control has focus.</span></span>|  
|<span data-ttu-id="cc242-136">Odaklanmadan gözetle</span><span class="sxs-lookup"><span data-stu-id="cc242-136">Unfocused</span></span>|<span data-ttu-id="cc242-137">Odaklardaki durumlar</span><span class="sxs-lookup"><span data-stu-id="cc242-137">FocusStates</span></span>|<span data-ttu-id="cc242-138">Denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="cc242-138">The control does not have focus.</span></span>|  
|<span data-ttu-id="cc242-139">Geçerli</span><span class="sxs-lookup"><span data-stu-id="cc242-139">Valid</span></span>|<span data-ttu-id="cc242-140">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="cc242-140">ValidationStates</span></span>|<span data-ttu-id="cc242-141">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği kullanır `false` .</span><span class="sxs-lookup"><span data-stu-id="cc242-141">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="cc242-142">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="cc242-142">InvalidFocused</span></span>|<span data-ttu-id="cc242-143">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="cc242-143">ValidationStates</span></span>|<span data-ttu-id="cc242-144"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özellikte `true` denetimin odağı vardır.</span><span class="sxs-lookup"><span data-stu-id="cc242-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="cc242-145">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="cc242-145">InvalidUnfocused</span></span>|<span data-ttu-id="cc242-146">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="cc242-146">ValidationStates</span></span>|<span data-ttu-id="cc242-147"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>İliştirilmiş özellikte, `true` denetimin odağı yok.</span><span class="sxs-lookup"><span data-stu-id="cc242-147">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="cc242-148">TextBox ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="cc242-148">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="cc242-149">Aşağıdaki örnek, denetimi için nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="cc242-149">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="cc242-150">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cc242-150">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="cc242-151">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="cc242-151">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc242-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc242-152">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="cc242-153">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="cc242-153">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="cc242-154">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cc242-154">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="cc242-155">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc242-155">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="cc242-156">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc242-156">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
