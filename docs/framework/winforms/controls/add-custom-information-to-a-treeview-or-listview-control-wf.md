---
title: 'Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- ListItem
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- examples [Windows Forms], ListView control
- ListView control [Windows Forms], adding custom information
- TreeView control [Windows Forms], adding custom information
ms.assetid: 68be11de-1d5b-430e-901f-cfbe48d14b19
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8c7d8b881b3aa79122134deda7f5d95a98a68461
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="c2272-102">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c2272-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="c2272-103">Windows Forms'ta türetilmiş bir düğüm oluşturabilirsiniz <xref:System.Windows.Forms.TreeView> denetimi veya türetilmiş bir öğesinde bir <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="c2272-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="c2272-104">Türetme özel yöntemler ve bunları işlemek için oluşturucular yanı sıra, gerekli tüm alanları eklemenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="c2272-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="c2272-105">Bu özellik bir kullanımını her ağaç düğümü veya liste öğesi için bir müşteri nesnesi eklemektir.</span><span class="sxs-lookup"><span data-stu-id="c2272-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="c2272-106">Burada için örnekler bir <xref:System.Windows.Forms.TreeView> için denetimi, ancak aynı yaklaşımı kullanılabilir bir <xref:System.Windows.Forms.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="c2272-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="c2272-107">Bir ağaç düğümü çıkarmaya</span><span class="sxs-lookup"><span data-stu-id="c2272-107">To derive a tree node</span></span>  
  
-   <span data-ttu-id="c2272-108">Türetilen yeni bir düğüm sınıf oluşturmak <xref:System.Windows.Forms.TreeNode> sahip bir dosya yolu kaydetmek için özel bir alan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c2272-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
    ```vb  
    Class myTreeNode  
       Inherits TreeNode  
  
       Public FilePath As String  
  
       Sub New(ByVal fp As String)  
          MyBase.New()  
          FilePath = fp  
          Me.Text = fp.Substring(fp.LastIndexOf("\"))  
       End Sub  
    End Class  
    ```  
  
    ```csharp  
    class myTreeNode : TreeNode  
    {  
       public string FilePath;  
  
       public myTreeNode(string fp)  
       {  
          FilePath = fp;  
          this.Text = fp.Substring(fp.LastIndexOf("\\"));  
       }  
    }  
    ```  
  
    ```cpp  
    ref class myTreeNode : public TreeNode  
    {  
    public:  
       System::String ^ FilePath;  
  
       myTreeNode(System::String ^ fp)  
       {  
          FilePath = fp;  
          this->Text = fp->Substring(fp->LastIndexOf("\\"));  
       }  
    };  
    ```  
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="c2272-109">Bir türetilmiş ağaç düğümü kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c2272-109">To use a derived tree node</span></span>  
  
1.  <span data-ttu-id="c2272-110">İşlev çağrıları için bir parametre olarak yeni türetilmiş ağaç düğümü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2272-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="c2272-111">Aşağıdaki örnekte, metin dosyasının konumunu ayarlayın Belgelerim klasörünü yoludur.</span><span class="sxs-lookup"><span data-stu-id="c2272-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="c2272-112">Windows işletim sistemi çalıştıran bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu yapılır.</span><span class="sxs-lookup"><span data-stu-id="c2272-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="c2272-113">Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri olan kullanıcılar da sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2272-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
    ```vb  
    ' You should replace the bold text file   
    ' in the sample below with a text file of your own choosing.  
    TreeView1.Nodes.Add(New myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\ TextFile.txt ") )  
    ```  
  
    ```csharp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    treeView1.Nodes.Add(new myTreeNode (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\TextFile.txt") );  
    ```  
  
    ```cpp  
    // You should replace the bold text file   
    // in the sample below with a text file of your own choosing.  
    treeView1->Nodes->Add(new myTreeNode(String::Concat(  
       System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\TextFile.txt")));  
    ```  
  
2.  <span data-ttu-id="c2272-114">Ağaç düğümünün geçirilir ve olarak yazılan bir <xref:System.Windows.Forms.TreeNode> sınıfından türetilen sınıfınıza cast gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="c2272-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="c2272-115">Atama nesnesi türünden açık bir dönüştürme başka bir ' dir.</span><span class="sxs-lookup"><span data-stu-id="c2272-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="c2272-116">Atama hakkında daha fazla bilgi için bkz: [dolaylı ve açık dönüştürmeler](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic) [ta](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#) veya [atama işleci: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="c2272-116">For more information on casting, see [Implicit and Explicit Conversions](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [() Operator](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).</span></span>  
  
    ```vb  
    Public Sub TreeView1_AfterSelect(ByVal sender As Object, ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       Dim mynode As myTreeNode  
       mynode = CType(e.node, myTreeNode)  
       MessageBox.Show("Node selected is " & mynode.filepath)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,  
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       myTreeNode myNode = (myTreeNode)e.Node;  
       MessageBox.Show("Node selected is " + myNode.FilePath);  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          myTreeNode ^ myNode = safe_cast<myTreeNode^>(e->Node);  
          MessageBox::Show(String::Concat("Node selected is ",   
             myNode->FilePath));  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c2272-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2272-117">See Also</span></span>  
 [<span data-ttu-id="c2272-118">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="c2272-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="c2272-119">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="c2272-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
