---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde Sanal Modu Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode
- DataGridView control [Windows Forms], large data sets
ms.assetid: 98236267-f08e-4918-bcf9-77acf050a3ca
ms.openlocfilehash: 69c0f53f4ab86c7851db5e940fd0c4b5d5ebb3fc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651626"
---
# <a name="how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminde Sanal Modu Uygulama
Aşağıdaki kod örneği, veri kullanımının büyük kümelerini yönetmek gösterilmiştir bir <xref:System.Windows.Forms.DataGridView> denetimini kendi <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğini `true`.  
  
 Bu kod örneği tam bir açıklaması için bkz. [izlenecek yol: Sanal modu uygulama içinde Windows Forms DataGridView denetiminde](implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#000)]
 [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [İzlenecek yol: Windows Forms DataGridView denetiminde sanal modu uygulama](implementing-virtual-mode-wf-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Performans Ayarlaması](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sanal Mod](virtual-mode-in-the-windows-forms-datagridview-control.md)
