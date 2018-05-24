---
title: ContextMenu Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: 671fb0a4f178c9e16149f6d47945670ea0e64d48
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="222b6-102">ContextMenu Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="222b6-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="222b6-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.ContextMenu> denetim.</span><span class="sxs-lookup"><span data-stu-id="222b6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="222b6-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="222b6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="222b6-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="222b6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="222b6-106">ContextMenu bölümleri</span><span class="sxs-lookup"><span data-stu-id="222b6-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="222b6-107"><xref:System.Windows.Controls.ContextMenu> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="222b6-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="222b6-108">Oluştururken bir <xref:System.Windows.Controls.ControlTemplate> için bir <xref:System.Windows.Controls.ContextMenu>, şablonunuzu içerebilir bir <xref:System.Windows.Controls.ItemsPresenter> içinde bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="222b6-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="222b6-109">( <xref:System.Windows.Controls.ItemsPresenter> Her öğe görüntüler <xref:System.Windows.Controls.ContextMenu>; <xref:System.Windows.Controls.ScrollViewer> içinde denetimin kaydırma sağlar).</span><span class="sxs-lookup"><span data-stu-id="222b6-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="222b6-110">Varsa <xref:System.Windows.Controls.ItemsPresenter> doğrudan alt öğesi değil <xref:System.Windows.Controls.ScrollViewer>, vermeniz gerekir <xref:System.Windows.Controls.ItemsPresenter> adı `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="222b6-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="222b6-111">ContextMenu durumları</span><span class="sxs-lookup"><span data-stu-id="222b6-111">ContextMenu States</span></span>  
 <span data-ttu-id="222b6-112">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.ContextMenu> denetim.</span><span class="sxs-lookup"><span data-stu-id="222b6-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="222b6-113">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="222b6-113">VisualState Name</span></span>|<span data-ttu-id="222b6-114">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="222b6-114">VisualStateGroup Name</span></span>|<span data-ttu-id="222b6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="222b6-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="222b6-116">Geçerli</span><span class="sxs-lookup"><span data-stu-id="222b6-116">Valid</span></span>|<span data-ttu-id="222b6-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="222b6-117">ValidationStates</span></span>|<span data-ttu-id="222b6-118">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="222b6-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="222b6-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="222b6-119">InvalidFocused</span></span>|<span data-ttu-id="222b6-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="222b6-120">ValidationStates</span></span>|<span data-ttu-id="222b6-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="222b6-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="222b6-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="222b6-122">InvalidUnfocused</span></span>|<span data-ttu-id="222b6-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="222b6-123">ValidationStates</span></span>|<span data-ttu-id="222b6-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="222b6-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="222b6-125">ContextMenu ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="222b6-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="222b6-126">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ContextMenu> denetim.</span><span class="sxs-lookup"><span data-stu-id="222b6-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="222b6-127"><xref:System.Windows.Controls.ControlTemplate> Aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="222b6-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="222b6-128">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="222b6-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="222b6-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="222b6-129">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="222b6-130">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="222b6-130">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="222b6-131">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="222b6-131">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="222b6-132">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="222b6-132">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="222b6-133">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="222b6-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
