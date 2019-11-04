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
ms.openlocfilehash: f30a0abb3e4252737e513b531b8d5f49a0d47f0b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458449"
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="eef83-102">ScrollBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="eef83-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="eef83-103">Bu konuda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eef83-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="eef83-104">Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eef83-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="eef83-105">Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="eef83-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="eef83-106">Kaydırma çubuğu bölümleri</span><span class="sxs-lookup"><span data-stu-id="eef83-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="eef83-107">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="eef83-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="eef83-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="eef83-108">Part</span></span>|<span data-ttu-id="eef83-109">Tür</span><span class="sxs-lookup"><span data-stu-id="eef83-109">Type</span></span>|<span data-ttu-id="eef83-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eef83-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="eef83-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="eef83-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="eef83-112"><xref:System.Windows.Controls.Primitives.ScrollBar>konumunu gösteren öğe için kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="eef83-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="eef83-113">Kaydırma çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="eef83-113">ScrollBar States</span></span>  
 <span data-ttu-id="eef83-114">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="eef83-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="eef83-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="eef83-115">VisualState Name</span></span>|<span data-ttu-id="eef83-116">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="eef83-116">VisualStateGroup Name</span></span>|<span data-ttu-id="eef83-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eef83-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="eef83-118">Olağan</span><span class="sxs-lookup"><span data-stu-id="eef83-118">Normal</span></span>|<span data-ttu-id="eef83-119">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="eef83-119">CommonStates</span></span>|<span data-ttu-id="eef83-120">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="eef83-120">The default state.</span></span>|  
|<span data-ttu-id="eef83-121">Gelme olayından</span><span class="sxs-lookup"><span data-stu-id="eef83-121">MouseOver</span></span>|<span data-ttu-id="eef83-122">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="eef83-122">CommonStates</span></span>|<span data-ttu-id="eef83-123">Fare işaretçisi denetimin üzerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="eef83-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="eef83-124">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="eef83-124">Disabled</span></span>|<span data-ttu-id="eef83-125">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="eef83-125">CommonStates</span></span>|<span data-ttu-id="eef83-126">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="eef83-126">The control is disabled.</span></span>|  
|<span data-ttu-id="eef83-127">Geçerli</span><span class="sxs-lookup"><span data-stu-id="eef83-127">Valid</span></span>|<span data-ttu-id="eef83-128">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="eef83-128">ValidationStates</span></span>|<span data-ttu-id="eef83-129">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="eef83-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="eef83-130">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="eef83-130">InvalidFocused</span></span>|<span data-ttu-id="eef83-131">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="eef83-131">ValidationStates</span></span>|<span data-ttu-id="eef83-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `true` ve denetim odağa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="eef83-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="eef83-133">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="eef83-133">InvalidUnfocused</span></span>|<span data-ttu-id="eef83-134">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="eef83-134">ValidationStates</span></span>|<span data-ttu-id="eef83-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `true` ve denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="eef83-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="eef83-136">ScrollBar ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="eef83-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="eef83-137">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.ScrollBar> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eef83-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="eef83-138">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eef83-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="eef83-139">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="eef83-139">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef83-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eef83-140">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="eef83-141">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="eef83-141">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="eef83-142">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="eef83-142">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="eef83-143">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eef83-143">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="eef83-144">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="eef83-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
