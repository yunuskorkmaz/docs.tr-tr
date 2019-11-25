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
ms.openlocfilehash: 01233c5d0179e1a6f9bed651cd1f18058bfac168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283606"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="51a34-102">Pencere Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="51a34-102">Window Styles and Templates</span></span>
<span data-ttu-id="51a34-103">Bu konuda <xref:System.Windows.Window> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="51a34-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="51a34-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51a34-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="51a34-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="51a34-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="51a34-106">Pencere parçaları</span><span class="sxs-lookup"><span data-stu-id="51a34-106">Window Parts</span></span>  
 <span data-ttu-id="51a34-107"><xref:System.Windows.Window> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="51a34-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="51a34-108">Pencere durumları</span><span class="sxs-lookup"><span data-stu-id="51a34-108">Window States</span></span>  
 <span data-ttu-id="51a34-109">Aşağıdaki tabloda <xref:System.Windows.Window> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="51a34-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="51a34-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="51a34-110">VisualState Name</span></span>|<span data-ttu-id="51a34-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="51a34-111">VisualStateGroup Name</span></span>|<span data-ttu-id="51a34-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51a34-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="51a34-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="51a34-113">Valid</span></span>|<span data-ttu-id="51a34-114">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="51a34-114">ValidationStates</span></span>|<span data-ttu-id="51a34-115">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="51a34-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="51a34-116">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="51a34-116">InvalidFocused</span></span>|<span data-ttu-id="51a34-117">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="51a34-117">ValidationStates</span></span>|<span data-ttu-id="51a34-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="51a34-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="51a34-119">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="51a34-119">InvalidUnfocused</span></span>|<span data-ttu-id="51a34-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="51a34-120">ValidationStates</span></span>|<span data-ttu-id="51a34-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="51a34-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="51a34-122">Pencere ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="51a34-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="51a34-123">Aşağıdaki örnek, <xref:System.Windows.Window> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="51a34-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="51a34-124"><xref:System.Windows.Controls.ControlTemplate> aşağıdaki kaynaklardan bir veya daha fazlasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="51a34-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="51a34-125">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="51a34-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a34-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51a34-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="51a34-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="51a34-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="51a34-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="51a34-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="51a34-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="51a34-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="51a34-130">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="51a34-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
