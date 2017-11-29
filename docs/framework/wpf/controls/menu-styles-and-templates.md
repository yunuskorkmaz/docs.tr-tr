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
ms.openlocfilehash: 1e007ae09e57353446feb13b3693e62c985f522d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="96b4d-102">Menü Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="96b4d-102">Menu Styles and Templates</span></span>
<span data-ttu-id="96b4d-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Menu> denetim.</span><span class="sxs-lookup"><span data-stu-id="96b4d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="96b4d-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="96b4d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="96b4d-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="96b4d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="96b4d-106">Menü bölümleri</span><span class="sxs-lookup"><span data-stu-id="96b4d-106">Menu Parts</span></span>  
 <span data-ttu-id="96b4d-107"><xref:System.Windows.Controls.Menu> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="96b4d-107">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="96b4d-108">Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.Menu>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="96b4d-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="96b4d-109">( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.Menu>; <xref:System.Windows.Controls.ScrollViewer> içinde denetimin kaydırma sağlar).</span><span class="sxs-lookup"><span data-stu-id="96b4d-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="96b4d-110">Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, vermeniz gerekir <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="96b4d-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="96b4d-111">Menu durumları</span><span class="sxs-lookup"><span data-stu-id="96b4d-111">Menu States</span></span>  
 <span data-ttu-id="96b4d-112">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Menu> denetim.</span><span class="sxs-lookup"><span data-stu-id="96b4d-112">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="96b4d-113">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="96b4d-113">VisualState Name</span></span>|<span data-ttu-id="96b4d-114">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="96b4d-114">VisualStateGroup Name</span></span>|<span data-ttu-id="96b4d-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96b4d-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="96b4d-116">Geçerli</span><span class="sxs-lookup"><span data-stu-id="96b4d-116">Valid</span></span>|<span data-ttu-id="96b4d-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="96b4d-117">ValidationStates</span></span>|<span data-ttu-id="96b4d-118">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="96b4d-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="96b4d-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="96b4d-119">InvalidFocused</span></span>|<span data-ttu-id="96b4d-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="96b4d-120">ValidationStates</span></span>|<span data-ttu-id="96b4d-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="96b4d-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="96b4d-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="96b4d-122">InvalidUnfocused</span></span>|<span data-ttu-id="96b4d-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="96b4d-123">ValidationStates</span></span>|<span data-ttu-id="96b4d-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="96b4d-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="96b4d-125">MenuItem bölümleri</span><span class="sxs-lookup"><span data-stu-id="96b4d-125">MenuItem Parts</span></span>  
 <span data-ttu-id="96b4d-126">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Menu> denetim.</span><span class="sxs-lookup"><span data-stu-id="96b4d-126">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="96b4d-127">Bölümü</span><span class="sxs-lookup"><span data-stu-id="96b4d-127">Part</span></span>|<span data-ttu-id="96b4d-128">Tür</span><span class="sxs-lookup"><span data-stu-id="96b4d-128">Type</span></span>|<span data-ttu-id="96b4d-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96b4d-129">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="96b4d-130">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="96b4d-130">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="96b4d-131">Alt alan.</span><span class="sxs-lookup"><span data-stu-id="96b4d-131">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="96b4d-132">Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.MenuItem>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="96b4d-132">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="96b4d-133">( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.MenuItem>; <xref:System.Windows.Controls.ScrollViewer> içinde denetimin kaydırma sağlar).</span><span class="sxs-lookup"><span data-stu-id="96b4d-133">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="96b4d-134">Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, vermeniz gerekir <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="96b4d-134">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="96b4d-135">MenuItem durumları</span><span class="sxs-lookup"><span data-stu-id="96b4d-135">MenuItem States</span></span>  
 <span data-ttu-id="96b4d-136">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.MenuItem> denetim.</span><span class="sxs-lookup"><span data-stu-id="96b4d-136">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="96b4d-137">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="96b4d-137">VisualState Name</span></span>|<span data-ttu-id="96b4d-138">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="96b4d-138">VisualStateGroup Name</span></span>|<span data-ttu-id="96b4d-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96b4d-139">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="96b4d-140">Geçerli</span><span class="sxs-lookup"><span data-stu-id="96b4d-140">Valid</span></span>|<span data-ttu-id="96b4d-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="96b4d-141">ValidationStates</span></span>|<span data-ttu-id="96b4d-142">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="96b4d-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="96b4d-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="96b4d-143">InvalidFocused</span></span>|<span data-ttu-id="96b4d-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="96b4d-144">ValidationStates</span></span>|<span data-ttu-id="96b4d-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="96b4d-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="96b4d-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="96b4d-146">InvalidUnfocused</span></span>|<span data-ttu-id="96b4d-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="96b4d-147">ValidationStates</span></span>|<span data-ttu-id="96b4d-148"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="96b4d-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="96b4d-149">Menü ve MenuItem ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="96b4d-149">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="96b4d-150">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Menu> denetim.</span><span class="sxs-lookup"><span data-stu-id="96b4d-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="96b4d-151">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.MenuItem> denetim.</span><span class="sxs-lookup"><span data-stu-id="96b4d-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="96b4d-152">Aşağıdaki örnek tanımlar `MenuScrollViewer`, önceki örnekte kullanılan.</span><span class="sxs-lookup"><span data-stu-id="96b4d-152">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="96b4d-153"><xref:System.Windows.Controls.ControlTemplate> Örnekler, bir veya daha fazla aşağıdaki kaynakları kullanın.</span><span class="sxs-lookup"><span data-stu-id="96b4d-153">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="96b4d-154">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="96b4d-154">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b4d-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96b4d-155">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="96b4d-156">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="96b4d-156">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="96b4d-157">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="96b4d-157">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="96b4d-158">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="96b4d-158">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="96b4d-159">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="96b4d-159">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
