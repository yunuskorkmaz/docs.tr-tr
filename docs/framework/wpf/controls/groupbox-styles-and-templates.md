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
ms.openlocfilehash: c67dd3fe7163bc09c74fb62fc448005334a24395
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685132"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="61dd0-102">GroupBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="61dd0-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a> <span data-ttu-id="61dd0-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.GroupBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="61dd0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="61dd0-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="61dd0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="61dd0-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="61dd0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="61dd0-106">GroupBox bölümleri</span><span class="sxs-lookup"><span data-stu-id="61dd0-106">GroupBox Parts</span></span>  
 <span data-ttu-id="61dd0-107"><xref:System.Windows.Controls.GroupBox> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="61dd0-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="61dd0-108">GroupBox durumları</span><span class="sxs-lookup"><span data-stu-id="61dd0-108">GroupBox States</span></span>  
 <span data-ttu-id="61dd0-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.GroupBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="61dd0-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="61dd0-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="61dd0-110">VisualState Name</span></span>|<span data-ttu-id="61dd0-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="61dd0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="61dd0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61dd0-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="61dd0-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="61dd0-113">Valid</span></span>|<span data-ttu-id="61dd0-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="61dd0-114">ValidationStates</span></span>|<span data-ttu-id="61dd0-115">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="61dd0-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="61dd0-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="61dd0-116">InvalidFocused</span></span>|<span data-ttu-id="61dd0-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="61dd0-117">ValidationStates</span></span>|<span data-ttu-id="61dd0-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="61dd0-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="61dd0-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="61dd0-119">InvalidUnfocused</span></span>|<span data-ttu-id="61dd0-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="61dd0-120">ValidationStates</span></span>|<span data-ttu-id="61dd0-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="61dd0-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="61dd0-122">GroupBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="61dd0-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="61dd0-123">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.GroupBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="61dd0-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="61dd0-124"><xref:System.Windows.Controls.ControlTemplate> Bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="61dd0-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="61dd0-125">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="61dd0-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61dd0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61dd0-126">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="61dd0-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="61dd0-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="61dd0-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="61dd0-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="61dd0-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="61dd0-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="61dd0-130">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="61dd0-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
