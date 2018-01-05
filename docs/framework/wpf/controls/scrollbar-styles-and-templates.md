---
title: "ScrollBar Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14b40a458b271a4f8b88c167367771235f25c7a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="beb7e-102">ScrollBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="beb7e-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="beb7e-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Primitives.ScrollBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="beb7e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="beb7e-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="beb7e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="beb7e-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="beb7e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="beb7e-106">ScrollBar bölümleri</span><span class="sxs-lookup"><span data-stu-id="beb7e-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="beb7e-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Primitives.ScrollBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="beb7e-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="beb7e-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="beb7e-108">Part</span></span>|<span data-ttu-id="beb7e-109">Tür</span><span class="sxs-lookup"><span data-stu-id="beb7e-109">Type</span></span>|<span data-ttu-id="beb7e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="beb7e-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="beb7e-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="beb7e-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="beb7e-112">Kapsayıcı konumunu gösterir öğesinin <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="beb7e-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="beb7e-113">ScrollBar durumları</span><span class="sxs-lookup"><span data-stu-id="beb7e-113">ScrollBar States</span></span>  
 <span data-ttu-id="beb7e-114">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Primitives.ScrollBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="beb7e-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="beb7e-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="beb7e-115">VisualState Name</span></span>|<span data-ttu-id="beb7e-116">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="beb7e-116">VisualStateGroup Name</span></span>|<span data-ttu-id="beb7e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="beb7e-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="beb7e-118">Normal</span><span class="sxs-lookup"><span data-stu-id="beb7e-118">Normal</span></span>|<span data-ttu-id="beb7e-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="beb7e-119">CommonStates</span></span>|<span data-ttu-id="beb7e-120">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="beb7e-120">The default state.</span></span>|  
|<span data-ttu-id="beb7e-121">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="beb7e-121">MouseOver</span></span>|<span data-ttu-id="beb7e-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="beb7e-122">CommonStates</span></span>|<span data-ttu-id="beb7e-123">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="beb7e-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="beb7e-124">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="beb7e-124">Disabled</span></span>|<span data-ttu-id="beb7e-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="beb7e-125">CommonStates</span></span>|<span data-ttu-id="beb7e-126">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="beb7e-126">The control is disabled.</span></span>|  
|<span data-ttu-id="beb7e-127">Geçerli</span><span class="sxs-lookup"><span data-stu-id="beb7e-127">Valid</span></span>|<span data-ttu-id="beb7e-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="beb7e-128">ValidationStates</span></span>|<span data-ttu-id="beb7e-129">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="beb7e-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="beb7e-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="beb7e-130">InvalidFocused</span></span>|<span data-ttu-id="beb7e-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="beb7e-131">ValidationStates</span></span>|<span data-ttu-id="beb7e-132"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="beb7e-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="beb7e-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="beb7e-133">InvalidUnfocused</span></span>|<span data-ttu-id="beb7e-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="beb7e-134">ValidationStates</span></span>|<span data-ttu-id="beb7e-135"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="beb7e-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="beb7e-136">ScrollBar ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="beb7e-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="beb7e-137">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Primitives.ScrollBar> denetim.</span><span class="sxs-lookup"><span data-stu-id="beb7e-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="beb7e-138">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="beb7e-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="beb7e-139">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="beb7e-139">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb7e-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="beb7e-140">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="beb7e-141">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="beb7e-141">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="beb7e-142">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="beb7e-142">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="beb7e-143">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="beb7e-143">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="beb7e-144">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="beb7e-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
