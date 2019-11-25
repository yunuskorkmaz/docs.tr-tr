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
ms.openlocfilehash: 35fcd9c15bf44d15a08c16d58847698c5ec6e574
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283499"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="c26de-102">Etiket Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="c26de-102">Label Styles and Templates</span></span>
<span data-ttu-id="c26de-103">Bu konuda <xref:System.Windows.Controls.Label> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c26de-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="c26de-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c26de-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c26de-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="c26de-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="c26de-106">Etiket bölümleri</span><span class="sxs-lookup"><span data-stu-id="c26de-106">Label Parts</span></span>  
 <span data-ttu-id="c26de-107"><xref:System.Windows.Controls.Label> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="c26de-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="c26de-108">Etiket durumları</span><span class="sxs-lookup"><span data-stu-id="c26de-108">Label States</span></span>  
 <span data-ttu-id="c26de-109">Aşağıdaki tabloda <xref:System.Windows.Controls.Label> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="c26de-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="c26de-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="c26de-110">VisualState Name</span></span>|<span data-ttu-id="c26de-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="c26de-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c26de-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c26de-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c26de-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="c26de-113">Valid</span></span>|<span data-ttu-id="c26de-114">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="c26de-114">ValidationStates</span></span>|<span data-ttu-id="c26de-115">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="c26de-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c26de-116">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="c26de-116">InvalidFocused</span></span>|<span data-ttu-id="c26de-117">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="c26de-117">ValidationStates</span></span>|<span data-ttu-id="c26de-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="c26de-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c26de-119">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="c26de-119">InvalidUnfocused</span></span>|<span data-ttu-id="c26de-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="c26de-120">ValidationStates</span></span>|<span data-ttu-id="c26de-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="c26de-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="c26de-122">Label ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="c26de-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="c26de-123">Aşağıdaki örnek, <xref:System.Windows.Controls.Label> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c26de-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="c26de-124"><xref:System.Windows.Controls.ControlTemplate> aşağıdaki kaynaklardan bir veya daha fazlasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c26de-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c26de-125">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="c26de-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26de-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c26de-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c26de-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="c26de-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c26de-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c26de-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c26de-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c26de-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="c26de-130">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="c26de-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
