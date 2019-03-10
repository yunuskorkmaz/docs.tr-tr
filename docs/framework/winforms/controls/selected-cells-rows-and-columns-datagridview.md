---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde seçili hücre, satır ve sütunları alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: ad6e704b64e3f25f456b98691dfe12c13f8440a2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713312"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetiminde seçili hücre, satır ve sütunları alma
Seçili hücre, satır veya sütun alabileceğiniz bir <xref:System.Windows.Forms.DataGridView> karşılık gelen özelliklerini kullanarak denetim: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Aşağıdaki yordamlarda, seçili hücreleri alma ve satır ve sütun dizinlerini görüntüleme bir <xref:System.Windows.Forms.MessageBox>.  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>DataGridView denetiminde seçili hücre almak için  
  
-   Kullanım <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> özelliği.  
  
    > [!NOTE]
    >  Kullanım <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> potansiyel olarak büyük bir hücre sayısını gösteren önlemek için yöntemi.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>DataGridView denetiminde seçili satır almak için  
  
-   Kullanım <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> özelliği. Satırları seçmek kullanıcıları etkinleştirmek için ayarlamalısınız <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>DataGridView denetiminde Seçili sütunları almak için  
  
-   Kullanım <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> özelliği. Sütunları seçmek kullanıcıları etkinleştirmek için ayarlamalısınız <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   <xref:System.Windows.Forms.Button> adlarında `selectedCellsButton`, `selectedRowsButton`, ve `selectedColumnsButton`, her biri için işleyiciler <xref:System.Windows.Forms.Control.Click> ekli olay.  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Text?displayProperty=nameWithType> derlemeler.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu konuda açıklanan koleksiyonları, çok sayıda hücreler, satırlar veya sütunlar seçili olduğunda verimli bir şekilde gerçekleştirmeyin. Büyük miktarlarda veri bu koleksiyonlara kullanma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
