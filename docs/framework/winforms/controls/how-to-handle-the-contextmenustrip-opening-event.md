---
title: "Nasıl yapılır: ContextMenuStrip Açma Olayını İşleme"
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
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5de244abd35c83bce329882d679df8303ef3a833
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>Nasıl yapılır: ContextMenuStrip Açma Olayını İşleme
Davranışını özelleştirebilirsiniz, <xref:System.Windows.Forms.ContextMenuStrip> denetim işleme tarafından <xref:System.Windows.Forms.ToolStripDropDown.Opening> olay.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl işleneceğini gösterir <xref:System.Windows.Forms.ToolStripDropDown.Opening> olay. Olay işleyicisi öğeleri dinamik olarak çok ekler bir <xref:System.Windows.Forms.ContextMenuStrip> denetim. Tam kod örneği için bkz: [nasıl yapılır: ToolStrip öğeleri dinamik olarak eklemek](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 Ayarlama <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> özelliğine `true` menü açılmasını engellemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [ToolStrip Denetimi](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
