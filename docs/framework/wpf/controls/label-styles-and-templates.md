---
title: Etiket Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
ms.openlocfilehash: e77c27546f4575fb6fae1081ec5a64e904721586
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377540"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="7facd-102">Etiket Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="7facd-102">Label Styles and Templates</span></span>
<span data-ttu-id="7facd-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Label> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7facd-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="7facd-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="7facd-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7facd-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="7facd-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="7facd-106">Etiket bölümleri</span><span class="sxs-lookup"><span data-stu-id="7facd-106">Label Parts</span></span>  
 <span data-ttu-id="7facd-107"><xref:System.Windows.Controls.Label> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="7facd-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="7facd-108">Etiket durumları</span><span class="sxs-lookup"><span data-stu-id="7facd-108">Label States</span></span>  
 <span data-ttu-id="7facd-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Label> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7facd-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="7facd-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="7facd-110">VisualState Name</span></span>|<span data-ttu-id="7facd-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="7facd-111">VisualStateGroup Name</span></span>|<span data-ttu-id="7facd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7facd-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7facd-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="7facd-113">Valid</span></span>|<span data-ttu-id="7facd-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7facd-114">ValidationStates</span></span>|<span data-ttu-id="7facd-115">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="7facd-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7facd-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7facd-116">InvalidFocused</span></span>|<span data-ttu-id="7facd-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7facd-117">ValidationStates</span></span>|<span data-ttu-id="7facd-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="7facd-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7facd-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7facd-119">InvalidUnfocused</span></span>|<span data-ttu-id="7facd-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7facd-120">ValidationStates</span></span>|<span data-ttu-id="7facd-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="7facd-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="7facd-122">ControlTemplate Etiket örneği</span><span class="sxs-lookup"><span data-stu-id="7facd-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="7facd-123">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Label> denetimi.</span><span class="sxs-lookup"><span data-stu-id="7facd-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="7facd-124"><xref:System.Windows.Controls.ControlTemplate> Bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="7facd-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7facd-125">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="7facd-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7facd-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7facd-126">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="7facd-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="7facd-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="7facd-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7facd-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="7facd-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7facd-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="7facd-130">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7facd-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
