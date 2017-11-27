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
ms.openlocfilehash: 7d9f0b8559497939737b97568a679953d392d5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="d3fdb-102">Parmak Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d3fdb-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="d3fdb-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Primitives.Thumb> denetim.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="d3fdb-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d3fdb-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d3fdb-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="d3fdb-106">Flash bölümleri</span><span class="sxs-lookup"><span data-stu-id="d3fdb-106">Thumb Parts</span></span>  
 <span data-ttu-id="d3fdb-107"><xref:System.Windows.Controls.Primitives.Thumb> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="d3fdb-108">Flash durumları</span><span class="sxs-lookup"><span data-stu-id="d3fdb-108">Thumb States</span></span>  
 <span data-ttu-id="d3fdb-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.Thumb> denetim.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="d3fdb-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="d3fdb-110">VisualState Name</span></span>|<span data-ttu-id="d3fdb-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="d3fdb-111">VisualStateGroup Name</span></span>|<span data-ttu-id="d3fdb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3fdb-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d3fdb-113">Normal</span><span class="sxs-lookup"><span data-stu-id="d3fdb-113">Normal</span></span>|<span data-ttu-id="d3fdb-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d3fdb-114">CommonStates</span></span>|<span data-ttu-id="d3fdb-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-115">The default state.</span></span>|  
|<span data-ttu-id="d3fdb-116">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="d3fdb-116">MouseOver</span></span>|<span data-ttu-id="d3fdb-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d3fdb-117">CommonStates</span></span>|<span data-ttu-id="d3fdb-118">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="d3fdb-119">Basılı</span><span class="sxs-lookup"><span data-stu-id="d3fdb-119">Pressed</span></span>|<span data-ttu-id="d3fdb-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d3fdb-120">CommonStates</span></span>|<span data-ttu-id="d3fdb-121">Denetim basıldığında.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-121">The control is pressed.</span></span>|  
|<span data-ttu-id="d3fdb-122">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="d3fdb-122">Disabled</span></span>|<span data-ttu-id="d3fdb-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="d3fdb-123">CommonStates</span></span>|<span data-ttu-id="d3fdb-124">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-124">The control is disabled.</span></span>|  
|<span data-ttu-id="d3fdb-125">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="d3fdb-125">Focused</span></span>|<span data-ttu-id="d3fdb-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d3fdb-126">FocusStates</span></span>|<span data-ttu-id="d3fdb-127">Denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-127">The control has focus.</span></span>|  
|<span data-ttu-id="d3fdb-128">Odaksız</span><span class="sxs-lookup"><span data-stu-id="d3fdb-128">Unfocused</span></span>|<span data-ttu-id="d3fdb-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="d3fdb-129">FocusStates</span></span>|<span data-ttu-id="d3fdb-130">Denetim odağı yok.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="d3fdb-131">Geçerli</span><span class="sxs-lookup"><span data-stu-id="d3fdb-131">Valid</span></span>|<span data-ttu-id="d3fdb-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d3fdb-132">ValidationStates</span></span>|<span data-ttu-id="d3fdb-133">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d3fdb-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d3fdb-134">InvalidFocused</span></span>|<span data-ttu-id="d3fdb-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d3fdb-135">ValidationStates</span></span>|<span data-ttu-id="d3fdb-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d3fdb-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d3fdb-137">InvalidUnfocused</span></span>|<span data-ttu-id="d3fdb-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d3fdb-138">ValidationStates</span></span>|<span data-ttu-id="d3fdb-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="d3fdb-140">Flash ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="d3fdb-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="d3fdb-141">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.Thumb> denetim.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="d3fdb-142">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d3fdb-143">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="d3fdb-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3fdb-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3fdb-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="d3fdb-145">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="d3fdb-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="d3fdb-146">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d3fdb-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="d3fdb-147">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="d3fdb-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="d3fdb-148">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d3fdb-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
