---
title: DataGridView denetiminde geçerli hücreyi al ve ayarla
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 0fb01d5392e02b53e0e5bf905c872dbeeb22fad9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745666"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Geçerli Hücreyi Alma ve Ayarlama
<xref:System.Windows.Forms.DataGridView> etkileşim genellikle, şu anda hangi hücrenin etkin olduğunu programlı bir şekilde keşfetmenizi gerektirir. Geçerli hücreyi de değiştirmeniz gerekebilir. <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliği ile bu görevleri gerçekleştirebilirsiniz.  
  
> [!NOTE]
> Geçerli hücreyi, <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> özelliği `false`olarak ayarlanmış bir satır veya sütunda ayarlayamazsınız.  
  
 <xref:System.Windows.Forms.DataGridView> denetiminin seçim moduna bağlı olarak, geçerli hücreyi değiştirmek seçimi değiştirebilir. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki seçim modları](selection-modes-in-the-windows-forms-datagridview-control.md)bölümüne bakın.  
  
### <a name="to-get-the-current-cell-programmatically"></a>Geçerli hücreyi programlı bir şekilde almak için  
  
- <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini kullanın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Geçerli hücreyi programlı bir şekilde ayarlamak için  
  
- <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğini ayarlayın. Aşağıdaki kod örneğinde, geçerli hücre satır 0, sütun 1 olarak ayarlanır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- `getCurrentCellButton` ve `setCurrentCellButton`adlı denetimleri <xref:System.Windows.Forms.Button>. Görselde C#, her düğmenin <xref:System.Windows.Forms.Control.Click> olaylarını örnek kodda ilişkili olay işleyicisine eklemeniz gerekir.  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Seçim Modları](selection-modes-in-the-windows-forms-datagridview-control.md)
