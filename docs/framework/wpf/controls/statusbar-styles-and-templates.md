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
ms.openlocfilehash: b1dd575d58571b845fc849ca432ad440d1ce3ec4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458266"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="c5fbb-102">StatusBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="c5fbb-103">Bu konuda <xref:System.Windows.Controls.Primitives.StatusBar> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="c5fbb-104">Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c5fbb-105">Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c5fbb-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="c5fbb-106">Durum çubuğu parçaları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-106">StatusBar Parts</span></span>  
 <span data-ttu-id="c5fbb-107"><xref:System.Windows.Controls.Primitives.StatusBar> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="c5fbb-108">Durum çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-108">StatusBar States</span></span>  
 <span data-ttu-id="c5fbb-109">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.StatusBar> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="c5fbb-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="c5fbb-110">VisualState Name</span></span>|<span data-ttu-id="c5fbb-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="c5fbb-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c5fbb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5fbb-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c5fbb-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="c5fbb-113">Valid</span></span>|<span data-ttu-id="c5fbb-114">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-114">ValidationStates</span></span>|<span data-ttu-id="c5fbb-115">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c5fbb-116">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="c5fbb-116">InvalidFocused</span></span>|<span data-ttu-id="c5fbb-117">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-117">ValidationStates</span></span>|<span data-ttu-id="c5fbb-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c5fbb-119">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="c5fbb-119">InvalidUnfocused</span></span>|<span data-ttu-id="c5fbb-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-120">ValidationStates</span></span>|<span data-ttu-id="c5fbb-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="c5fbb-122">StatusBarItem parçalar</span><span class="sxs-lookup"><span data-stu-id="c5fbb-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="c5fbb-123"><xref:System.Windows.Controls.Primitives.StatusBarItem> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="c5fbb-124">Durum çubuğu durumları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-124">StatusBar States</span></span>  
 <span data-ttu-id="c5fbb-125">Aşağıdaki tabloda <xref:System.Windows.Controls.Primitives.StatusBarItem> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="c5fbb-126">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="c5fbb-126">VisualState Name</span></span>|<span data-ttu-id="c5fbb-127">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="c5fbb-127">VisualStateGroup Name</span></span>|<span data-ttu-id="c5fbb-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5fbb-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c5fbb-129">Geçerli</span><span class="sxs-lookup"><span data-stu-id="c5fbb-129">Valid</span></span>|<span data-ttu-id="c5fbb-130">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-130">ValidationStates</span></span>|<span data-ttu-id="c5fbb-131">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c5fbb-132">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="c5fbb-132">InvalidFocused</span></span>|<span data-ttu-id="c5fbb-133">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-133">ValidationStates</span></span>|<span data-ttu-id="c5fbb-134"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c5fbb-135">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="c5fbb-135">InvalidUnfocused</span></span>|<span data-ttu-id="c5fbb-136">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-136">ValidationStates</span></span>|<span data-ttu-id="c5fbb-137"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="c5fbb-138">StatusBar ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="c5fbb-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="c5fbb-139">Aşağıdaki örnek, <xref:System.Windows.Controls.Primitives.StatusBar> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="c5fbb-140"><xref:System.Windows.Controls.ControlTemplate> aşağıdaki kaynaklardan bir veya daha fazlasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c5fbb-141">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="c5fbb-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fbb-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5fbb-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c5fbb-143">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="c5fbb-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c5fbb-144">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c5fbb-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c5fbb-145">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5fbb-145">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c5fbb-146">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c5fbb-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
