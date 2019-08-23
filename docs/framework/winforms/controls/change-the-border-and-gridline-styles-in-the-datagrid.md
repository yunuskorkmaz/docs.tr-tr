---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Kenarlık ve Kılavuz Çizgi Stillerini Değiştirme'
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
ms.openlocfilehash: ebeca5f933eac4da2bf3d4f300866fd2ff52b32a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917668"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Kenarlık ve Kılavuz Çizgi Stillerini Değiştirme
<xref:System.Windows.Forms.DataGridView> Denetim ile, Kullanıcı deneyimini geliştirmek için denetimin kenarlığının ve kılavuz çizgilerinin görünümünü özelleştirebilirsiniz. Denetim içindeki hücrelerin kenarlık stillerine ek olarak kılavuz çizgisi rengini ve denetim kenarlığı stilini değiştirebilirsiniz. Ayrıca, normal hücreler, satır üst bilgisi hücreleri ve sütun üst bilgisi hücreleri için farklı hücre kenarlık stilleri uygulayabilirsiniz.  
  
> [!NOTE]
> Kılavuz çizgisi rengi yalnızca <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle> sabit <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal> <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> listesinin,<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> ve değerleri ile numaralandırma değeriilekullanılır.<xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> Bu Numaralandırmaların diğer değerleri, işletim sistemi tarafından belirtilen renkleri kullanır. Ayrıca, Windows XP ve Windows Server 2003 ailesinde <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi <xref:System.Windows.Forms.DataGridView.GridColor%2A> aracılığıyla görsel stiller etkinleştirildiğinde Özellik değeri kullanılmaz.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Kılavuz çizgisi rengini programlı olarak değiştirmek için  
  
- <xref:System.Windows.Forms.DataGridView.GridColor%2A> Özelliği ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Tüm DataGridView denetiminin kenarlık stilini programlı olarak değiştirme  
  
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> Özelliğini <xref:System.Windows.Forms.BorderStyle> sabit listesi değerlerinden birine ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>DataGridView hücrelerinin kenarlık stillerini programlı olarak değiştirmek için  
  
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A> ,<xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>Ve özelliklerini<xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Windows.Forms.DataGridView> Adlı`dataGridView1`bir denetim.  
  
- <xref:System?displayProperty=nameWithType> ,<xref:System.Windows.Forms?displayProperty=nameWithType>Ve derlemelerinin<xref:System.Drawing?displayProperty=nameWithType> başvuruları.  
  
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
