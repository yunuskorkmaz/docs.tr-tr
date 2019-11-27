---
title: ProgressBar Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 6551701e86dd6abcd42f143f146c7bdadfeabbcf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283448"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="b2991-102">ProgressBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="b2991-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="b2991-103">Bu konuda <xref:System.Windows.Controls.ProgressBar> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2991-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="b2991-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2991-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b2991-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="b2991-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="b2991-106">ProgressBar parçaları</span><span class="sxs-lookup"><span data-stu-id="b2991-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="b2991-107">Aşağıdaki tabloda <xref:System.Windows.Controls.ProgressBar> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2991-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="b2991-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="b2991-108">Part</span></span>|<span data-ttu-id="b2991-109">Type</span><span class="sxs-lookup"><span data-stu-id="b2991-109">Type</span></span>|<span data-ttu-id="b2991-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2991-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b2991-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="b2991-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="b2991-112">İlerlemeyi belirten nesne.</span><span class="sxs-lookup"><span data-stu-id="b2991-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="b2991-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="b2991-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="b2991-114">İlerleme göstergesinin yolunu tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="b2991-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="b2991-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="b2991-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="b2991-116">İlerleme çubuğunu gösteren bir nesne.</span><span class="sxs-lookup"><span data-stu-id="b2991-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="b2991-117">ProgressBar durumları</span><span class="sxs-lookup"><span data-stu-id="b2991-117">ProgressBar States</span></span>  
 <span data-ttu-id="b2991-118">Aşağıdaki tabloda <xref:System.Windows.Controls.ProgressBar> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="b2991-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="b2991-119">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="b2991-119">VisualState Name</span></span>|<span data-ttu-id="b2991-120">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="b2991-120">VisualStateGroup Name</span></span>|<span data-ttu-id="b2991-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2991-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="b2991-122">Kararlı</span><span class="sxs-lookup"><span data-stu-id="b2991-122">Determinate</span></span>|<span data-ttu-id="b2991-123">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="b2991-123">CommonStates</span></span>|<span data-ttu-id="b2991-124"><xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliğine göre ilerlemeyi raporlar.</span><span class="sxs-lookup"><span data-stu-id="b2991-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="b2991-125">Belirsiz</span><span class="sxs-lookup"><span data-stu-id="b2991-125">Indeterminate</span></span>|<span data-ttu-id="b2991-126">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="b2991-126">CommonStates</span></span>|<span data-ttu-id="b2991-127"><xref:System.Windows.Controls.ProgressBar>, yinelenen bir desenli genel ilerlemeyi raporlar.</span><span class="sxs-lookup"><span data-stu-id="b2991-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="b2991-128">Geçerli</span><span class="sxs-lookup"><span data-stu-id="b2991-128">Valid</span></span>|<span data-ttu-id="b2991-129">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="b2991-129">ValidationStates</span></span>|<span data-ttu-id="b2991-130">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="b2991-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b2991-131">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="b2991-131">InvalidFocused</span></span>|<span data-ttu-id="b2991-132">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="b2991-132">ValidationStates</span></span>|<span data-ttu-id="b2991-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="b2991-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b2991-134">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="b2991-134">InvalidUnfocused</span></span>|<span data-ttu-id="b2991-135">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="b2991-135">ValidationStates</span></span>|<span data-ttu-id="b2991-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="b2991-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="b2991-137">ProgressBar ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="b2991-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="b2991-138">Aşağıdaki örnek, <xref:System.Windows.Controls.ProgressBar> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2991-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="b2991-139">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2991-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b2991-140">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="b2991-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2991-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2991-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b2991-142">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="b2991-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b2991-143">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b2991-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b2991-144">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2991-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="b2991-145">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="b2991-145">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
