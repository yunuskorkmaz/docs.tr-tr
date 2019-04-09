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
ms.openlocfilehash: 1cbb8d54a544b70b4a484c06c6bb2e9ca25029da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156331"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="2ea41-102">ToolBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="2ea41-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="2ea41-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.ToolBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2ea41-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="2ea41-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="2ea41-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2ea41-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2ea41-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="2ea41-106">Araç çubuğu bölümleri</span><span class="sxs-lookup"><span data-stu-id="2ea41-106">ToolBar Parts</span></span>  
 <span data-ttu-id="2ea41-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.ToolBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2ea41-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="2ea41-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="2ea41-108">Part</span></span>|<span data-ttu-id="2ea41-109">Tür</span><span class="sxs-lookup"><span data-stu-id="2ea41-109">Type</span></span>|<span data-ttu-id="2ea41-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ea41-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2ea41-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="2ea41-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="2ea41-112">Üzerinde denetimleri içeren nesneyi <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="2ea41-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="2ea41-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="2ea41-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="2ea41-114">Taşma alanında denetimler içeren nesneyi <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="2ea41-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="2ea41-115">Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.ToolBar>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2ea41-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="2ea41-116">( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.ToolBar>; <xref:System.Windows.Controls.ScrollViewer> denetimi içinde kaydırma sağlar).</span><span class="sxs-lookup"><span data-stu-id="2ea41-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="2ea41-117">Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, size gereken <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="2ea41-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="2ea41-118">Araç çubuğu durumu</span><span class="sxs-lookup"><span data-stu-id="2ea41-118">ToolBar States</span></span>  
 <span data-ttu-id="2ea41-119">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.ToolBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2ea41-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="2ea41-120">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="2ea41-120">VisualState Name</span></span>|<span data-ttu-id="2ea41-121">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="2ea41-121">VisualStateGroup Name</span></span>|<span data-ttu-id="2ea41-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ea41-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2ea41-123">Geçerli</span><span class="sxs-lookup"><span data-stu-id="2ea41-123">Valid</span></span>|<span data-ttu-id="2ea41-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2ea41-124">ValidationStates</span></span>|<span data-ttu-id="2ea41-125">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="2ea41-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2ea41-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2ea41-126">InvalidFocused</span></span>|<span data-ttu-id="2ea41-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2ea41-127">ValidationStates</span></span>|<span data-ttu-id="2ea41-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="2ea41-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2ea41-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2ea41-129">InvalidUnfocused</span></span>|<span data-ttu-id="2ea41-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2ea41-130">ValidationStates</span></span>|<span data-ttu-id="2ea41-131"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2ea41-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="2ea41-132">Araç çubuğu ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="2ea41-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="2ea41-133">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ToolBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="2ea41-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="2ea41-134">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ea41-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2ea41-135">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2ea41-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea41-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ea41-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2ea41-137">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="2ea41-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2ea41-138">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2ea41-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2ea41-139">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ea41-139">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="2ea41-140">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2ea41-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
