---
title: "PasswordBox Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f22b73704d21fa719a678799c1d95fc266c661e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="17b2c-102">PasswordBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="17b2c-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="17b2c-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.PasswordBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="17b2c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="17b2c-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="17b2c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="17b2c-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="17b2c-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="17b2c-106">PasswordBox bölümleri</span><span class="sxs-lookup"><span data-stu-id="17b2c-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="17b2c-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.PasswordBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="17b2c-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="17b2c-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="17b2c-108">Part</span></span>|<span data-ttu-id="17b2c-109">Tür</span><span class="sxs-lookup"><span data-stu-id="17b2c-109">Type</span></span>|<span data-ttu-id="17b2c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17b2c-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="17b2c-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="17b2c-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="17b2c-112">İçerebilir bir görsel öğe bir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="17b2c-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="17b2c-113">Metnin <xref:System.Windows.Controls.PasswordBox> bu öğesinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="17b2c-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="17b2c-114">PasswordBox durumları</span><span class="sxs-lookup"><span data-stu-id="17b2c-114">PasswordBox States</span></span>  
 <span data-ttu-id="17b2c-115">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.PasswordBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="17b2c-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="17b2c-116">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="17b2c-116">VisualState Name</span></span>|<span data-ttu-id="17b2c-117">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="17b2c-117">VisualStateGroup Name</span></span>|<span data-ttu-id="17b2c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17b2c-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="17b2c-119">Normal</span><span class="sxs-lookup"><span data-stu-id="17b2c-119">Normal</span></span>|<span data-ttu-id="17b2c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="17b2c-120">CommonStates</span></span>|<span data-ttu-id="17b2c-121">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="17b2c-121">The default state.</span></span>|  
|<span data-ttu-id="17b2c-122">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="17b2c-122">MouseOver</span></span>|<span data-ttu-id="17b2c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="17b2c-123">CommonStates</span></span>|<span data-ttu-id="17b2c-124">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="17b2c-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="17b2c-125">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="17b2c-125">Disabled</span></span>|<span data-ttu-id="17b2c-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="17b2c-126">CommonStates</span></span>|<span data-ttu-id="17b2c-127">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="17b2c-127">The control is disabled.</span></span>|  
|<span data-ttu-id="17b2c-128">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="17b2c-128">Focused</span></span>|<span data-ttu-id="17b2c-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="17b2c-129">FocusStates</span></span>|<span data-ttu-id="17b2c-130">Denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="17b2c-130">The control has focus.</span></span>|  
|<span data-ttu-id="17b2c-131">Odaksız</span><span class="sxs-lookup"><span data-stu-id="17b2c-131">Unfocused</span></span>|<span data-ttu-id="17b2c-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="17b2c-132">FocusStates</span></span>|<span data-ttu-id="17b2c-133">Denetim odağı yok.</span><span class="sxs-lookup"><span data-stu-id="17b2c-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="17b2c-134">Geçerli</span><span class="sxs-lookup"><span data-stu-id="17b2c-134">Valid</span></span>|<span data-ttu-id="17b2c-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17b2c-135">ValidationStates</span></span>|<span data-ttu-id="17b2c-136">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="17b2c-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="17b2c-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="17b2c-137">InvalidFocused</span></span>|<span data-ttu-id="17b2c-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17b2c-138">ValidationStates</span></span>|<span data-ttu-id="17b2c-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="17b2c-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="17b2c-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="17b2c-140">InvalidUnfocused</span></span>|<span data-ttu-id="17b2c-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="17b2c-141">ValidationStates</span></span>|<span data-ttu-id="17b2c-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="17b2c-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="17b2c-143">PasswordBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="17b2c-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="17b2c-144">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.PasswordBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="17b2c-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="17b2c-145">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="17b2c-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="17b2c-146">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="17b2c-146">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b2c-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17b2c-147">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="17b2c-148">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="17b2c-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="17b2c-149">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="17b2c-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="17b2c-150">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="17b2c-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="17b2c-151">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="17b2c-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
