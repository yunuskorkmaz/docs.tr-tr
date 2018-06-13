---
title: "Nasıl yapılır: Bir ContextMenuStrip'ne Menü Öğeleri Ekleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
ms.openlocfilehash: d044cf92cf7ce6db3425aacf397d6c7b4f111324
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524631"
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a>Nasıl yapılır: Bir ContextMenuStrip'ne Menü Öğeleri Ekleme
Bir seferde sadece bir menü öğesi veya çeşitli öğeleri ekleyebilirsiniz bir <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a>Bir Contextmenustrip'ne tek menü öğesi eklemek için  
  
-   Kullanım <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> bir menü öğesi ekleme yöntemi bir <xref:System.Windows.Forms.ContextMenuStrip>.  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a>Bir Contextmenustrip'ne birkaç menü öğelerini eklemek için  
  
-   Kullanım <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> birkaç menü öğeleri ekleme yöntemi bir <xref:System.Windows.Forms.ContextMenuStrip>.  
  
    ```vb  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ContextMenuStrip Denetimi](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
