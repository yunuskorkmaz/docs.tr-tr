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
ms.openlocfilehash: cf70a5cc426b6c6075d1deb11aa2685c39a065c0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332189"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Nasıl yapılır: Windows Forms ContextMenu Bileşeni ile Menü Öğesi Ekleme ve Kaldırma
Kısayol menüsü öğelerini Windows Forms'ta ekleyip açıklanmaktadır.  
  
 Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeni menüsü seçili nesne için uygun olan sık kullanılan komutlar sağlar. Ekleyerek öğeler için kısayol menüsünü ekleyebilirsiniz <xref:System.Windows.Forms.MenuItem> nesneleri için <xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonu.  
  
 Öğe bir kısayol menüsünden kalıcı olarak kaldırabilirsiniz. Ancak, çalışma zamanında öğeleri yerine devre dışı bırakmak veya gizlemek daha uygun olabilir.  
  
> [!IMPORTANT]
>  Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimleri önceki sürümlerinin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Bir kısayol menüsünden öğeleri kaldırmak için  
  
1. Kullanım <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> veya <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> yöntemi <xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonunu <xref:System.Windows.Forms.ContextMenu> belirli menü öğesini kaldırmak için bileşen.  
  
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
  
2. Kullanım `Clear` yöntemi `MenuItems` koleksiyonunu <xref:System.Windows.Forms.ContextMenu> menüsünden tüm öğeleri kaldırmak için bileşen.  
  
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
