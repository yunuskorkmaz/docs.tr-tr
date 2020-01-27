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
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Nasıl yapılır: Windows Forms ContextMenu Bileşeni ile Menü Öğesi Ekleme ve Kaldırma
Windows Forms kısayol menü öğelerinin nasıl ekleneceğini ve kaldırılacağını açıklar.  
  
 Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeni, seçili nesneyle ilgili sık kullanılan komutların bir menüsünü sağlar. <xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonuna <xref:System.Windows.Forms.MenuItem> nesneleri ekleyerek kısayol menüsüne öğe ekleyebilirsiniz.  
  
 Bir kısayol menüsünden öğeleri kalıcı olarak kaldırabilirsiniz; Bununla birlikte, çalışma zamanında öğelerin gizlenmesi veya devre dışı bırakılması daha uygun olabilir.  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> önceki sürümlerin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimlerine işlev ekleyip ekler ve bu, <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>, hem geri uyumluluk hem de daha ileride kullanılmak üzere korunur.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Bir kısayol menüsünden öğeleri kaldırmak için  
  
1. Belirli bir menü öğesini kaldırmak için <xref:System.Windows.Forms.ContextMenu> bileşeni <xref:System.Windows.Forms.Menu.MenuItems%2A> koleksiyonunun <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> veya <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> yöntemini kullanın.  
  
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
  
     veya  
  
2. Menüden tüm öğeleri kaldırmak için <xref:System.Windows.Forms.ContextMenu> bileşeni `MenuItems` koleksiyonunun `Clear` yöntemini kullanın.  
  
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
