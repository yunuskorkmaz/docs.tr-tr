---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], customizing cells
- DataGridView control [Windows Forms], customizing cells
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 478b20c9-625c-4116-9c5c-5a16e6f4ec67
ms.openlocfilehash: 14667854ce4ebad561aa662fcf7d92632cc43530
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515985"
---
# <a name="how-to-customize-the-appearance-of-cells-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme
İşleyerek herhangi bir hücreyi görünümünü özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.CellPainting> olay. Ayıklayabilmeniz için <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Drawing.Graphics> gelen <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.Graphics%2A> özelliği <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs>. Bu <xref:System.Drawing.Graphics>, tüm görünümünü etkileyebilir <xref:System.Windows.Forms.DataGridView> denetimidir, ancak genellikle Environment yalnızca şu anda boyanan hücre görünümünü etkileyebilir. <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs.ClipBounds%2A> Özelliği <xref:System.Windows.Forms.DataGridViewCellPaintingEventArgs> boyama işlemlerinizi şu anda boyanan hücreye sınırlamak sağlar.  
  
 Aşağıdaki kod örneği, tüm hücreleri boyama bir `ContactName` sütun kullanarak <xref:System.Windows.Forms.DataGridView> denetimin renk şeması. Her hücrenin metin içeriği içinde boyanır <xref:System.Drawing.Color.Crimson%2A>, ve bir iç dikdörtgen aynı renkte çizilir <xref:System.Windows.Forms.DataGridView> denetimin <xref:System.Windows.Forms.DataGridView.GridColor%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms.DataGridViewCellPainting#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCellPainting/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` ile bir `ContactName` gibi Northwind örnek veritabanındaki Müşteriler tablosunda bir sütun.  
  
-   Sistem, System.Windows.Forms ve System.Drawing derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellPainting>
- [Windows Forms DataGridView Denetimini Özelleştirme](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)
