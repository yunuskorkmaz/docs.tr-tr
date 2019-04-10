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
ms.openlocfilehash: 50882ab9a1a498bf8f76381e3f4aac53876abbb8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217412"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme
Bazen iş nesnelerin bir koleksiyonda depolanan bilgilerinin bir tablosunu görüntülemek yararlıdır. Bağladığınızda bir <xref:System.Windows.Forms.DataGridView> denetimi gibi bir koleksiyona her ortak özelliği, kendi sütunda görüntülenir, özelliği ile gözatılabilir dışı olarak işaretlenmiş sürece bir <xref:System.ComponentModel.BrowsableAttribute>. Örneğin, bir koleksiyonunu `Customer` nesneleri haritamın sütunlar gibi **adı** ve **adresi**.  
  
 Bu nesne, ek bilgi ve erişmek istediğiniz kodu içeriyorsa, satır nesnelerde ulaşabilirsiniz. Aşağıdaki kod örneğinde, kullanıcılar birden çok satır seçin ve karşılık gelen müşterilerin her birine bir fatura göndermek için bir düğmeye tıklayın.  
  
### <a name="to-access-row-bound-objects"></a>Satır bağlı nesnelere erişmek için  
  
-   Kullanım <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>Örnek  
 Basit bir tam kod örneği içerir `Customer` uygulama ve bağlamalar <xref:System.Windows.Forms.DataGridView> için bir <xref:System.Collections.ArrayList> birkaç içeren `Customer` nesneleri. <xref:System.Windows.Forms.Control.Click> Olay işleyicisine <xref:System.Windows.Forms.Button?displayProperty=nameWithType> erişmesi gereken `Customer` nesneleri satırları, müşteri koleksiyonunun dışında erişilebilir olmadığından <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> olay işleyicisi.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
