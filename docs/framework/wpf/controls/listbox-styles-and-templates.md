---
title: "ListBox Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edf8c50424a9694c4e00f5bf319d3122999bda85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="listbox-styles-and-templates"></a><span data-ttu-id="077d5-102">ListBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="077d5-102">ListBox Styles and Templates</span></span>
<span data-ttu-id="077d5-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.ListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="077d5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="077d5-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="077d5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="077d5-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="077d5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listbox-parts"></a><span data-ttu-id="077d5-106">ListBox bölümleri</span><span class="sxs-lookup"><span data-stu-id="077d5-106">ListBox Parts</span></span>  
 <span data-ttu-id="077d5-107"><xref:System.Windows.Controls.ListBox> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="077d5-107">The <xref:System.Windows.Controls.ListBox> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="077d5-108">Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.ListBox>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="077d5-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListBox>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="077d5-109">( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.ListBox>; <xref:System.Windows.Controls.ScrollViewer> içinde denetimin kaydırma sağlar).</span><span class="sxs-lookup"><span data-stu-id="077d5-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListBox>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="077d5-110">Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, vermeniz gerekir <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="077d5-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listbox-states"></a><span data-ttu-id="077d5-111">ListBox durumları</span><span class="sxs-lookup"><span data-stu-id="077d5-111">ListBox States</span></span>  
 <span data-ttu-id="077d5-112">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.ListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="077d5-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="077d5-113">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="077d5-113">VisualState Name</span></span>|<span data-ttu-id="077d5-114">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="077d5-114">VisualStateGroup Name</span></span>|<span data-ttu-id="077d5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="077d5-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="077d5-116">Geçerli</span><span class="sxs-lookup"><span data-stu-id="077d5-116">Valid</span></span>|<span data-ttu-id="077d5-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="077d5-117">ValidationStates</span></span>|<span data-ttu-id="077d5-118">Denetim geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="077d5-118">The control is valid.</span></span>|  
|<span data-ttu-id="077d5-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="077d5-119">InvalidFocused</span></span>|<span data-ttu-id="077d5-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="077d5-120">ValidationStates</span></span>|<span data-ttu-id="077d5-121">Denetim geçerli değil ve odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="077d5-121">The control is not valid and has focus.</span></span>|  
|<span data-ttu-id="077d5-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="077d5-122">InvalidUnfocused</span></span>|<span data-ttu-id="077d5-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="077d5-123">ValidationStates</span></span>|<span data-ttu-id="077d5-124">Denetim geçerli değil ve odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="077d5-124">The control is not valid and does not have focus.</span></span>|  
  
## <a name="listboxitem-parts"></a><span data-ttu-id="077d5-125">ListBoxItem bölümleri</span><span class="sxs-lookup"><span data-stu-id="077d5-125">ListBoxItem Parts</span></span>  
 <span data-ttu-id="077d5-126"><xref:System.Windows.Controls.ListBoxItem> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="077d5-126">The <xref:System.Windows.Controls.ListBoxItem> control does not have any named parts.</span></span>  
  
## <a name="listboxitem-states"></a><span data-ttu-id="077d5-127">ListBoxItem durumları</span><span class="sxs-lookup"><span data-stu-id="077d5-127">ListBoxItem States</span></span>  
 <span data-ttu-id="077d5-128">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.ListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="077d5-128">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="077d5-129">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="077d5-129">VisualState Name</span></span>|<span data-ttu-id="077d5-130">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="077d5-130">VisualStateGroup Name</span></span>|<span data-ttu-id="077d5-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="077d5-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="077d5-132">Normal</span><span class="sxs-lookup"><span data-stu-id="077d5-132">Normal</span></span>|<span data-ttu-id="077d5-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="077d5-133">CommonStates</span></span>|<span data-ttu-id="077d5-134">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="077d5-134">The default state.</span></span>|  
|<span data-ttu-id="077d5-135">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="077d5-135">MouseOver</span></span>|<span data-ttu-id="077d5-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="077d5-136">CommonStates</span></span>|<span data-ttu-id="077d5-137">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="077d5-137">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="077d5-138">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="077d5-138">Disabled</span></span>|<span data-ttu-id="077d5-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="077d5-139">CommonStates</span></span>|<span data-ttu-id="077d5-140">Öğesi devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="077d5-140">The item is disabled.</span></span>|  
|<span data-ttu-id="077d5-141">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="077d5-141">Focused</span></span>|<span data-ttu-id="077d5-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="077d5-142">FocusStates</span></span>|<span data-ttu-id="077d5-143">Öğenin odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="077d5-143">The item has focus.</span></span>|  
|<span data-ttu-id="077d5-144">Odaksız</span><span class="sxs-lookup"><span data-stu-id="077d5-144">Unfocused</span></span>|<span data-ttu-id="077d5-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="077d5-145">FocusStates</span></span>|<span data-ttu-id="077d5-146">Öğenin odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="077d5-146">The item does not have focus.</span></span>|  
|<span data-ttu-id="077d5-147">Seçilmemiş</span><span class="sxs-lookup"><span data-stu-id="077d5-147">Unselected</span></span>|<span data-ttu-id="077d5-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="077d5-148">SelectionStates</span></span>|<span data-ttu-id="077d5-149">Öğe seçilmedi.</span><span class="sxs-lookup"><span data-stu-id="077d5-149">The item is not selected.</span></span>|  
|<span data-ttu-id="077d5-150">Seçili</span><span class="sxs-lookup"><span data-stu-id="077d5-150">Selected</span></span>|<span data-ttu-id="077d5-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="077d5-151">SelectionStates</span></span>|<span data-ttu-id="077d5-152">Seçili currentlyplate öğesidir.</span><span class="sxs-lookup"><span data-stu-id="077d5-152">The item is currentlyplate selected.</span></span>|  
|<span data-ttu-id="077d5-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="077d5-153">SelectedUnfocused</span></span>|<span data-ttu-id="077d5-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="077d5-154">SelectionStates</span></span>|<span data-ttu-id="077d5-155">Öğe seçilir, ancak odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="077d5-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="077d5-156">Geçerli</span><span class="sxs-lookup"><span data-stu-id="077d5-156">Valid</span></span>|<span data-ttu-id="077d5-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="077d5-157">ValidationStates</span></span>|<span data-ttu-id="077d5-158">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="077d5-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="077d5-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="077d5-159">InvalidFocused</span></span>|<span data-ttu-id="077d5-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="077d5-160">ValidationStates</span></span>|<span data-ttu-id="077d5-161"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="077d5-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="077d5-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="077d5-162">InvalidUnfocused</span></span>|<span data-ttu-id="077d5-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="077d5-163">ValidationStates</span></span>|<span data-ttu-id="077d5-164"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="077d5-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listbox-controltemplate-example"></a><span data-ttu-id="077d5-165">ListBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="077d5-165">ListBox ControlTemplate Example</span></span>  
 <span data-ttu-id="077d5-166">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ListBox> ve <xref:System.Windows.Controls.ListBoxItem> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="077d5-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListBox> and <xref:System.Windows.Controls.ListBoxItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 <span data-ttu-id="077d5-167">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="077d5-167">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="077d5-168">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="077d5-168">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="077d5-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="077d5-169">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="077d5-170">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="077d5-170">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="077d5-171">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="077d5-171">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="077d5-172">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="077d5-172">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="077d5-173">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="077d5-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
