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
ms.openlocfilehash: 4e91a640b36e4793567c9e728fd71ec8ce596743
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158424"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="edf62-102">DocumentViewer Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="edf62-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="edf62-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.DocumentViewer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="edf62-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="edf62-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="edf62-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="edf62-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="edf62-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="edf62-106">DocumentViewer bölümleri</span><span class="sxs-lookup"><span data-stu-id="edf62-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="edf62-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.DocumentViewer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="edf62-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="edf62-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="edf62-108">Part</span></span>|<span data-ttu-id="edf62-109">Tür</span><span class="sxs-lookup"><span data-stu-id="edf62-109">Type</span></span>|<span data-ttu-id="edf62-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edf62-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="edf62-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="edf62-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="edf62-112">İçerik ve kaydırma alanını.</span><span class="sxs-lookup"><span data-stu-id="edf62-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="edf62-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="edf62-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="edf62-114">Varsayılan olarak altındaki arama kutusu.</span><span class="sxs-lookup"><span data-stu-id="edf62-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="edf62-115">DocumentViewer durumları</span><span class="sxs-lookup"><span data-stu-id="edf62-115">DocumentViewer States</span></span>  
 <span data-ttu-id="edf62-116">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.DocumentViewer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="edf62-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="edf62-117">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="edf62-117">VisualState Name</span></span>|<span data-ttu-id="edf62-118">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="edf62-118">VisualStateGroup Name</span></span>|<span data-ttu-id="edf62-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edf62-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="edf62-120">Geçerli</span><span class="sxs-lookup"><span data-stu-id="edf62-120">Valid</span></span>|<span data-ttu-id="edf62-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="edf62-121">ValidationStates</span></span>|<span data-ttu-id="edf62-122">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="edf62-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="edf62-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="edf62-123">InvalidFocused</span></span>|<span data-ttu-id="edf62-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="edf62-124">ValidationStates</span></span>|<span data-ttu-id="edf62-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="edf62-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="edf62-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="edf62-126">InvalidUnfocused</span></span>|<span data-ttu-id="edf62-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="edf62-127">ValidationStates</span></span>|<span data-ttu-id="edf62-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="edf62-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="edf62-129">DocumentViewer ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="edf62-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="edf62-130">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.DocumentViewer> denetimi.</span><span class="sxs-lookup"><span data-stu-id="edf62-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="edf62-131">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="edf62-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="edf62-132">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="edf62-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf62-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edf62-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="edf62-134">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="edf62-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="edf62-135">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="edf62-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="edf62-136">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="edf62-136">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="edf62-137">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="edf62-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
