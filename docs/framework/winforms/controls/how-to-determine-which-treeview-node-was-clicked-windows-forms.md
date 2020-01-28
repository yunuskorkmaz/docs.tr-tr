---
title: 'Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
ms.openlocfilehash: 7a0e2b69bbec0eb03d40bee2c8e2d4bc9c3558f9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742006"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TreeView> denetimiyle çalışırken, ortak bir görev hangi düğümün tıklandığını belirlemektir ve uygun şekilde yanıt verir.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Hangi TreeView Düğümüne Tıklandığını Belirleme  
  
1. Tıklanan düğüm nesnesine bir başvuru döndürmek için <xref:System.EventArgs> nesnesini kullanın.  
  
2. Olayla ilgili verileri içeren <xref:System.Windows.Forms.TreeViewEventArgs> sınıfını denetleyerek hangi düğümün tıklandığını saptayın.  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    > Alternatif olarak, tıklama gerçekleştiği <xref:System.Drawing.Point.Y%2A> <xref:System.Drawing.Point.X%2A> ve <xref:System.Drawing.Point> koordinat değerlerini almak için <xref:System.Windows.Forms.Control.MouseDown> veya <xref:System.Windows.Forms.Control.MouseUp> olayının <xref:System.Windows.Forms.MouseEventArgs> kullanabilirsiniz. Ardından, hangi düğümün tıklandığını anlamak için <xref:System.Windows.Forms.TreeView> denetimin <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metodunu kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
