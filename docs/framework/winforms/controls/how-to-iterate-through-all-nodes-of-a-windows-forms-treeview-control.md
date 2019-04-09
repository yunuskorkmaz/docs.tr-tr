---
title: 'Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
ms.openlocfilehash: e8e5ef299ca7b5555a02e86e4422ca9f5b8a584f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199719"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a><span data-ttu-id="989d0-102">Nasıl yapılır: Bir Windows Forms TreeView Denetiminin Tüm Düğümlerinde Yineleme</span><span class="sxs-lookup"><span data-stu-id="989d0-102">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>
<span data-ttu-id="989d0-103">Her düğüm bir Windows Forms incelemeniz bazen kullanışlıdır <xref:System.Windows.Forms.TreeView> düğüm değerleri üzerinde bazı hesaplama gerçekleştirmek için denetimi.</span><span class="sxs-lookup"><span data-stu-id="989d0-103">It is sometimes useful to examine every node in a Windows Forms <xref:System.Windows.Forms.TreeView> control in order to perform some calculation on the node values.</span></span> <span data-ttu-id="989d0-104">Bu işlem yapılabilir bir özyinelemeli yordamı kullanarak (yinelemeli yönteminde C# ve C++) ağacının her bir koleksiyon içindeki her bir düğümün aracılığıyla yinelenir.</span><span class="sxs-lookup"><span data-stu-id="989d0-104">This operation can be done using a recursive procedure (recursive method in C# and C++) that iterates through each node in each collection of the tree.</span></span>  
  
 <span data-ttu-id="989d0-105">Her <xref:System.Windows.Forms.TreeNode> nesne ağaç görünümünde, ağaç görünümünde gezinmek için kullanabileceğiniz özelliklere sahiptir: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, ve <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span><span class="sxs-lookup"><span data-stu-id="989d0-105">Each <xref:System.Windows.Forms.TreeNode> object in a tree view has properties that you can use to navigate the tree view: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>, <xref:System.Windows.Forms.TreeNode.LastNode%2A>, <xref:System.Windows.Forms.TreeNode.NextNode%2A>, <xref:System.Windows.Forms.TreeNode.PrevNode%2A>, and <xref:System.Windows.Forms.TreeNode.Parent%2A>.</span></span> <span data-ttu-id="989d0-106">Değerini <xref:System.Windows.Forms.TreeNode.Parent%2A> üst düğümünün geçerli düğüm bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="989d0-106">The value of the <xref:System.Windows.Forms.TreeNode.Parent%2A> property is the parent node of the current node.</span></span> <span data-ttu-id="989d0-107">Varsa, geçerli düğümünün alt düğümleri listelenen kendi <xref:System.Windows.Forms.TreeNode.Nodes%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="989d0-107">The child nodes of the current node, if there are any, are listed in its <xref:System.Windows.Forms.TreeNode.Nodes%2A> property.</span></span> <span data-ttu-id="989d0-108"><xref:System.Windows.Forms.TreeView> Denetiminin kendisini <xref:System.Windows.Forms.TreeView.TopNode%2A> tüm ağaç görünümünün kök düğüm özelliği.</span><span class="sxs-lookup"><span data-stu-id="989d0-108">The <xref:System.Windows.Forms.TreeView> control itself has the <xref:System.Windows.Forms.TreeView.TopNode%2A> property, which is the root node of the entire tree view.</span></span>  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a><span data-ttu-id="989d0-109">TreeView denetiminin tüm düğümlerinde yineleme için</span><span class="sxs-lookup"><span data-stu-id="989d0-109">To iterate through all nodes of the TreeView control</span></span>  
  
1.  <span data-ttu-id="989d0-110">Bir özyinelemeli yordam oluşturma (özyinelemeli yönteminde C# ve C++), her düğüm test eder.</span><span class="sxs-lookup"><span data-stu-id="989d0-110">Create a recursive procedure (recursive method in C# and C++) that tests each node.</span></span>  
  
2.  <span data-ttu-id="989d0-111">Yordam çağrısı.</span><span class="sxs-lookup"><span data-stu-id="989d0-111">Call the procedure.</span></span>  
  
     <span data-ttu-id="989d0-112">Aşağıdaki örnek, her yazdırma işlemi gösterilmektedir <xref:System.Windows.Forms.TreeNode> nesnenin <xref:System.Windows.Forms.TreeNode.Text%2A> özelliği:</span><span class="sxs-lookup"><span data-stu-id="989d0-112">The following example shows how to print each <xref:System.Windows.Forms.TreeNode> object's <xref:System.Windows.Forms.TreeNode.Text%2A> property:</span></span>  
  
    ```vb  
    Private Sub PrintRecursive(ByVal n As TreeNode)  
       System.Diagnostics.Debug.WriteLine(n.Text)  
       MessageBox.Show(n.Text)  
       Dim aNode As TreeNode  
       For Each aNode In n.Nodes  
          PrintRecursive(aNode)  
       Next  
    End Sub  
  
    ' Call the procedure using the top nodes of the treeview.  
    Private Sub CallRecursive(ByVal aTreeView As TreeView)  
       Dim n As TreeNode  
       For Each n In aTreeView.Nodes  
          PrintRecursive(n)  
       Next  
    End Sub  
    ```  
  
    ```csharp  
    private void PrintRecursive(TreeNode treeNode)  
    {  
       // Print the node.  
       System.Diagnostics.Debug.WriteLine(treeNode.Text);  
       MessageBox.Show(treeNode.Text);  
       // Print each node recursively.  
       foreach (TreeNode tn in treeNode.Nodes)  
       {  
          PrintRecursive(tn);  
       }  
    }  
  
    // Call the procedure using the TreeView.  
    private void CallRecursive(TreeView treeView)  
    {  
       // Print each node recursively.  
       TreeNodeCollection nodes = treeView.Nodes;  
       foreach (TreeNode n in nodes)  
       {  
          PrintRecursive(n);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void PrintRecursive( TreeNode^ treeNode )  
       {  
          // Print the node.  
          System::Diagnostics::Debug::WriteLine( treeNode->Text );  
          MessageBox::Show( treeNode->Text );  
  
          // Print each node recursively.  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(treeNode->Nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ tn = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( tn );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
  
       // Call the procedure using the TreeView.  
       void CallRecursive( TreeView^ treeView )  
       {  
          // Print each node recursively.  
          TreeNodeCollection^ nodes = treeView->Nodes;  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ n = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( n );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="989d0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="989d0-113">See also</span></span>

- [<span data-ttu-id="989d0-114">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="989d0-114">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="989d0-115">Özyinelemeli Yordamlar</span><span class="sxs-lookup"><span data-stu-id="989d0-115">Recursive Procedures</span></span>](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
