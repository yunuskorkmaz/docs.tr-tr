---
title: "İzlenecek yol: Windows Forms'da Sürükle ve Bırak İşlemi Gerçekleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: cda3e87a4b0eb680d374eb0419a6b6b3157dc4a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957130"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>İzlenecek yol: Windows Forms'da Sürükle ve Bırak İşlemi Gerçekleştirme
Windows tabanlı uygulamalarda sürükle ve bırak işlemleri gerçekleştirmek için, bir dizi olayı, özellikle <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragLeave>, ve <xref:System.Windows.Forms.Control.DragDrop> olaylarını işlemeniz gerekir. Bu olayların olay bağımsız değişkenlerinde bulunan bilgilerle çalışarak, sürükle ve bırak işlemlerini kolayca kolaylaştırabilirsiniz.  
  
## <a name="dragging-data"></a>Verileri sürükleme  
 Tüm sürükle ve bırak işlemleri sürüklemeye başlar. Sürükleme başladığında verilerin toplanmasına olanak sağlayan işlevsellik, <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemi içinde uygulanır.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> en sezgisel olan (sürükleme ve bırakma eylemleri fare düğmesi basılı olarak başlar), sürükleme işlemini başlatmak için olay kullanılır. Ancak, bir sürükle ve bırak yordamını başlatmak için herhangi bir olayın kullanılabileceğini unutmayın.  
  
> [!NOTE]
> Belirli denetimlerin özel sürüklemeye özgü olayları vardır. Ve denetimleri, örneğin, bir <xref:System.Windows.Forms.TreeView.ItemDrag> olayıdır. <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.ListView>  
  
#### <a name="to-start-a-drag-operation"></a>Bir sürükleme işlemini başlatmak için  
  
1. Sürüklediğiniz denetimin başlayacağı `DoDragDrop` olayda,verilerisürüklenecektirveizinverilenefektsürüklemeyesahipolacakşekildeayarlamak<xref:System.Windows.Forms.Control.MouseDown> için yöntemini kullanın. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Aşağıdaki örnek, bir sürükleme işleminin nasıl başlatılacağı gösterilmektedir. Sürükleme işleminin başladığı denetim bir <xref:System.Windows.Forms.Button> denetimdir, sürüklediğiniz veri <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğini temsil eden dizedir ve izin verilen etkiler kopyalama veya taşıma olur.  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    > Tüm veriler `DoDragDrop` yönteminde parametre olarak kullanılabilir; Yukarıdaki örnekte <xref:System.Windows.Forms.Control.Text%2A> , <xref:System.Windows.Forms.Button> denetimin özelliği kullanılmıştır (bir değer kodlanması veya bir veri kümesinden verileri almak yerine), özelliği sürüklenen konum ( <xref:System.Windows.Forms.Button> denetim). Windows tabanlı uygulamalarınıza sürükle ve bırak işlemleri eklediğinizde bunu göz önünde bulundurun.  
  
 Bir sürükleme işlemi etkin olsa da, sürükleme işlemine devam etmek için <xref:System.Windows.Forms.Control.QueryContinueDrag> sistemin "izin sorar" olayını işleyebilirsiniz. Bu yöntemi işlerken, imleç üzerine geldiğinde bir <xref:System.Windows.Forms.TreeNode> <xref:System.Windows.Forms.TreeView> denetimde genişletme gibi, sürükleme işleminde bir etkisi olan yöntemleri çağırdığınızda de uygun bir nokta vardır.  
  
## <a name="dropping-data"></a>Verileri bırakma  
 Bir Windows formundaki veya denetimindeki bir konumdan veri sürüklemeye başladıktan sonra doğal olarak bir yere bırakmak istersiniz. İmleç, veri bırakma için doğru şekilde yapılandırılmış bir formun veya denetimin bir alanını aştığında değişecektir. Bir Windows form veya denetim içindeki herhangi bir alan, <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği ayarlayarak ve <xref:System.Windows.Forms.Control.DragDrop> olayları <xref:System.Windows.Forms.Control.DragEnter> işleyerek bırakılan verileri kabul etmek için yapılabilir.  
  
#### <a name="to-perform-a-drop"></a>Bir bırakma işlemi gerçekleştirmek için  
  
1. <xref:System.Windows.Forms.Control.AllowDrop%2A> Özelliği true olarak ayarlayın.  
  
2. Bırakma işleminin gerçekleşeceği denetim <xref:System.Windows.Forms.Control.Text%2A> olayında,sürüklenenverilerinkabuledilebilirbirtür(Budurumda)olduğundaneminolun.`DragEnter` Kod daha sonra, <xref:System.Windows.Forms.DragDropEffects> Numaralandırmadaki bir değere bırakma gerçekleştiğinde gerçekleşecek etkiyi ayarlar. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    > Yöntemin<xref:System.Windows.Forms.DataObject.SetData%2A> <xref:System.Windows.Forms.DataFormats> parametresi<xref:System.Object> olarak kendi nesneniz belirterek kendi uygulamanızı tanımlayabilirsiniz. Bunu yaparken, belirtilen nesnenin seri hale getirilebilir olduğundan emin olun. Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.  
  
3. Bırakma işleminin gerçekleşeceği denetim <xref:System.Windows.Forms.DataObject.GetData%2A> olayında,sürüklediğinizverilerialmakiçinyönteminikullanın.<xref:System.Windows.Forms.Control.DragDrop> Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     Aşağıdaki örnekte, bir <xref:System.Windows.Forms.TextBox> denetim Sürüklenmekte olan denetimdir (bırakma gerçekleşir). Kod, <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.TextBox> denetimin özelliğini sürüklenen verilere eşit olarak ayarlar.  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    > Ayrıca, <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> özelliği ile birlikte çalışarak, sürükle ve bırak işlemi sırasında tuşlara bağlı olarak belirli etkileri oluşur (örneğin, CTRL tuşuna basıldığında sürüklenen verileri kopyalamak standart olur).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Panoya veri ekleme](how-to-add-data-to-the-clipboard.md)
- [Nasıl yapılır: Panodan veri alma](how-to-retrieve-data-from-the-clipboard.md)
- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
