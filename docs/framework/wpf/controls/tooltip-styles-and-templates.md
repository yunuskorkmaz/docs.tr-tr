---
title: "ToolTip Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e39372083ede5649addee4b493f2425116ec2aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="5b45d-102">ToolTip Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="5b45d-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="5b45d-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.ToolTip> denetim.</span><span class="sxs-lookup"><span data-stu-id="5b45d-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="5b45d-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="5b45d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5b45d-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="5b45d-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="5b45d-106">Araç İpucu bölümleri</span><span class="sxs-lookup"><span data-stu-id="5b45d-106">ToolTip Parts</span></span>  
 <span data-ttu-id="5b45d-107"><xref:System.Windows.Controls.ToolTip> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5b45d-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="5b45d-108">Araç İpucu durumları</span><span class="sxs-lookup"><span data-stu-id="5b45d-108">ToolTip States</span></span>  
 <span data-ttu-id="5b45d-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.ToolTip> denetim.</span><span class="sxs-lookup"><span data-stu-id="5b45d-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="5b45d-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="5b45d-110">VisualState Name</span></span>|<span data-ttu-id="5b45d-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="5b45d-111">VisualStateGroup Name</span></span>|<span data-ttu-id="5b45d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b45d-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5b45d-113">Closed</span><span class="sxs-lookup"><span data-stu-id="5b45d-113">Closed</span></span>|<span data-ttu-id="5b45d-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="5b45d-114">OpenStates</span></span>|<span data-ttu-id="5b45d-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="5b45d-115">The default state.</span></span>|  
|<span data-ttu-id="5b45d-116">Open</span><span class="sxs-lookup"><span data-stu-id="5b45d-116">Open</span></span>|<span data-ttu-id="5b45d-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="5b45d-117">OpenStates</span></span>|<span data-ttu-id="5b45d-118"><xref:System.Windows.Controls.ToolTip> Görünür.</span><span class="sxs-lookup"><span data-stu-id="5b45d-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="5b45d-119">Geçerli</span><span class="sxs-lookup"><span data-stu-id="5b45d-119">Valid</span></span>|<span data-ttu-id="5b45d-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5b45d-120">ValidationStates</span></span>|<span data-ttu-id="5b45d-121">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="5b45d-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5b45d-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5b45d-122">InvalidFocused</span></span>|<span data-ttu-id="5b45d-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5b45d-123">ValidationStates</span></span>|<span data-ttu-id="5b45d-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="5b45d-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5b45d-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5b45d-125">InvalidUnfocused</span></span>|<span data-ttu-id="5b45d-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5b45d-126">ValidationStates</span></span>|<span data-ttu-id="5b45d-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5b45d-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="5b45d-128">Araç İpucu ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="5b45d-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="5b45d-129">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ToolTip> denetim.</span><span class="sxs-lookup"><span data-stu-id="5b45d-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="5b45d-130">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5b45d-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5b45d-131">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="5b45d-131">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b45d-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b45d-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="5b45d-133">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="5b45d-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="5b45d-134">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5b45d-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="5b45d-135">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b45d-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="5b45d-136">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5b45d-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
