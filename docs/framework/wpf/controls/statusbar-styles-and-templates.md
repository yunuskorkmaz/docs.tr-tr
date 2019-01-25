---
title: StatusBar Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: ee3bd060268d5ab6f713a74f871d7de0dd77782b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660469"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="563da-102">StatusBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="563da-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="563da-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Primitives.StatusBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="563da-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="563da-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="563da-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="563da-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="563da-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="563da-106">StatusBar bölümleri</span><span class="sxs-lookup"><span data-stu-id="563da-106">StatusBar Parts</span></span>  
 <span data-ttu-id="563da-107"><xref:System.Windows.Controls.Primitives.StatusBar> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="563da-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="563da-108">StatusBar durumları</span><span class="sxs-lookup"><span data-stu-id="563da-108">StatusBar States</span></span>  
 <span data-ttu-id="563da-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.StatusBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="563da-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="563da-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="563da-110">VisualState Name</span></span>|<span data-ttu-id="563da-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="563da-111">VisualStateGroup Name</span></span>|<span data-ttu-id="563da-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="563da-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="563da-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="563da-113">Valid</span></span>|<span data-ttu-id="563da-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="563da-114">ValidationStates</span></span>|<span data-ttu-id="563da-115">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="563da-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="563da-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="563da-116">InvalidFocused</span></span>|<span data-ttu-id="563da-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="563da-117">ValidationStates</span></span>|<span data-ttu-id="563da-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="563da-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="563da-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="563da-119">InvalidUnfocused</span></span>|<span data-ttu-id="563da-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="563da-120">ValidationStates</span></span>|<span data-ttu-id="563da-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="563da-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="563da-122">StatusBarItem bölümleri</span><span class="sxs-lookup"><span data-stu-id="563da-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="563da-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="563da-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="563da-124">StatusBar durumları</span><span class="sxs-lookup"><span data-stu-id="563da-124">StatusBar States</span></span>  
 <span data-ttu-id="563da-125">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.StatusBarItem> denetimi.</span><span class="sxs-lookup"><span data-stu-id="563da-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="563da-126">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="563da-126">VisualState Name</span></span>|<span data-ttu-id="563da-127">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="563da-127">VisualStateGroup Name</span></span>|<span data-ttu-id="563da-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="563da-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="563da-129">Geçerli</span><span class="sxs-lookup"><span data-stu-id="563da-129">Valid</span></span>|<span data-ttu-id="563da-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="563da-130">ValidationStates</span></span>|<span data-ttu-id="563da-131">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="563da-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="563da-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="563da-132">InvalidFocused</span></span>|<span data-ttu-id="563da-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="563da-133">ValidationStates</span></span>|<span data-ttu-id="563da-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="563da-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="563da-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="563da-135">InvalidUnfocused</span></span>|<span data-ttu-id="563da-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="563da-136">ValidationStates</span></span>|<span data-ttu-id="563da-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="563da-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="563da-138">StatusBar ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="563da-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="563da-139">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.StatusBar> denetimi.</span><span class="sxs-lookup"><span data-stu-id="563da-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="563da-140"><xref:System.Windows.Controls.ControlTemplate> Bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="563da-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="563da-141">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="563da-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="563da-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="563da-142">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="563da-143">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="563da-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="563da-144">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="563da-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="563da-145">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="563da-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="563da-146">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="563da-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
