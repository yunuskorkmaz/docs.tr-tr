---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütun Başlıklarını Gizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: 85332bfdbb80e4c49bab1ff208228a88337fbb43
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115251"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütun Başlıklarını Gizleme
Bazen görüntülemek istediğiniz bir <xref:System.Windows.Forms.DataGridView> sütun üst bilgileri olmadan. İçinde <xref:System.Windows.Forms.DataGridView> denetimi <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> özellik değeri, sütun başlıklarına görüntülenip görüntülenmeyeceğini belirler.  
  
### <a name="to-hide-the-column-headers"></a>Sütun üst bilgilerini gizlemek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> özelliğini `false`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.  
  
-   Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri](basic-column-row-and-cell-features-wf-datagridview-control.md)
