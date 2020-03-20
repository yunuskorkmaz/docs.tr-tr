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
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187472"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="23176-102">GroupBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="23176-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="23176-103">Bu <xref:System.Windows.Controls.GroupBox> konu, denetim in stilleri ve şablonlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="23176-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="23176-104">Denetime benzersiz <xref:System.Windows.Controls.ControlTemplate> bir görünüm kazandırmak için varsayılanı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23176-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="23176-105">Daha fazla bilgi [için](../../../desktop-wpf/themes/how-to-create-apply-template.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="23176-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a><span data-ttu-id="23176-106">GroupBox Parçaları</span><span class="sxs-lookup"><span data-stu-id="23176-106">GroupBox Parts</span></span>  
 <span data-ttu-id="23176-107">Denetimde <xref:System.Windows.Controls.GroupBox> herhangi bir adlandırılmış parça yok.</span><span class="sxs-lookup"><span data-stu-id="23176-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a><span data-ttu-id="23176-108">GroupBox Durumları</span><span class="sxs-lookup"><span data-stu-id="23176-108">GroupBox States</span></span>  
 <span data-ttu-id="23176-109">Aşağıdaki <xref:System.Windows.Controls.GroupBox> tabloda denetim için görsel durumları listeler.</span><span class="sxs-lookup"><span data-stu-id="23176-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="23176-110">VisualState Adı</span><span class="sxs-lookup"><span data-stu-id="23176-110">VisualState Name</span></span>|<span data-ttu-id="23176-111">VisualStateGroup Adı</span><span class="sxs-lookup"><span data-stu-id="23176-111">VisualStateGroup Name</span></span>|<span data-ttu-id="23176-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23176-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="23176-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="23176-113">Valid</span></span>|<span data-ttu-id="23176-114">Doğrulama Durumları</span><span class="sxs-lookup"><span data-stu-id="23176-114">ValidationStates</span></span>|<span data-ttu-id="23176-115">Denetim <xref:System.Windows.Controls.Validation> sınıfı kullanır ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli `false`özellik.</span><span class="sxs-lookup"><span data-stu-id="23176-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="23176-116">GeçersizOdaklanmış</span><span class="sxs-lookup"><span data-stu-id="23176-116">InvalidFocused</span></span>|<span data-ttu-id="23176-117">Doğrulama Durumları</span><span class="sxs-lookup"><span data-stu-id="23176-117">ValidationStates</span></span>|<span data-ttu-id="23176-118">Ekli <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> özellik denetim `true` odak vardır.</span><span class="sxs-lookup"><span data-stu-id="23176-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="23176-119">Geçersiz Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="23176-119">InvalidUnfocused</span></span>|<span data-ttu-id="23176-120">Doğrulama Durumları</span><span class="sxs-lookup"><span data-stu-id="23176-120">ValidationStates</span></span>|<span data-ttu-id="23176-121">Ekli <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> özellik denetim `true` odak yok olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="23176-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="23176-122">GroupBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="23176-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="23176-123">Aşağıdaki örnek, denetim için <xref:System.Windows.Controls.ControlTemplate> a'nın <xref:System.Windows.Controls.GroupBox> nasıl tanımlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="23176-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="23176-124">Aşağıdaki <xref:System.Windows.Controls.ControlTemplate> kaynaklardan birini veya birkaçını kullanır.</span><span class="sxs-lookup"><span data-stu-id="23176-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="23176-125">Tam örnek için [ControlTemplates Örnek ile Şekillendirme'ye](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)bakın.</span><span class="sxs-lookup"><span data-stu-id="23176-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23176-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23176-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="23176-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="23176-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="23176-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="23176-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="23176-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="23176-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="23176-130">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="23176-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
