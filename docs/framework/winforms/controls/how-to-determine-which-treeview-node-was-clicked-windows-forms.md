---
title: 'Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme (Windows Forms)'
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
ms.openlocfilehash: d1e9df6a928f1ea60e4663c78d204ec2b16baf23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530633"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a><span data-ttu-id="17b8d-102">Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="17b8d-102">How to: Determine Which TreeView Node Was Clicked (Windows Forms)</span></span>
<span data-ttu-id="17b8d-103">Windows Forms ile çalışırken <xref:System.Windows.Forms.TreeView> denetimi, bir ortak görevdir belirlemek için hangi düğümüne tıklandığını ve uygun şekilde yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="17b8d-103">When working with the Windows Forms <xref:System.Windows.Forms.TreeView> control, a common task is to determine which node was clicked, and respond appropriately.</span></span>  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a><span data-ttu-id="17b8d-104">Hangi TreeView düğümüne tıklandığını belirleme</span><span class="sxs-lookup"><span data-stu-id="17b8d-104">To determine which TreeView node was clicked</span></span>  
  
1.  <span data-ttu-id="17b8d-105">Kullanım <xref:System.EventArgs> tıklatılan düğüm nesnesi bir başvuru döndürmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="17b8d-105">Use the <xref:System.EventArgs> object to return a reference to the clicked node object.</span></span>  
  
2.  <span data-ttu-id="17b8d-106">Denetleyerek hangi düğümüne tıklandığını belirleme <xref:System.Windows.Forms.TreeViewEventArgs> olaya ilgili verileri içeren sınıf.</span><span class="sxs-lookup"><span data-stu-id="17b8d-106">Determine which node was clicked by checking the <xref:System.Windows.Forms.TreeViewEventArgs> class, which contains data related to the event.</span></span>  
  
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
    >  <span data-ttu-id="17b8d-107">Alternatif olarak, kullandığınız <xref:System.Windows.Forms.MouseEventArgs> , <xref:System.Windows.Forms.Control.MouseDown> veya <xref:System.Windows.Forms.Control.MouseUp> almak için olay <xref:System.Drawing.Point.X%2A> ve <xref:System.Drawing.Point.Y%2A> koordine değerlerini <xref:System.Drawing.Point> oluştuğu tıklatın.</span><span class="sxs-lookup"><span data-stu-id="17b8d-107">As an alternative, you can use the <xref:System.Windows.Forms.MouseEventArgs> of the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.MouseUp> event to get the <xref:System.Drawing.Point.X%2A> and <xref:System.Drawing.Point.Y%2A> coordinate values of the <xref:System.Drawing.Point> where the click occurred.</span></span> <span data-ttu-id="17b8d-108">Ardından, <xref:System.Windows.Forms.TreeView> denetimin <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> hangi düğümüne tıklandığını belirleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="17b8d-108">Then, use the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> method to determine which node was clicked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b8d-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17b8d-109">See Also</span></span>  
 [<span data-ttu-id="17b8d-110">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="17b8d-110">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
