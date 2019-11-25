---
title: GroupBox Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: e5befffc86f26176da4accfc01239a08d4978713
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283757"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="24769-102">GroupBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="24769-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="24769-103">Bu konuda <xref:System.Windows.Controls.GroupBox> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24769-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="24769-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24769-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="24769-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="24769-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="24769-106">GroupBox bölümleri</span><span class="sxs-lookup"><span data-stu-id="24769-106">GroupBox Parts</span></span>  
 <span data-ttu-id="24769-107"><xref:System.Windows.Controls.GroupBox> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="24769-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="24769-108">GroupBox durumları</span><span class="sxs-lookup"><span data-stu-id="24769-108">GroupBox States</span></span>  
 <span data-ttu-id="24769-109">Aşağıdaki tabloda <xref:System.Windows.Controls.GroupBox> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="24769-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="24769-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="24769-110">VisualState Name</span></span>|<span data-ttu-id="24769-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="24769-111">VisualStateGroup Name</span></span>|<span data-ttu-id="24769-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24769-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="24769-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="24769-113">Valid</span></span>|<span data-ttu-id="24769-114">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="24769-114">ValidationStates</span></span>|<span data-ttu-id="24769-115">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="24769-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="24769-116">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="24769-116">InvalidFocused</span></span>|<span data-ttu-id="24769-117">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="24769-117">ValidationStates</span></span>|<span data-ttu-id="24769-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="24769-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="24769-119">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="24769-119">InvalidUnfocused</span></span>|<span data-ttu-id="24769-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="24769-120">ValidationStates</span></span>|<span data-ttu-id="24769-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="24769-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="24769-122">GroupBox ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="24769-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="24769-123">Aşağıdaki örnek, <xref:System.Windows.Controls.GroupBox> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="24769-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="24769-124"><xref:System.Windows.Controls.ControlTemplate> aşağıdaki kaynaklardan bir veya daha fazlasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="24769-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="24769-125">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="24769-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24769-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24769-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="24769-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="24769-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="24769-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="24769-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="24769-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="24769-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="24769-130">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="24769-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
