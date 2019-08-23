---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 25b3ed50081add77b9f522ca8e597f2b3306cb2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960523"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma
Bir <xref:System.Windows.Forms.DataGridView> denetimden seçili hücreleri, satırları veya sütunları, ilgili özellikleri kullanarak alabilirsiniz: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Aşağıdaki yordamlarda, seçili hücreleri alacak ve satır ve sütun dizinlerini bir <xref:System.Windows.Forms.MessageBox>içinde görüntüleyecek.  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Bir DataGridView denetiminde seçili hücreleri almak için  
  
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> Özelliğini kullanın.  
  
    > [!NOTE]
    > Olası çok sayıda hücreyi göstermeyi önlemek için yönteminikullanın.<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Bir DataGridView denetiminde seçili satırları almak için  
  
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> Özelliğini kullanın. Kullanıcıların satır seçmesini sağlamak için, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>olarak <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ayarlamanız gerekir.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Bir DataGridView denetiminde seçili sütunları almak için  
  
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> Özelliğini kullanın. Kullanıcıların sütun seçmesini sağlamak için, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>olarak <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> ayarlamanız gerekir.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Windows.Forms.Button>her biri `selectedCellsButton`, `selectedRowsButton` `selectedColumnsButton`eklenen olaya<xref:System.Windows.Forms.Control.Click> yönelik işleyiciler içeren,, ve adlı denetimler.  
  
- <xref:System.Windows.Forms.DataGridView> Adlı`dataGridView1`bir denetim.  
  
- <xref:System?displayProperty=nameWithType> ,<xref:System.Windows.Forms?displayProperty=nameWithType>Ve derlemelerinin<xref:System.Text?displayProperty=nameWithType> başvuruları.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu konu başlığı altında açıklanan koleksiyonlar, çok sayıda hücre, satır veya sütun seçildiğinde verimli bir şekilde gerçekleştirmez. Bu koleksiyonları büyük miktarda verilerle kullanma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirmek Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
