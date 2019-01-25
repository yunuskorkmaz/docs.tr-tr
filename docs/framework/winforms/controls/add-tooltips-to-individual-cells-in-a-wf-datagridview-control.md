---
title: 'Nasıl yapılır: Bir Windows Forms DataGridView denetiminde ayrı hücrelere ToolTips ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: baa6f79f2e0d454412992d9c951734a3437a96cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517649"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Nasıl yapılır: Bir Windows Forms DataGridView denetiminde ayrı hücrelere ToolTips ekleme
Varsayılan olarak, araç ipuçları değerlerini görüntülemek için kullanılan <xref:System.Windows.Forms.DataGridView> tüm içerikleri göstermek için çok küçük hücreleri. Ancak, tek tek hücrelere araç ipucu metin değerlerini ayarlamak için bu davranış, kılabilirsiniz. Bu, kullanıcıların bir hücre hakkında ek bilgi görüntülemek veya kullanıcılara hücre içeriğini başka bir açıklamasını sağlamak için kullanışlıdır. Örneğin, durum simgelerini görüntüleyen bir satır varsa, araç ipuçlarını kullanarak metin açıklamaları sağlamak isteyebilirsiniz.  
  
 Ayarlayarak da hücre düzeyinde araç ipuçlarının görüntülenmesini devre dışı bırakabilirsiniz <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> özelliğini `false`.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Bir araç ipucu bir hücreye eklemek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `Rating` dört yıldız arasında bir dize değerleri görüntülemek için ("*") simgeler. <xref:System.Windows.Forms.DataGridView.CellFormatting> Olay denetimin olmalıdır ilişkili örnekte gösterilen olay işleyicisi yöntemi ile.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bağladığınızda <xref:System.Windows.Forms.DataGridView> denetlemek için bir dış veri kaynağına veya sanal modu uygulama tarafından kendi veri kaynağı sağlamak için performans sorunlarıyla karşılaşabilirsiniz. Büyük miktarlarda veri ile çalışırken, bir performans cezasını önlemek için tanıtıcı <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> ayar yerine olay <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> birden çok hücre özelliği. Ne zaman ele bu olay bir hücrenin değerini alma <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> özelliği olayını başlatır ve değerini döndürür <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> özelliği olarak belirtilen olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
