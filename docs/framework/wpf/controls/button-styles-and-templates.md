---
title: "Düğme Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7bea309cea0ed6d21b747f31794f1ebb440bf102
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="6c1c7-102">Düğme Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="6c1c7-102">Button Styles and Templates</span></span>
<span data-ttu-id="6c1c7-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="6c1c7-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6c1c7-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6c1c7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="6c1c7-106">Düğme bölümleri</span><span class="sxs-lookup"><span data-stu-id="6c1c7-106">Button Parts</span></span>  
 <span data-ttu-id="6c1c7-107"><xref:System.Windows.Controls.Button> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="6c1c7-108">Düğme durumları</span><span class="sxs-lookup"><span data-stu-id="6c1c7-108">Button States</span></span>  
 <span data-ttu-id="6c1c7-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="6c1c7-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="6c1c7-110">VisualState Name</span></span>|<span data-ttu-id="6c1c7-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="6c1c7-111">VisualStateGroup Name</span></span>|<span data-ttu-id="6c1c7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c1c7-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6c1c7-113">Normal</span><span class="sxs-lookup"><span data-stu-id="6c1c7-113">Normal</span></span>|<span data-ttu-id="6c1c7-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6c1c7-114">CommonStates</span></span>|<span data-ttu-id="6c1c7-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-115">The default state.</span></span>|  
|<span data-ttu-id="6c1c7-116">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="6c1c7-116">MouseOver</span></span>|<span data-ttu-id="6c1c7-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6c1c7-117">CommonStates</span></span>|<span data-ttu-id="6c1c7-118">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="6c1c7-119">Basılı</span><span class="sxs-lookup"><span data-stu-id="6c1c7-119">Pressed</span></span>|<span data-ttu-id="6c1c7-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6c1c7-120">CommonStates</span></span>|<span data-ttu-id="6c1c7-121">Denetim basıldığında.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-121">The control is pressed.</span></span>|  
|<span data-ttu-id="6c1c7-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="6c1c7-122">Disabled</span></span>|<span data-ttu-id="6c1c7-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="6c1c7-123">CommonStates</span></span>|<span data-ttu-id="6c1c7-124">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-124">The control is disabled.</span></span>|  
|<span data-ttu-id="6c1c7-125">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="6c1c7-125">Focused</span></span>|<span data-ttu-id="6c1c7-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6c1c7-126">FocusStates</span></span>|<span data-ttu-id="6c1c7-127">Denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-127">The control has focus.</span></span>|  
|<span data-ttu-id="6c1c7-128">Odaksız</span><span class="sxs-lookup"><span data-stu-id="6c1c7-128">Unfocused</span></span>|<span data-ttu-id="6c1c7-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="6c1c7-129">FocusStates</span></span>|<span data-ttu-id="6c1c7-130">Denetim odağı yok.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="6c1c7-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="6c1c7-131">Valid</span></span>|<span data-ttu-id="6c1c7-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6c1c7-132">ValidationStates</span></span>|<span data-ttu-id="6c1c7-133">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6c1c7-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6c1c7-134">InvalidFocused</span></span>|<span data-ttu-id="6c1c7-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6c1c7-135">ValidationStates</span></span>|<span data-ttu-id="6c1c7-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6c1c7-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6c1c7-137">InvalidUnfocused</span></span>|<span data-ttu-id="6c1c7-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6c1c7-138">ValidationStates</span></span>|<span data-ttu-id="6c1c7-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="6c1c7-140">Düğme ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="6c1c7-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="6c1c7-141">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Button> denetim.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="6c1c7-142">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6c1c7-143">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="6c1c7-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c1c7-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c1c7-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="6c1c7-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="6c1c7-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="6c1c7-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6c1c7-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="6c1c7-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6c1c7-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="6c1c7-148">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6c1c7-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
