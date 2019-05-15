---
title: 'Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 244047f27b0eb109aba599bd26881046eb538163
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582614"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme
Bazen iş nesnelerin bir koleksiyonda depolanan bilgilerinin bir tablosunu görüntülemek yararlıdır. Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> denetimi gibi bir koleksiyona her ortak özelliği, kendi sütunda görüntülenir, özelliği ile gözatılabilir dışı olarak işaretlenmiş sürece bir <xref:System.ComponentModel.BrowsableAttribute>. Örneğin, bir koleksiyonunu `Customer` nesneleri haritamın sütunlar gibi **adı** ve **adresi**.  
  
 Bu nesne, ek bilgi ve erişmek istediğiniz kodu içeriyorsa, satır nesnelerde ulaşabilirsiniz. Aşağıdaki kod örneğinde, kullanıcılar birden çok satır seçin ve karşılık gelen müşterilerin her birine bir fatura göndermek için bir düğmeye tıklayın.  
  
### <a name="to-access-row-bound-objects"></a>Satır bağlı nesnelere erişmek için  
  
- Kullanım <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Örnek  
 Basit bir tam kod örneği içerir `Customer` uygulama ve bağlamalar <xref:System.Windows.Forms.DataGridView> için bir <xref:System.Collections.ArrayList> birkaç içeren `Customer` nesneleri. <xref:System.Windows.Forms.Control.Click> Olay işleyicisine <xref:System.Windows.Forms.Button?displayProperty=nameWithType> erişmesi gereken `Customer` nesneleri satırları, müşteri koleksiyonunun dışında erişilebilir olmadığından <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> olay işleyicisi.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetimlerine nesne bağlama](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
