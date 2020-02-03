---
title: DataGridView denetiminde seçili hücreleri, satırları ve sütunları al
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 0079c590ee6e4732523fd50be157bd58ec1bfb1b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743075"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma
<xref:System.Windows.Forms.DataGridView> denetiminden seçili hücreleri, satırları veya sütunları, ilgili özellikleri kullanarak alabilirsiniz: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>. Aşağıdaki yordamlarda, seçili hücreleri alacak ve satır ve sütun dizinlerini bir <xref:System.Windows.Forms.MessageBox>görüntüleyecek şekilde görüntüleyirsiniz.  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Bir DataGridView denetiminde seçili hücreleri almak için  
  
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> özelliğini kullanın.  
  
    > [!NOTE]
    > Potansiyel olarak çok sayıda hücre gösterilmemek için <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> yöntemini kullanın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Bir DataGridView denetiminde seçili satırları almak için  
  
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> özelliğini kullanın. Kullanıcıların satır seçmesini sağlamak için <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>olarak ayarlamanız gerekir.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Bir DataGridView denetiminde seçili sütunları almak için  
  
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> özelliğini kullanın. Kullanıcıların sütun seçmesini sağlamak için <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> veya <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>olarak ayarlamanız gerekir.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- `selectedCellsButton`, `selectedRowsButton`ve `selectedColumnsButton`adlı, her biri <xref:System.Windows.Forms.Control.Click> olayı için işleyiciler içeren <xref:System.Windows.Forms.Button> denetimleri.  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>ve <xref:System.Text?displayProperty=nameWithType> derlemelerine başvurular.  
  
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
