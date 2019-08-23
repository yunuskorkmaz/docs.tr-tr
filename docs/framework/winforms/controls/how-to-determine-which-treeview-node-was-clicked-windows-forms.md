---
title: 'Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını belirle (Windows Forms)'
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
ms.openlocfilehash: ab93158daf987e2f19516b8fb3abf80bfe79a12c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967339"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını belirle (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TreeView> denetimiyle çalışırken, ortak bir görev hangi düğümün tıklandığını belirlemektir ve uygun şekilde yanıt verir.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Hangi TreeView Düğümüne Tıklandığını Belirleme  
  
1. Tıklanan düğüm nesnesine bir başvuru döndürmek için nesnesinikullanın.<xref:System.EventArgs>  
  
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
    > Alternatif <xref:System.Windows.Forms.MouseEventArgs> olarak, <xref:System.Windows.Forms.Control.MouseUp> <xref:System.Drawing.Point.X%2A> <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Drawing.Point.Y%2A> tıklamın gerçekleştiği yerin<xref:System.Drawing.Point> değerlerini almak için veya olayını kullanabilirsiniz. Ardından, hangi düğümün <xref:System.Windows.Forms.TreeView> tıklandığını <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> anlamak için denetimin yöntemini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
