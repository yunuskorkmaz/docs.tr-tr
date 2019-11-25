---
title: ScrollBar Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 7093a78555aefd73f9bb05c0a7b5fab6b66176fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283410"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="3b442-102">ScrollBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="3b442-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="3b442-103">Bu konuda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b442-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="3b442-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b442-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3b442-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="3b442-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="3b442-106">Kaydırma çubuğu bölümleri</span><span class="sxs-lookup"><span data-stu-id="3b442-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="3b442-107">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b442-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="3b442-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="3b442-108">Part</span></span>|<span data-ttu-id="3b442-109">Type</span><span class="sxs-lookup"><span data-stu-id="3b442-109">Type</span></span>|<span data-ttu-id="3b442-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b442-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3b442-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="3b442-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="3b442-112"><xref:System.Windows.Controls.Primitives.ScrollBar>konumunu gösteren öğe için kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="3b442-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="3b442-113">Kaydırma çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="3b442-113">ScrollBar States</span></span>  
 <span data-ttu-id="3b442-114">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b442-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="3b442-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="3b442-115">VisualState Name</span></span>|<span data-ttu-id="3b442-116">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="3b442-116">VisualStateGroup Name</span></span>|<span data-ttu-id="3b442-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b442-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="3b442-118">Normal</span><span class="sxs-lookup"><span data-stu-id="3b442-118">Normal</span></span>|<span data-ttu-id="3b442-119">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="3b442-119">CommonStates</span></span>|<span data-ttu-id="3b442-120">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="3b442-120">The default state.</span></span>|  
|<span data-ttu-id="3b442-121">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="3b442-121">MouseOver</span></span>|<span data-ttu-id="3b442-122">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="3b442-122">CommonStates</span></span>|<span data-ttu-id="3b442-123">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3b442-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="3b442-124">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="3b442-124">Disabled</span></span>|<span data-ttu-id="3b442-125">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="3b442-125">CommonStates</span></span>|<span data-ttu-id="3b442-126">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="3b442-126">The control is disabled.</span></span>|  
|<span data-ttu-id="3b442-127">Geçerli</span><span class="sxs-lookup"><span data-stu-id="3b442-127">Valid</span></span>|<span data-ttu-id="3b442-128">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="3b442-128">ValidationStates</span></span>|<span data-ttu-id="3b442-129">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b442-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3b442-130">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="3b442-130">InvalidFocused</span></span>|<span data-ttu-id="3b442-131">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="3b442-131">ValidationStates</span></span>|<span data-ttu-id="3b442-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `true` ve denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3b442-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="3b442-133">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="3b442-133">InvalidUnfocused</span></span>|<span data-ttu-id="3b442-134">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="3b442-134">ValidationStates</span></span>|<span data-ttu-id="3b442-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `true` ve denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3b442-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="3b442-136">ScrollBar ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="3b442-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="3b442-137">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b442-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="3b442-138">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b442-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3b442-139">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="3b442-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b442-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b442-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3b442-141">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="3b442-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3b442-142">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="3b442-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3b442-143">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b442-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="3b442-144">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="3b442-144">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
