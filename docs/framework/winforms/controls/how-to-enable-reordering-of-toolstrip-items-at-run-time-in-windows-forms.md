---
title: "Nasıl yapılır: Windows Forms'ta çalışma zamanında ToolStrip öğelerinin yeniden sıralanmasını etkinleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
ms.openlocfilehash: daff9d6d351db514d552225853f977775f8e3204
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220415"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta çalışma zamanında ToolStrip öğelerinin yeniden sıralanmasını etkinleştirme
Kullanıcının yeniden etkinleştirebilirsiniz <xref:System.Windows.Forms.ToolStripItem> denetimlerini <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Çalışma zamanında ToolStripItem yeniden etkinleştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> özelliğini `true`. Varsayılan olarak, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> olduğu `false`.  
  
     Çalışma zamanında kullanıcı ALT tuşunu ve sürüklemek için sol fare düğmesini tutar bir <xref:System.Windows.Forms.ToolStripItem> farklı bir konuma <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
- [ToolStrip Denetim, Mimarisi](toolstrip-control-architecture.md)
- [ToolStrip Teknoloji Özeti](toolstrip-technology-summary.md)
