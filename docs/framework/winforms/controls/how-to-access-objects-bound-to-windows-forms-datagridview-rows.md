---
title: DataGridView Satırlarına Bağlı Nesnelere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743169"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme
Bazen iş nesneleri koleksiyonunda depolanan bilgilerin bir tablosunu göstermek yararlıdır. Bu tür bir koleksiyona bir <xref:System.Windows.Forms.DataGridView> denetimi bağladığınızda, özellik bir <xref:System.ComponentModel.BrowsableAttribute>ile gözatılabilir olarak işaretlenmedikçe her genel özellik kendi sütununda görüntülenir. Örneğin, `Customer` nesnelerinin bir koleksiyonu **ad** ve **Adres**gibi sütunlara sahip olabilir.  
  
 Bu nesneler, erişmek istediğiniz ek bilgileri ve kodu içeriyorsa, satır nesneleri aracılığıyla buna ulaşabilirsiniz. Aşağıdaki kod örneğinde, kullanıcılar birden çok satırı seçip ilgili müşterilerin her birine bir fatura göndermek için bir düğmeye tıklayabilir.  
  
### <a name="to-access-row-bound-objects"></a>Satır bağlantılı nesnelere erişmek için  
  
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> özelliğini kullanın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Örnek  
 Tüm kod örneği basit bir `Customer` uygulamasını içerir ve <xref:System.Windows.Forms.DataGridView> birkaç `Customer` nesnesini içeren bir <xref:System.Collections.ArrayList> bağlar. <xref:System.Windows.Forms.Control.Click> olay <xref:System.Windows.Forms.Button?displayProperty=nameWithType> işleyicisi, müşteri koleksiyonu <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> olay işleyicisi dışında erişilebilir olmadığı için `Customer` nesnelerine satırlar aracılığıyla erişmelidir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
