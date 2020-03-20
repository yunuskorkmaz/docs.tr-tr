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
ms.openlocfilehash: d960eaae2aa479e0be74e9a5e4fdbfec8ff411c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182187"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TreeView> denetimiyle çalışırken, ortak bir görev hangi düğümün tıklatıldığını belirlemek ve uygun şekilde yanıt vermektir.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Hangi TreeView düğümüne tıklandığını belirlemek için  
  
1. Tıklatılan düğüm nesnesine bir başvuru döndürmek için <xref:System.EventArgs> nesneyi kullanın.  
  
2. Olayla ilgili verileri içeren <xref:System.Windows.Forms.TreeViewEventArgs> sınıfı işaretleyerek hangi düğümün tıklandığını belirleyin.  
  
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
    > Alternatif olarak, <xref:System.Windows.Forms.MouseEventArgs> tıklamanın oluştuğu <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> <xref:System.Drawing.Point.X%2A> <xref:System.Drawing.Point.Y%2A> <xref:System.Drawing.Point> yerin değerlerini almak ve koordine etmek için olayın veya olayın kullanımını kullanabilirsiniz. Ardından, hangi <xref:System.Windows.Forms.TreeView> düğümün <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> tıklatıldığını belirlemek için denetim yöntemini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
