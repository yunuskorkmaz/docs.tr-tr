---
title: DataGridView Denetimlerine Nesne Bağlama
description: Her nesnenin ayrı bir satır olarak görüntülenmesini sağlamak için bir nesne koleksiyonunu Windows Forms DataGridView denetimine bağlamayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: add0047937b404dcec1ea12bac8053bb9bdfcf1c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325860"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama
Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.DataGridView> her nesnenin ayrı bir satır olarak görünmesi için bir nesne koleksiyonunun bir denetime nasıl bağlanacağı gösterilmektedir. Bu örnek ayrıca, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> Birleşik giriş kutusu açılan listesinin numaralandırma değerlerini içermesi için bir içinde numaralandırma türü olan bir özelliğin nasıl görüntüleneceğini gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
