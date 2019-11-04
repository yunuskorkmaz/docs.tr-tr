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
ms.openlocfilehash: 4112306dab648d022e171401f5b9b362f2c91fdc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460754"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="49418-102">ContextMenu Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="49418-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="49418-103">Bu konuda <xref:System.Windows.Controls.ContextMenu> denetimine yönelik stiller ve şablonlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49418-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="49418-104">Denetime benzersiz bir görünüm sağlamak için, varsayılan <xref:System.Windows.Controls.ControlTemplate> ' i değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49418-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="49418-105">Daha fazla bilgi için, bkz. [bir ControlTemplate oluşturarak varolan denetimin görünümünü özelleştirme](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="49418-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="49418-106">ContextMenu parçaları</span><span class="sxs-lookup"><span data-stu-id="49418-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="49418-107"><xref:System.Windows.Controls.ContextMenu> denetiminde hiç adlandırılmış bölüm yok.</span><span class="sxs-lookup"><span data-stu-id="49418-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="49418-108">Bir <xref:System.Windows.Controls.ContextMenu>için <xref:System.Windows.Controls.ControlTemplate> oluşturduğunuzda, şablonunuz <xref:System.Windows.Controls.ScrollViewer>içinde bir <xref:System.Windows.Controls.ItemsPresenter> içerebilir.</span><span class="sxs-lookup"><span data-stu-id="49418-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="49418-109">(<xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ContextMenu>her öğeyi görüntüler; <xref:System.Windows.Controls.ScrollViewer> denetimin içinde kaydırmaya izin vermez).</span><span class="sxs-lookup"><span data-stu-id="49418-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="49418-110"><xref:System.Windows.Controls.ItemsPresenter>, <xref:System.Windows.Controls.ScrollViewer>doğrudan alt öğesi değilse, `ItemsPresenter`adına <xref:System.Windows.Controls.ItemsPresenter> vermelisiniz.</span><span class="sxs-lookup"><span data-stu-id="49418-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="49418-111">ContextMenu durumları</span><span class="sxs-lookup"><span data-stu-id="49418-111">ContextMenu States</span></span>  
 <span data-ttu-id="49418-112">Aşağıdaki tabloda <xref:System.Windows.Controls.ContextMenu> denetimi için görsel durumlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="49418-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="49418-113">VisualState adı</span><span class="sxs-lookup"><span data-stu-id="49418-113">VisualState Name</span></span>|<span data-ttu-id="49418-114">VisualStateGroup adı</span><span class="sxs-lookup"><span data-stu-id="49418-114">VisualStateGroup Name</span></span>|<span data-ttu-id="49418-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49418-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="49418-116">Geçerli</span><span class="sxs-lookup"><span data-stu-id="49418-116">Valid</span></span>|<span data-ttu-id="49418-117">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="49418-117">ValidationStates</span></span>|<span data-ttu-id="49418-118">Denetim, <xref:System.Windows.Controls.Validation> sınıfını ve <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> iliştirilmiş özelliği `false`kullanır.</span><span class="sxs-lookup"><span data-stu-id="49418-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="49418-119">Invalidodaklanmış</span><span class="sxs-lookup"><span data-stu-id="49418-119">InvalidFocused</span></span>|<span data-ttu-id="49418-120">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="49418-120">ValidationStates</span></span>|<span data-ttu-id="49418-121"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="49418-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="49418-122">Invalidunodaklanmış</span><span class="sxs-lookup"><span data-stu-id="49418-122">InvalidUnfocused</span></span>|<span data-ttu-id="49418-123">Doğrulama durumları</span><span class="sxs-lookup"><span data-stu-id="49418-123">ValidationStates</span></span>|<span data-ttu-id="49418-124"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> ekli özelliği, denetimin odağa sahip `true`.</span><span class="sxs-lookup"><span data-stu-id="49418-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="49418-125">ContextMenu ControlTemplate örneği</span><span class="sxs-lookup"><span data-stu-id="49418-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="49418-126">Aşağıdaki örnek, <xref:System.Windows.Controls.ContextMenu> denetimi için <xref:System.Windows.Controls.ControlTemplate> tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="49418-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="49418-127"><xref:System.Windows.Controls.ControlTemplate> aşağıdaki kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="49418-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="49418-128">Tüm örnek için bkz. [ControlTemplates Ile stillendirme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="49418-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49418-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49418-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="49418-130">Denetim Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="49418-130">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="49418-131">Denetim Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="49418-131">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="49418-132">Stil ve Şablon Oluşturma</span><span class="sxs-lookup"><span data-stu-id="49418-132">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="49418-133">ControlTemplate Oluşturarak Varolan Denetimin Görünümünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="49418-133">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
