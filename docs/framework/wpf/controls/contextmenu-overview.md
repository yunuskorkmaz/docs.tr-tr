---
title: ContextMenu Genel Bakışı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: b973d47711632f4c0fe56f042545598272c79d2d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124370"
---
# <a name="contextmenu-overview"></a><span data-ttu-id="63769-102">ContextMenu Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="63769-102">ContextMenu Overview</span></span>
<span data-ttu-id="63769-103"><xref:System.Windows.Controls.ContextMenu> sınıfı, içeriğe özgü bir <xref:System.Windows.Controls.Menu>kullanarak işlevselliği kullanıma sunan öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="63769-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="63769-104">Genellikle, bir Kullanıcı fare düğmesine sağ tıklayarak [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] <xref:System.Windows.Controls.ContextMenu> kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="63769-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="63769-105">Bu konu, <xref:System.Windows.Controls.ContextMenu> öğesini tanıtır ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kodda nasıl kullanılacağına ilişkin örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="63769-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  

<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a><span data-ttu-id="63769-106">ContextMenu denetimi</span><span class="sxs-lookup"><span data-stu-id="63769-106">ContextMenu Control</span></span>  
 <span data-ttu-id="63769-107"><xref:System.Windows.Controls.ContextMenu> belirli bir denetime iliştirilir.</span><span class="sxs-lookup"><span data-stu-id="63769-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="63769-108"><xref:System.Windows.Controls.ContextMenu> öğesi, kullanıcılara belirli bir denetimle ilişkili komutları veya seçenekleri belirten bir öğe listesi (örneğin, bir <xref:System.Windows.Controls.Button>) sunmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="63769-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="63769-109">Kullanıcılar, menünün görünmesini sağlamak için denetime sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="63769-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="63769-110">Genellikle, bir <xref:System.Windows.Controls.MenuItem> tıklamak bir alt menü açar veya bir uygulamanın bir komutu gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="63769-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a><span data-ttu-id="63769-111">ContextMenus oluşturma</span><span class="sxs-lookup"><span data-stu-id="63769-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="63769-112">Aşağıdaki örneklerde, alt menülerde <xref:System.Windows.Controls.ContextMenu> oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="63769-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="63769-113"><xref:System.Windows.Controls.ContextMenu> denetimleri düğme denetimlerine iliştirilir.</span><span class="sxs-lookup"><span data-stu-id="63769-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="63769-114">ContextMenu 'ye stil uygulama</span><span class="sxs-lookup"><span data-stu-id="63769-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="63769-115">Bir denetim <xref:System.Windows.Style>kullanarak, bir <xref:System.Windows.Controls.ContextMenu> görünümünü ve davranışını özel bir denetim yazmadan önemli ölçüde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63769-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="63769-116">Görsel özellikleri ayarlamaya ek olarak, bir denetimin bölümlerine da stil uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63769-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="63769-117">Örneğin, özellikleri kullanarak denetimin bölümlerinin davranışını değiştirebilir veya bir <xref:System.Windows.Controls.ContextMenu>için parçalar ekleyebilir veya yerleşimini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63769-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="63769-118">Aşağıdaki örneklerde <xref:System.Windows.Controls.ContextMenu> denetimlerine stil eklemenin birkaç yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="63769-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="63769-119">İlk örnek, `SimpleSysResources`adlı bir stil tanımlar, bu, stilinize geçerli sistem ayarlarının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63769-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="63769-120">Örnek, <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> <xref:System.Windows.Controls.Control.Background%2A> rengi olarak atar ve <xref:System.Windows.Controls.ContextMenu><xref:System.Windows.Controls.Control.Foreground%2A> rengi olarak <xref:System.Windows.SystemColors.MenuTextBrushKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="63769-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="63769-121">Aşağıdaki örnek, <xref:System.Windows.Controls.ContextMenu>oluşturulan olaylara yanıt olarak bir <xref:System.Windows.Controls.Menu> görünümünü değiştirmek için <xref:System.Windows.Trigger> öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="63769-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="63769-122">Kullanıcı fareyi menünün üzerine taşıdıkça <xref:System.Windows.Controls.ContextMenu> öğelerinin görünümü değişir.</span><span class="sxs-lookup"><span data-stu-id="63769-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63769-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63769-123">See also</span></span>

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [<span data-ttu-id="63769-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="63769-124">ContextMenu</span></span>](contextmenu.md)
- [<span data-ttu-id="63769-125">ContextMenu Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="63769-125">ContextMenu Styles and Templates</span></span>](contextmenu-styles-and-templates.md)
- [<span data-ttu-id="63769-126">WPF denetimleri Galeri örneği</span><span class="sxs-lookup"><span data-stu-id="63769-126">WPF Controls Gallery Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
