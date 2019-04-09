---
title: Çerçeve Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
ms.openlocfilehash: 6b084cfa31efebe2456871a99cd810741aa26609
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131033"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="d527f-102">Çerçeve Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d527f-102">Frame Styles and Templates</span></span>
<span data-ttu-id="d527f-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Frame> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d527f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="d527f-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d527f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="d527f-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="d527f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="d527f-106">Çerçeve bölümü</span><span class="sxs-lookup"><span data-stu-id="d527f-106">Frame Parts</span></span>  
 <span data-ttu-id="d527f-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Controls.Frame> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d527f-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="d527f-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="d527f-108">Part</span></span>|<span data-ttu-id="d527f-109">Tür</span><span class="sxs-lookup"><span data-stu-id="d527f-109">Type</span></span>|<span data-ttu-id="d527f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d527f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d527f-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="d527f-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="d527f-112">İçerik alanı.</span><span class="sxs-lookup"><span data-stu-id="d527f-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="d527f-113">Çerçeve durumları</span><span class="sxs-lookup"><span data-stu-id="d527f-113">Frame States</span></span>  
 <span data-ttu-id="d527f-114">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Frame> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d527f-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="d527f-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="d527f-115">VisualState Name</span></span>|<span data-ttu-id="d527f-116">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="d527f-116">VisualStateGroup Name</span></span>|<span data-ttu-id="d527f-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d527f-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d527f-118">Geçerli</span><span class="sxs-lookup"><span data-stu-id="d527f-118">Valid</span></span>|<span data-ttu-id="d527f-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d527f-119">ValidationStates</span></span>|<span data-ttu-id="d527f-120">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="d527f-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="d527f-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="d527f-121">InvalidFocused</span></span>|<span data-ttu-id="d527f-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d527f-122">ValidationStates</span></span>|<span data-ttu-id="d527f-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="d527f-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="d527f-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="d527f-124">InvalidUnfocused</span></span>|<span data-ttu-id="d527f-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="d527f-125">ValidationStates</span></span>|<span data-ttu-id="d527f-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d527f-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="d527f-127">Çerçeve ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="d527f-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="d527f-128">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Frame> denetimi.</span><span class="sxs-lookup"><span data-stu-id="d527f-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="d527f-129">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d527f-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="d527f-130">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="d527f-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d527f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d527f-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="d527f-132">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="d527f-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="d527f-133">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d527f-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="d527f-134">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d527f-134">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="d527f-135">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="d527f-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
