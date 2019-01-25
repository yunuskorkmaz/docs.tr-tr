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
ms.openlocfilehash: 9b87c5c80533e12f5a93e4fc59cb5265a8374a33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521965"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="77834-102">ToolTip Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="77834-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="77834-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.ToolTip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="77834-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="77834-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="77834-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="77834-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="77834-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="77834-106">Araç İpucu bölümleri</span><span class="sxs-lookup"><span data-stu-id="77834-106">ToolTip Parts</span></span>  
 <span data-ttu-id="77834-107"><xref:System.Windows.Controls.ToolTip> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="77834-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="77834-108">Araç İpucu durumları</span><span class="sxs-lookup"><span data-stu-id="77834-108">ToolTip States</span></span>  
 <span data-ttu-id="77834-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.ToolTip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="77834-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="77834-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="77834-110">VisualState Name</span></span>|<span data-ttu-id="77834-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="77834-111">VisualStateGroup Name</span></span>|<span data-ttu-id="77834-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77834-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="77834-113">Closed</span><span class="sxs-lookup"><span data-stu-id="77834-113">Closed</span></span>|<span data-ttu-id="77834-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="77834-114">OpenStates</span></span>|<span data-ttu-id="77834-115">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="77834-115">The default state.</span></span>|  
|<span data-ttu-id="77834-116">Open</span><span class="sxs-lookup"><span data-stu-id="77834-116">Open</span></span>|<span data-ttu-id="77834-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="77834-117">OpenStates</span></span>|<span data-ttu-id="77834-118"><xref:System.Windows.Controls.ToolTip> Görülebilir.</span><span class="sxs-lookup"><span data-stu-id="77834-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="77834-119">Geçerli</span><span class="sxs-lookup"><span data-stu-id="77834-119">Valid</span></span>|<span data-ttu-id="77834-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="77834-120">ValidationStates</span></span>|<span data-ttu-id="77834-121">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="77834-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="77834-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="77834-122">InvalidFocused</span></span>|<span data-ttu-id="77834-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="77834-123">ValidationStates</span></span>|<span data-ttu-id="77834-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="77834-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="77834-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="77834-125">InvalidUnfocused</span></span>|<span data-ttu-id="77834-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="77834-126">ValidationStates</span></span>|<span data-ttu-id="77834-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="77834-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="77834-128">Araç İpucu ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="77834-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="77834-129">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.ToolTip> denetimi.</span><span class="sxs-lookup"><span data-stu-id="77834-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="77834-130">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="77834-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="77834-131">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="77834-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77834-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77834-132">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="77834-133">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="77834-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="77834-134">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="77834-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="77834-135">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="77834-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="77834-136">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="77834-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
