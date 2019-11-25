---
title: StatusBar Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: 843c9003edbe94115719a63a968eda3833515a85
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283370"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="718a3-102">StatusBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="718a3-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="718a3-103">Bu konuda <xref:System.Windows.Controls.Primitives.StatusBar> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="718a3-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="718a3-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="718a3-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="718a3-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="718a3-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="718a3-106">Durum çubuğu parçaları</span><span class="sxs-lookup"><span data-stu-id="718a3-106">StatusBar Parts</span></span>  
 <span data-ttu-id="718a3-107"><xref:System.Windows.Controls.Primitives.StatusBar> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="718a3-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="718a3-108">Durum çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="718a3-108">StatusBar States</span></span>  
 <span data-ttu-id="718a3-109">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.StatusBar> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="718a3-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="718a3-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="718a3-110">VisualState Name</span></span>|<span data-ttu-id="718a3-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="718a3-111">VisualStateGroup Name</span></span>|<span data-ttu-id="718a3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="718a3-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="718a3-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="718a3-113">Valid</span></span>|<span data-ttu-id="718a3-114">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="718a3-114">ValidationStates</span></span>|<span data-ttu-id="718a3-115">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="718a3-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="718a3-116">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="718a3-116">InvalidFocused</span></span>|<span data-ttu-id="718a3-117">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="718a3-117">ValidationStates</span></span>|<span data-ttu-id="718a3-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="718a3-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="718a3-119">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="718a3-119">InvalidUnfocused</span></span>|<span data-ttu-id="718a3-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="718a3-120">ValidationStates</span></span>|<span data-ttu-id="718a3-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="718a3-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="718a3-122">StatusBarItem parçalar</span><span class="sxs-lookup"><span data-stu-id="718a3-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="718a3-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="718a3-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="718a3-124">Durum çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="718a3-124">StatusBar States</span></span>  
 <span data-ttu-id="718a3-125">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.StatusBarItem> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="718a3-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="718a3-126">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="718a3-126">VisualState Name</span></span>|<span data-ttu-id="718a3-127">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="718a3-127">VisualStateGroup Name</span></span>|<span data-ttu-id="718a3-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="718a3-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="718a3-129">Geçerli</span><span class="sxs-lookup"><span data-stu-id="718a3-129">Valid</span></span>|<span data-ttu-id="718a3-130">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="718a3-130">ValidationStates</span></span>|<span data-ttu-id="718a3-131">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="718a3-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="718a3-132">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="718a3-132">InvalidFocused</span></span>|<span data-ttu-id="718a3-133">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="718a3-133">ValidationStates</span></span>|<span data-ttu-id="718a3-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="718a3-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="718a3-135">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="718a3-135">InvalidUnfocused</span></span>|<span data-ttu-id="718a3-136">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="718a3-136">ValidationStates</span></span>|<span data-ttu-id="718a3-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="718a3-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="718a3-138">StatusBar ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="718a3-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="718a3-139">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.StatusBar> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="718a3-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="718a3-140"><xref:System.Windows.Controls.ControlTemplate> aşağıdaki kaynaklardan bir veya daha fazlasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="718a3-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="718a3-141">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="718a3-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="718a3-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="718a3-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="718a3-143">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="718a3-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="718a3-144">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="718a3-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="718a3-145">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="718a3-145">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="718a3-146">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="718a3-146">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
