---
title: ScrollViewer Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: 1f5c3d98d6fe2814addaad3e6c898f5341fac7f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672207"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="e1d9f-102">ScrollViewer Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="e1d9f-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="e1d9f-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.ScrollViewer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="e1d9f-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="e1d9f-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="e1d9f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="e1d9f-106">ScrollViewer bölümleri</span><span class="sxs-lookup"><span data-stu-id="e1d9f-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="e1d9f-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.ScrollViewer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="e1d9f-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="e1d9f-108">Part</span></span>|<span data-ttu-id="e1d9f-109">Tür</span><span class="sxs-lookup"><span data-stu-id="e1d9f-109">Type</span></span>|<span data-ttu-id="e1d9f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1d9f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e1d9f-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="e1d9f-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="e1d9f-112">İçeriği için yer tutucu <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="e1d9f-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="e1d9f-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="e1d9f-114"><xref:System.Windows.Controls.Primitives.ScrollBar> İçeriği yatay kaydırma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="e1d9f-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="e1d9f-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="e1d9f-116"><xref:System.Windows.Controls.Primitives.ScrollBar> İçeriği dikey olarak kaydırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="e1d9f-117">ScrollViewer durumları</span><span class="sxs-lookup"><span data-stu-id="e1d9f-117">ScrollViewer States</span></span>  
 <span data-ttu-id="e1d9f-118">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.ScrollViewer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="e1d9f-119">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="e1d9f-119">VisualState Name</span></span>|<span data-ttu-id="e1d9f-120">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="e1d9f-120">VisualStateGroup Name</span></span>|<span data-ttu-id="e1d9f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1d9f-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="e1d9f-122">Geçerli</span><span class="sxs-lookup"><span data-stu-id="e1d9f-122">Valid</span></span>|<span data-ttu-id="e1d9f-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e1d9f-123">ValidationStates</span></span>|<span data-ttu-id="e1d9f-124">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="e1d9f-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="e1d9f-125">InvalidFocused</span></span>|<span data-ttu-id="e1d9f-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e1d9f-126">ValidationStates</span></span>|<span data-ttu-id="e1d9f-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="e1d9f-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="e1d9f-128">InvalidUnfocused</span></span>|<span data-ttu-id="e1d9f-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="e1d9f-129">ValidationStates</span></span>|<span data-ttu-id="e1d9f-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="e1d9f-131">ScrollViewer ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="e1d9f-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="e1d9f-132">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ScrollViewer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="e1d9f-133">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="e1d9f-134">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="e1d9f-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d9f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1d9f-135">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="e1d9f-136">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="e1d9f-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="e1d9f-137">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e1d9f-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="e1d9f-138">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1d9f-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="e1d9f-139">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e1d9f-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
