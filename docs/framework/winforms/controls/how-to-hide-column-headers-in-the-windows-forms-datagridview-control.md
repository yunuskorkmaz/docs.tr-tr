---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde sütun başlıklarını gizleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: b9b78020a567d05ea000be97bb116b4f8353d56c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709464"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView denetiminde sütun başlıklarını gizleme
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
