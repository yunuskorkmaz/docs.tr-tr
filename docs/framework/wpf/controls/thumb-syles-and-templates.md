---
title: "Parmak Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 780ddc07c79aab111c17f9e7e551cfde85c68f3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="bbe6b-102">Parmak Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="bbe6b-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="bbe6b-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Primitives.Thumb> denetim.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="bbe6b-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="bbe6b-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="bbe6b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="bbe6b-106">Flash bölümleri</span><span class="sxs-lookup"><span data-stu-id="bbe6b-106">Thumb Parts</span></span>  
 <span data-ttu-id="bbe6b-107"><xref:System.Windows.Controls.Primitives.Thumb> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="bbe6b-108">Flash durumları</span><span class="sxs-lookup"><span data-stu-id="bbe6b-108">Thumb States</span></span>  
 <span data-ttu-id="bbe6b-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.Thumb> denetim.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="bbe6b-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="bbe6b-110">VisualState Name</span></span>|<span data-ttu-id="bbe6b-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="bbe6b-111">VisualStateGroup Name</span></span>|<span data-ttu-id="bbe6b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbe6b-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="bbe6b-113">Normal</span><span class="sxs-lookup"><span data-stu-id="bbe6b-113">Normal</span></span>|<span data-ttu-id="bbe6b-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbe6b-114">CommonStates</span></span>|<span data-ttu-id="bbe6b-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-115">The default state.</span></span>|  
|<span data-ttu-id="bbe6b-116">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="bbe6b-116">MouseOver</span></span>|<span data-ttu-id="bbe6b-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbe6b-117">CommonStates</span></span>|<span data-ttu-id="bbe6b-118">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="bbe6b-119">Basılı</span><span class="sxs-lookup"><span data-stu-id="bbe6b-119">Pressed</span></span>|<span data-ttu-id="bbe6b-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbe6b-120">CommonStates</span></span>|<span data-ttu-id="bbe6b-121">Denetim basıldığında.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-121">The control is pressed.</span></span>|  
|<span data-ttu-id="bbe6b-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="bbe6b-122">Disabled</span></span>|<span data-ttu-id="bbe6b-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="bbe6b-123">CommonStates</span></span>|<span data-ttu-id="bbe6b-124">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-124">The control is disabled.</span></span>|  
|<span data-ttu-id="bbe6b-125">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="bbe6b-125">Focused</span></span>|<span data-ttu-id="bbe6b-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="bbe6b-126">FocusStates</span></span>|<span data-ttu-id="bbe6b-127">Denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-127">The control has focus.</span></span>|  
|<span data-ttu-id="bbe6b-128">Odaksız</span><span class="sxs-lookup"><span data-stu-id="bbe6b-128">Unfocused</span></span>|<span data-ttu-id="bbe6b-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="bbe6b-129">FocusStates</span></span>|<span data-ttu-id="bbe6b-130">Denetim odağı yok.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="bbe6b-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="bbe6b-131">Valid</span></span>|<span data-ttu-id="bbe6b-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bbe6b-132">ValidationStates</span></span>|<span data-ttu-id="bbe6b-133">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="bbe6b-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="bbe6b-134">InvalidFocused</span></span>|<span data-ttu-id="bbe6b-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bbe6b-135">ValidationStates</span></span>|<span data-ttu-id="bbe6b-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="bbe6b-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="bbe6b-137">InvalidUnfocused</span></span>|<span data-ttu-id="bbe6b-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bbe6b-138">ValidationStates</span></span>|<span data-ttu-id="bbe6b-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="bbe6b-140">Flash ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="bbe6b-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="bbe6b-141">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.Thumb> denetim.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="bbe6b-142">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="bbe6b-143">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="bbe6b-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbe6b-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbe6b-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="bbe6b-145">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="bbe6b-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="bbe6b-146">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="bbe6b-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="bbe6b-147">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bbe6b-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="bbe6b-148">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="bbe6b-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
