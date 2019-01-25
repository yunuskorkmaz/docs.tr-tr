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
ms.openlocfilehash: c04c1386f4663f5893915a07a1e0896a69c5412a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663680"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="5a7f5-102">TextBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="5a7f5-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="5a7f5-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="5a7f5-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5a7f5-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="5a7f5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="5a7f5-106">Metin parçaları</span><span class="sxs-lookup"><span data-stu-id="5a7f5-106">TextBox Parts</span></span>  
 <span data-ttu-id="5a7f5-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="5a7f5-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="5a7f5-108">Part</span></span>|<span data-ttu-id="5a7f5-109">Tür</span><span class="sxs-lookup"><span data-stu-id="5a7f5-109">Type</span></span>|<span data-ttu-id="5a7f5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a7f5-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5a7f5-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="5a7f5-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="5a7f5-112">İçeren bir görsel öğe bir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="5a7f5-113">Metnin <xref:System.Windows.Controls.TextBox> bu öğe görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="5a7f5-114">Metin kutusuna durumları</span><span class="sxs-lookup"><span data-stu-id="5a7f5-114">TextBox States</span></span>  
 <span data-ttu-id="5a7f5-115">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="5a7f5-116">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="5a7f5-116">VisualState Name</span></span>|<span data-ttu-id="5a7f5-117">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="5a7f5-117">VisualStateGroup Name</span></span>|<span data-ttu-id="5a7f5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a7f5-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="5a7f5-119">Normal</span><span class="sxs-lookup"><span data-stu-id="5a7f5-119">Normal</span></span>|<span data-ttu-id="5a7f5-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5a7f5-120">CommonStates</span></span>|<span data-ttu-id="5a7f5-121">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-121">The default state.</span></span>|  
|<span data-ttu-id="5a7f5-122">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="5a7f5-122">MouseOver</span></span>|<span data-ttu-id="5a7f5-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5a7f5-123">CommonStates</span></span>|<span data-ttu-id="5a7f5-124">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="5a7f5-125">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="5a7f5-125">Disabled</span></span>|<span data-ttu-id="5a7f5-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5a7f5-126">CommonStates</span></span>|<span data-ttu-id="5a7f5-127">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-127">The control is disabled.</span></span>|  
|<span data-ttu-id="5a7f5-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="5a7f5-128">ReadOnly</span></span>|<span data-ttu-id="5a7f5-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5a7f5-129">CommonStates</span></span>|<span data-ttu-id="5a7f5-130">Kullanıcının metni değiştiremezsiniz <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="5a7f5-131">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="5a7f5-131">Focused</span></span>|<span data-ttu-id="5a7f5-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5a7f5-132">FocusStates</span></span>|<span data-ttu-id="5a7f5-133">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-133">The control has focus.</span></span>|  
|<span data-ttu-id="5a7f5-134">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="5a7f5-134">Unfocused</span></span>|<span data-ttu-id="5a7f5-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5a7f5-135">FocusStates</span></span>|<span data-ttu-id="5a7f5-136">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="5a7f5-137">Geçerli</span><span class="sxs-lookup"><span data-stu-id="5a7f5-137">Valid</span></span>|<span data-ttu-id="5a7f5-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5a7f5-138">ValidationStates</span></span>|<span data-ttu-id="5a7f5-139">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5a7f5-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5a7f5-140">InvalidFocused</span></span>|<span data-ttu-id="5a7f5-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5a7f5-141">ValidationStates</span></span>|<span data-ttu-id="5a7f5-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5a7f5-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5a7f5-143">InvalidUnfocused</span></span>|<span data-ttu-id="5a7f5-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5a7f5-144">ValidationStates</span></span>|<span data-ttu-id="5a7f5-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="5a7f5-146">TextBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="5a7f5-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="5a7f5-147">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="5a7f5-148">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5a7f5-149">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="5a7f5-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a7f5-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a7f5-150">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="5a7f5-151">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="5a7f5-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="5a7f5-152">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5a7f5-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="5a7f5-153">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a7f5-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="5a7f5-154">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5a7f5-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
