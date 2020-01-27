---
title: DataGridView Denetimlerine Nesne Bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: d5aa5cb64c7fb2b82d69d6c87134ee901b84f5c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746707"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama
Aşağıdaki kod örneğinde, her nesnenin ayrı bir satır olarak görünmesi için bir nesne koleksiyonunun <xref:System.Windows.Forms.DataGridView> denetimine nasıl bağlanacağı gösterilmektedir. Bu örnek ayrıca, Birleşik giriş kutusu açılan listesinin numaralandırma değerlerini içermesi için bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> numaralandırma türüyle bir özelliğin nasıl görüntüleneceğini gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
