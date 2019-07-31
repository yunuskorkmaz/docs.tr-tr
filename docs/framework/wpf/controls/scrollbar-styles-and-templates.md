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
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671977"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="2e058-102">ScrollBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="2e058-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="2e058-103">Bu konuda, <xref:System.Windows.Controls.Primitives.ScrollBar> denetimin stilleri ve şablonları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e058-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="2e058-104">Denetim için benzersiz bir görünüm <xref:System.Windows.Controls.ControlTemplate> sağlamak üzere varsayılan ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e058-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2e058-105">Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2e058-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="2e058-106">Kaydırma çubuğu bölümleri</span><span class="sxs-lookup"><span data-stu-id="2e058-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="2e058-107">Aşağıdaki tabloda, <xref:System.Windows.Controls.Primitives.ScrollBar> denetimin adlandırılmış parçaları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e058-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="2e058-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="2e058-108">Part</span></span>|<span data-ttu-id="2e058-109">Tür</span><span class="sxs-lookup"><span data-stu-id="2e058-109">Type</span></span>|<span data-ttu-id="2e058-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e058-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2e058-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="2e058-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="2e058-112">Öğesinin konumunu <xref:System.Windows.Controls.Primitives.ScrollBar>gösteren öğesi için kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="2e058-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="2e058-113">Kaydırma çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="2e058-113">ScrollBar States</span></span>  
 <span data-ttu-id="2e058-114">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetim için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2e058-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="2e058-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="2e058-115">VisualState Name</span></span>|<span data-ttu-id="2e058-116">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="2e058-116">VisualStateGroup Name</span></span>|<span data-ttu-id="2e058-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e058-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="2e058-118">Normal</span><span class="sxs-lookup"><span data-stu-id="2e058-118">Normal</span></span>|<span data-ttu-id="2e058-119">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="2e058-119">CommonStates</span></span>|<span data-ttu-id="2e058-120">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="2e058-120">The default state.</span></span>|  
|<span data-ttu-id="2e058-121">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="2e058-121">MouseOver</span></span>|<span data-ttu-id="2e058-122">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="2e058-122">CommonStates</span></span>|<span data-ttu-id="2e058-123">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2e058-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="2e058-124">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="2e058-124">Disabled</span></span>|<span data-ttu-id="2e058-125">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="2e058-125">CommonStates</span></span>|<span data-ttu-id="2e058-126">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="2e058-126">The control is disabled.</span></span>|  
|<span data-ttu-id="2e058-127">Geçerli</span><span class="sxs-lookup"><span data-stu-id="2e058-127">Valid</span></span>|<span data-ttu-id="2e058-128">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="2e058-128">ValidationStates</span></span>|<span data-ttu-id="2e058-129">Denetim, <xref:System.Windows.Controls.Validation> sınıfını <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ve ekli özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e058-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2e058-130">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="2e058-130">InvalidFocused</span></span>|<span data-ttu-id="2e058-131">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="2e058-131">ValidationStates</span></span>|<span data-ttu-id="2e058-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> İliştirilmiş`true` özelliği ve denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2e058-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="2e058-133">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="2e058-133">InvalidUnfocused</span></span>|<span data-ttu-id="2e058-134">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="2e058-134">ValidationStates</span></span>|<span data-ttu-id="2e058-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> İliştirilmiş`true` özelliği ve denetim odağa sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="2e058-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="2e058-136">ScrollBar ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="2e058-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="2e058-137">Aşağıdaki örnek, <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi için nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e058-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="2e058-138">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e058-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2e058-139">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2e058-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e058-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e058-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2e058-141">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="2e058-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2e058-142">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2e058-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2e058-143">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2e058-143">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="2e058-144">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2e058-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
