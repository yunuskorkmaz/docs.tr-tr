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
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)
Windows Forms <xref:System.Windows.Forms.TreeView> denetiminde türetilmiş bir düğüm veya denetimde <xref:System.Windows.Forms.ListView> türetilmiş bir öğe oluşturabilirsiniz. Türetme, gereksinim duyduğunuz alanlarıve bunları işlemek için özel yöntemler ve yapıcılar eklemenize olanak tanır. Bu özelliğin kullanımı, her ağaç düğümü veya liste öğesine bir Müşteri nesnesi eklemektir. Buradaki örnekler bir <xref:System.Windows.Forms.TreeView> denetim içindir, ancak aynı yaklaşım <xref:System.Windows.Forms.ListView> bir denetim için kullanılabilir.  
  
### <a name="to-derive-a-tree-node"></a>Ağaç düğümü türetmek için  
  
- Dosya yolunu kaydetmek için özel <xref:System.Windows.Forms.TreeNode> bir alana sahip sınıftan türetilen yeni bir düğüm sınıfı oluşturun.  
  
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
  
### <a name="to-use-a-derived-tree-node"></a>Türetilmiş ağaç düğümü kullanmak için  
  
1. Çağrıları işletmek için yeni türetilmiş ağaç düğümunu parametre olarak kullanabilirsiniz.  
  
     Aşağıdaki örnekte, metin dosyasının konumu için ayarlanan yol Belgelerim klasörüdür. Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içereceğini varsayabileceğiniz için bu işlem yapılır. Bu aynı zamanda en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenli bir şekilde çalıştırmasına olanak tanır.  
  
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
  
2. Ağaç düğümü geçtiyseniz ve sınıf <xref:System.Windows.Forms.TreeNode> olarak yazılıyorsa, türemiş sınıfınıza dökmeniz gerekir. Döküm, bir nesne türünden diğerine açık bir dönüştürmedir. Döküm hakkında daha fazla bilgi için [örtük ve Açık Dönüşümler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic), [Döküm ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md) (Visual C#) veya [Cast Operator: ()](/cpp/cpp/cast-operator-parens) (Visual C++) bakın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [TreeView Denetimi](treeview-control-windows-forms.md)
- [ListView Denetimi](listview-control-windows-forms.md)
