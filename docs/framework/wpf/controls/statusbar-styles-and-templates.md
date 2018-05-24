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
ms.openlocfilehash: 11fa3ab6edd62f0b5484d9ccf76c101d04be353c
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="57c4d-102">StatusBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="57c4d-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="57c4d-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Primitives.StatusBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="57c4d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="57c4d-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="57c4d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="57c4d-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="57c4d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="57c4d-106">StatusBar bölümleri</span><span class="sxs-lookup"><span data-stu-id="57c4d-106">StatusBar Parts</span></span>  
 <span data-ttu-id="57c4d-107"><xref:System.Windows.Controls.Primitives.StatusBar> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="57c4d-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="57c4d-108">StatusBar durumları</span><span class="sxs-lookup"><span data-stu-id="57c4d-108">StatusBar States</span></span>  
 <span data-ttu-id="57c4d-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.StatusBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="57c4d-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="57c4d-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="57c4d-110">VisualState Name</span></span>|<span data-ttu-id="57c4d-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="57c4d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="57c4d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57c4d-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="57c4d-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="57c4d-113">Valid</span></span>|<span data-ttu-id="57c4d-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="57c4d-114">ValidationStates</span></span>|<span data-ttu-id="57c4d-115">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="57c4d-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="57c4d-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="57c4d-116">InvalidFocused</span></span>|<span data-ttu-id="57c4d-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="57c4d-117">ValidationStates</span></span>|<span data-ttu-id="57c4d-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="57c4d-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="57c4d-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="57c4d-119">InvalidUnfocused</span></span>|<span data-ttu-id="57c4d-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="57c4d-120">ValidationStates</span></span>|<span data-ttu-id="57c4d-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="57c4d-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="57c4d-122">StatusBarItem bölümleri</span><span class="sxs-lookup"><span data-stu-id="57c4d-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="57c4d-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="57c4d-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="57c4d-124">StatusBar durumları</span><span class="sxs-lookup"><span data-stu-id="57c4d-124">StatusBar States</span></span>  
 <span data-ttu-id="57c4d-125">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.StatusBarItem> denetim.</span><span class="sxs-lookup"><span data-stu-id="57c4d-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="57c4d-126">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="57c4d-126">VisualState Name</span></span>|<span data-ttu-id="57c4d-127">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="57c4d-127">VisualStateGroup Name</span></span>|<span data-ttu-id="57c4d-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57c4d-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="57c4d-129">Geçerli</span><span class="sxs-lookup"><span data-stu-id="57c4d-129">Valid</span></span>|<span data-ttu-id="57c4d-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="57c4d-130">ValidationStates</span></span>|<span data-ttu-id="57c4d-131">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="57c4d-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="57c4d-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="57c4d-132">InvalidFocused</span></span>|<span data-ttu-id="57c4d-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="57c4d-133">ValidationStates</span></span>|<span data-ttu-id="57c4d-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="57c4d-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="57c4d-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="57c4d-135">InvalidUnfocused</span></span>|<span data-ttu-id="57c4d-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="57c4d-136">ValidationStates</span></span>|<span data-ttu-id="57c4d-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="57c4d-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="57c4d-138">StatusBar ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="57c4d-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="57c4d-139">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.StatusBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="57c4d-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="57c4d-140"><xref:System.Windows.Controls.ControlTemplate> Bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="57c4d-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="57c4d-141">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="57c4d-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c4d-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57c4d-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="57c4d-143">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="57c4d-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="57c4d-144">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="57c4d-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="57c4d-145">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="57c4d-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="57c4d-146">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="57c4d-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
