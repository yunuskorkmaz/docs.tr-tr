---
title: "Menü Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3b93de0089db58ed0a91aad4150432f8e7a1019
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="11e51-102">Menü Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="11e51-102">Menu Styles and Templates</span></span>
<span data-ttu-id="11e51-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Menu> denetim.</span><span class="sxs-lookup"><span data-stu-id="11e51-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="11e51-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="11e51-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="11e51-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="11e51-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="11e51-106">Menü bölümleri</span><span class="sxs-lookup"><span data-stu-id="11e51-106">Menu Parts</span></span>  
 <span data-ttu-id="11e51-107"><xref:System.Windows.Controls.Menu> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="11e51-107">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="11e51-108">Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Menu>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="11e51-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="11e51-109">( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.Menu>; <xref:System.Windows.Controls.ScrollViewer> içinde denetimin kaydırma sağlar).</span><span class="sxs-lookup"><span data-stu-id="11e51-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="11e51-110">Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, vermeniz gerekir <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="11e51-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="11e51-111">Menu durumları</span><span class="sxs-lookup"><span data-stu-id="11e51-111">Menu States</span></span>  
 <span data-ttu-id="11e51-112">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Menu> denetim.</span><span class="sxs-lookup"><span data-stu-id="11e51-112">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="11e51-113">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="11e51-113">VisualState Name</span></span>|<span data-ttu-id="11e51-114">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="11e51-114">VisualStateGroup Name</span></span>|<span data-ttu-id="11e51-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11e51-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="11e51-116">Geçerli</span><span class="sxs-lookup"><span data-stu-id="11e51-116">Valid</span></span>|<span data-ttu-id="11e51-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="11e51-117">ValidationStates</span></span>|<span data-ttu-id="11e51-118">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="11e51-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="11e51-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="11e51-119">InvalidFocused</span></span>|<span data-ttu-id="11e51-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="11e51-120">ValidationStates</span></span>|<span data-ttu-id="11e51-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="11e51-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="11e51-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="11e51-122">InvalidUnfocused</span></span>|<span data-ttu-id="11e51-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="11e51-123">ValidationStates</span></span>|<span data-ttu-id="11e51-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="11e51-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="11e51-125">MenuItem bölümleri</span><span class="sxs-lookup"><span data-stu-id="11e51-125">MenuItem Parts</span></span>  
 <span data-ttu-id="11e51-126">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Menu> denetim.</span><span class="sxs-lookup"><span data-stu-id="11e51-126">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="11e51-127">Bölümü</span><span class="sxs-lookup"><span data-stu-id="11e51-127">Part</span></span>|<span data-ttu-id="11e51-128">Tür</span><span class="sxs-lookup"><span data-stu-id="11e51-128">Type</span></span>|<span data-ttu-id="11e51-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11e51-129">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="11e51-130">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="11e51-130">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="11e51-131">Alt alan.</span><span class="sxs-lookup"><span data-stu-id="11e51-131">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="11e51-132">Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.MenuItem>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="11e51-132">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="11e51-133">( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.MenuItem>; <xref:System.Windows.Controls.ScrollViewer> içinde denetimin kaydırma sağlar).</span><span class="sxs-lookup"><span data-stu-id="11e51-133">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="11e51-134">Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, vermeniz gerekir <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="11e51-134">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="11e51-135">MenuItem durumları</span><span class="sxs-lookup"><span data-stu-id="11e51-135">MenuItem States</span></span>  
 <span data-ttu-id="11e51-136">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.MenuItem> denetim.</span><span class="sxs-lookup"><span data-stu-id="11e51-136">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="11e51-137">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="11e51-137">VisualState Name</span></span>|<span data-ttu-id="11e51-138">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="11e51-138">VisualStateGroup Name</span></span>|<span data-ttu-id="11e51-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11e51-139">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="11e51-140">Geçerli</span><span class="sxs-lookup"><span data-stu-id="11e51-140">Valid</span></span>|<span data-ttu-id="11e51-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="11e51-141">ValidationStates</span></span>|<span data-ttu-id="11e51-142">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="11e51-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="11e51-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="11e51-143">InvalidFocused</span></span>|<span data-ttu-id="11e51-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="11e51-144">ValidationStates</span></span>|<span data-ttu-id="11e51-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="11e51-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="11e51-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="11e51-146">InvalidUnfocused</span></span>|<span data-ttu-id="11e51-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="11e51-147">ValidationStates</span></span>|<span data-ttu-id="11e51-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="11e51-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="11e51-149">Menü ve MenuItem ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="11e51-149">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="11e51-150">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Menu> denetim.</span><span class="sxs-lookup"><span data-stu-id="11e51-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="11e51-151">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.MenuItem> denetim.</span><span class="sxs-lookup"><span data-stu-id="11e51-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="11e51-152">Aşağıdaki örnek tanımlar `MenuScrollViewer`, önceki örnekte kullanılan.</span><span class="sxs-lookup"><span data-stu-id="11e51-152">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="11e51-153"><xref:System.Windows.Controls.ControlTemplate> Örnekler, bir veya daha fazla aşağıdaki kaynakları kullanın.</span><span class="sxs-lookup"><span data-stu-id="11e51-153">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="11e51-154">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="11e51-154">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e51-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11e51-155">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="11e51-156">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="11e51-156">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="11e51-157">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="11e51-157">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="11e51-158">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="11e51-158">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="11e51-159">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="11e51-159">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
