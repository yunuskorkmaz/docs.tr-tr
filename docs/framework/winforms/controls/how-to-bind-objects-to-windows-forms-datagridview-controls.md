---
title: 'Nasıl yapılır: Windows Forms DataGridView denetimlerine nesne bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 0e69e67201d95b912467ccfd74bc5fb08196f11d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614673"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>Nasıl yapılır: Windows Forms DataGridView denetimlerine nesne bağlama
Aşağıdaki kod örneği, bir nesne koleksiyonu bağlamak gösterilmiştir bir <xref:System.Windows.Forms.DataGridView> böylece her nesneyi ayrı bir satır olarak görüntüler. Bu örnek ayrıca bir numaralandırma türü ile bir özelliği görüntülemek nasıl gösterir bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> böylece birleşik giriş kutusu açılır listede numaralandırma değerlerini içerir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView satırlarına bağlı nesnelere erişme](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
