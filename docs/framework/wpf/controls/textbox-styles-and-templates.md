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
ms.openlocfilehash: 16f087051e438fa0dbe248c46b0ec555c07cc06c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367914"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="6be82-102">TextBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="6be82-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="6be82-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="6be82-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="6be82-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="6be82-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6be82-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6be82-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="6be82-106">Metin parçaları</span><span class="sxs-lookup"><span data-stu-id="6be82-106">TextBox Parts</span></span>  
 <span data-ttu-id="6be82-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="6be82-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="6be82-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="6be82-108">Part</span></span>|<span data-ttu-id="6be82-109">Tür</span><span class="sxs-lookup"><span data-stu-id="6be82-109">Type</span></span>|<span data-ttu-id="6be82-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be82-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6be82-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="6be82-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="6be82-112">İçeren bir görsel öğe bir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="6be82-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="6be82-113">Metnin <xref:System.Windows.Controls.TextBox> bu öğe görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6be82-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="6be82-114">Metin kutusuna durumları</span><span class="sxs-lookup"><span data-stu-id="6be82-114">TextBox States</span></span>  
 <span data-ttu-id="6be82-115">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="6be82-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="6be82-116">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="6be82-116">VisualState Name</span></span>|<span data-ttu-id="6be82-117">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="6be82-117">VisualStateGroup Name</span></span>|<span data-ttu-id="6be82-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6be82-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="6be82-119">Normal</span><span class="sxs-lookup"><span data-stu-id="6be82-119">Normal</span></span>|<span data-ttu-id="6be82-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6be82-120">CommonStates</span></span>|<span data-ttu-id="6be82-121">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="6be82-121">The default state.</span></span>|  
|<span data-ttu-id="6be82-122">Fareyi üzerine getirme</span><span class="sxs-lookup"><span data-stu-id="6be82-122">MouseOver</span></span>|<span data-ttu-id="6be82-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6be82-123">CommonStates</span></span>|<span data-ttu-id="6be82-124">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6be82-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="6be82-125">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="6be82-125">Disabled</span></span>|<span data-ttu-id="6be82-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6be82-126">CommonStates</span></span>|<span data-ttu-id="6be82-127">Denetim devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="6be82-127">The control is disabled.</span></span>|  
|<span data-ttu-id="6be82-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="6be82-128">ReadOnly</span></span>|<span data-ttu-id="6be82-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6be82-129">CommonStates</span></span>|<span data-ttu-id="6be82-130">Kullanıcının metni değiştiremezsiniz <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="6be82-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="6be82-131">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="6be82-131">Focused</span></span>|<span data-ttu-id="6be82-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6be82-132">FocusStates</span></span>|<span data-ttu-id="6be82-133">Denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="6be82-133">The control has focus.</span></span>|  
|<span data-ttu-id="6be82-134">Plana odaklanmadan</span><span class="sxs-lookup"><span data-stu-id="6be82-134">Unfocused</span></span>|<span data-ttu-id="6be82-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6be82-135">FocusStates</span></span>|<span data-ttu-id="6be82-136">Denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6be82-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="6be82-137">Geçerli</span><span class="sxs-lookup"><span data-stu-id="6be82-137">Valid</span></span>|<span data-ttu-id="6be82-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6be82-138">ValidationStates</span></span>|<span data-ttu-id="6be82-139">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="6be82-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6be82-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6be82-140">InvalidFocused</span></span>|<span data-ttu-id="6be82-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6be82-141">ValidationStates</span></span>|<span data-ttu-id="6be82-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="6be82-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6be82-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6be82-143">InvalidUnfocused</span></span>|<span data-ttu-id="6be82-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6be82-144">ValidationStates</span></span>|<span data-ttu-id="6be82-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6be82-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="6be82-146">TextBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="6be82-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="6be82-147">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="6be82-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="6be82-148">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6be82-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6be82-149">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="6be82-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be82-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6be82-150">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6be82-151">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="6be82-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6be82-152">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6be82-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6be82-153">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6be82-153">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="6be82-154">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6be82-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
