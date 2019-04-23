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
ms.openlocfilehash: 302eb1b88d4e43b4e2bd6395e27a3a6489320085
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344162"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)
Windows Forms'ta türetilmiş bir düğüm oluşturabilirsiniz <xref:System.Windows.Forms.TreeView> denetimi veya türetilmiş bir öğede bir <xref:System.Windows.Forms.ListView> denetimi. Türetme yanı sıra özel yöntemleri ve bunları işlemek için oluşturucuları, gerekli tüm alanlar eklemenize olanak sağlar. Bu özellik bir kullanımı, her ağaç düğümü veya liste öğesi için bir müşteri nesnesi eklemektir. Buradaki örnekler için olan bir <xref:System.Windows.Forms.TreeView> için denetimi, ancak aynı yaklaşımı kullanılabilir bir <xref:System.Windows.Forms.ListView> denetimi.  
  
### <a name="to-derive-a-tree-node"></a>Bir ağaç düğümü türetmek için  
  
-   Türetilmiş yeni bir düğüm sınıfı oluşturmak <xref:System.Windows.Forms.TreeNode> dosya yolunu kaydetmek için özel bir alan olan sınıf.  
  
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
  
### <a name="to-use-a-derived-tree-node"></a>Türetilen bir ağaç düğümünü kullanmak için  
  
1. İşlev çağrıları bir parametre olarak, yeni türetilmiş ağaç düğümü kullanabilirsiniz.  
  
     Aşağıdaki örnekte, metin dosyasının konumunu için belirtilen yolda Belgelerim klasördür. Bunun yapılmasının nedeni, Windows işletim sistemi çalıştırılan bilgisayarların çoğu bu dizin içerdiğini varsayar. Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeylerine sahip kullanıcılar da sağlar.  
  
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
  
2. Ağaç düğümünde geçirilir ve olarak belirlenmiş bir <xref:System.Windows.Forms.TreeNode> sınıfından türetilmiş sınıfınızın cast gerekecektir. Atama, nesnenin bir türden diğerine açık bir dönüştürme ' dir. Atama hakkında daha fazla bilgi için bkz. [örtük ve açık dönüştürmeler](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic) [() işleci](~/docs/csharp/language-reference/operators/invocation-operator.md) (görsel C#), veya [atama işleci: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) .  
  
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
