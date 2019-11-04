---
title: ToolTip Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: 626d0b4d49d653f820d1506f0aa09f06d26352c2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458638"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="192a6-102">ToolTip Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="192a6-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="192a6-103">Bu konuda <xref:System.Windows.Controls.ToolTip> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="192a6-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="192a6-104">Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="192a6-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="192a6-105">Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="192a6-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="192a6-106">Araç Ipucu parçaları</span><span class="sxs-lookup"><span data-stu-id="192a6-106">ToolTip Parts</span></span>  
 <span data-ttu-id="192a6-107"><xref:System.Windows.Controls.ToolTip> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="192a6-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="192a6-108">Araç Ipucu durumları</span><span class="sxs-lookup"><span data-stu-id="192a6-108">ToolTip States</span></span>  
 <span data-ttu-id="192a6-109">Aşağıdaki tabloda <xref:System.Windows.Controls.ToolTip> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="192a6-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="192a6-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="192a6-110">VisualState Name</span></span>|<span data-ttu-id="192a6-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="192a6-111">VisualStateGroup Name</span></span>|<span data-ttu-id="192a6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="192a6-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="192a6-113">Kapatıldı</span><span class="sxs-lookup"><span data-stu-id="192a6-113">Closed</span></span>|<span data-ttu-id="192a6-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="192a6-114">OpenStates</span></span>|<span data-ttu-id="192a6-115">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="192a6-115">The default state.</span></span>|  
|<span data-ttu-id="192a6-116">Open</span><span class="sxs-lookup"><span data-stu-id="192a6-116">Open</span></span>|<span data-ttu-id="192a6-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="192a6-117">OpenStates</span></span>|<span data-ttu-id="192a6-118"><xref:System.Windows.Controls.ToolTip> görünür.</span><span class="sxs-lookup"><span data-stu-id="192a6-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="192a6-119">Geçerli</span><span class="sxs-lookup"><span data-stu-id="192a6-119">Valid</span></span>|<span data-ttu-id="192a6-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="192a6-120">ValidationStates</span></span>|<span data-ttu-id="192a6-121">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="192a6-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="192a6-122">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="192a6-122">InvalidFocused</span></span>|<span data-ttu-id="192a6-123">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="192a6-123">ValidationStates</span></span>|<span data-ttu-id="192a6-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="192a6-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="192a6-125">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="192a6-125">InvalidUnfocused</span></span>|<span data-ttu-id="192a6-126">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="192a6-126">ValidationStates</span></span>|<span data-ttu-id="192a6-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="192a6-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="192a6-128">Araç Ipucu ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="192a6-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="192a6-129">Aşağıdaki örnek, <xref:System.Windows.Controls.ToolTip> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="192a6-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="192a6-130">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="192a6-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="192a6-131">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="192a6-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192a6-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="192a6-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="192a6-133">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="192a6-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="192a6-134">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="192a6-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="192a6-135">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="192a6-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="192a6-136">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="192a6-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
