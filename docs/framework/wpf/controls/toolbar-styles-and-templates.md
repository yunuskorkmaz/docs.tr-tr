---
title: ToolBar Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
ms.openlocfilehash: a984311234386cb205d5db35f18a743ca535ff05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283665"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="ea68f-102">ToolBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="ea68f-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="ea68f-103">Bu konuda <xref:System.Windows.Controls.ToolBar> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea68f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="ea68f-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea68f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ea68f-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="ea68f-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="ea68f-106">Araç çubuğu bölümleri</span><span class="sxs-lookup"><span data-stu-id="ea68f-106">ToolBar Parts</span></span>  
 <span data-ttu-id="ea68f-107">Aşağıdaki tabloda <xref:System.Windows.Controls.ToolBar> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea68f-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="ea68f-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="ea68f-108">Part</span></span>|<span data-ttu-id="ea68f-109">Type</span><span class="sxs-lookup"><span data-stu-id="ea68f-109">Type</span></span>|<span data-ttu-id="ea68f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea68f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ea68f-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="ea68f-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="ea68f-112"><xref:System.Windows.Controls.ToolBar>denetimleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="ea68f-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="ea68f-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="ea68f-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="ea68f-114"><xref:System.Windows.Controls.ToolBar>taşma alanındaki denetimleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="ea68f-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="ea68f-115">Bir <xref:System.Windows.Controls.ToolBar>için <xref:System.Windows.Controls.ControlTemplate> oluşturduğunuzda, şablonunuz <xref:System.Windows.Controls.ScrollViewer>içinde bir <xref:System.Windows.Controls.ItemsPresenter> içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ea68f-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="ea68f-116">(<xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ToolBar>her öğeyi görüntüler; <xref:System.Windows.Controls.ScrollViewer> denetimin içinde kaydırmaya izin vermez).</span><span class="sxs-lookup"><span data-stu-id="ea68f-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="ea68f-117"><xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ScrollViewer>doğrudan alt öğesi değilse, `ItemsPresenter`adına <xref:System.Windows.Controls.ItemsPresenter> vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ea68f-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="ea68f-118">Araç çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="ea68f-118">ToolBar States</span></span>  
 <span data-ttu-id="ea68f-119">Aşağıdaki tabloda <xref:System.Windows.Controls.ToolBar> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ea68f-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="ea68f-120">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="ea68f-120">VisualState Name</span></span>|<span data-ttu-id="ea68f-121">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="ea68f-121">VisualStateGroup Name</span></span>|<span data-ttu-id="ea68f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea68f-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ea68f-123">Geçerli</span><span class="sxs-lookup"><span data-stu-id="ea68f-123">Valid</span></span>|<span data-ttu-id="ea68f-124">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="ea68f-124">ValidationStates</span></span>|<span data-ttu-id="ea68f-125">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="ea68f-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ea68f-126">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="ea68f-126">InvalidFocused</span></span>|<span data-ttu-id="ea68f-127">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="ea68f-127">ValidationStates</span></span>|<span data-ttu-id="ea68f-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="ea68f-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ea68f-129">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="ea68f-129">InvalidUnfocused</span></span>|<span data-ttu-id="ea68f-130">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="ea68f-130">ValidationStates</span></span>|<span data-ttu-id="ea68f-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="ea68f-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="ea68f-132">ToolBar ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="ea68f-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="ea68f-133">Aşağıdaki örnek, <xref:System.Windows.Controls.ToolBar> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea68f-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="ea68f-134">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea68f-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ea68f-135">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="ea68f-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea68f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea68f-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ea68f-137">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="ea68f-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ea68f-138">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ea68f-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ea68f-139">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ea68f-139">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ea68f-140">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="ea68f-140">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
