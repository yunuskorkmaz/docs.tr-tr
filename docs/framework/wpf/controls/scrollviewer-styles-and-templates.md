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
ms.openlocfilehash: b54dcacf55a750d7c1253db20147d18de47d027e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283404"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="81945-102">ScrollViewer Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="81945-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="81945-103">Bu konuda <xref:System.Windows.Controls.ScrollViewer> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81945-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="81945-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81945-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="81945-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="81945-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="81945-106">ScrollViewer bölümleri</span><span class="sxs-lookup"><span data-stu-id="81945-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="81945-107">Aşağıdaki tabloda <xref:System.Windows.Controls.ScrollViewer> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="81945-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="81945-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="81945-108">Part</span></span>|<span data-ttu-id="81945-109">Type</span><span class="sxs-lookup"><span data-stu-id="81945-109">Type</span></span>|<span data-ttu-id="81945-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81945-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="81945-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="81945-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="81945-112"><xref:System.Windows.Controls.ScrollViewer>içerik için yer tutucu.</span><span class="sxs-lookup"><span data-stu-id="81945-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="81945-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="81945-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="81945-114">İçeriği yatay kaydırmak için kullanılan <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="81945-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="81945-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="81945-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="81945-116">İçeriği dikey kaydırmak için kullanılan <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="81945-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="81945-117">ScrollViewer durumları</span><span class="sxs-lookup"><span data-stu-id="81945-117">ScrollViewer States</span></span>  
 <span data-ttu-id="81945-118">Aşağıdaki tabloda <xref:System.Windows.Controls.ScrollViewer> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="81945-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="81945-119">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="81945-119">VisualState Name</span></span>|<span data-ttu-id="81945-120">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="81945-120">VisualStateGroup Name</span></span>|<span data-ttu-id="81945-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="81945-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="81945-122">Geçerli</span><span class="sxs-lookup"><span data-stu-id="81945-122">Valid</span></span>|<span data-ttu-id="81945-123">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="81945-123">ValidationStates</span></span>|<span data-ttu-id="81945-124">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="81945-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="81945-125">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="81945-125">InvalidFocused</span></span>|<span data-ttu-id="81945-126">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="81945-126">ValidationStates</span></span>|<span data-ttu-id="81945-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="81945-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="81945-128">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="81945-128">InvalidUnfocused</span></span>|<span data-ttu-id="81945-129">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="81945-129">ValidationStates</span></span>|<span data-ttu-id="81945-130"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="81945-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="81945-131">ScrollViewer ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="81945-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="81945-132">Aşağıdaki örnek, <xref:System.Windows.Controls.ScrollViewer> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="81945-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="81945-133">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="81945-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="81945-134">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="81945-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81945-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81945-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="81945-136">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="81945-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="81945-137">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="81945-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="81945-138">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="81945-138">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="81945-139">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="81945-139">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
