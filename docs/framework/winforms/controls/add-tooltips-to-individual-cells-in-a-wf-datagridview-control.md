---
title: DataGridView Denetimindeki ayrı hücrelere araç Ipucu ekleme
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
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732186"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>Nasıl yapılır: Bir Windows Forms DataGridView Denetiminde Ayrı Hücrelere ToolTips Ekleme
Varsayılan olarak, araç Ipuçları, tüm içeriğini göstermek için çok küçük olan <xref:System.Windows.Forms.DataGridView> hücrelerinin değerlerini görüntülemek için kullanılır. Bununla birlikte, tek tek hücreler için araç Ipucu metin değerlerini ayarlamak için bu davranışı geçersiz kılabilirsiniz. Bu, kullanıcılara bir hücreyle ilgili ek bilgiler göstermek veya kullanıcılara hücre içeriğinin alternatif bir açıklamasını sağlamak için yararlıdır. Örneğin, durum simgelerini görüntüleyen bir satırınız varsa, araç Ipuçlarını kullanarak metin açıklamaları sağlamak isteyebilirsiniz.  
  
 Ayrıca, <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> özelliğini `false`olarak ayarlayarak hücre düzeyi araç Ipuçlarının görüntülenmesini devre dışı bırakabilirsiniz.  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>Bir hücreye araç Ipucu eklemek için  
  
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> özelliğini ayarlayın.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- Bu örnek şunları gerektirir:  
  
- `dataGridView1` adlı bir <xref:System.Windows.Forms.DataGridView> denetim, bir-dört yıldız işareti ("*") sembollerinin dize değerlerini görüntülemek için `Rating` adlı bir sütun içerir. Denetimin <xref:System.Windows.Forms.DataGridView.CellFormatting> olayının, örnekte gösterilen olay işleyicisi yöntemiyle ilişkilendirilmesi gerekir.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.Windows.Forms.DataGridView> denetimini bir dış veri kaynağına bağladığınızda veya sanal modu uygulayarak kendi veri kaynağınızı sağladığınızda, performans sorunlarıyla karşılaşabilirsiniz. Büyük miktarlardaki verilerle çalışırken bir performans cezasından kaçınmak için, birden çok hücrenin <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> özelliğini ayarlamak yerine <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> olayı işleyin. Bu olayı işlerken, bir hücrenin değerini alma <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> özelliği olayı oluşturur ve olay işleyicisinde belirtilen <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> özelliğinin değerini döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama](programming-with-cells-rows-and-columns-in-the-datagrid.md)
