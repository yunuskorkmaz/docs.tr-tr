---
title: "DocumentViewer Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33631b0a63b69f848cb3f09b4dcb617fb328b06c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="b3602-102">DocumentViewer Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="b3602-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="b3602-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.DocumentViewer> denetim.</span><span class="sxs-lookup"><span data-stu-id="b3602-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="b3602-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="b3602-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b3602-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="b3602-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="b3602-106">DocumentViewer bölümleri</span><span class="sxs-lookup"><span data-stu-id="b3602-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="b3602-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.DocumentViewer> denetim.</span><span class="sxs-lookup"><span data-stu-id="b3602-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="b3602-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="b3602-108">Part</span></span>|<span data-ttu-id="b3602-109">Tür</span><span class="sxs-lookup"><span data-stu-id="b3602-109">Type</span></span>|<span data-ttu-id="b3602-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3602-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b3602-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="b3602-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="b3602-112">İçerik ve kaydırma alanını.</span><span class="sxs-lookup"><span data-stu-id="b3602-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="b3602-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="b3602-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="b3602-114">Varsayılan olarak altındaki arama kutusu.</span><span class="sxs-lookup"><span data-stu-id="b3602-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="b3602-115">DocumentViewer durumları</span><span class="sxs-lookup"><span data-stu-id="b3602-115">DocumentViewer States</span></span>  
 <span data-ttu-id="b3602-116">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.DocumentViewer> denetim.</span><span class="sxs-lookup"><span data-stu-id="b3602-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="b3602-117">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="b3602-117">VisualState Name</span></span>|<span data-ttu-id="b3602-118">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="b3602-118">VisualStateGroup Name</span></span>|<span data-ttu-id="b3602-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3602-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b3602-120">Geçerli</span><span class="sxs-lookup"><span data-stu-id="b3602-120">Valid</span></span>|<span data-ttu-id="b3602-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b3602-121">ValidationStates</span></span>|<span data-ttu-id="b3602-122">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="b3602-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b3602-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b3602-123">InvalidFocused</span></span>|<span data-ttu-id="b3602-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b3602-124">ValidationStates</span></span>|<span data-ttu-id="b3602-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="b3602-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b3602-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b3602-126">InvalidUnfocused</span></span>|<span data-ttu-id="b3602-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b3602-127">ValidationStates</span></span>|<span data-ttu-id="b3602-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b3602-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="b3602-129">DocumentViewer ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="b3602-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="b3602-130">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.DocumentViewer> denetim.</span><span class="sxs-lookup"><span data-stu-id="b3602-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="b3602-131">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3602-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b3602-132">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="b3602-132">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3602-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3602-133">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="b3602-134">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="b3602-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="b3602-135">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b3602-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="b3602-136">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b3602-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="b3602-137">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b3602-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
