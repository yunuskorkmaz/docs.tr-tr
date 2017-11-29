---
title: "Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c59b09f6df7fdc6a7bb237ff6eafcad99329256
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme (Windows Forms)
Windows Forms ile çalışırken <xref:System.Windows.Forms.TreeView> denetimi, bir ortak görevdir belirlemek için hangi düğümüne tıklandığını ve uygun şekilde yanıt verir.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Hangi TreeView düğümüne tıklandığını belirleme  
  
1.  Kullanım <xref:System.EventArgs> tıklatılan düğüm nesnesi bir başvuru döndürmek için nesne.  
  
2.  Denetleyerek hangi düğümüne tıklandığını belirleme <xref:System.Windows.Forms.TreeViewEventArgs> olaya ilgili verileri içeren sınıf.  
  
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
    >  Alternatif olarak, kullandığınız <xref:System.Windows.Forms.MouseEventArgs> , <xref:System.Windows.Forms.Control.MouseDown> veya <xref:System.Windows.Forms.Control.MouseUp> almak için olay <xref:System.Drawing.Point.X%2A> ve <xref:System.Drawing.Point.Y%2A> koordine değerlerini <xref:System.Drawing.Point> oluştuğu tıklatın. Ardından, <xref:System.Windows.Forms.TreeView> denetimin <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> hangi düğümüne tıklandığını belirleme yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TreeView denetimi](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
