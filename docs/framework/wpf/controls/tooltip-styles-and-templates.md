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
ms.openlocfilehash: ec946e7982983519a317ee1936e8584eef63479c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="a12b5-102">ToolTip Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="a12b5-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="a12b5-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.ToolTip> denetim.</span><span class="sxs-lookup"><span data-stu-id="a12b5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="a12b5-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="a12b5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a12b5-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="a12b5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="a12b5-106">Araç İpucu bölümleri</span><span class="sxs-lookup"><span data-stu-id="a12b5-106">ToolTip Parts</span></span>  
 <span data-ttu-id="a12b5-107"><xref:System.Windows.Controls.ToolTip> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a12b5-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="a12b5-108">Araç İpucu durumları</span><span class="sxs-lookup"><span data-stu-id="a12b5-108">ToolTip States</span></span>  
 <span data-ttu-id="a12b5-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.ToolTip> denetim.</span><span class="sxs-lookup"><span data-stu-id="a12b5-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="a12b5-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="a12b5-110">VisualState Name</span></span>|<span data-ttu-id="a12b5-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="a12b5-111">VisualStateGroup Name</span></span>|<span data-ttu-id="a12b5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a12b5-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a12b5-113">Closed</span><span class="sxs-lookup"><span data-stu-id="a12b5-113">Closed</span></span>|<span data-ttu-id="a12b5-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="a12b5-114">OpenStates</span></span>|<span data-ttu-id="a12b5-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="a12b5-115">The default state.</span></span>|  
|<span data-ttu-id="a12b5-116">Open</span><span class="sxs-lookup"><span data-stu-id="a12b5-116">Open</span></span>|<span data-ttu-id="a12b5-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="a12b5-117">OpenStates</span></span>|<span data-ttu-id="a12b5-118"><xref:System.Windows.Controls.ToolTip> Görünür.</span><span class="sxs-lookup"><span data-stu-id="a12b5-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="a12b5-119">Geçerli</span><span class="sxs-lookup"><span data-stu-id="a12b5-119">Valid</span></span>|<span data-ttu-id="a12b5-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a12b5-120">ValidationStates</span></span>|<span data-ttu-id="a12b5-121">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="a12b5-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a12b5-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a12b5-122">InvalidFocused</span></span>|<span data-ttu-id="a12b5-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a12b5-123">ValidationStates</span></span>|<span data-ttu-id="a12b5-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="a12b5-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a12b5-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a12b5-125">InvalidUnfocused</span></span>|<span data-ttu-id="a12b5-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a12b5-126">ValidationStates</span></span>|<span data-ttu-id="a12b5-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a12b5-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="a12b5-128">Araç İpucu ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="a12b5-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="a12b5-129">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ToolTip> denetim.</span><span class="sxs-lookup"><span data-stu-id="a12b5-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="a12b5-130">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="a12b5-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a12b5-131">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="a12b5-131">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a12b5-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a12b5-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="a12b5-133">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="a12b5-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="a12b5-134">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a12b5-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="a12b5-135">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="a12b5-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="a12b5-136">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a12b5-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
