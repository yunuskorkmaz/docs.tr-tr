---
title: "Çerçeve Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 603c4f766b836c7a301cc151112457ddb0972d10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="6d67e-102">Çerçeve Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="6d67e-102">Frame Styles and Templates</span></span>
<span data-ttu-id="6d67e-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Frame> denetim.</span><span class="sxs-lookup"><span data-stu-id="6d67e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="6d67e-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="6d67e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6d67e-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6d67e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="6d67e-106">Çerçeve bölümleri</span><span class="sxs-lookup"><span data-stu-id="6d67e-106">Frame Parts</span></span>  
 <span data-ttu-id="6d67e-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.Frame> denetim.</span><span class="sxs-lookup"><span data-stu-id="6d67e-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="6d67e-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="6d67e-108">Part</span></span>|<span data-ttu-id="6d67e-109">Tür</span><span class="sxs-lookup"><span data-stu-id="6d67e-109">Type</span></span>|<span data-ttu-id="6d67e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d67e-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6d67e-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="6d67e-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="6d67e-112">İçerik alanı.</span><span class="sxs-lookup"><span data-stu-id="6d67e-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="6d67e-113">Çerçeve durumları</span><span class="sxs-lookup"><span data-stu-id="6d67e-113">Frame States</span></span>  
 <span data-ttu-id="6d67e-114">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Frame> denetim.</span><span class="sxs-lookup"><span data-stu-id="6d67e-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="6d67e-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="6d67e-115">VisualState Name</span></span>|<span data-ttu-id="6d67e-116">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="6d67e-116">VisualStateGroup Name</span></span>|<span data-ttu-id="6d67e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d67e-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6d67e-118">Geçerli</span><span class="sxs-lookup"><span data-stu-id="6d67e-118">Valid</span></span>|<span data-ttu-id="6d67e-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6d67e-119">ValidationStates</span></span>|<span data-ttu-id="6d67e-120">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="6d67e-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6d67e-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6d67e-121">InvalidFocused</span></span>|<span data-ttu-id="6d67e-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6d67e-122">ValidationStates</span></span>|<span data-ttu-id="6d67e-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="6d67e-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6d67e-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6d67e-124">InvalidUnfocused</span></span>|<span data-ttu-id="6d67e-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6d67e-125">ValidationStates</span></span>|<span data-ttu-id="6d67e-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="6d67e-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="6d67e-127">Çerçeve ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="6d67e-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="6d67e-128">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Frame> denetim.</span><span class="sxs-lookup"><span data-stu-id="6d67e-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="6d67e-129">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="6d67e-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6d67e-130">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="6d67e-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d67e-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d67e-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="6d67e-132">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="6d67e-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="6d67e-133">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6d67e-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="6d67e-134">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d67e-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="6d67e-135">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6d67e-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
