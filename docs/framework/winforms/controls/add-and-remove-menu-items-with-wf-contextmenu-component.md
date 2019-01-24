---
title: 'Nasıl yapılır: Windows Forms ContextMenu bileşeni ile menü öğelerini ekleyip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], removing items
- ContextMenu component [Windows Forms], adding items
- shortcut menus [Windows Forms], removing items
- shortcut menus [Windows Forms], examples
- context menus [Windows Forms], adding items
- shortcut menus [Windows Forms], adding items
- ContextMenu component [Windows Forms], removing items
- context menus [Windows Forms], examples
- examples [Windows Forms], context menus
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
ms.openlocfilehash: ac554f080cdabc7034ca839c3a9086e927429f7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520041"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="e17db-102">Nasıl yapılır: Windows Forms ContextMenu bileşeni ile menü öğelerini ekleyip</span><span class="sxs-lookup"><span data-stu-id="e17db-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="e17db-103">Kısayol menüsü öğelerini Windows Forms'ta ekleyip açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e17db-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="e17db-104">Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeni menüsü seçili nesne için uygun olan sık kullanılan komutlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e17db-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="e17db-105">Ekleyerek öğeler için kısayol menüsünü ekleyebilirsiniz <xref:System.Windows.Forms.MenuItem> nesneleri için <xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e17db-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="e17db-106">Öğe bir kısayol menüsünden kalıcı olarak kaldırabilirsiniz. Ancak, çalışma zamanında öğeleri yerine devre dışı bırakmak veya gizlemek daha uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="e17db-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e17db-107">Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimleri önceki sürümlerinin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="e17db-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="e17db-108">Bir kısayol menüsünden öğeleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="e17db-108">To remove items from a shortcut menu</span></span>  
  
1.  <span data-ttu-id="e17db-109">Kullanım <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> veya <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> yöntemi <xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonunu <xref:System.Windows.Forms.ContextMenu> belirli menü öğesini kaldırmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="e17db-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     <span data-ttu-id="e17db-110">-veya-</span><span class="sxs-lookup"><span data-stu-id="e17db-110">-or-</span></span>  
  
2.  <span data-ttu-id="e17db-111">Kullanım `Clear` yöntemi `MenuItems` koleksiyonunu <xref:System.Windows.Forms.ContextMenu> menüsünden tüm öğeleri kaldırmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="e17db-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e17db-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e17db-112">See also</span></span>
- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="e17db-113">ContextMenu Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e17db-113">ContextMenu Component</span></span>](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)
- [<span data-ttu-id="e17db-114">ContextMenu Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e17db-114">ContextMenu Component Overview</span></span>](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)
