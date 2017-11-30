---
title: "NavigationWindow Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b48b0b4451f0cf93b86ee448db255f337a859b74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="2ee26-102">NavigationWindow Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="2ee26-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="2ee26-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Navigation.NavigationWindow> denetim.</span><span class="sxs-lookup"><span data-stu-id="2ee26-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="2ee26-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="2ee26-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2ee26-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2ee26-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="2ee26-106">NavigationWindow bölümleri</span><span class="sxs-lookup"><span data-stu-id="2ee26-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="2ee26-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Navigation.NavigationWindow> denetim.</span><span class="sxs-lookup"><span data-stu-id="2ee26-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="2ee26-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="2ee26-108">Part</span></span>|<span data-ttu-id="2ee26-109">Tür</span><span class="sxs-lookup"><span data-stu-id="2ee26-109">Type</span></span>|<span data-ttu-id="2ee26-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ee26-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2ee26-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="2ee26-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="2ee26-112">İçerik için alan.</span><span class="sxs-lookup"><span data-stu-id="2ee26-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="2ee26-113">NavigationWindow durumları</span><span class="sxs-lookup"><span data-stu-id="2ee26-113">NavigationWindow States</span></span>  
 <span data-ttu-id="2ee26-114">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Navigation.NavigationWindow> denetim.</span><span class="sxs-lookup"><span data-stu-id="2ee26-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="2ee26-115">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="2ee26-115">VisualState Name</span></span>|<span data-ttu-id="2ee26-116">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="2ee26-116">VisualStateGroup Name</span></span>|<span data-ttu-id="2ee26-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ee26-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2ee26-118">Geçerli</span><span class="sxs-lookup"><span data-stu-id="2ee26-118">Valid</span></span>|<span data-ttu-id="2ee26-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2ee26-119">ValidationStates</span></span>|<span data-ttu-id="2ee26-120">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="2ee26-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2ee26-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2ee26-121">InvalidFocused</span></span>|<span data-ttu-id="2ee26-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2ee26-122">ValidationStates</span></span>|<span data-ttu-id="2ee26-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="2ee26-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2ee26-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2ee26-124">InvalidUnfocused</span></span>|<span data-ttu-id="2ee26-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2ee26-125">ValidationStates</span></span>|<span data-ttu-id="2ee26-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2ee26-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="2ee26-127">NavigationWindow ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="2ee26-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="2ee26-128">Bu örnek içinde tanımlanan tüm öğeleri içerse bile <xref:System.Windows.Controls.ControlTemplate> , bir <xref:System.Windows.Navigation.NavigationWindow> varsayılan olarak, belirli değerleri, örnek düşünülmelidir.</span><span class="sxs-lookup"><span data-stu-id="2ee26-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="2ee26-129">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ee26-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2ee26-130">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="2ee26-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee26-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ee26-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="2ee26-132">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="2ee26-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="2ee26-133">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2ee26-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="2ee26-134">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ee26-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="2ee26-135">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2ee26-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
