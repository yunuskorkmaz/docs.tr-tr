---
title: 'Nasıl yapılır: Windows Forms ContextMenu Bileşeni ile Menü Öğesi Ekleme ve Kaldırma'
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
ms.openlocfilehash: 5d1862b1fc1398f0f8c2217b51c4efb93db639af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957026"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Nasıl yapılır: Windows Forms ContextMenu Bileşeni ile Menü Öğesi Ekleme ve Kaldırma
Windows Forms kısayol menü öğelerinin nasıl ekleneceğini ve kaldırılacağını açıklar.  
  
 Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeni, seçili nesneyle ilgili sık kullanılan komutların bir menüsünü sağlar. Koleksiyona<xref:System.Windows.Forms.Menu.MenuItems%2A> nesneler ekleyerek <xref:System.Windows.Forms.MenuItem> kısayol menüsüne öğe ekleyebilirsiniz.  
  
 Bir kısayol menüsünden öğeleri kalıcı olarak kaldırabilirsiniz; Bununla birlikte, çalışma zamanında öğelerin gizlenmesi veya devre dışı bırakılması daha uygun olabilir.  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> , Ve '<xref:System.Windows.Forms.ContextMenuStrip> i önceki sürümlerin ve denetimlerine değiştirebilir ve bunları değiştirip, ve ' ı seçerseniz hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. <xref:System.Windows.Forms.MenuStrip>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Bir kısayol menüsünden öğeleri kaldırmak için  
  
1. Belirli bir menü <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> öğesini kaldırmak için <xref:System.Windows.Forms.Menu.MenuItems%2A> <xref:System.Windows.Forms.ContextMenu> bileşen koleksiyonunun veyayönteminikullanın.<xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>  
  
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
  
     -veya-  
  
2. Menüden tüm öğeleri kaldırmak için `MenuItems` <xref:System.Windows.Forms.ContextMenu> bileşen koleksiyonunun yönteminikullanın.`Clear`  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContextMenu>
- [ContextMenu Bileşeni](contextmenu-component-windows-forms.md)
- [ContextMenu Bileşenine Genel Bakış](contextmenu-component-overview-windows-forms.md)
