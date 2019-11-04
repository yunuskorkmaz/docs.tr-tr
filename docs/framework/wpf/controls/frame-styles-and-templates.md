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
ms.openlocfilehash: 89f4fc21637d20ca226507463093bc6bae2241fc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460314"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="015a5-102">Çerçeve Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="015a5-102">Frame Styles and Templates</span></span>
<span data-ttu-id="015a5-103">Bu konuda <xref:System.Windows.Controls.Frame> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="015a5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="015a5-104">Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="015a5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="015a5-105">Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="015a5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="015a5-106">Çerçeve bölümleri</span><span class="sxs-lookup"><span data-stu-id="015a5-106">Frame Parts</span></span>  
 <span data-ttu-id="015a5-107">Aşağıdaki tabloda <xref:System.Windows.Controls.Frame> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="015a5-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="015a5-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="015a5-108">Part</span></span>|<span data-ttu-id="015a5-109">Tür</span><span class="sxs-lookup"><span data-stu-id="015a5-109">Type</span></span>|<span data-ttu-id="015a5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="015a5-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="015a5-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="015a5-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="015a5-112">İçerik alanı.</span><span class="sxs-lookup"><span data-stu-id="015a5-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="015a5-113">Çerçeve durumları</span><span class="sxs-lookup"><span data-stu-id="015a5-113">Frame States</span></span>  
 <span data-ttu-id="015a5-114">Aşağıdaki tabloda <xref:System.Windows.Controls.Frame> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="015a5-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="015a5-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="015a5-115">VisualState Name</span></span>|<span data-ttu-id="015a5-116">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="015a5-116">VisualStateGroup Name</span></span>|<span data-ttu-id="015a5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="015a5-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="015a5-118">Geçerli</span><span class="sxs-lookup"><span data-stu-id="015a5-118">Valid</span></span>|<span data-ttu-id="015a5-119">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="015a5-119">ValidationStates</span></span>|<span data-ttu-id="015a5-120">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="015a5-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="015a5-121">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="015a5-121">InvalidFocused</span></span>|<span data-ttu-id="015a5-122">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="015a5-122">ValidationStates</span></span>|<span data-ttu-id="015a5-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="015a5-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="015a5-124">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="015a5-124">InvalidUnfocused</span></span>|<span data-ttu-id="015a5-125">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="015a5-125">ValidationStates</span></span>|<span data-ttu-id="015a5-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="015a5-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="015a5-127">Frame ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="015a5-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="015a5-128">Aşağıdaki örnek, <xref:System.Windows.Controls.Frame> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="015a5-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="015a5-129">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="015a5-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="015a5-130">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="015a5-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015a5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="015a5-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="015a5-132">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="015a5-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="015a5-133">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="015a5-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="015a5-134">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="015a5-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="015a5-135">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="015a5-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
