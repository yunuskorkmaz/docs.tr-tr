---
title: 'Nasıl yapılır: Yerleştirme Değerini Alma veya Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock values [WPF], setting
- Dock values [WPF], getting
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
ms.openlocfilehash: fb6c8a7d62aa09a6e1d82cb4079d1425a7f39f8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160748"
---
# <a name="how-to-get-or-set-a-dock-value"></a>Nasıl yapılır: Yerleştirme Değerini Alma veya Ayarlama
Aşağıdaki örnek nasıl atanacağını gösterir bir <xref:System.Windows.Controls.Dock> nesnenin değeri. Örnekte <xref:System.Windows.Controls.DockPanel.GetDock%2A> ve <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemlerinin <xref:System.Windows.Controls.DockPanel>.  
  
## <a name="example"></a>Örnek  
 Örnek örneği oluşturur <xref:System.Windows.Controls.TextBlock> öğesi `txt1`ve atar bir <xref:System.Windows.Controls.Dock> değerini `Top` kullanarak <xref:System.Windows.Controls.DockPanel.SetDock%2A> yöntemi <xref:System.Windows.Controls.DockPanel>. Ardından değerini ekler <xref:System.Windows.Controls.Dock> özelliğini <xref:System.Windows.Controls.TextBlock.Text%2A> , <xref:System.Windows.Controls.TextBlock> kullanarak öğesi <xref:System.Windows.Controls.DockPanel.GetDock%2A> yöntemi. Son olarak, örnek ekler <xref:System.Windows.Controls.TextBlock> üst öğeye <xref:System.Windows.Controls.DockPanel>, `dp1`.  
  
 [!code-csharp[DockPanelSetDock#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.DockPanel>
- <xref:System.Windows.Controls.DockPanel.GetDock%2A>
- <xref:System.Windows.Controls.DockPanel.SetDock%2A>
- [Panellere Genel Bakış](panels-overview.md)
