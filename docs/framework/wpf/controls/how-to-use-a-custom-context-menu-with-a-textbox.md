---
title: 'Nasıl yapılır: TextBox ile Özel Bağlam Menüsü Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: edcf6bdf381ae51a3354f9bc0b3c91d86e1f8f44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552785"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a><span data-ttu-id="f6e5c-102">Nasıl yapılır: TextBox ile Özel Bağlam Menüsü Kullanma</span><span class="sxs-lookup"><span data-stu-id="f6e5c-102">How to: Use a Custom Context Menu with a TextBox</span></span>
<span data-ttu-id="f6e5c-103">Bu örnek tanımlamak ve uygulamak için basit özel bağlam menüsü gösterilmektedir bir <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-103">This example shows how to define and implement a simple custom context menu for a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6e5c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6e5c-104">Example</span></span>  
 <span data-ttu-id="f6e5c-105">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek tanımlayan bir <xref:System.Windows.Controls.TextBox> özel bağlam menüsünü içeren denetim.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example defines a <xref:System.Windows.Controls.TextBox> control that includes a custom context menu.</span></span>  
  
 <span data-ttu-id="f6e5c-106">Bağlam menüsü kullanılarak tanımlanan bir <xref:System.Windows.Controls.ContextMenu> öğesi.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-106">The context menu is defined using a <xref:System.Windows.Controls.ContextMenu> element.</span></span>  <span data-ttu-id="f6e5c-107">Bağlam menüsüne bir dizi oluşur <xref:System.Windows.Controls.MenuItem> öğeleri ve <xref:System.Windows.Controls.Separator> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-107">The context menu itself consists of a series of <xref:System.Windows.Controls.MenuItem> elements and <xref:System.Windows.Controls.Separator> elements.</span></span>  <span data-ttu-id="f6e5c-108">Her <xref:System.Windows.Controls.MenuItem> öğesi bağlam menüsünde; bir komut tanımlar <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> özniteliği menü komutu için görüntü metni tanımlar ve <xref:System.Windows.Controls.MenuItem.Click> özniteliği, her bir menü öğesi için bir işleyici yöntemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-108">Each <xref:System.Windows.Controls.MenuItem> element defines a command in the context menu; the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> attribute defines the display text for the menu command, and the <xref:System.Windows.Controls.MenuItem.Click> attribute specifies a handler method for each menu item.</span></span>  <span data-ttu-id="f6e5c-109"><xref:System.Windows.Controls.Separator> Öğenin yalnızca önceki ve sonraki menü öğeleri arasında işlenmek üzere ayıran bir çizginin neden olur.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-109">The <xref:System.Windows.Controls.Separator> element simply causes a separating line to be rendered between the previous and subsequent menu items.</span></span>  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a><span data-ttu-id="f6e5c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6e5c-110">Example</span></span>  
 <span data-ttu-id="f6e5c-111">Aşağıdaki örnek, önceki bağlam menü tanımının uygulama kodunu yanı sıra, sağlar ve bağlam menüsünden devre dışı bırakan kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-111">The following example shows the implementation code for the preceding context menu definition, as well as the code that enables and disables the context menu.</span></span>  <span data-ttu-id="f6e5c-112"><xref:System.Windows.Controls.ContextMenu.Opened> Dinamik olarak etkinleştirmek veya geçerli durumuna bağlı olarak bazı komutlar devre dışı bırakmak için kullanılan olay <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-112">The <xref:System.Windows.Controls.ContextMenu.Opened> event is used to dynamically enable or disable certain commands depending on the current state of the <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="f6e5c-113">Varsayılan bağlam menüsünü geri yüklemek için kullanmak <xref:System.Windows.DependencyObject.ClearValue%2A> değerini temizlemek için yöntemi <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-113">To restore the default context menu, use the <xref:System.Windows.DependencyObject.ClearValue%2A> method to clear the value of the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property.</span></span>  <span data-ttu-id="f6e5c-114">Bağlam menüsü tamamen devre dışı bırakmak için ayarlanmış <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliği bir null başvuru için (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="f6e5c-114">To disable the context menu altogether, set the <xref:System.Windows.FrameworkElement.ContextMenu%2A> property to a null reference (`Nothing` in Visual Basic).</span></span>  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a><span data-ttu-id="f6e5c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6e5c-115">See Also</span></span>  
 [<span data-ttu-id="f6e5c-116">Açılır Menü ile Yazım Denetimi Kullanma</span><span class="sxs-lookup"><span data-stu-id="f6e5c-116">Use Spell Checking with a Context Menu</span></span>](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)  
 [<span data-ttu-id="f6e5c-117">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f6e5c-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="f6e5c-118">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f6e5c-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
