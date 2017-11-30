---
title: "ToolBar Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e153ff0fd89259dafedf6f8abb669090a944e91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="57877-102">ToolBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="57877-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="57877-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.ToolBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="57877-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="57877-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="57877-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="57877-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="57877-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="57877-106">Araç çubuğu bölümleri</span><span class="sxs-lookup"><span data-stu-id="57877-106">ToolBar Parts</span></span>  
 <span data-ttu-id="57877-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.ToolBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="57877-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="57877-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="57877-108">Part</span></span>|<span data-ttu-id="57877-109">Tür</span><span class="sxs-lookup"><span data-stu-id="57877-109">Type</span></span>|<span data-ttu-id="57877-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57877-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="57877-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="57877-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="57877-112">Üzerinde denetimleri içeren nesneyi <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="57877-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="57877-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="57877-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="57877-114">Taşma alanında denetimleri içeren nesneyi <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="57877-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="57877-115">Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.ToolBar>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="57877-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="57877-116">( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.ToolBar>; <xref:System.Windows.Controls.ScrollViewer> içinde denetimin kaydırma sağlar).</span><span class="sxs-lookup"><span data-stu-id="57877-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="57877-117">Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, vermeniz gerekir <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="57877-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="57877-118">Araç çubuğu durumu</span><span class="sxs-lookup"><span data-stu-id="57877-118">ToolBar States</span></span>  
 <span data-ttu-id="57877-119">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.ToolBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="57877-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="57877-120">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="57877-120">VisualState Name</span></span>|<span data-ttu-id="57877-121">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="57877-121">VisualStateGroup Name</span></span>|<span data-ttu-id="57877-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57877-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="57877-123">Geçerli</span><span class="sxs-lookup"><span data-stu-id="57877-123">Valid</span></span>|<span data-ttu-id="57877-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="57877-124">ValidationStates</span></span>|<span data-ttu-id="57877-125">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="57877-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="57877-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="57877-126">InvalidFocused</span></span>|<span data-ttu-id="57877-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="57877-127">ValidationStates</span></span>|<span data-ttu-id="57877-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="57877-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="57877-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="57877-129">InvalidUnfocused</span></span>|<span data-ttu-id="57877-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="57877-130">ValidationStates</span></span>|<span data-ttu-id="57877-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="57877-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="57877-132">Araç çubuğu ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="57877-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="57877-133">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ToolBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="57877-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="57877-134">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="57877-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="57877-135">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="57877-135">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57877-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57877-136">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="57877-137">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="57877-137">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="57877-138">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="57877-138">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="57877-139">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="57877-139">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="57877-140">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="57877-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
