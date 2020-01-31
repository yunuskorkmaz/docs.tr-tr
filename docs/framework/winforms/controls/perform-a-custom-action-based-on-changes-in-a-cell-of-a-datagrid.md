---
title: DataGridView denetiminin hücresindeki değişikliklere dayalı olarak özel eylem gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: a809134b0a79bc9685c5b84acce58b4c61b5c526
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744288"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a>Nasıl yapılır: Bir Windows Forms DataGridView Denetiminin Bir Hücresindeki Değişikliklere Dayalı Olarak Özel Eylem Gerçekleştirme
<xref:System.Windows.Forms.DataGridView> denetiminde, <xref:System.Windows.Forms.DataGridView> hücrelerinin durumundaki değişiklikleri algılamak için kullanabileceğiniz bir dizi olay vardır. En yaygın olarak kullanılan ikisi <xref:System.Windows.Forms.DataGridView.CellValueChanged> ve <xref:System.Windows.Forms.DataGridView.CellStateChanged> olaylardır.  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a>DataGridView hücrelerinin değerlerinde değişiklik algılamak için  
  
- <xref:System.Windows.Forms.DataGridView.CellValueChanged> olayı için bir işleyici yazın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a>DataGridView hücrelerinin durumlarındaki değişiklikleri algılamak için  
  
- <xref:System.Windows.Forms.DataGridView.CellStateChanged> olayı için bir işleyici yazın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim. İçin C#, olay işleyicilerinin ilgili olaylara bağlı olması gerekir.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [İzlenecek yol: Windows Forms DataGridView Denetiminde Verileri Doğrulama](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
