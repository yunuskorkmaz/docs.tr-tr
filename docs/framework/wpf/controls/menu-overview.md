---
title: "Menüye Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Menu control [WPF]
- controls [WPF], Menu
ms.assetid: 67df6de5-db96-4c71-b752-af90729a6537
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ab5092b1bc9db22390a18b2c1cb1ad5725a2037
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="menu-overview"></a><span data-ttu-id="9b18f-102">Menüye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9b18f-102">Menu Overview</span></span>
<span data-ttu-id="9b18f-103"><xref:System.Windows.Controls.Menu> Sınıfı komutlar ve hiyerarşik sırada olay işleyicileri ile ilişkili öğeleri düzenlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b18f-103">The <xref:System.Windows.Controls.Menu> class enables you to organize elements associated with commands and event handlers in a hierarchical order.</span></span> <span data-ttu-id="9b18f-104">Her <xref:System.Windows.Controls.Menu> öğesi içeren bir koleksiyonu <xref:System.Windows.Controls.MenuItem> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9b18f-104">Each <xref:System.Windows.Controls.Menu> element contains a collection of <xref:System.Windows.Controls.MenuItem> elements.</span></span>  
  
  
<a name="menu_control"></a>   
## <a name="menu-control"></a><span data-ttu-id="9b18f-105">Menü denetimi</span><span class="sxs-lookup"><span data-stu-id="9b18f-105">Menu Control</span></span>  
 <span data-ttu-id="9b18f-106"><xref:System.Windows.Controls.Menu> Denetimi komutları veya bir uygulama için seçenekler belirtin öğelerin listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9b18f-106">The <xref:System.Windows.Controls.Menu> control presents a list of items that specify commands or options for an application.</span></span> <span data-ttu-id="9b18f-107">Genellikle, tıklatarak bir <xref:System.Windows.Controls.MenuItem> bir alt açar veya bir komutu gerçekleştirmek bir uygulamanın neden olur.</span><span class="sxs-lookup"><span data-stu-id="9b18f-107">Typically, clicking a <xref:System.Windows.Controls.MenuItem> opens a submenu or causes an application to carry out a command.</span></span>  
  
