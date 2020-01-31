---
title: DataGridView Denetimindeki kenarlık ve kılavuz çizgisi stillerini değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: 918102a87ee29a3d3b78d6e6eedce57237135a51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744703"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Kenarlık ve Kılavuz Çizgi Stillerini Değiştirme
<xref:System.Windows.Forms.DataGridView> denetimiyle, Kullanıcı deneyimini geliştirmek için denetimin kenarlığının ve kılavuz çizgilerinin görünümünü özelleştirebilirsiniz. Denetim içindeki hücrelerin kenarlık stillerine ek olarak kılavuz çizgisi rengini ve denetim kenarlığı stilini değiştirebilirsiniz. Ayrıca, normal hücreler, satır üst bilgisi hücreleri ve sütun üst bilgisi hücreleri için farklı hücre kenarlık stilleri uygulayabilirsiniz.  
  
> [!NOTE]
> Kılavuz çizgisi rengi yalnızca <xref:System.Windows.Forms.DataGridViewCellBorderStyle> numaralandırmanın <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>ve <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> değerleriyle ve <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> numaralandırmasının <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> değerine sahip olacak şekilde kullanılır. Bu Numaralandırmaların diğer değerleri, işletim sistemi tarafından belirtilen renkleri kullanır. Ayrıca, Windows XP ve Windows Server 2003 ailesinde <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi aracılığıyla görsel stiller etkinleştirildiğinde <xref:System.Windows.Forms.DataGridView.GridColor%2A> Özellik değeri kullanılmaz.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Kılavuz çizgisi rengini programlı olarak değiştirmek için  
  
- <xref:System.Windows.Forms.DataGridView.GridColor%2A> özelliğini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Tüm DataGridView denetiminin kenarlık stilini programlı olarak değiştirme  
  
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> özelliğini <xref:System.Windows.Forms.BorderStyle> sabit listesi değerlerinden birine ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>DataGridView hücrelerinin kenarlık stillerini programlı olarak değiştirmek için  
  
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>ve <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> özelliklerini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>ve <xref:System.Drawing?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
