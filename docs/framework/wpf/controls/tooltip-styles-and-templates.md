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
ms.openlocfilehash: c7a14034d665c124d01e8a4b43c5d42968241925
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283640"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="80132-102">ToolTip Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="80132-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="80132-103">Bu konuda <xref:System.Windows.Controls.ToolTip> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80132-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="80132-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80132-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="80132-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="80132-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="80132-106">Araç Ipucu parçaları</span><span class="sxs-lookup"><span data-stu-id="80132-106">ToolTip Parts</span></span>  
 <span data-ttu-id="80132-107"><xref:System.Windows.Controls.ToolTip> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="80132-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="80132-108">Araç Ipucu durumları</span><span class="sxs-lookup"><span data-stu-id="80132-108">ToolTip States</span></span>  
 <span data-ttu-id="80132-109">Aşağıdaki tabloda <xref:System.Windows.Controls.ToolTip> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="80132-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="80132-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="80132-110">VisualState Name</span></span>|<span data-ttu-id="80132-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="80132-111">VisualStateGroup Name</span></span>|<span data-ttu-id="80132-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80132-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="80132-113">Kapatıldı</span><span class="sxs-lookup"><span data-stu-id="80132-113">Closed</span></span>|<span data-ttu-id="80132-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="80132-114">OpenStates</span></span>|<span data-ttu-id="80132-115">Varsayılan durum.</span><span class="sxs-lookup"><span data-stu-id="80132-115">The default state.</span></span>|  
|<span data-ttu-id="80132-116">Açık</span><span class="sxs-lookup"><span data-stu-id="80132-116">Open</span></span>|<span data-ttu-id="80132-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="80132-117">OpenStates</span></span>|<span data-ttu-id="80132-118"><xref:System.Windows.Controls.ToolTip> görünür.</span><span class="sxs-lookup"><span data-stu-id="80132-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="80132-119">Geçerli</span><span class="sxs-lookup"><span data-stu-id="80132-119">Valid</span></span>|<span data-ttu-id="80132-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="80132-120">ValidationStates</span></span>|<span data-ttu-id="80132-121">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="80132-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="80132-122">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="80132-122">InvalidFocused</span></span>|<span data-ttu-id="80132-123">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="80132-123">ValidationStates</span></span>|<span data-ttu-id="80132-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="80132-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="80132-125">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="80132-125">InvalidUnfocused</span></span>|<span data-ttu-id="80132-126">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="80132-126">ValidationStates</span></span>|<span data-ttu-id="80132-127"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="80132-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="80132-128">Araç Ipucu ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="80132-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="80132-129">Aşağıdaki örnek, <xref:System.Windows.Controls.ToolTip> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="80132-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="80132-130">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80132-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="80132-131">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="80132-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80132-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80132-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="80132-133">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="80132-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="80132-134">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="80132-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="80132-135">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="80132-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="80132-136">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="80132-136">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
