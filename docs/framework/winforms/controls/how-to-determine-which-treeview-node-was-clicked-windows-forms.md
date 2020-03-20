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
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a><span data-ttu-id="d2397-102">Nasıl yapılır: Hangi TreeView Düğümüne Tıklandığını Belirleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d2397-102">How to: Determine Which TreeView Node Was Clicked (Windows Forms)</span></span>
<span data-ttu-id="d2397-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetimiyle çalışırken, ortak bir görev hangi düğümün tıklatıldığını belirlemek ve uygun şekilde yanıt vermektir.</span><span class="sxs-lookup"><span data-stu-id="d2397-103">When working with the Windows Forms <xref:System.Windows.Forms.TreeView> control, a common task is to determine which node was clicked, and respond appropriately.</span></span>  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a><span data-ttu-id="d2397-104">Hangi TreeView düğümüne tıklandığını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="d2397-104">To determine which TreeView node was clicked</span></span>  
  
1. <span data-ttu-id="d2397-105">Tıklatılan düğüm nesnesine bir başvuru döndürmek için <xref:System.EventArgs> nesneyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2397-105">Use the <xref:System.EventArgs> object to return a reference to the clicked node object.</span></span>  
  
2. <span data-ttu-id="d2397-106">Olayla ilgili verileri içeren <xref:System.Windows.Forms.TreeViewEventArgs> sınıfı işaretleyerek hangi düğümün tıklandığını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d2397-106">Determine which node was clicked by checking the <xref:System.Windows.Forms.TreeViewEventArgs> class, which contains data related to the event.</span></span>  
  
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
    > <span data-ttu-id="d2397-107">Alternatif olarak, <xref:System.Windows.Forms.MouseEventArgs> tıklamanın oluştuğu <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> <xref:System.Drawing.Point.X%2A> <xref:System.Drawing.Point.Y%2A> <xref:System.Drawing.Point> yerin değerlerini almak ve koordine etmek için olayın veya olayın kullanımını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2397-107">As an alternative, you can use the <xref:System.Windows.Forms.MouseEventArgs> of the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.MouseUp> event to get the <xref:System.Drawing.Point.X%2A> and <xref:System.Drawing.Point.Y%2A> coordinate values of the <xref:System.Drawing.Point> where the click occurred.</span></span> <span data-ttu-id="d2397-108">Ardından, hangi <xref:System.Windows.Forms.TreeView> düğümün <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> tıklatıldığını belirlemek için denetim yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2397-108">Then, use the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> method to determine which node was clicked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2397-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2397-109">See also</span></span>

- [<span data-ttu-id="d2397-110">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="d2397-110">TreeView Control</span></span>](treeview-control-windows-forms.md)
