---
title: 'Nasıl yapilir: TreeView veya ListView Denetimine Özel Bilgiler Ekleme'
ms.date: 03/30/2017
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
ms.openlocfilehash: faed586a5814526b0169ea46c8bb452e3777d8ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182434"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="9b91b-102">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9b91b-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="9b91b-103">Windows Forms <xref:System.Windows.Forms.TreeView> denetiminde türetilmiş bir düğüm veya denetimde <xref:System.Windows.Forms.ListView> türetilmiş bir öğe oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b91b-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="9b91b-104">Türetme, gereksinim duyduğunuz alanlarıve bunları işlemek için özel yöntemler ve yapıcılar eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9b91b-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="9b91b-105">Bu özelliğin kullanımı, her ağaç düğümü veya liste öğesine bir Müşteri nesnesi eklemektir.</span><span class="sxs-lookup"><span data-stu-id="9b91b-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="9b91b-106">Buradaki örnekler bir <xref:System.Windows.Forms.TreeView> denetim içindir, ancak aynı yaklaşım <xref:System.Windows.Forms.ListView> bir denetim için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9b91b-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="9b91b-107">Ağaç düğümü türetmek için</span><span class="sxs-lookup"><span data-stu-id="9b91b-107">To derive a tree node</span></span>  
  
- <span data-ttu-id="9b91b-108">Dosya yolunu kaydetmek için özel <xref:System.Windows.Forms.TreeNode> bir alana sahip sınıftan türetilen yeni bir düğüm sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9b91b-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="9b91b-109">Türetilmiş ağaç düğümü kullanmak için</span><span class="sxs-lookup"><span data-stu-id="9b91b-109">To use a derived tree node</span></span>  
  
1. <span data-ttu-id="9b91b-110">Çağrıları işletmek için yeni türetilmiş ağaç düğümunu parametre olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b91b-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="9b91b-111">Aşağıdaki örnekte, metin dosyasının konumu için ayarlanan yol Belgelerim klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="9b91b-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="9b91b-112">Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içereceğini varsayabileceğiniz için bu işlem yapılır.</span><span class="sxs-lookup"><span data-stu-id="9b91b-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="9b91b-113">Bu aynı zamanda en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenli bir şekilde çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9b91b-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
    treeView1.Nodes.Add(new myTreeNode(System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
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
  
2. <span data-ttu-id="9b91b-114">Ağaç düğümü geçtiyseniz ve sınıf <xref:System.Windows.Forms.TreeNode> olarak yazılıyorsa, türemiş sınıfınıza dökmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b91b-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="9b91b-115">Döküm, bir nesne türünden diğerine açık bir dönüştürmedir.</span><span class="sxs-lookup"><span data-stu-id="9b91b-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="9b91b-116">Döküm hakkında daha fazla bilgi için [örtük ve Açık Dönüşümler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [Döküm ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#) veya [Cast Operator: ()](/cpp/cpp/cast-operator-parens) (Visual C++) bakın.</span><span class="sxs-lookup"><span data-stu-id="9b91b-116">For more information on casting, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [Casting and type conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) (Visual C++).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9b91b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b91b-117">See also</span></span>

- [<span data-ttu-id="9b91b-118">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="9b91b-118">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="9b91b-119">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="9b91b-119">ListView Control</span></span>](listview-control-windows-forms.md)
