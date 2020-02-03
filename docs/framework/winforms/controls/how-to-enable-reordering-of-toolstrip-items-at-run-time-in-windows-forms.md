---
title: 'Nasıl yapılır: Çalışma Zamanında ToolStrip Öğelerinin Yeniden Sıralanmasını Etkinleştirme'
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
ms.openlocfilehash: 44b52bf997819f090569d08eb395d8af18f61370
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745480"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Çalışma Zamanında ToolStrip Öğelerinin Yeniden Sıralanmasını Etkinleştirme
Kullanıcının <xref:System.Windows.Forms.ToolStrip><xref:System.Windows.Forms.ToolStripItem> denetimleri yeniden düzenlenmesini sağlayabilirsiniz.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Çalışma zamanında ToolStripItem yeniden düzenlemesini etkinleştirmek için  
  
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> özelliğini `true`olarak ayarlayın. Varsayılan olarak, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> `false`.  
  
     Çalışma zamanında Kullanıcı, bir <xref:System.Windows.Forms.ToolStripItem> <xref:System.Windows.Forms.ToolStrip>farklı bir konuma sürüklemek için ALT tuşunu ve sol fare düğmesini tutar.  
  
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
