---
title: 'İzlenecek yol: sürükle ve bırak işlemi gerçekleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 265e6d4f9e3370d28a18b86dea983bb0b556be41
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746797"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme
Windows tabanlı uygulamalarda sürükle ve bırak işlemleri gerçekleştirmek için, en önemlisi <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>ve <xref:System.Windows.Forms.Control.DragDrop> olaylarını bir dizi olayı işlemeniz gerekir. Bu olayların olay bağımsız değişkenlerinde bulunan bilgilerle çalışarak, sürükle ve bırak işlemlerini kolayca kolaylaştırabilirsiniz.  
  
## <a name="dragging-data"></a>Verileri sürükleme  
 Tüm sürükle ve bırak işlemleri sürüklemeye başlar. Sürükleme başladığında verilerin toplanmasına olanak sağlayan işlevsellik, <xref:System.Windows.Forms.Control.DoDragDrop%2A> yönteminde uygulanır.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> olayı, en sezgisel olduğu için (sürükleme ve bırakma eylemleri fare düğmesi basılı olarak başlar) sürükleme işlemini başlatmak için kullanılır. Ancak, bir sürükle ve bırak yordamını başlatmak için herhangi bir olayın kullanılabileceğini unutmayın.  
  
> [!NOTE]
> Belirli denetimlerin özel sürüklemeye özgü olayları vardır. <xref:System.Windows.Forms.ListView> ve <xref:System.Windows.Forms.TreeView> denetimleri (örneğin, bir <xref:System.Windows.Forms.TreeView.ItemDrag> olayına sahiptir).  
  
#### <a name="to-start-a-drag-operation"></a>Bir sürükleme işlemini başlatmak için  
  
1. Sürüklediğiniz denetimin başlayacağı denetim için <xref:System.Windows.Forms.Control.MouseDown> olayında, verileri sürüklemek üzere ve izin verilen efekt sürüklemeye sahip olacak şekilde ayarlamak için `DoDragDrop` yöntemini kullanın. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Aşağıdaki örnek, bir sürükleme işleminin nasıl başlatılacağı gösterilmektedir. Sürükleme işleminin başladığı denetim bir <xref:System.Windows.Forms.Button> denetimidir, sürüklediğiniz veriler <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliğini temsil eden dizedir ve izin verilen efektler kopyalama veya taşıma olur.  
  
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
    > Tüm veriler `DoDragDrop` yönteminde parametre olarak kullanılabilir; Yukarıdaki örnekte, özelliği Sürüklenmekte olan konumla (<xref:System.Windows.Forms.Button> denetim) ilişkili olduğundan, <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliği kullanılmıştır (bir değer kodlamak veya bir veri kümesinden verileri almak yerine). Windows tabanlı uygulamalarınıza sürükle ve bırak işlemleri eklediğinizde bunu göz önünde bulundurun.  
  
 Bir sürükleme işlemi etkin olsa da, sürükleme işlemine devam etmek için sistemin "izin sorar" olayını <xref:System.Windows.Forms.Control.QueryContinueDrag> olayı işleyebilirsiniz. Bu yöntemi işlerken, imleç onun üzerine geldiğinde, bir <xref:System.Windows.Forms.TreeView> denetimindeki <xref:System.Windows.Forms.TreeNode> genişletme gibi, sürükleme işleminde bir etkisi olan yöntemleri çağırmanız için de uygun bir noktasıdır.  
  
## <a name="dropping-data"></a>Verileri bırakma  
 Bir Windows formundaki veya denetimindeki bir konumdan veri sürüklemeye başladıktan sonra doğal olarak bir yere bırakmak istersiniz. İmleç, veri bırakma için doğru şekilde yapılandırılmış bir formun veya denetimin bir alanını aştığında değişecektir. Bir Windows form veya denetim içindeki herhangi bir alan, <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliğini ayarlayarak ve <xref:System.Windows.Forms.Control.DragEnter> ve <xref:System.Windows.Forms.Control.DragDrop> olaylarını işleyerek bırakılan verileri kabul etmek için kullanılabilir.  
  
#### <a name="to-perform-a-drop"></a>Bir bırakma işlemi gerçekleştirmek için  
  
1. <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliğini true olarak ayarlayın.  
  
2. Bırakma işleminin gerçekleşeceği denetim için `DragEnter` olayında, sürüklenen verilerin kabul edilebilir bir tür olduğundan emin olun (Bu durumda, <xref:System.Windows.Forms.Control.Text%2A>). Kod daha sonra, <xref:System.Windows.Forms.DragDropEffects> Numaralandırmadaki bir değere bırakma gerçekleştiğinde gerçekleştirilecek etkiyi ayarlar. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Kendi <xref:System.Windows.Forms.DataFormats>, kendi nesneniz <xref:System.Windows.Forms.DataObject.SetData%2A> yönteminin <xref:System.Object> parametresi olarak belirterek tanımlayabilirsiniz. Bunu yaparken, belirtilen nesnenin seri hale getirilebilir olduğundan emin olun. Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.  
  
3. Bırakma işleminin gerçekleşeceği denetimin <xref:System.Windows.Forms.Control.DragDrop> olayında, sürüklediğiniz verileri almak için <xref:System.Windows.Forms.DataObject.GetData%2A> metodunu kullanın. Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     Aşağıdaki örnekte, <xref:System.Windows.Forms.TextBox> denetim Sürüklenmekte olan denetimdir (bırakma gerçekleşir). Kod, <xref:System.Windows.Forms.TextBox> denetiminin <xref:System.Windows.Forms.Control.Text%2A> özelliğini sürüklenen verilere eşit olarak ayarlar.  
  
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
    > Ayrıca, sürükle ve bırak işlemi sırasında anahtarlara bağlı olarak, bazı etkileri meydana geldiğinden (örneğin, CTRL tuşuna basıldığında sürüklenen verileri kopyalamak için standart olan) <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> özelliğiyle çalışabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Panoya Veri Ekleme](how-to-add-data-to-the-clipboard.md)
- [Nasıl yapılır: Panodan Veri Alma](how-to-retrieve-data-from-the-clipboard.md)
- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
