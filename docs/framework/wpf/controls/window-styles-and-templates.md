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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62023838"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="0cdce-102">Pencere Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="0cdce-102">Window Styles and Templates</span></span>
<span data-ttu-id="0cdce-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Window> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0cdce-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="0cdce-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="0cdce-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="0cdce-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="0cdce-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="0cdce-106">Pencere bölümleri</span><span class="sxs-lookup"><span data-stu-id="0cdce-106">Window Parts</span></span>  
 <span data-ttu-id="0cdce-107"><xref:System.Windows.Window> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="0cdce-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="0cdce-108">Pencere durumları</span><span class="sxs-lookup"><span data-stu-id="0cdce-108">Window States</span></span>  
 <span data-ttu-id="0cdce-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Window> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0cdce-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="0cdce-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="0cdce-110">VisualState Name</span></span>|<span data-ttu-id="0cdce-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="0cdce-111">VisualStateGroup Name</span></span>|<span data-ttu-id="0cdce-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cdce-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0cdce-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="0cdce-113">Valid</span></span>|<span data-ttu-id="0cdce-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0cdce-114">ValidationStates</span></span>|<span data-ttu-id="0cdce-115">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="0cdce-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="0cdce-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="0cdce-116">InvalidFocused</span></span>|<span data-ttu-id="0cdce-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0cdce-117">ValidationStates</span></span>|<span data-ttu-id="0cdce-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="0cdce-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="0cdce-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="0cdce-119">InvalidUnfocused</span></span>|<span data-ttu-id="0cdce-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="0cdce-120">ValidationStates</span></span>|<span data-ttu-id="0cdce-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="0cdce-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="0cdce-122">Pencere ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="0cdce-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="0cdce-123">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Window> denetimi.</span><span class="sxs-lookup"><span data-stu-id="0cdce-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="0cdce-124"><xref:System.Windows.Controls.ControlTemplate> Bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cdce-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="0cdce-125">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="0cdce-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdce-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cdce-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="0cdce-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="0cdce-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="0cdce-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0cdce-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="0cdce-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0cdce-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="0cdce-130">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0cdce-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
