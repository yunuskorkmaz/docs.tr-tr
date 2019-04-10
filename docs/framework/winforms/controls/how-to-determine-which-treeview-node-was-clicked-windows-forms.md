---
title: 'Nasıl yapılır: (Windows Forms) hangi TreeView düğümüne tıklandığını belirleme'
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
ms.openlocfilehash: 71f13c7b160822c92475d4d03e923b40d4f0454d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296738"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Nasıl yapılır: (Windows Forms) hangi TreeView düğümüne tıklandığını belirleme
Windows Forms ile çalışırken <xref:System.Windows.Forms.TreeView> denetimi, genel bir görevdir belirlemek için hangi düğümüne tıklandığını ve uygun şekilde yanıt verin.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Hangi TreeView düğümüne tıklandığını belirleme  
  
1. Kullanım <xref:System.EventArgs> tıklanan düğümü nesnesine bir başvuru döndürülecek nesne.  
  
2. Kontrol ederek hangi düğümüne tıklandığını belirleme <xref:System.Windows.Forms.TreeViewEventArgs> ve olayla ilişkili verileri içeren sınıf.  
  
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
    >  Alternatif olarak, kullandığınız <xref:System.Windows.Forms.MouseEventArgs> , <xref:System.Windows.Forms.Control.MouseDown> veya <xref:System.Windows.Forms.Control.MouseUp> almak için olay <xref:System.Drawing.Point.X%2A> ve <xref:System.Drawing.Point.Y%2A> koordinat değerlerini <xref:System.Drawing.Point> oluştuğu yeri tıklatın. Ardından, <xref:System.Windows.Forms.TreeView> denetimin <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> hangi düğümüne tıklandığını belirleme için yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
