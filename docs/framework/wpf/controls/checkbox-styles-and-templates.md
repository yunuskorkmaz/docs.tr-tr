---
title: "CheckBox Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], CheckBox
- templates [WPF], CheckBox
- parts [WPF], CheckBox
- ControlTemplate [WPF], CheckBox
- CheckBox [WPF], styles and templates
- styles [WPF], CheckBox
ms.assetid: bfdaec96-d101-4d3d-864d-c27e6b621d03
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c901d710e96cd111104b9fef2219b157377adc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="checkbox-styles-and-templates"></a><span data-ttu-id="d3b84-102">CheckBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d3b84-102">CheckBox Styles and Templates</span></span>
<span data-ttu-id="d3b84-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.CheckBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="d3b84-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.CheckBox> control.</span></span> <span data-ttu-id="d3b84-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="d3b84-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d3b84-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d3b84-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="checkbox-parts"></a><span data-ttu-id="d3b84-106">Onay kutusu bölümleri</span><span class="sxs-lookup"><span data-stu-id="d3b84-106">CheckBox Parts</span></span>  
 <span data-ttu-id="d3b84-107"><xref:System.Windows.Controls.CheckBox> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d3b84-107">The <xref:System.Windows.Controls.CheckBox> control does not have any named parts.</span></span>  
  
## <a name="checkbox-states"></a><span data-ttu-id="d3b84-108">CheckBox durumları</span><span class="sxs-lookup"><span data-stu-id="d3b84-108">CheckBox States</span></span>  
 <span data-ttu-id="d3b84-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.CheckBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="d3b84-109">The following table lists the visual states for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
|<span data-ttu-id="d3b84-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="d3b84-110">VisualState Name</span></span>|<span data-ttu-id="d3b84-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="d3b84-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d3b84-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3b84-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="d3b84-113">Normal</span><span class="sxs-lookup"><span data-stu-id="d3b84-113">Normal</span></span>|<span data-ttu-id="d3b84-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-114">CommonStates</span></span>|<span data-ttu-id="d3b84-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="d3b84-115">The default state.</span></span>|  
|<span data-ttu-id="d3b84-116">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="d3b84-116">MouseOver</span></span>|<span data-ttu-id="d3b84-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-117">CommonStates</span></span>|<span data-ttu-id="d3b84-118">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="d3b84-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="d3b84-119">Basılı</span><span class="sxs-lookup"><span data-stu-id="d3b84-119">Pressed</span></span>|<span data-ttu-id="d3b84-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-120">CommonStates</span></span>|<span data-ttu-id="d3b84-121">Denetim basıldığında.</span><span class="sxs-lookup"><span data-stu-id="d3b84-121">The control is pressed.</span></span>|  
|<span data-ttu-id="d3b84-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="d3b84-122">Disabled</span></span>|<span data-ttu-id="d3b84-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-123">CommonStates</span></span>|<span data-ttu-id="d3b84-124">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d3b84-124">The control is disabled.</span></span>|  
|<span data-ttu-id="d3b84-125">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="d3b84-125">Focused</span></span>|<span data-ttu-id="d3b84-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-126">FocusStates</span></span>|<span data-ttu-id="d3b84-127">Denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d3b84-127">The control has focus.</span></span>|  
|<span data-ttu-id="d3b84-128">Odaksız</span><span class="sxs-lookup"><span data-stu-id="d3b84-128">Unfocused</span></span>|<span data-ttu-id="d3b84-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-129">FocusStates</span></span>|<span data-ttu-id="d3b84-130">Denetim odağı yok.</span><span class="sxs-lookup"><span data-stu-id="d3b84-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="d3b84-131">İşaretli</span><span class="sxs-lookup"><span data-stu-id="d3b84-131">Checked</span></span>|<span data-ttu-id="d3b84-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-132">CheckStates</span></span>|<span data-ttu-id="d3b84-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>olan `true`.</span><span class="sxs-lookup"><span data-stu-id="d3b84-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="d3b84-134">İşaretli</span><span class="sxs-lookup"><span data-stu-id="d3b84-134">Unchecked</span></span>|<span data-ttu-id="d3b84-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-135">CheckStates</span></span>|<span data-ttu-id="d3b84-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>olan `false`.</span><span class="sxs-lookup"><span data-stu-id="d3b84-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="d3b84-137">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="d3b84-137">Indeterminate</span></span>|<span data-ttu-id="d3b84-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-138">CheckStates</span></span>|<span data-ttu-id="d3b84-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>olan `true`, ve <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> olan `null`.</span><span class="sxs-lookup"><span data-stu-id="d3b84-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="d3b84-140">Geçerli</span><span class="sxs-lookup"><span data-stu-id="d3b84-140">Valid</span></span>|<span data-ttu-id="d3b84-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-141">ValidationStates</span></span>|<span data-ttu-id="d3b84-142">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="d3b84-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d3b84-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d3b84-143">InvalidUnfocused</span></span>|<span data-ttu-id="d3b84-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-144">ValidationStates</span></span>|<span data-ttu-id="d3b84-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d3b84-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d3b84-146">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d3b84-146">InvalidFocused</span></span>|<span data-ttu-id="d3b84-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d3b84-147">ValidationStates</span></span>|<span data-ttu-id="d3b84-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d3b84-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="checkbox-controltemplate-example"></a><span data-ttu-id="d3b84-149">Onay kutusu ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="d3b84-149">CheckBox ControlTemplate Example</span></span>  
 <span data-ttu-id="d3b84-150">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.CheckBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="d3b84-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
 <span data-ttu-id="d3b84-151">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3b84-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d3b84-152">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="d3b84-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b84-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3b84-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d3b84-154">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="d3b84-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d3b84-155">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d3b84-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d3b84-156">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3b84-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d3b84-157">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d3b84-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
