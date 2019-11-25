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
ms.openlocfilehash: ac1dc4f74a8e8f3ad2e84c6d50239ec827306c28
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283527"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="2f7ae-102">DocumentViewer Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="2f7ae-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="2f7ae-103">Bu konuda <xref:System.Windows.Controls.DocumentViewer> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="2f7ae-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2f7ae-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="2f7ae-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="2f7ae-106">DocumentViewer parçaları</span><span class="sxs-lookup"><span data-stu-id="2f7ae-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="2f7ae-107">Aşağıdaki tabloda <xref:System.Windows.Controls.DocumentViewer> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="2f7ae-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="2f7ae-108">Part</span></span>|<span data-ttu-id="2f7ae-109">Type</span><span class="sxs-lookup"><span data-stu-id="2f7ae-109">Type</span></span>|<span data-ttu-id="2f7ae-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f7ae-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2f7ae-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="2f7ae-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="2f7ae-112">İçerik ve kaydırma alanı.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="2f7ae-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="2f7ae-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="2f7ae-114">Varsayılan olarak alt kısımdaki arama kutusu.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="2f7ae-115">DocumentViewer durumları</span><span class="sxs-lookup"><span data-stu-id="2f7ae-115">DocumentViewer States</span></span>  
 <span data-ttu-id="2f7ae-116">Aşağıdaki tabloda <xref:System.Windows.Controls.DocumentViewer> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="2f7ae-117">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="2f7ae-117">VisualState Name</span></span>|<span data-ttu-id="2f7ae-118">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="2f7ae-118">VisualStateGroup Name</span></span>|<span data-ttu-id="2f7ae-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2f7ae-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2f7ae-120">Geçerli</span><span class="sxs-lookup"><span data-stu-id="2f7ae-120">Valid</span></span>|<span data-ttu-id="2f7ae-121">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="2f7ae-121">ValidationStates</span></span>|<span data-ttu-id="2f7ae-122">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2f7ae-123">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="2f7ae-123">InvalidFocused</span></span>|<span data-ttu-id="2f7ae-124">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="2f7ae-124">ValidationStates</span></span>|<span data-ttu-id="2f7ae-125"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2f7ae-126">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="2f7ae-126">InvalidUnfocused</span></span>|<span data-ttu-id="2f7ae-127">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="2f7ae-127">ValidationStates</span></span>|<span data-ttu-id="2f7ae-128"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="2f7ae-129">DocumentViewer ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="2f7ae-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="2f7ae-130">Aşağıdaki örnek, <xref:System.Windows.Controls.DocumentViewer> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="2f7ae-131">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2f7ae-132">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2f7ae-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f7ae-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2f7ae-134">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="2f7ae-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2f7ae-135">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2f7ae-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2f7ae-136">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f7ae-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="2f7ae-137">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f7ae-137">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