<a name="creating_menus"></a>   
## <a name="creating-menus"></a><span data-ttu-id="9b18f-108">Menüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="9b18f-108">Creating Menus</span></span>  
 <span data-ttu-id="9b18f-109">Aşağıdaki örnekte bir <xref:System.Windows.Controls.Menu> içindeki metni düzenlemek için bir <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="9b18f-109">The following example creates a <xref:System.Windows.Controls.Menu> to manipulate text in a <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="9b18f-110"><xref:System.Windows.Controls.Menu> İçeren <xref:System.Windows.Controls.MenuItem> nesneleri kullanan <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, ve <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özellikleri ve <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, ve <xref:System.Windows.Controls.MenuItem.Click> olaylar.</span><span class="sxs-lookup"><span data-stu-id="9b18f-110">The <xref:System.Windows.Controls.Menu> contains <xref:System.Windows.Controls.MenuItem> objects that use the <xref:System.Windows.Controls.MenuItem.Command%2A>, <xref:System.Windows.Controls.MenuItem.IsCheckable%2A>, and <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> properties and the <xref:System.Windows.Controls.MenuItem.Checked>, <xref:System.Windows.Controls.MenuItem.Unchecked>, and <xref:System.Windows.Controls.MenuItem.Click> events.</span></span>  
  
 [!code-xaml[MenuItemCommandsAndEvents#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml#1)]  
  
 [!code-csharp[MenuItemCommandsAndEvents#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuItemCommandsAndEvents/CSharp/Window1.xaml.cs#2)]
 [!code-vb[MenuItemCommandsAndEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MenuItemCommandsAndEvents/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="menus_with_shortcutkeys"></a>   
## <a name="menuitems-with-keyboard-shortcuts"></a><span data-ttu-id="9b18f-111">Klavye kısayolu olan MenuItems</span><span class="sxs-lookup"><span data-stu-id="9b18f-111">MenuItems with Keyboard Shortcuts</span></span>  
 <span data-ttu-id="9b18f-112">Klavye kısayolları olan çağrılacak klavyeyle girilebilir karakter birleşimleri <xref:System.Windows.Controls.Menu> komutları.</span><span class="sxs-lookup"><span data-stu-id="9b18f-112">Keyboard shortcuts are character combinations that can be entered with the keyboard to invoke <xref:System.Windows.Controls.Menu> commands.</span></span> <span data-ttu-id="9b18f-113">Örneğin, için kısayol **kopyalama** CTRL + C'dir.</span><span class="sxs-lookup"><span data-stu-id="9b18f-113">For example, the shortcut for **Copy** is CTRL+C.</span></span> <span data-ttu-id="9b18f-114">Klavye kısayolları ve menü öğeleri ile kullanmak için iki özellik —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> veya <xref:System.Windows.Controls.MenuItem.Command%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b18f-114">There are two properties to use with keyboard shortcuts and menu items —<xref:System.Windows.Controls.MenuItem.InputGestureText%2A> or <xref:System.Windows.Controls.MenuItem.Command%2A>.</span></span>  
  
<a name="menus_inputgesturetext"></a>   
### <a name="inputgesturetext"></a><span data-ttu-id="9b18f-115">InputGestureText</span><span class="sxs-lookup"><span data-stu-id="9b18f-115">InputGestureText</span></span>  
 <span data-ttu-id="9b18f-116">Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> klavye kısayol metni atamak için özellik <xref:System.Windows.Controls.MenuItem> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="9b18f-116">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.InputGestureText%2A> property to assign keyboard shortcut text to <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="9b18f-117">Bu, yalnızca klavye kısayol menü öğesi yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="9b18f-117">This only places the keyboard shortcut in the menu item.</span></span>  <span data-ttu-id="9b18f-118">Komutuyla ilişkilendirmez <xref:System.Windows.Controls.MenuItem>.</span><span class="sxs-lookup"><span data-stu-id="9b18f-118">It does not associate the command with the <xref:System.Windows.Controls.MenuItem>.</span></span> <span data-ttu-id="9b18f-119">Uygulama eylemi gerçekleştirmek için kullanıcının giriş işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="9b18f-119">The application must handle the user's input to carry out the action.</span></span>  
  
 [!code-xaml[MenuEvent#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#6)]  
  
<a name="menus_commands"></a>   
### <a name="command"></a><span data-ttu-id="9b18f-120">Komut</span><span class="sxs-lookup"><span data-stu-id="9b18f-120">Command</span></span>  
 <span data-ttu-id="9b18f-121">Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.MenuItem.Command%2A> ilişkilendirilecek özellik **açık** ve **kaydetmek** ile komutları <xref:System.Windows.Controls.MenuItem> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="9b18f-121">The following example shows how to use the <xref:System.Windows.Controls.MenuItem.Command%2A> property to associate the **Open** and **Save** commands with <xref:System.Windows.Controls.MenuItem> controls.</span></span> <span data-ttu-id="9b18f-122">Komut özelliği yalnızca bir komutla ilişkilendirmek bir <xref:System.Windows.Controls.MenuItem>, ancak bir kısayol olarak kullanılacak giriş hareketi metin de sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b18f-122">Not only does the command property associate a command with a <xref:System.Windows.Controls.MenuItem>, but it also supplies the input gesture text to use as a shortcut.</span></span>  
  
 [!code-xaml[MenuEvent#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuEvent/CSharp/Pane1.xaml#8)]  
  
 <span data-ttu-id="9b18f-123"><xref:System.Windows.Controls.MenuItem> Sınıfı ayrıca sahip bir <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> komutu oluştuğu öğesi belirttiğinden özelliği.</span><span class="sxs-lookup"><span data-stu-id="9b18f-123">The <xref:System.Windows.Controls.MenuItem> class also has a <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> property, which specifies the element where the command occurs.</span></span> <span data-ttu-id="9b18f-124">Varsa <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> ayarlanmazsa klavye odağı olan öğe komutu alır.</span><span class="sxs-lookup"><span data-stu-id="9b18f-124">If <xref:System.Windows.Controls.MenuItem.CommandTarget%2A> is not set, the element that has keyboard focus receives the command.</span></span> <span data-ttu-id="9b18f-125">Komutlar hakkında daha fazla bilgi için bkz: [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9b18f-125">For more information about commands, see [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
<a name="menu_styling"></a>   
## <a name="menu-styling"></a><span data-ttu-id="9b18f-126">Menü stil</span><span class="sxs-lookup"><span data-stu-id="9b18f-126">Menu Styling</span></span>  
 <span data-ttu-id="9b18f-127">Denetim stil ile önemli ölçüde görünümünü ve davranışını değiştirebilirsiniz <xref:System.Windows.Controls.Menu> özel denetim yazmak zorunda kalmadan kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="9b18f-127">With control styling, you can dramatically change the appearance and behavior of <xref:System.Windows.Controls.Menu> controls without having to write a custom control.</span></span> <span data-ttu-id="9b18f-128">Görsel özellikler ayarlamaya ek olarak, aynı zamanda uygulayabilirsiniz bir <xref:System.Windows.Style> tek tek parçaları bir denetimin denetimi özellikleri, aracılığıyla bölümlerini davranışını değiştirmek veya ek bölümleri eklemek veya bir denetimi düzenini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="9b18f-128">In addition to setting visual properties, you can also apply a <xref:System.Windows.Style> to individual parts of a control, change the behavior of parts of the control through properties, or add additional parts or change the layout of a control.</span></span> <span data-ttu-id="9b18f-129">Aşağıdaki örnekler eklemek için çeşitli yollar gösterir bir <xref:System.Windows.Style> için bir <xref:System.Windows.Controls.Menu> denetim.</span><span class="sxs-lookup"><span data-stu-id="9b18f-129">The following examples demonstrate several ways to add a <xref:System.Windows.Style> to a <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 <span data-ttu-id="9b18f-130">İlk örnek kod tanımlayan bir <xref:System.Windows.Style> adlı `Simple` geçerli sistem ayarları stil kodunuzu nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9b18f-130">The first code example defines a <xref:System.Windows.Style> called `Simple` that shows how to use the current system settings in your style.</span></span> <span data-ttu-id="9b18f-131">Rengi kodunu atar `MenuHighlightBrush` menünün arka plan rengi olarak ve `MenuTextBrush` menünün ön plan rengini olarak.</span><span class="sxs-lookup"><span data-stu-id="9b18f-131">The code assigns the color of the `MenuHighlightBrush` as the menu's background color and the `MenuTextBrush` as the menu's foreground color.</span></span> <span data-ttu-id="9b18f-132">Fırçalar atamak için kaynak anahtarları kullandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9b18f-132">Notice that you use resource keys to assign the brushes.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#1)]  
  
 <span data-ttu-id="9b18f-133">Aşağıdaki örnek kullanır <xref:System.Windows.Trigger> görünümünü değiştirmenizi etkinleştiren öğelerini bir <xref:System.Windows.Controls.MenuItem> üzerinde gerçekleşen olaylara yanıt olarak <xref:System.Windows.Controls.Menu>.</span><span class="sxs-lookup"><span data-stu-id="9b18f-133">The following sample uses <xref:System.Windows.Trigger> elements that enable you to change the appearance of a <xref:System.Windows.Controls.MenuItem> in response to events that occur on the <xref:System.Windows.Controls.Menu>.</span></span> <span data-ttu-id="9b18f-134">Fare taşıdığınızda <xref:System.Windows.Controls.Menu>, ön plan rengini ve menü öğelerinin yazı tipi özelliklerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9b18f-134">When you move the mouse over the <xref:System.Windows.Controls.Menu>, the foreground color and the font characteristics of the menu items change.</span></span>  
  
 [!code-xaml[MenuStylesSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MenuStylesSnippet/CS/app.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9b18f-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b18f-135">See Also</span></span>  
 [<span data-ttu-id="9b18f-136">WPF denetimleri galeri örneği</span><span class="sxs-lookup"><span data-stu-id="9b18f-136">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
