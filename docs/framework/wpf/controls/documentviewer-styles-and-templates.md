---
title: DocumentViewer Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
ms.openlocfilehash: 217fa0ff7b8c34de817a269effbf64311bbea7f2
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="de353-102">DocumentViewer Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="de353-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="de353-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.DocumentViewer> denetim.</span><span class="sxs-lookup"><span data-stu-id="de353-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="de353-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="de353-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="de353-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="de353-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="de353-106">DocumentViewer bölümleri</span><span class="sxs-lookup"><span data-stu-id="de353-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="de353-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.DocumentViewer> denetim.</span><span class="sxs-lookup"><span data-stu-id="de353-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="de353-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="de353-108">Part</span></span>|<span data-ttu-id="de353-109">Tür</span><span class="sxs-lookup"><span data-stu-id="de353-109">Type</span></span>|<span data-ttu-id="de353-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de353-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="de353-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="de353-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="de353-112">İçerik ve kaydırma alanını.</span><span class="sxs-lookup"><span data-stu-id="de353-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="de353-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="de353-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="de353-114">Varsayılan olarak altındaki arama kutusu.</span><span class="sxs-lookup"><span data-stu-id="de353-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="de353-115">DocumentViewer durumları</span><span class="sxs-lookup"><span data-stu-id="de353-115">DocumentViewer States</span></span>  
 <span data-ttu-id="de353-116">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.DocumentViewer> denetim.</span><span class="sxs-lookup"><span data-stu-id="de353-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="de353-117">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="de353-117">VisualState Name</span></span>|<span data-ttu-id="de353-118">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="de353-118">VisualStateGroup Name</span></span>|<span data-ttu-id="de353-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de353-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="de353-120">Geçerli</span><span class="sxs-lookup"><span data-stu-id="de353-120">Valid</span></span>|<span data-ttu-id="de353-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="de353-121">ValidationStates</span></span>|<span data-ttu-id="de353-122">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="de353-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="de353-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="de353-123">InvalidFocused</span></span>|<span data-ttu-id="de353-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="de353-124">ValidationStates</span></span>|<span data-ttu-id="de353-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="de353-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="de353-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="de353-126">InvalidUnfocused</span></span>|<span data-ttu-id="de353-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="de353-127">ValidationStates</span></span>|<span data-ttu-id="de353-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="de353-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="de353-129">DocumentViewer ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="de353-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="de353-130">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.DocumentViewer> denetim.</span><span class="sxs-lookup"><span data-stu-id="de353-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="de353-131">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="de353-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="de353-132">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="de353-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de353-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de353-133">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="de353-134">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="de353-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="de353-135">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="de353-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="de353-136">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="de353-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="de353-137">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="de353-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
