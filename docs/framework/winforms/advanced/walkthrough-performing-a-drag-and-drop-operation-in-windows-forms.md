---
title: 'Walkthrough: Sürükle ve bırak işlemi gerçekleştirin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182437"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme
Windows tabanlı uygulamalarda sürükle ve bırak işlemleri gerçekleştirmek için, en önemlisi <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>ve <xref:System.Windows.Forms.Control.DragDrop> olaylar olmak üzere bir dizi olayı ele almalısınız. Bu olayların olay argümanlarında bulunan bilgilerle çalışarak sürükle ve bırak işlemlerini kolayca kolaylaştırabilirsiniz.  
  
## <a name="dragging-data"></a>Verileri Sürükleme  
 Tüm sürükle ve bırak işlemleri sürükleme ile başlar. Sürükleme başladığında verilerin toplanmasını etkinleştirme işlevi <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemde uygulanır.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> en sezgisel olduğu için sürükle işlemini başlatmak için olay kullanılır (çoğu sürükle ve bırak eylemi fare düğmesinin depresif olmasıyla başlar). Ancak, herhangi bir olayın sürükle ve bırak yordamı başlatmak için kullanılabileceğini unutmayın.  
  
> [!NOTE]
> Bazı denetimlerde özel sürüme özel olaylar vardır. Ve <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> denetimleri, örneğin, <xref:System.Windows.Forms.TreeView.ItemDrag> bir olay var.  
  
#### <a name="to-start-a-drag-operation"></a>Sürükleme işlemini başlatmak için  
  
1. Sürüklemenin <xref:System.Windows.Forms.Control.MouseDown> başlayacağı denetim durumunda, sürükleme nin `DoDragDrop` verilen verileri ayarlamak için yöntemi kullanın ve izin verilen efekt sürükleme olacaktır. Daha fazla bilgi için <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> bölümlerine bakın.  
  
     Aşağıdaki örnek, sürükleme işleminin nasıl başlatılabildiğini gösterir. Sürüklemenin başladığı denetim bir <xref:System.Windows.Forms.Button> denetimdir, sürüklenen veriler <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button> denetimin özelliğini temsil eden dizedir ve izin verilen efektler kopyalama veya taşımadır.  
  
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
    > Herhangi bir veri `DoDragDrop` yöntemde bir parametre olarak kullanılabilir; yukarıdaki örnekte, <xref:System.Windows.Forms.Control.Text%2A> denetimin <xref:System.Windows.Forms.Button> özelliği (bir değeri zor kodlamak veya veri kümesinden veri almak yerine) kullanılmıştır, çünkü özellik sürüklenen <xref:System.Windows.Forms.Button> konumla (denetim) ilgilidir. Sürükle ve bırak işlemlerini Windows tabanlı uygulamalarınıza dahil ederken bunu aklınızda bulundurun.  
  
 Sürükleme işlemi etkinken, sürükle işlemine devam etmek için sistemin "izin istediği" <xref:System.Windows.Forms.Control.QueryContinueDrag> olayı işleyebilirsiniz. Bu yöntemi işlerken, imleç üzerinde gezinirken bir <xref:System.Windows.Forms.TreeNode> denetimi <xref:System.Windows.Forms.TreeView> genişletmek gibi sürükleme işlemini etkileyecek yöntemleri aramanız da uygun bir noktadır.  
  
## <a name="dropping-data"></a>Veri Bırakma  
 Windows Formu veya denetimindeki bir konumdan veri sürüklemeye başladıktan sonra, doğal olarak verileri bir yere bırakmak isteyeceksiniz. İmleç, veri bırakmak için doğru şekilde yapılandırılan bir form veya denetim alanını geçtiğinde değişir. Windows Formu veya denetimi içindeki herhangi bir alan, <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği ayarlayarak ve <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> olayları işleyerek bırakılan verileri kabul etmek için yapılabilir.  
  
#### <a name="to-perform-a-drop"></a>Bir damla gerçekleştirmek için  
  
1. Özelliği <xref:System.Windows.Forms.Control.AllowDrop%2A> gerçeğe ayarlayın.  
  
2. `DragEnter` Bırakmanın gerçekleşeceği denetim durumunda, sürüklenen verilerin kabul edilebilir bir türde olduğundan emin <xref:System.Windows.Forms.Control.Text%2A>olun (bu durumda). Kod daha sonra, numaralandırmadaki <xref:System.Windows.Forms.DragDropEffects> bir değerde düşüş oluştuğunda oluşacak efekti ayarlar. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Yöntemin <xref:System.Windows.Forms.DataFormats> <xref:System.Object> parametresi <xref:System.Windows.Forms.DataObject.SetData%2A> olarak kendi nesnenizi belirterek kendi nesnenizi tanımlayabilirsiniz. Bunu yaparken, belirtilen nesnenin serileştirilebilir olduğundan emin olun. Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.  
  
3. <xref:System.Windows.Forms.Control.DragDrop> Bırakmanın gerçekleşeceği denetim durumunda, sürüklenen <xref:System.Windows.Forms.DataObject.GetData%2A> verileri almak için yöntemi kullanın. Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     Aşağıdaki örnekte, <xref:System.Windows.Forms.TextBox> denetim sürülmekte olan denetimdir (bırakmanın gerçekleşeceği yer). Kod, denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğini <xref:System.Windows.Forms.TextBox> sürüklenen verilere eşit olarak ayarlar.  
  
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
    > Ayrıca, <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> sürükle ve bırak işlemi sırasında bunalıma girmiş anahtarlara bağlı olarak belirli efektlerin oluşması (örneğin, CTRL tuşuna basıldığında sürüklenen verileri kopyalamak standarttır) özelliğiyle birlikte çalışabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Panoya Veri Ekleme](how-to-add-data-to-the-clipboard.md)
- [Nasıl yapılır: Panodan Veri Alma](how-to-retrieve-data-from-the-clipboard.md)
- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
