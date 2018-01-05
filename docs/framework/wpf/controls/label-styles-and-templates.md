---
title: "Etiket Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6189470b5a0a01911bfe71ddfa003f72f64356c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="b1fc4-102">Etiket Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="b1fc4-102">Label Styles and Templates</span></span>
<span data-ttu-id="b1fc4-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.Label> denetim.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="b1fc4-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b1fc4-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="b1fc4-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="b1fc4-106">Etiket bölümleri</span><span class="sxs-lookup"><span data-stu-id="b1fc4-106">Label Parts</span></span>  
 <span data-ttu-id="b1fc4-107"><xref:System.Windows.Controls.Label> Denetim adlandırılmış tüm bölümler sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="b1fc4-108">Etiket durumları</span><span class="sxs-lookup"><span data-stu-id="b1fc4-108">Label States</span></span>  
 <span data-ttu-id="b1fc4-109">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.Label> denetim.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="b1fc4-110">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="b1fc4-110">VisualState Name</span></span>|<span data-ttu-id="b1fc4-111">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="b1fc4-111">VisualStateGroup Name</span></span>|<span data-ttu-id="b1fc4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1fc4-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b1fc4-113">Geçerli</span><span class="sxs-lookup"><span data-stu-id="b1fc4-113">Valid</span></span>|<span data-ttu-id="b1fc4-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b1fc4-114">ValidationStates</span></span>|<span data-ttu-id="b1fc4-115">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b1fc4-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b1fc4-116">InvalidFocused</span></span>|<span data-ttu-id="b1fc4-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b1fc4-117">ValidationStates</span></span>|<span data-ttu-id="b1fc4-118"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="b1fc4-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b1fc4-119">InvalidUnfocused</span></span>|<span data-ttu-id="b1fc4-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b1fc4-120">ValidationStates</span></span>|<span data-ttu-id="b1fc4-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="b1fc4-122">ControlTemplate Etiket örneği</span><span class="sxs-lookup"><span data-stu-id="b1fc4-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="b1fc4-123">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.Label> denetim.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="b1fc4-124"><xref:System.Windows.Controls.ControlTemplate> Bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b1fc4-125">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="b1fc4-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1fc4-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="b1fc4-127">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="b1fc4-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="b1fc4-128">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b1fc4-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="b1fc4-129">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1fc4-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="b1fc4-130">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="b1fc4-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
