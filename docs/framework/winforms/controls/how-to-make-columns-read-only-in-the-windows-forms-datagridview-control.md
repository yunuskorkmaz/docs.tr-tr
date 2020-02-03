---
title: DataGridView denetiminde sütunları salt okuma yapın
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 11d008d47ec5edb594d3d862c68ff3b9920e0e25
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736189"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunları Salt Okunur Yapma
Verilerin hepsi düzenlenmez. <xref:System.Windows.Forms.DataGridView> denetiminde, sütun <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> Özellik değeri, kullanıcıların söz konusu sütundaki hücreleri düzenleyip düzenleyemeyeceğini belirler. Denetimi tamamen salt okuma yapma hakkında daha fazla bilgi için, bkz. [nasıl yapılır: satır ekleme ve silmeyi engelleme Windows Forms DataGridView denetiminde](prevent-row-addition-and-deletion-datagridview.md).  
  
 Visual Studio 'da bu görev için destek vardır.  Ayrıca bkz. [nasıl yapılır: tasarımcı kullanarak sütunları salt okuma yapma Windows Forms DataGridView denetiminde](make-columns-read-only-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-make-a-column-read-only-programmatically"></a>Sütunu programlı olarak salt okunabilir hale getirmek için  
  
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> özelliğini `true`olarak ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- `CompanyName`adlı bir sütunla `dataGridView1` adlı <xref:System.Windows.Forms.DataGridView> denetim.  
  
- <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Satır Eklemeyi ve Silmeyi Engelleme](prevent-row-addition-and-deletion-datagridview.md)
