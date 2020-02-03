---
title: ContextMenu bileşeniyle menü öğeleri ekleme ve kaldırma
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
ms.openlocfilehash: 989ab6d47ec761930a32f542b5fa1136e831f73d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746274"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="da88d-102">Nasıl yapılır: Windows Forms ContextMenu Bileşeni ile Menü Öğesi Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="da88d-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="da88d-103">Windows Forms kısayol menü öğelerinin nasıl ekleneceğini ve kaldırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="da88d-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="da88d-104">Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeni, seçili nesneyle ilgili sık kullanılan komutların bir menüsünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="da88d-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="da88d-105"><xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonuna <xref:System.Windows.Forms.MenuItem> nesneleri ekleyerek kısayol menüsüne öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da88d-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="da88d-106">Bir kısayol menüsünden öğeleri kalıcı olarak kaldırabilirsiniz; Bununla birlikte, çalışma zamanında öğelerin gizlenmesi veya devre dışı bırakılması daha uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="da88d-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="da88d-107"><xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> önceki sürümlerin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimlerine işlev ekleyip ekler ve bu, <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>, hem geri uyumluluk hem de daha ileride kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="da88d-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="da88d-108">Bir kısayol menüsünden öğeleri kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="da88d-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="da88d-109">Belirli bir menü öğesini kaldırmak için <xref:System.Windows.Forms.ContextMenu> bileşeni <xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonunun <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> veya <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="da88d-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="da88d-110">veya</span><span class="sxs-lookup"><span data-stu-id="da88d-110">-or-</span></span>  
  
2. <span data-ttu-id="da88d-111">Menüden tüm öğeleri kaldırmak için <xref:System.Windows.Forms.ContextMenu> bileşeni `MenuItems` koleksiyonunun `Clear` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="da88d-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="da88d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da88d-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="da88d-113">ContextMenu Bileşeni</span><span class="sxs-lookup"><span data-stu-id="da88d-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="da88d-114">ContextMenu Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="da88d-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
