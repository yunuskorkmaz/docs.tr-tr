---
title: 'Nasıl yapılır: ContextMenuStrip Açma Olayını İşleme'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3001480959ef90cb31048cbcf70aeff1632979fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941303"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>Nasıl yapılır: ContextMenuStrip Açma Olayını İşleme
Davranışını özelleştirebilirsiniz, <xref:System.Windows.Forms.ContextMenuStrip> denetim işleme tarafından <xref:System.Windows.Forms.ToolStripDropDown.Opening> olay.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl işleneceğini gösterir <xref:System.Windows.Forms.ToolStripDropDown.Opening> olay. Olay işleyicisi için dinamik olarak öğeler ekleyen bir <xref:System.Windows.Forms.ContextMenuStrip> denetimi. Tam kod örneği için bkz. [nasıl yapılır: Dinamik olarak ToolStrip öğeleri ekleme](how-to-add-toolstrip-items-dynamically.md).  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 Ayarlama <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> özelliğini `true` menüsünün açılmasını engelleyen için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [ToolStrip Denetimi](toolstrip-control-windows-forms.md)
