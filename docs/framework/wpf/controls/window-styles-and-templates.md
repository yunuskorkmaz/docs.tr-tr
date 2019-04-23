---
title: Pencere Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
ms.openlocfilehash: ebd21829591b8fefe87aeba0b86280f18eff4f06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203736"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="bb919-102">Pencere Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="bb919-102">Window Styles and Templates</span></span>
<span data-ttu-id="bb919-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Window> denetimi.</span><span class="sxs-lookup"><span data-stu-id="bb919-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="bb919-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="bb919-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="bb919-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="bb919-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="bb919-106">Pencere bölümleri</span><span class="sxs-lookup"><span data-stu-id="bb919-106">Window Parts</span></span>  
 <span data-ttu-id="bb919-107"><xref:System.Windows.Window> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="bb919-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="bb919-108">Pencere durumları</span><span class="sxs-lookup"><span data-stu-id="bb919-108">Window States</span></span>  
 <span data-ttu-id="bb919-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Window> denetimi.</span><span class="sxs-lookup"><span data-stu-id="bb919-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="bb919-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="bb919-110">VisualState Name</span></span>|<span data-ttu-id="bb919-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="bb919-111">VisualStateGroup Name</span></span>|<span data-ttu-id="bb919-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb919-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="bb919-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="bb919-113">Valid</span></span>|<span data-ttu-id="bb919-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bb919-114">ValidationStates</span></span>|<span data-ttu-id="bb919-115">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="bb919-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="bb919-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="bb919-116">InvalidFocused</span></span>|<span data-ttu-id="bb919-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bb919-117">ValidationStates</span></span>|<span data-ttu-id="bb919-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="bb919-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="bb919-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="bb919-119">InvalidUnfocused</span></span>|<span data-ttu-id="bb919-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="bb919-120">ValidationStates</span></span>|<span data-ttu-id="bb919-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="bb919-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="bb919-122">Pencere ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="bb919-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="bb919-123">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Window> denetimi.</span><span class="sxs-lookup"><span data-stu-id="bb919-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="bb919-124"><xref:System.Windows.Controls.ControlTemplate> Bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="bb919-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="bb919-125">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="bb919-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb919-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb919-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="bb919-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="bb919-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="bb919-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="bb919-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="bb919-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bb919-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="bb919-130">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="bb919-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
