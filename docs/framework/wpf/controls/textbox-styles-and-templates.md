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
ms.openlocfilehash: ccc89e0e0c8977398ed162b246ff6cdede3b8351
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177950"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="8bf4f-102">TextBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="8bf4f-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="8bf4f-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="8bf4f-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8bf4f-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="8bf4f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="8bf4f-106">Metin parçaları</span><span class="sxs-lookup"><span data-stu-id="8bf4f-106">TextBox Parts</span></span>  
 <span data-ttu-id="8bf4f-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="8bf4f-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="8bf4f-108">Part</span></span>|<span data-ttu-id="8bf4f-109">Tür</span><span class="sxs-lookup"><span data-stu-id="8bf4f-109">Type</span></span>|<span data-ttu-id="8bf4f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bf4f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8bf4f-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="8bf4f-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="8bf4f-112">İçeren bir görsel öğe bir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="8bf4f-113">Metnin <xref:System.Windows.Controls.TextBox> bu öğe görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="8bf4f-114">Metin kutusuna durumları</span><span class="sxs-lookup"><span data-stu-id="8bf4f-114">TextBox States</span></span>  
 <span data-ttu-id="8bf4f-115">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="8bf4f-116">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="8bf4f-116">VisualState Name</span></span>|<span data-ttu-id="8bf4f-117">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="8bf4f-117">VisualStateGroup Name</span></span>|<span data-ttu-id="8bf4f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bf4f-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="8bf4f-119">Normal</span><span class="sxs-lookup"><span data-stu-id="8bf4f-119">Normal</span></span>|<span data-ttu-id="8bf4f-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8bf4f-120">CommonStates</span></span>|<span data-ttu-id="8bf4f-121">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-121">The default state.</span></span>|  
|<span data-ttu-id="8bf4f-122">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="8bf4f-122">MouseOver</span></span>|<span data-ttu-id="8bf4f-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8bf4f-123">CommonStates</span></span>|<span data-ttu-id="8bf4f-124">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="8bf4f-125">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="8bf4f-125">Disabled</span></span>|<span data-ttu-id="8bf4f-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8bf4f-126">CommonStates</span></span>|<span data-ttu-id="8bf4f-127">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-127">The control is disabled.</span></span>|  
|<span data-ttu-id="8bf4f-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="8bf4f-128">ReadOnly</span></span>|<span data-ttu-id="8bf4f-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8bf4f-129">CommonStates</span></span>|<span data-ttu-id="8bf4f-130">Kullanıcının metni değiştiremezsiniz <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="8bf4f-131">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="8bf4f-131">Focused</span></span>|<span data-ttu-id="8bf4f-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8bf4f-132">FocusStates</span></span>|<span data-ttu-id="8bf4f-133">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-133">The control has focus.</span></span>|  
|<span data-ttu-id="8bf4f-134">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="8bf4f-134">Unfocused</span></span>|<span data-ttu-id="8bf4f-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8bf4f-135">FocusStates</span></span>|<span data-ttu-id="8bf4f-136">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="8bf4f-137">Geçerli</span><span class="sxs-lookup"><span data-stu-id="8bf4f-137">Valid</span></span>|<span data-ttu-id="8bf4f-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8bf4f-138">ValidationStates</span></span>|<span data-ttu-id="8bf4f-139">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8bf4f-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8bf4f-140">InvalidFocused</span></span>|<span data-ttu-id="8bf4f-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8bf4f-141">ValidationStates</span></span>|<span data-ttu-id="8bf4f-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8bf4f-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8bf4f-143">InvalidUnfocused</span></span>|<span data-ttu-id="8bf4f-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8bf4f-144">ValidationStates</span></span>|<span data-ttu-id="8bf4f-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="8bf4f-146">TextBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="8bf4f-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="8bf4f-147">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="8bf4f-148">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8bf4f-149">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="8bf4f-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf4f-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bf4f-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="8bf4f-151">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="8bf4f-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="8bf4f-152">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8bf4f-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="8bf4f-153">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bf4f-153">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="8bf4f-154">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8bf4f-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
