---
title: 'Nasıl yapılır: bir TreeView veya ListView denetimine özel bilgi ekleme'
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
ms.openlocfilehash: fe507c41de97e9332f3f27e453a476d992f86627
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732223"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a><span data-ttu-id="4567e-102">Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="4567e-102">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>
<span data-ttu-id="4567e-103">Bir Windows Forms <xref:System.Windows.Forms.TreeView> denetiminde veya bir <xref:System.Windows.Forms.ListView> denetimindeki türetilmiş bir öğede türetilmiş bir düğüm oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4567e-103">You can create a derived node in a Windows Forms <xref:System.Windows.Forms.TreeView> control or a derived item in a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="4567e-104">Türetme, ihtiyacınız olan tüm alanları, ayrıca bunları işlemeye yönelik özel yöntemleri ve oluşturucuları eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4567e-104">Derivation allows you to add any fields you require, as well as custom methods and constructors for handling them.</span></span> <span data-ttu-id="4567e-105">Bu özelliğin bir kullanımı, her ağaç düğümüne veya liste öğesine bir müşteri nesnesi eklemektir.</span><span class="sxs-lookup"><span data-stu-id="4567e-105">One use of this feature is to attach a Customer object to each tree node or list item.</span></span> <span data-ttu-id="4567e-106">Buradaki örnekler bir <xref:System.Windows.Forms.TreeView> denetimine yöneliktir, ancak aynı yaklaşım bir <xref:System.Windows.Forms.ListView> denetimi için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4567e-106">The examples here are for a <xref:System.Windows.Forms.TreeView> control, but the same approach can be used for a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
### <a name="to-derive-a-tree-node"></a><span data-ttu-id="4567e-107">Bir ağaç düğümü türetmek için</span><span class="sxs-lookup"><span data-stu-id="4567e-107">To derive a tree node</span></span>  
  
- <span data-ttu-id="4567e-108">Bir dosya yolunu kaydetmek için özel bir alan olan <xref:System.Windows.Forms.TreeNode> sınıfından türetilmiş yeni bir Node sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4567e-108">Create a new node class, derived from the <xref:System.Windows.Forms.TreeNode> class, which has a custom field to record a file path.</span></span>  
  
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
  
### <a name="to-use-a-derived-tree-node"></a><span data-ttu-id="4567e-109">Türetilmiş bir ağaç düğümünü kullanmak için</span><span class="sxs-lookup"><span data-stu-id="4567e-109">To use a derived tree node</span></span>  
  
1. <span data-ttu-id="4567e-110">İşlev çağrılarını bir parametre olarak, yeni türetilmiş ağaç düğümünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4567e-110">You can use the new derived tree node as a parameter to function calls.</span></span>  
  
     <span data-ttu-id="4567e-111">Aşağıdaki örnekte, metin dosyasının konumu için ayarlanan yol Belgelerim klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="4567e-111">In the example below, the path set for the location of the text file is the My Documents folder.</span></span> <span data-ttu-id="4567e-112">Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır.</span><span class="sxs-lookup"><span data-stu-id="4567e-112">This is done because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="4567e-113">Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4567e-113">This also allows users with minimal system access levels to safely run the application.</span></span>  
  
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
  
2. <span data-ttu-id="4567e-114">Ağaç düğümünü geçirmiş ve bu bir <xref:System.Windows.Forms.TreeNode> sınıfı olarak yazılmışsa, türetilmiş sınıfınıza dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4567e-114">If you are passed the tree node and it is typed as a <xref:System.Windows.Forms.TreeNode> class, then you will need to cast to your derived class.</span></span> <span data-ttu-id="4567e-115">Atama bir nesne türünden diğerine açık bir dönüşümtür.</span><span class="sxs-lookup"><span data-stu-id="4567e-115">Casting is an explicit conversion from one type of object to another.</span></span> <span data-ttu-id="4567e-116">Atama hakkında daha fazla bilgi için bkz. [örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic) [, atama ve tür dönüştürmeleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md) ( C#görsel) veya [atama işleci: ()](/cpp/cpp/cast-operator-parens) (görsel C++).</span><span class="sxs-lookup"><span data-stu-id="4567e-116">For more information on casting, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [Casting and type conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#), or [Cast Operator: ()](/cpp/cpp/cast-operator-parens) (Visual C++).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4567e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4567e-117">See also</span></span>

- [<span data-ttu-id="4567e-118">TreeView Denetimi</span><span class="sxs-lookup"><span data-stu-id="4567e-118">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="4567e-119">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="4567e-119">ListView Control</span></span>](listview-control-windows-forms.md)
