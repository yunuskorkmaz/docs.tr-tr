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
ms.openlocfilehash: 4d2d8db0f614b5240705146dbe91432b96b46dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185912"
---
# <a name="contextmenu-overview"></a><span data-ttu-id="0b7fb-102">ContextMenu Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="0b7fb-102">ContextMenu Overview</span></span>
<span data-ttu-id="0b7fb-103">Sınıf, <xref:System.Windows.Controls.ContextMenu> içeriğe özgü <xref:System.Windows.Controls.Menu>bir öğe kullanarak işlevselliği ortaya çıkaran öğeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-103">The <xref:System.Windows.Controls.ContextMenu> class represents the element that exposes functionality by using a context-specific <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="0b7fb-104">Genellikle, bir kullanıcı fare <xref:System.Windows.Controls.ContextMenu> düğmesini [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] sağ tıklayarak içinde ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-104">Typically, a user exposes the <xref:System.Windows.Controls.ContextMenu> in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] by right-clicking the mouse button.</span></span> <span data-ttu-id="0b7fb-105">Bu konu öğeyi <xref:System.Windows.Controls.ContextMenu> tanır ve nasıl kullanılacağı [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ve kod örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-105">This topic introduces the <xref:System.Windows.Controls.ContextMenu> element and provides examples of how to use it in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span>  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a><span data-ttu-id="0b7fb-106">ContextMenu Denetimi</span><span class="sxs-lookup"><span data-stu-id="0b7fb-106">ContextMenu Control</span></span>  
 <span data-ttu-id="0b7fb-107">A <xref:System.Windows.Controls.ContextMenu> belirli bir denetime eklenir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-107">A <xref:System.Windows.Controls.ContextMenu> is attached to a specific control.</span></span> <span data-ttu-id="0b7fb-108">Öğe, <xref:System.Windows.Controls.ContextMenu> kullanıcılara belirli bir denetimle ilişkili komutları veya seçenekleri belirten öğelerin bir listesini <xref:System.Windows.Controls.Button>sunmanızı sağlar, örneğin, bir .</span><span class="sxs-lookup"><span data-stu-id="0b7fb-108">The <xref:System.Windows.Controls.ContextMenu> element enables you to present users with a list of items that specify commands or options that are associated with a particular control, for example, a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="0b7fb-109">Kullanıcılar, menüyü görüntülemek için denetimi sağ tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-109">Users right-click the control to make the menu appear.</span></span> <span data-ttu-id="0b7fb-110">Genellikle, bir <xref:System.Windows.Controls.MenuItem> alt menüyü tıklatmak bir alt menüyü açar veya bir uygulamanın bir komut u gerçekleştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-110">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a><span data-ttu-id="0b7fb-111">ContextMenüoluşturma</span><span class="sxs-lookup"><span data-stu-id="0b7fb-111">Creating ContextMenus</span></span>  
 <span data-ttu-id="0b7fb-112">Aşağıdaki örnekler, alt <xref:System.Windows.Controls.ContextMenu> menülerle nasıl oluşturulacak larını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-112">The following examples show how to create a <xref:System.Windows.Controls.ContextMenu> with submenus.</span></span> <span data-ttu-id="0b7fb-113">Denetimler <xref:System.Windows.Controls.ContextMenu> düğme denetimlerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-113">The <xref:System.Windows.Controls.ContextMenu> controls are attached to button controls.</span></span>  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a><span data-ttu-id="0b7fb-114">Bağlam Menüsüne Stilleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="0b7fb-114">Applying Styles to a ContextMenu</span></span>  
 <span data-ttu-id="0b7fb-115">Bir denetim <xref:System.Windows.Style>kullanarak, özel bir denetim yazmadan <xref:System.Windows.Controls.ContextMenu> bir görünümünü ve davranışını önemli ölçüde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-115">By using a control <xref:System.Windows.Style>, you can dramatically change the appearance and behavior of a <xref:System.Windows.Controls.ContextMenu> without writing a custom control.</span></span> <span data-ttu-id="0b7fb-116">Görsel özellikler ayarlamaya ek olarak, stilleri denetimin bölümlerine de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-116">In addition to setting visual properties, you can also apply styles to parts of a control.</span></span> <span data-ttu-id="0b7fb-117">Örneğin, özellikleri kullanarak denetim bölümlerinin davranışını değiştirebilir veya bir <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-117">For example, you can change the behavior of parts of the control by using properties, or you can add parts to, or change the layout of, a <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="0b7fb-118">Aşağıdaki örnekler, denetimlere stil <xref:System.Windows.Controls.ContextMenu> eklemenin çeşitli yollarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-118">The following examples show several ways to add styles to <xref:System.Windows.Controls.ContextMenu> controls.</span></span>  
  
 <span data-ttu-id="0b7fb-119">İlk örnek, stilinizde `SimpleSysResources`geçerli sistem ayarlarının nasıl kullanılacağını gösteren , adlı bir stil tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-119">The first example defines a style called `SimpleSysResources`, which shows how to use the current system settings in your style.</span></span> <span data-ttu-id="0b7fb-120">Örnek, <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> <xref:System.Windows.Controls.Control.Background%2A> renk ve <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> <xref:System.Windows.Controls.Control.Foreground%2A> renk olarak <xref:System.Windows.Controls.ContextMenu>atar.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-120">The example assigns <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> as the <xref:System.Windows.Controls.Control.Background%2A> color and <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> as the <xref:System.Windows.Controls.Control.Foreground%2A> color of the <xref:System.Windows.Controls.ContextMenu>.</span></span>  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 <span data-ttu-id="0b7fb-121">Aşağıdaki örnekte, <xref:System.Windows.Trigger> <xref:System.Windows.Controls.ContextMenu>'de yükseltilen <xref:System.Windows.Controls.Menu> olaylara yanıt olarak bir görünümü değiştirmek için öğe yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-121">The following example uses the <xref:System.Windows.Trigger> element to change the appearance of a <xref:System.Windows.Controls.Menu> in response to events that are raised on the <xref:System.Windows.Controls.ContextMenu>.</span></span> <span data-ttu-id="0b7fb-122">Bir kullanıcı fareyi menünün üzerinde hareket <xref:System.Windows.Controls.ContextMenu> ettirdiğinde, öğelerin görünümü değişir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-122">When a user moves the mouse over the menu, the appearance of the <xref:System.Windows.Controls.ContextMenu> items changes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0b7fb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-123">See also</span></span>

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [<span data-ttu-id="0b7fb-124">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="0b7fb-124">ContextMenu</span></span>](contextmenu.md)
- [<span data-ttu-id="0b7fb-125">ContextMenu Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="0b7fb-125">ContextMenu Styles and Templates</span></span>](contextmenu-styles-and-templates.md)
- [<span data-ttu-id="0b7fb-126">WPF Denetimleri Galeri Örneği</span><span class="sxs-lookup"><span data-stu-id="0b7fb-126">WPF Controls Gallery Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
