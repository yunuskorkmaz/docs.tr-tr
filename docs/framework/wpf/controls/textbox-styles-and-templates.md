---
title: "TextBox Stilleri ve Şablonları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f5cfd1c0715c7f9610f85201cd40a3973a2be64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="88107-102">TextBox Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="88107-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="88107-103">Stilleri ve şablonları için bu konuda açıklanmaktadır <xref:System.Windows.Controls.TextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="88107-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="88107-104">Varsayılan değiştirebileceğiniz <xref:System.Windows.Controls.ControlTemplate> denetimi benzersiz bir görünüm vermek için.</span><span class="sxs-lookup"><span data-stu-id="88107-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="88107-105">Daha fazla bilgi için bkz: [ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="88107-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="88107-106">TextBox bölümleri</span><span class="sxs-lookup"><span data-stu-id="88107-106">TextBox Parts</span></span>  
 <span data-ttu-id="88107-107">Adlandırılmış bölümleri için aşağıdaki tabloda listelenmektedir <xref:System.Windows.Controls.TextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="88107-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="88107-108">Bölümü</span><span class="sxs-lookup"><span data-stu-id="88107-108">Part</span></span>|<span data-ttu-id="88107-109">Tür</span><span class="sxs-lookup"><span data-stu-id="88107-109">Type</span></span>|<span data-ttu-id="88107-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88107-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="88107-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="88107-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="88107-112">İçerebilir bir görsel öğe bir <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="88107-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="88107-113">Metnin <xref:System.Windows.Controls.TextBox> bu öğesinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="88107-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="88107-114">TextBox durumları</span><span class="sxs-lookup"><span data-stu-id="88107-114">TextBox States</span></span>  
 <span data-ttu-id="88107-115">Aşağıdaki tablo için görsel durumlarını listeler <xref:System.Windows.Controls.TextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="88107-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="88107-116">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="88107-116">VisualState Name</span></span>|<span data-ttu-id="88107-117">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="88107-117">VisualStateGroup Name</span></span>|<span data-ttu-id="88107-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88107-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="88107-119">Normal</span><span class="sxs-lookup"><span data-stu-id="88107-119">Normal</span></span>|<span data-ttu-id="88107-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="88107-120">CommonStates</span></span>|<span data-ttu-id="88107-121">Varsayılan durumu.</span><span class="sxs-lookup"><span data-stu-id="88107-121">The default state.</span></span>|  
|<span data-ttu-id="88107-122">Fare üzerinde</span><span class="sxs-lookup"><span data-stu-id="88107-122">MouseOver</span></span>|<span data-ttu-id="88107-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="88107-123">CommonStates</span></span>|<span data-ttu-id="88107-124">Fare işaretçisini üzerinde denetim konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="88107-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="88107-125">Devre dışı</span><span class="sxs-lookup"><span data-stu-id="88107-125">Disabled</span></span>|<span data-ttu-id="88107-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="88107-126">CommonStates</span></span>|<span data-ttu-id="88107-127">Denetim devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="88107-127">The control is disabled.</span></span>|  
|<span data-ttu-id="88107-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="88107-128">ReadOnly</span></span>|<span data-ttu-id="88107-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="88107-129">CommonStates</span></span>|<span data-ttu-id="88107-130">Kullanıcı metni değiştiremez <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="88107-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="88107-131">Odaklanmış</span><span class="sxs-lookup"><span data-stu-id="88107-131">Focused</span></span>|<span data-ttu-id="88107-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="88107-132">FocusStates</span></span>|<span data-ttu-id="88107-133">Denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="88107-133">The control has focus.</span></span>|  
|<span data-ttu-id="88107-134">Odaksız</span><span class="sxs-lookup"><span data-stu-id="88107-134">Unfocused</span></span>|<span data-ttu-id="88107-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="88107-135">FocusStates</span></span>|<span data-ttu-id="88107-136">Denetim odağı yok.</span><span class="sxs-lookup"><span data-stu-id="88107-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="88107-137">Geçerli</span><span class="sxs-lookup"><span data-stu-id="88107-137">Valid</span></span>|<span data-ttu-id="88107-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="88107-138">ValidationStates</span></span>|<span data-ttu-id="88107-139">Denetim kullanan <xref:System.Windows.Controls.Validation> sınıfı ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`.</span><span class="sxs-lookup"><span data-stu-id="88107-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="88107-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="88107-140">InvalidFocused</span></span>|<span data-ttu-id="88107-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="88107-141">ValidationStates</span></span>|<span data-ttu-id="88107-142"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip.</span><span class="sxs-lookup"><span data-stu-id="88107-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="88107-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="88107-143">InvalidUnfocused</span></span>|<span data-ttu-id="88107-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="88107-144">ValidationStates</span></span>|<span data-ttu-id="88107-145"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Ekli özellik `true` sahip denetimi odağa sahip değil.</span><span class="sxs-lookup"><span data-stu-id="88107-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="88107-146">TextBox ControlTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="88107-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="88107-147">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.ControlTemplate> için <xref:System.Windows.Controls.TextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="88107-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="88107-148">Önceki örnekte, bir veya daha fazla aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="88107-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="88107-149">Tam bir örnek için bkz: [ControlTemplates örneği ile stil oluşturma](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="88107-149">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88107-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88107-150">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="88107-151">Denetim stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="88107-151">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="88107-152">Denetim özelleştirme</span><span class="sxs-lookup"><span data-stu-id="88107-152">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="88107-153">Stil ve şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="88107-153">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="88107-154">ControlTemplate oluşturarak varolan denetiminin görünümünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="88107-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
