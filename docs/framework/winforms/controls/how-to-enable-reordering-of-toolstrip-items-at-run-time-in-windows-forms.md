---
title: "Nasıl yapılır: Windows Forms'ta Çalışma Zamanında ToolStrip Öğelerinin Yeniden Sıralanmasını Etkinleştirme"
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
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e295e761f9ac0ec090bf950a67008d19cb350d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Çalışma Zamanında ToolStrip Öğelerinin Yeniden Sıralanmasını Etkinleştirme
Yeniden düzenlemek kullanıcı etkinleştirebilirsiniz <xref:System.Windows.Forms.ToolStripItem> denetimlerini <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>Çalışma zamanında ToolStripItem yeniden düzenleme yapılmasını etkinleştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> özelliğine `true`. Varsayılan olarak, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> olan `false`.  
  
     Çalışma zamanında kullanıcı ALT anahtarı ve sürüklemek için sol fare düğmesini tutan bir <xref:System.Windows.Forms.ToolStripItem> farklı bir konuma <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip Denetim, Mimarisi](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip Teknoloji Özeti](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
