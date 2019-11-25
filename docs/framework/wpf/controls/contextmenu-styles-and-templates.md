---
title: ContextMenu Stilleri ve Şablonları
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: fa192e20ea84e96c9f85ff84e16c63b7f56c8a98
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283546"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="2961a-102">ContextMenu Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="2961a-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="2961a-103">Bu konuda <xref:System.Windows.Controls.ContextMenu> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2961a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="2961a-104">Denetime benzersiz bir görünüm sağlamak için varsayılan <xref:System.Windows.Controls.ControlTemplate> değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2961a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2961a-105">Daha fazla bilgi için bkz. [Denetim için şablon oluşturma](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="2961a-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="2961a-106">ContextMenu parçaları</span><span class="sxs-lookup"><span data-stu-id="2961a-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="2961a-107"><xref:System.Windows.Controls.ContextMenu> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="2961a-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="2961a-108">Bir <xref:System.Windows.Controls.ContextMenu>için <xref:System.Windows.Controls.ControlTemplate> oluşturduğunuzda, şablonunuz <xref:System.Windows.Controls.ScrollViewer>içinde bir <xref:System.Windows.Controls.ItemsPresenter> içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2961a-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="2961a-109">(<xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ContextMenu>her öğeyi görüntüler; <xref:System.Windows.Controls.ScrollViewer> denetimin içinde kaydırmaya izin vermez).</span><span class="sxs-lookup"><span data-stu-id="2961a-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="2961a-110"><xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ScrollViewer>doğrudan alt öğesi değilse, `ItemsPresenter`adına <xref:System.Windows.Controls.ItemsPresenter> vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="2961a-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="2961a-111">ContextMenu durumları</span><span class="sxs-lookup"><span data-stu-id="2961a-111">ContextMenu States</span></span>  
 <span data-ttu-id="2961a-112">Aşağıdaki tabloda <xref:System.Windows.Controls.ContextMenu> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2961a-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="2961a-113">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="2961a-113">VisualState Name</span></span>|<span data-ttu-id="2961a-114">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="2961a-114">VisualStateGroup Name</span></span>|<span data-ttu-id="2961a-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2961a-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2961a-116">Geçerli</span><span class="sxs-lookup"><span data-stu-id="2961a-116">Valid</span></span>|<span data-ttu-id="2961a-117">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="2961a-117">ValidationStates</span></span>|<span data-ttu-id="2961a-118">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="2961a-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2961a-119">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="2961a-119">InvalidFocused</span></span>|<span data-ttu-id="2961a-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="2961a-120">ValidationStates</span></span>|<span data-ttu-id="2961a-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="2961a-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2961a-122">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="2961a-122">InvalidUnfocused</span></span>|<span data-ttu-id="2961a-123">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="2961a-123">ValidationStates</span></span>|<span data-ttu-id="2961a-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="2961a-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="2961a-125">ContextMenu ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="2961a-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="2961a-126">Aşağıdaki örnek, <xref:System.Windows.Controls.ContextMenu> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2961a-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="2961a-127"><xref:System.Windows.Controls.ControlTemplate> aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="2961a-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2961a-128">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2961a-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2961a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2961a-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2961a-130">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="2961a-130">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2961a-131">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2961a-131">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2961a-132">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2961a-132">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="2961a-133">Denetim için şablon oluşturma</span><span class="sxs-lookup"><span data-stu-id="2961a-133">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
