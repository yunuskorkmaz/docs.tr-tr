---
title: 'Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)'
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
ms.openlocfilehash: f588a00c430eb1ae1f0cdcde6b7dd22f0c8671c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956994"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)
Bir Windows Forms <xref:System.Windows.Forms.TreeView> denetiminde veya bir <xref:System.Windows.Forms.ListView> denetimdeki türetilmiş bir öğede türetilmiş bir düğüm oluşturabilirsiniz. Türetme, ihtiyacınız olan tüm alanları, ayrıca bunları işlemeye yönelik özel yöntemleri ve oluşturucuları eklemenize olanak tanır. Bu özelliğin bir kullanımı, her ağaç düğümüne veya liste öğesine bir müşteri nesnesi eklemektir. Buradaki örnekler bir <xref:System.Windows.Forms.TreeView> denetim içindir, ancak aynı yaklaşım bir <xref:System.Windows.Forms.ListView> denetim için de kullanılabilir.  
  
### <a name="to-derive-a-tree-node"></a>Bir ağaç düğümü türetmek için  
  
- Bir dosya yolunu kaydetmek için özel bir alanı olan <xref:System.Windows.Forms.TreeNode> sınıfından türetilmiş yeni bir Node sınıfı oluşturun.  
  
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
  
### <a name="to-use-a-derived-tree-node"></a>Türetilmiş bir ağaç düğümünü kullanmak için  
  
1. İşlev çağrılarını bir parametre olarak, yeni türetilmiş ağaç düğümünü kullanabilirsiniz.  
  
     Aşağıdaki örnekte, metin dosyasının konumu için ayarlanan yol Belgelerim klasörüdür. Bu, Windows işletim sistemini çalıştıran bilgisayarların çoğunun bu dizini içerdiğini varsaydığı için yapılır. Bu Ayrıca, en az sistem erişim düzeylerine sahip kullanıcıların uygulamayı güvenle çalıştırmasına olanak tanır.  
  
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
  
2. Ağaç düğümünü geçirmiş ve bir <xref:System.Windows.Forms.TreeNode> sınıf olarak yazılmışsa, türetilmiş sınıfınıza dönüştürmeniz gerekir. Atama bir nesne türünden diğerine açık bir dönüşümtür. Atama hakkında daha fazla bilgi için bkz. [örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic) [, atama ve tür dönüştürmeleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md) ( C#görsel) veya [atama işleci: ()](/cpp/cpp/cast-operator-parens) (görsel C++).  
  
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
