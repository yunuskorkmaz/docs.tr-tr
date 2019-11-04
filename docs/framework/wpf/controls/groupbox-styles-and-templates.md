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
ms.openlocfilehash: 0835c106ffbda86bca8e01bc61adebfc1ab0c2cb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459645"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="ca6e2-102">GroupBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="ca6e2-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="ca6e2-103">Bu konuda <xref:System.Windows.Controls.GroupBox> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="ca6e2-104">Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ca6e2-105">Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ca6e2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="ca6e2-106">GroupBox bölümleri</span><span class="sxs-lookup"><span data-stu-id="ca6e2-106">GroupBox Parts</span></span>  
 <span data-ttu-id="ca6e2-107"><xref:System.Windows.Controls.GroupBox> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="ca6e2-108">GroupBox durumları</span><span class="sxs-lookup"><span data-stu-id="ca6e2-108">GroupBox States</span></span>  
 <span data-ttu-id="ca6e2-109">Aşağıdaki tabloda <xref:System.Windows.Controls.GroupBox> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="ca6e2-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="ca6e2-110">VisualState Name</span></span>|<span data-ttu-id="ca6e2-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="ca6e2-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ca6e2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca6e2-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ca6e2-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="ca6e2-113">Valid</span></span>|<span data-ttu-id="ca6e2-114">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="ca6e2-114">ValidationStates</span></span>|<span data-ttu-id="ca6e2-115">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ca6e2-116">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="ca6e2-116">InvalidFocused</span></span>|<span data-ttu-id="ca6e2-117">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="ca6e2-117">ValidationStates</span></span>|<span data-ttu-id="ca6e2-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ca6e2-119">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="ca6e2-119">InvalidUnfocused</span></span>|<span data-ttu-id="ca6e2-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="ca6e2-120">ValidationStates</span></span>|<span data-ttu-id="ca6e2-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="ca6e2-122">GroupBox ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="ca6e2-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="ca6e2-123">Aşağıdaki örnek, <xref:System.Windows.Controls.GroupBox> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="ca6e2-124"><xref:System.Windows.Controls.ControlTemplate> aşağıdaki kaynaklardan bir veya daha fazlasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ca6e2-125">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="ca6e2-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6e2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca6e2-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ca6e2-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="ca6e2-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ca6e2-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ca6e2-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ca6e2-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ca6e2-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ca6e2-130">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="ca6e2-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
