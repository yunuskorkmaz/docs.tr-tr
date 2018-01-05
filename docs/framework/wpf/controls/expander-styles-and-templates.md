---
title: "Genişletici Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 999b081d80680069d4c6fdf908814889afa60870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="expander-styles-and-templates"></a><span data-ttu-id="8bb4d-102">Genişletici Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="8bb4d-102">Expander Styles and Templates</span></span>
<span data-ttu-id="8bb4d-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Expander> denetim.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Expander> control.</span></span> <span data-ttu-id="8bb4d-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8bb4d-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="8bb4d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="expander-parts"></a><span data-ttu-id="8bb4d-106">Genişletici bölümleri</span><span class="sxs-lookup"><span data-stu-id="8bb4d-106">Expander Parts</span></span>  
 <span data-ttu-id="8bb4d-107"><xref:System.Windows.Controls.Expander> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-107">The <xref:System.Windows.Controls.Expander> control does not have any named parts.</span></span>  
  
## <a name="expander-states"></a><span data-ttu-id="8bb4d-108">Genişletici durumları</span><span class="sxs-lookup"><span data-stu-id="8bb4d-108">Expander States</span></span>  
 <span data-ttu-id="8bb4d-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Expander> denetim.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-109">The following table lists the visual states for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
|<span data-ttu-id="8bb4d-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="8bb4d-110">VisualState Name</span></span>|<span data-ttu-id="8bb4d-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="8bb4d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="8bb4d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bb4d-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8bb4d-113">Normal</span><span class="sxs-lookup"><span data-stu-id="8bb4d-113">Normal</span></span>|<span data-ttu-id="8bb4d-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-114">CommonStates</span></span>|<span data-ttu-id="8bb4d-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-115">The default state.</span></span>|  
|<span data-ttu-id="8bb4d-116">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="8bb4d-116">MouseOver</span></span>|<span data-ttu-id="8bb4d-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-117">CommonStates</span></span>|<span data-ttu-id="8bb4d-118">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="8bb4d-119">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="8bb4d-119">Disabled</span></span>|<span data-ttu-id="8bb4d-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-120">CommonStates</span></span>|<span data-ttu-id="8bb4d-121">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-121">The control is disabled.</span></span>|  
|<span data-ttu-id="8bb4d-122">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="8bb4d-122">Focused</span></span>|<span data-ttu-id="8bb4d-123">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-123">FocusStates</span></span>|<span data-ttu-id="8bb4d-124">Denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-124">The control has focus.</span></span>|  
|<span data-ttu-id="8bb4d-125">Odaksız</span><span class="sxs-lookup"><span data-stu-id="8bb4d-125">Unfocused</span></span>|<span data-ttu-id="8bb4d-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-126">FocusStates</span></span>|<span data-ttu-id="8bb4d-127">Denetim odağı yok.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-127">The control does not have focus.</span></span>|  
|<span data-ttu-id="8bb4d-128">Genişletilmiş</span><span class="sxs-lookup"><span data-stu-id="8bb4d-128">Expanded</span></span>|<span data-ttu-id="8bb4d-129">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-129">ExpansionStates</span></span>|<span data-ttu-id="8bb4d-130">Denetim genişletilir.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-130">The control is expanded.</span></span>|  
|<span data-ttu-id="8bb4d-131">Daraltılmış</span><span class="sxs-lookup"><span data-stu-id="8bb4d-131">Collapsed</span></span>|<span data-ttu-id="8bb4d-132">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-132">ExpansionStates</span></span>|<span data-ttu-id="8bb4d-133">Denetim genişletilmiş değil.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-133">The control is not expanded.</span></span>|  
|<span data-ttu-id="8bb4d-134">ExpandDown</span><span class="sxs-lookup"><span data-stu-id="8bb4d-134">ExpandDown</span></span>|<span data-ttu-id="8bb4d-135">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-135">ExpandDirectionStates</span></span>|<span data-ttu-id="8bb4d-136">Aşağı denetimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-136">The control expands down.</span></span>|  
|<span data-ttu-id="8bb4d-137">ExpandUp</span><span class="sxs-lookup"><span data-stu-id="8bb4d-137">ExpandUp</span></span>|<span data-ttu-id="8bb4d-138">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-138">ExpandDirectionStates</span></span>|<span data-ttu-id="8bb4d-139">Yukarı denetimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-139">The control expands up.</span></span>|  
|<span data-ttu-id="8bb4d-140">ExpandLeft</span><span class="sxs-lookup"><span data-stu-id="8bb4d-140">ExpandLeft</span></span>|<span data-ttu-id="8bb4d-141">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-141">ExpandDirectionStates</span></span>|<span data-ttu-id="8bb4d-142">Denetim sol genişletir.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-142">The control expands left.</span></span>|  
|<span data-ttu-id="8bb4d-143">ExpandRight</span><span class="sxs-lookup"><span data-stu-id="8bb4d-143">ExpandRight</span></span>|<span data-ttu-id="8bb4d-144">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-144">ExpandDirectionStates</span></span>|<span data-ttu-id="8bb4d-145">Denetimin sağ genişletir.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-145">The control expands right.</span></span>|  
|<span data-ttu-id="8bb4d-146">Geçerli</span><span class="sxs-lookup"><span data-stu-id="8bb4d-146">Valid</span></span>|<span data-ttu-id="8bb4d-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-147">ValidationStates</span></span>|<span data-ttu-id="8bb4d-148">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-148">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8bb4d-149">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8bb4d-149">InvalidFocused</span></span>|<span data-ttu-id="8bb4d-150">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-150">ValidationStates</span></span>|<span data-ttu-id="8bb4d-151"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-151">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8bb4d-152">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8bb4d-152">InvalidUnfocused</span></span>|<span data-ttu-id="8bb4d-153">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8bb4d-153">ValidationStates</span></span>|<span data-ttu-id="8bb4d-154"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-154">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="expander-controltemplate-example"></a><span data-ttu-id="8bb4d-155">Genişletici ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="8bb4d-155">Expander ControlTemplate Example</span></span>  
 <span data-ttu-id="8bb4d-156">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Expander> denetim.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-156">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 <span data-ttu-id="8bb4d-157">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-157">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8bb4d-158">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="8bb4d-158">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bb4d-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bb4d-159">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="8bb4d-160">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="8bb4d-160">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="8bb4d-161">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8bb4d-161">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="8bb4d-162">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8bb4d-162">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="8bb4d-163">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8bb4d-163">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
