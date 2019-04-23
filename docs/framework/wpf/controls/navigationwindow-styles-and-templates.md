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
ms.openlocfilehash: 32d8aac99d40693e66c7b52a6c7d2c116d2f3baf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225813"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="5f804-102">NavigationWindow Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="5f804-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="5f804-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Navigation.NavigationWindow> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5f804-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="5f804-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="5f804-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5f804-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="5f804-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="5f804-106">NavigationWindow bölümleri</span><span class="sxs-lookup"><span data-stu-id="5f804-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="5f804-107">Adlandırılmış bölümleri için aşağıdaki tabloda <xref:System.Windows.Navigation.NavigationWindow> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5f804-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="5f804-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="5f804-108">Part</span></span>|<span data-ttu-id="5f804-109">Tür</span><span class="sxs-lookup"><span data-stu-id="5f804-109">Type</span></span>|<span data-ttu-id="5f804-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f804-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5f804-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="5f804-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="5f804-112">İçerik için alan.</span><span class="sxs-lookup"><span data-stu-id="5f804-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="5f804-113">NavigationWindow durumları</span><span class="sxs-lookup"><span data-stu-id="5f804-113">NavigationWindow States</span></span>  
 <span data-ttu-id="5f804-114">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Navigation.NavigationWindow> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5f804-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="5f804-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="5f804-115">VisualState Name</span></span>|<span data-ttu-id="5f804-116">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="5f804-116">VisualStateGroup Name</span></span>|<span data-ttu-id="5f804-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f804-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5f804-118">Geçerli</span><span class="sxs-lookup"><span data-stu-id="5f804-118">Valid</span></span>|<span data-ttu-id="5f804-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5f804-119">ValidationStates</span></span>|<span data-ttu-id="5f804-120">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="5f804-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5f804-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5f804-121">InvalidFocused</span></span>|<span data-ttu-id="5f804-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5f804-122">ValidationStates</span></span>|<span data-ttu-id="5f804-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="5f804-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5f804-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5f804-124">InvalidUnfocused</span></span>|<span data-ttu-id="5f804-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5f804-125">ValidationStates</span></span>|<span data-ttu-id="5f804-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="5f804-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="5f804-127">NavigationWindow ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="5f804-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="5f804-128">Bu örnekte tanımlanan tüm öğeleri içerse de <xref:System.Windows.Controls.ControlTemplate> , bir <xref:System.Windows.Navigation.NavigationWindow> varsayılan olarak, belirli değerleri, örnek düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="5f804-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="5f804-129">Yukarıdaki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5f804-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5f804-130">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="5f804-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f804-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f804-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="5f804-132">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="5f804-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="5f804-133">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5f804-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="5f804-134">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5f804-134">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="5f804-135">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5f804-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
