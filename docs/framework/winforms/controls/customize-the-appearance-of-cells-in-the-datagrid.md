---
title: DataGridView Denetimindeki hücrelerin görünümünü özelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 754932427a365a7b032c1ac9627d3237d1f7d0c6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744045"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme
<xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CellPainting> olayını işleyerek herhangi bir hücrenin görünümünü özelleştirebilirsiniz. <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Drawing.Graphics> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs><xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> özelliğinden ayıklayabilirsiniz. Bu <xref:System.Drawing.Graphics>, tüm <xref:System.Windows.Forms.DataGridView> denetiminin görünümünü etkileyebilirsiniz, ancak genellikle boyanmış olan hücrenin görünümünü etkilemek isteyeceksiniz. <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> özelliği, boyama işlemlerinizi Şu anda boyanmış olan hücreyle kısıtlamanıza olanak sağlar.  
  
 Aşağıdaki kod örneğinde, bir `ContactName` sütunundaki tüm hücreleri <xref:System.Windows.Forms.DataGridView> denetimin renk düzenini kullanarak boyayabilirsiniz. Her hücrenin metin içeriği <xref:System.Drawing.Color.Crimson%2A>boyanır ve bir iç içe dikdörtgen <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.GridColor%2A> özelliği ile aynı renge çizilir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- Northwind örnek veritabanındaki Customers tablosunda bulunan gibi bir `ContactName` sütunuyla `dataGridView1` adlı bir <xref:System.Windows.Forms.DataGridView> denetim.  
  
- Sisteme, System. Windows. Forms ve System. Drawing derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [Windows Forms DataGridView Denetimini Özelleştirme](customizing-the-windows-forms-datagridview-control.md)
