---
title: 'Nasıl yapılır: Kenarlık ve kılavuz çizgi stillerini Windows Forms DataGridView denetiminde değiştirme'
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
ms.openlocfilehash: b4984dca6fb7dc8575b00758f0d61d9ff011e1ca
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703380"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Kenarlık ve kılavuz çizgi stillerini Windows Forms DataGridView denetiminde değiştirme
İle <xref:System.Windows.Forms.DataGridView> denetim, denetimin kenarlık ve kılavuz çizgileri, kullanıcı deneyimini iyileştirmek üzere görünümünü özelleştirebilirsiniz. Kılavuz çizgisi renk ve kenarlık tarzları denetiminde hücrelerin yanı sıra Denetim kenarlık stilini değiştirebilirsiniz. Sıradan bir hücre, satır üst bilgisi hücreleri ve sütun üst bilgisi hücreleri için farklı bir hücre kenarlık stillerini de uygulayabilirsiniz.  
  
> [!NOTE]
>  Kılavuz çizgisi rengi yalnızca kullanılan <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, ve <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> değerlerini <xref:System.Windows.Forms.DataGridViewCellBorderStyle> numaralandırma ve <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> değerini <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> sabit listesi. Bu numaralandırma, diğer değerleri, işletim sistemi tarafından belirtilen renkleri kullanın. Ayrıca, görsel stilleri Windows XP ve Windows Server 2003 ailesinde aracılığıyla etkin olduğunda <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi <xref:System.Windows.Forms.DataGridView.GridColor%2A> özellik değeri kullanılmaz.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Program aracılığıyla kılavuz çizgisi rengini değiştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.GridColor%2A> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Program aracılığıyla tüm DataGridView denetiminde kenarlık stilini değiştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> özelliğini birine <xref:System.Windows.Forms.BorderStyle> sabit listesi değerleri.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>DataGridView hücrelerinin kenarlık stillerini programlı olarak değiştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, ve <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> özellikleri.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Drawing?displayProperty=nameWithType> derlemeler.  
  
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
