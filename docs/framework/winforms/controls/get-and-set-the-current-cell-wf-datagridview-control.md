---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: fb71a6e3259d3007e11f528377c95a9c4cbeb023
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096985"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama
Etkileşim <xref:System.Windows.Forms.DataGridView> genellikle hangi hücre o anda etkin olan program aracılığıyla bulmak gerektirir. Geçerli hücreyi değiştirmeniz gerekebilir. Bu görevleri gerçekleştirebileceğiniz <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği.  
  
> [!NOTE]
>  Geçerli hücreyi bir satır veya olan sütunda ayarlanamaz, <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> özelliğini `false`.  
  
 Yapılandırmanıza bağlı olarak <xref:System.Windows.Forms.DataGridView> denetiminin seçim modunu, geçerli hücreyi değiştirme seçimi değiştirebilirsiniz. Daha fazla bilgi için [Windows Forms DataGridView denetimindeki seçim modları](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Geçerli hücreyi programlı olarak almak için  
  
-   Kullanım <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Geçerli hücreyi program üzerinden ayarlamak için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği <xref:System.Windows.Forms.DataGridView> denetimi. Aşağıdaki kod örneğinde, 0, sütun 1 satır için geçerli hücreyi ayarlanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   <xref:System.Windows.Forms.Button> adlarında `getCurrentCellButton` ve `setCurrentCellButton`. Görselde C#, iliştirmeniz gerekir <xref:System.Windows.Forms.Control.Click> her düğme için ilişkili olay işleyicisine kod örneği için olayları.  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Seçim Modları](selection-modes-in-the-windows-forms-datagridview-control.md)
