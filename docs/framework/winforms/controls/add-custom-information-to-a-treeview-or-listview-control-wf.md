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
ms.openlocfilehash: b4131504e5c5d7f2075c72c72b98153c783000d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527423"
---
# <a name="how-to-add-custom-information-to-a-treeview-or-listview-control-windows-forms"></a>Nasıl yapılır: Bir TreeView veya ListView Denetimine Özel Bilgi Ekleme (Windows Forms)
Windows Forms'ta türetilmiş bir düğüm oluşturabilirsiniz <xref:System.Windows.Forms.TreeView> denetimi veya türetilmiş bir öğesinde bir <xref:System.Windows.Forms.ListView> denetim. Türetme özel yöntemler ve bunları işlemek için oluşturucular yanı sıra, gerekli tüm alanları eklemenize izin verir. Bu özellik bir kullanımını her ağaç düğümü veya liste öğesi için bir müşteri nesnesi eklemektir. Burada için örnekler bir <xref:System.Windows.Forms.TreeView> için denetimi, ancak aynı yaklaşımı kullanılabilir bir <xref:System.Windows.Forms.ListView> denetim.  
  
### <a name="to-derive-a-tree-node"></a>Bir ağaç düğümü çıkarmaya  
  
-   Türetilen yeni bir düğüm sınıf oluşturmak <xref:System.Windows.Forms.TreeNode> sahip bir dosya yolu kaydetmek için özel bir alan sınıfı.  
  
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
  
### <a name="to-use-a-derived-tree-node"></a>Bir türetilmiş ağaç düğümü kullanmak için  
  
1.  İşlev çağrıları için bir parametre olarak yeni türetilmiş ağaç düğümü kullanabilirsiniz.  
  
     Aşağıdaki örnekte, metin dosyasının konumunu ayarlayın Belgelerim klasörünü yoludur. Windows işletim sistemi çalıştıran bilgisayarların çoğu bu dizin içerdiğini varsayar çünkü bu yapılır. Bu, güvenli bir şekilde uygulamayı çalıştırmak minimum sistem erişim düzeyleri olan kullanıcılar da sağlar.  
  
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
  
2.  Ağaç düğümünün geçirilir ve olarak yazılan bir <xref:System.Windows.Forms.TreeNode> sınıfından türetilen sınıfınıza cast gerekecektir. Atama nesnesi türünden açık bir dönüştürme başka bir ' dir. Atama hakkında daha fazla bilgi için bkz: [dolaylı ve açık dönüştürmeler](~/docs/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) (Visual Basic) [ta](~/docs/csharp/language-reference/operators/invocation-operator.md) (Visual C#) veya [atama işleci: ()](/cpp/cpp/cast-operator-parens) ([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TreeView Denetimi](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
