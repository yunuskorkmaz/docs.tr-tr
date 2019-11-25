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
ms.openlocfilehash: 5cc504956ce036505ac9261ea1438c7881fa2790
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283486"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="4431d-102">NavigationWindow Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="4431d-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="4431d-103">Bu konuda <xref:System.Windows.Navigation.NavigationWindow> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4431d-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="4431d-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4431d-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="4431d-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="4431d-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="4431d-106">NavigationWindow bölümleri</span><span class="sxs-lookup"><span data-stu-id="4431d-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="4431d-107">Aşağıdaki tabloda <xref:System.Windows.Navigation.NavigationWindow> denetimi için adlandırılmış bölümler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4431d-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="4431d-108">Bölümüyle</span><span class="sxs-lookup"><span data-stu-id="4431d-108">Part</span></span>|<span data-ttu-id="4431d-109">Type</span><span class="sxs-lookup"><span data-stu-id="4431d-109">Type</span></span>|<span data-ttu-id="4431d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4431d-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4431d-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="4431d-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="4431d-112">İçerik alanı.</span><span class="sxs-lookup"><span data-stu-id="4431d-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="4431d-113">NavigationWindow durumları</span><span class="sxs-lookup"><span data-stu-id="4431d-113">NavigationWindow States</span></span>  
 <span data-ttu-id="4431d-114">Aşağıdaki tabloda <xref:System.Windows.Navigation.NavigationWindow> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="4431d-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="4431d-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="4431d-115">VisualState Name</span></span>|<span data-ttu-id="4431d-116">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="4431d-116">VisualStateGroup Name</span></span>|<span data-ttu-id="4431d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4431d-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="4431d-118">Geçerli</span><span class="sxs-lookup"><span data-stu-id="4431d-118">Valid</span></span>|<span data-ttu-id="4431d-119">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="4431d-119">ValidationStates</span></span>|<span data-ttu-id="4431d-120">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="4431d-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="4431d-121">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="4431d-121">InvalidFocused</span></span>|<span data-ttu-id="4431d-122">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="4431d-122">ValidationStates</span></span>|<span data-ttu-id="4431d-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="4431d-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="4431d-124">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="4431d-124">InvalidUnfocused</span></span>|<span data-ttu-id="4431d-125">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="4431d-125">ValidationStates</span></span>|<span data-ttu-id="4431d-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="4431d-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="4431d-127">NavigationWindow ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="4431d-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="4431d-128">Bu örnek, varsayılan olarak bir <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.ControlTemplate> tanımlanmış tüm öğeleri içerse de, belirli değerler örnek olarak düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="4431d-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="4431d-129">Yukarıdaki örnekte aşağıdaki kaynaklardan biri veya daha fazlası kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4431d-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="4431d-130">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="4431d-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4431d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4431d-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="4431d-132">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="4431d-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="4431d-133">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4431d-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="4431d-134">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4431d-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="4431d-135">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="4431d-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
