---
title: "Nasıl yapılır: Windows Forms ContextMenu Bileşeni ile Menü Öğesi Ekleme ve Kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf0e579d5cf377169eeb4d394c4127d53fd54540
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="44be5-102">Nasıl yapılır: Windows Forms ContextMenu Bileşeni ile Menü Öğesi Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="44be5-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="44be5-103">Kısayol menüsü öğelerini Windows Forms'ta ekleyip açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44be5-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="44be5-104">Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeni, seçilen nesneye ilgili sık kullanılan komutlar menüsüne sağlar.</span><span class="sxs-lookup"><span data-stu-id="44be5-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="44be5-105">Ekleyerek kısayol menüsü öğelerini ekleyebilirsiniz <xref:System.Windows.Forms.MenuItem> nesneleri <xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="44be5-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="44be5-106">Öğe bir kısayol menüsünden kalıcı olarak kaldırabilirsiniz; Ancak, çalışma zamanında yerine öğelerini devre dışı bırakın veya gizlemek daha uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="44be5-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="44be5-107">Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> önceki sürümlerinin denetimleri <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="44be5-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="44be5-108">Kısayol menüsünden öğeleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="44be5-108">To remove items from a shortcut menu</span></span>  
  
1.  <span data-ttu-id="44be5-109">Kullanım <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> veya <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> yöntemi <xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonu <xref:System.Windows.Forms.ContextMenu> belirli menü öğesi kaldırmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="44be5-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="44be5-110">veya</span><span class="sxs-lookup"><span data-stu-id="44be5-110">-or-</span></span>  
  
2.  <span data-ttu-id="44be5-111">Kullanım `Clear` yöntemi `MenuItems` koleksiyonu <xref:System.Windows.Forms.ContextMenu> menüsünden tüm öğeleri kaldırmak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="44be5-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="44be5-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44be5-112">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenu>  
 [<span data-ttu-id="44be5-113">ContextMenu bileşeni</span><span class="sxs-lookup"><span data-stu-id="44be5-113">ContextMenu Component</span></span>](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)  
 [<span data-ttu-id="44be5-114">ContextMenu bileşenine genel bakış</span><span class="sxs-lookup"><span data-stu-id="44be5-114">ContextMenu Component Overview</span></span>](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)
