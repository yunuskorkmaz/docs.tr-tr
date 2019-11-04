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
ms.openlocfilehash: 3a1bea39ba9b6d2cff9937a3fee1d1de41daf16b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459875"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="32073-102">ProgressBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="32073-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="32073-103">Bu konuda <xref:System.Windows.Controls.ProgressBar> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32073-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="32073-104">Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32073-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="32073-105">Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="32073-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="32073-106">ProgressBar parçaları</span><span class="sxs-lookup"><span data-stu-id="32073-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="32073-107">Aşağıdaki tabloda <xref:System.Windows.Controls.ProgressBar> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="32073-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="32073-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="32073-108">Part</span></span>|<span data-ttu-id="32073-109">Tür</span><span class="sxs-lookup"><span data-stu-id="32073-109">Type</span></span>|<span data-ttu-id="32073-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32073-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="32073-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="32073-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="32073-112">İlerlemeyi belirten nesne.</span><span class="sxs-lookup"><span data-stu-id="32073-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="32073-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="32073-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="32073-114">İlerleme göstergesinin yolunu tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="32073-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="32073-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="32073-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="32073-116">İlerleme çubuğunu gösteren bir nesne.</span><span class="sxs-lookup"><span data-stu-id="32073-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="32073-117">ProgressBar durumları</span><span class="sxs-lookup"><span data-stu-id="32073-117">ProgressBar States</span></span>  
 <span data-ttu-id="32073-118">Aşağıdaki tabloda <xref:System.Windows.Controls.ProgressBar> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="32073-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="32073-119">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="32073-119">VisualState Name</span></span>|<span data-ttu-id="32073-120">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="32073-120">VisualStateGroup Name</span></span>|<span data-ttu-id="32073-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32073-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="32073-122">Kararlı</span><span class="sxs-lookup"><span data-stu-id="32073-122">Determinate</span></span>|<span data-ttu-id="32073-123">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="32073-123">CommonStates</span></span>|<span data-ttu-id="32073-124"><xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> özelliğine göre ilerlemeyi raporlar.</span><span class="sxs-lookup"><span data-stu-id="32073-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="32073-125">'Dır</span><span class="sxs-lookup"><span data-stu-id="32073-125">Indeterminate</span></span>|<span data-ttu-id="32073-126">Ortak durumlar</span><span class="sxs-lookup"><span data-stu-id="32073-126">CommonStates</span></span>|<span data-ttu-id="32073-127"><xref:System.Windows.Controls.ProgressBar>, yinelenen bir desenli genel ilerlemeyi raporlar.</span><span class="sxs-lookup"><span data-stu-id="32073-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="32073-128">Geçerli</span><span class="sxs-lookup"><span data-stu-id="32073-128">Valid</span></span>|<span data-ttu-id="32073-129">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="32073-129">ValidationStates</span></span>|<span data-ttu-id="32073-130">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="32073-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="32073-131">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="32073-131">InvalidFocused</span></span>|<span data-ttu-id="32073-132">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="32073-132">ValidationStates</span></span>|<span data-ttu-id="32073-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="32073-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="32073-134">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="32073-134">InvalidUnfocused</span></span>|<span data-ttu-id="32073-135">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="32073-135">ValidationStates</span></span>|<span data-ttu-id="32073-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="32073-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="32073-137">ProgressBar ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="32073-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="32073-138">Aşağıdaki örnek, <xref:System.Windows.Controls.ProgressBar> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="32073-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="32073-139">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32073-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="32073-140">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="32073-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32073-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32073-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="32073-142">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="32073-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="32073-143">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="32073-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="32073-144">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="32073-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="32073-145">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="32073-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
