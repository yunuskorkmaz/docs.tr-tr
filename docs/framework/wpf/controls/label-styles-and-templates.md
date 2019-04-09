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
ms.openlocfilehash: d2bb348fc9c0348fd8093452e022df7ab4e0b3f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137104"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="abac2-102">Etiket Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="abac2-102">Label Styles and Templates</span></span>
<span data-ttu-id="abac2-103">Bu konu için şablonları ve stilleri açıklar <xref:System.Windows.Controls.Label> denetimi.</span><span class="sxs-lookup"><span data-stu-id="abac2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="abac2-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetim benzersiz bir görünüm sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="abac2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="abac2-105">Daha fazla bilgi için [ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="abac2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="abac2-106">Etiket bölümleri</span><span class="sxs-lookup"><span data-stu-id="abac2-106">Label Parts</span></span>  
 <span data-ttu-id="abac2-107"><xref:System.Windows.Controls.Label> Denetim herhangi bir adlandırılmış bölümü yok.</span><span class="sxs-lookup"><span data-stu-id="abac2-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="abac2-108">Etiket durumları</span><span class="sxs-lookup"><span data-stu-id="abac2-108">Label States</span></span>  
 <span data-ttu-id="abac2-109">Görsel durumlar için aşağıdaki tabloda <xref:System.Windows.Controls.Label> denetimi.</span><span class="sxs-lookup"><span data-stu-id="abac2-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="abac2-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="abac2-110">VisualState Name</span></span>|<span data-ttu-id="abac2-111">Visualstategroup'u adı</span><span class="sxs-lookup"><span data-stu-id="abac2-111">VisualStateGroup Name</span></span>|<span data-ttu-id="abac2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abac2-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="abac2-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="abac2-113">Valid</span></span>|<span data-ttu-id="abac2-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="abac2-114">ValidationStates</span></span>|<span data-ttu-id="abac2-115">Denetimi kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="abac2-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="abac2-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="abac2-116">InvalidFocused</span></span>|<span data-ttu-id="abac2-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="abac2-117">ValidationStates</span></span>|<span data-ttu-id="abac2-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="abac2-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="abac2-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="abac2-119">InvalidUnfocused</span></span>|<span data-ttu-id="abac2-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="abac2-120">ValidationStates</span></span>|<span data-ttu-id="abac2-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özelliği `true` olan denetim odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="abac2-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="abac2-122">ControlTemplate Etiket örneği</span><span class="sxs-lookup"><span data-stu-id="abac2-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="abac2-123">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Label> denetimi.</span><span class="sxs-lookup"><span data-stu-id="abac2-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="abac2-124"><xref:System.Windows.Controls.ControlTemplate> Bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="abac2-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="abac2-125">Tam bir örnek için bkz. [ControlTemplates örneği ile stillendirme](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="abac2-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abac2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abac2-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="abac2-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="abac2-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="abac2-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="abac2-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="abac2-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="abac2-129">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="abac2-130">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="abac2-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
