---
title: DataGridView denetiminde seçili hücreleri, satırları ve sütunları al
description: Seçilen hücreleri, satırları veya sütunları, ilgili özellikleri kullanarak bir DataGridView denetiminden almayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 32ddae34104d23b8e5fbc0cce7da79f33fcce1d2
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904175"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Seçili Hücre, Satır ve Sütunları Alma
Bir denetimden seçili hücreleri, satırları veya sütunları, <xref:System.Windows.Forms.DataGridView> ilgili özellikleri kullanarak alabilirsiniz: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> , <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> . Aşağıdaki yordamlarda, seçili hücreleri alacak ve satır ve sütun dizinlerini bir içinde görüntüleyecek <xref:System.Windows.Forms.MessageBox> .  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Bir DataGridView denetiminde seçili hücreleri almak için  
  
- Özelliğini kullanın <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> .  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>Olası çok sayıda hücreyi göstermeyi önlemek için yöntemini kullanın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Bir DataGridView denetiminde seçili satırları almak için  
  
- Özelliğini kullanın <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> . Kullanıcıların satır seçmesini sağlamak için, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini veya olarak ayarlamanız gerekir <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Bir DataGridView denetiminde seçili sütunları almak için  
  
- Özelliğini kullanın <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> . Kullanıcıların sütun seçmesini sağlamak için, <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> özelliğini veya olarak ayarlamanız gerekir <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Windows.Forms.Button>`selectedCellsButton` `selectedRowsButton` `selectedColumnsButton` her biri, eklenen olaya yönelik işleyiciler içeren,, ve adlı denetimler <xref:System.Windows.Forms.Control.Click> .  
  
- <xref:System.Windows.Forms.DataGridView>Adlı bir denetim `dataGridView1` .  
  
- <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType> Ve <xref:System.Text?displayProperty=nameWithType> derlemelerinin başvuruları.  
  
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
