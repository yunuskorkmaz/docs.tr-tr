---
title: NavigationWindow Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
ms.openlocfilehash: e481c84b462bc8d5114aadda2a368c4e7506d778
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457283"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="80152-102">NavigationWindow Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="80152-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="80152-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Navigation.NavigationWindow> denetim.</span><span class="sxs-lookup"><span data-stu-id="80152-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="80152-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="80152-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="80152-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="80152-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="80152-106">NavigationWindow bölümleri</span><span class="sxs-lookup"><span data-stu-id="80152-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="80152-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Navigation.NavigationWindow> denetim.</span><span class="sxs-lookup"><span data-stu-id="80152-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="80152-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="80152-108">Part</span></span>|<span data-ttu-id="80152-109">Tür</span><span class="sxs-lookup"><span data-stu-id="80152-109">Type</span></span>|<span data-ttu-id="80152-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80152-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="80152-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="80152-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="80152-112">İçerik için alan.</span><span class="sxs-lookup"><span data-stu-id="80152-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="80152-113">NavigationWindow durumları</span><span class="sxs-lookup"><span data-stu-id="80152-113">NavigationWindow States</span></span>  
 <span data-ttu-id="80152-114">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Navigation.NavigationWindow> denetim.</span><span class="sxs-lookup"><span data-stu-id="80152-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="80152-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="80152-115">VisualState Name</span></span>|<span data-ttu-id="80152-116">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="80152-116">VisualStateGroup Name</span></span>|<span data-ttu-id="80152-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80152-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="80152-118">Geçerli</span><span class="sxs-lookup"><span data-stu-id="80152-118">Valid</span></span>|<span data-ttu-id="80152-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="80152-119">ValidationStates</span></span>|<span data-ttu-id="80152-120">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="80152-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="80152-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="80152-121">InvalidFocused</span></span>|<span data-ttu-id="80152-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="80152-122">ValidationStates</span></span>|<span data-ttu-id="80152-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="80152-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="80152-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="80152-124">InvalidUnfocused</span></span>|<span data-ttu-id="80152-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="80152-125">ValidationStates</span></span>|<span data-ttu-id="80152-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="80152-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="80152-127">NavigationWindow ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="80152-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="80152-128">Bu örnek içinde tanımlanan tüm öğeleri içerse bile <xref:System.Windows.Controls.ControlTemplate> , bir <xref:System.Windows.Navigation.NavigationWindow> varsayılan olarak, belirli değerleri, örnek düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="80152-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="80152-129">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="80152-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="80152-130">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="80152-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80152-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80152-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="80152-132">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="80152-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="80152-133">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="80152-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="80152-134">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="80152-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="80152-135">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="80152-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
