---
title: "GroupBox Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a39e09812c54df533fdac27b5bfcaedd3fb93ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="c50e8-102">GroupBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="c50e8-102">GroupBox Styles and Templates</span></span>
<span data-ttu-id="c50e8-103"><a name="introduction"></a>Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.GroupBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="c50e8-103"><a name="introduction"></a> This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="c50e8-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="c50e8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c50e8-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c50e8-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="c50e8-106">GroupBox bölümleri</span><span class="sxs-lookup"><span data-stu-id="c50e8-106">GroupBox Parts</span></span>  
 <span data-ttu-id="c50e8-107"><xref:System.Windows.Controls.GroupBox> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c50e8-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="c50e8-108">GroupBox durumları</span><span class="sxs-lookup"><span data-stu-id="c50e8-108">GroupBox States</span></span>  
 <span data-ttu-id="c50e8-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.GroupBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="c50e8-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="c50e8-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="c50e8-110">VisualState Name</span></span>|<span data-ttu-id="c50e8-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="c50e8-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c50e8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c50e8-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c50e8-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="c50e8-113">Valid</span></span>|<span data-ttu-id="c50e8-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c50e8-114">ValidationStates</span></span>|<span data-ttu-id="c50e8-115">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="c50e8-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c50e8-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c50e8-116">InvalidFocused</span></span>|<span data-ttu-id="c50e8-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c50e8-117">ValidationStates</span></span>|<span data-ttu-id="c50e8-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="c50e8-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c50e8-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c50e8-119">InvalidUnfocused</span></span>|<span data-ttu-id="c50e8-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c50e8-120">ValidationStates</span></span>|<span data-ttu-id="c50e8-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c50e8-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="c50e8-122">GroupBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="c50e8-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="c50e8-123">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.GroupBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="c50e8-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="c50e8-124"><xref:System.Windows.Controls.ControlTemplate> Bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="c50e8-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c50e8-125">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="c50e8-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c50e8-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c50e8-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c50e8-127">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="c50e8-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c50e8-128">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c50e8-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c50e8-129">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="c50e8-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c50e8-130">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c50e8-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
