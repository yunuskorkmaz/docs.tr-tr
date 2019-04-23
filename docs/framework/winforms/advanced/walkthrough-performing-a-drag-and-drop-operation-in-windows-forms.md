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
ms.openlocfilehash: f7551f28d07c9517865f60af99954eb40e57daa2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340730"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>İzlenecek yol: Windows Forms'da Sürükle ve Bırak İşlemi Gerçekleştirme
Windows tabanlı uygulamalar sürükle-bırak işlemlerini gerçekleştirmek için bir dizi olayı, özellikle işlemelidir <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, ve <xref:System.Windows.Forms.Control.DragDrop> olayları. Kullanılabilir bilgilerle olay bağımsız değişkenleri bu olayların çalışarak, sürükle ve bırak işlemleri kolayca kolaylaştırabilir.  
  
## <a name="dragging-data"></a>Veriler sürükleme  
 Tüm sürükle ve bırak işlemleri sürüklemeye ile başlayın. Sürükleme işlemi başladığında, toplanacak veri geliştirebilme işlevselliği uygulanan <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemi.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> olayını en sezgisel çünkü bu sürükleme işlemi başlatmak için kullanılır (çoğu sürükle ve bırak Eylemler fare düğmesini basılı ile başlar). Ancak, herhangi bir olay, bir Sürükle ve bırak yordam başlatmak için kullanılabilir unutmayın.  
  
> [!NOTE]
>  Belirli denetimler özel Sürükle özgü olaylar sahiptir. <xref:System.Windows.Forms.ListView> Ve <xref:System.Windows.Forms.TreeView> denetimleri, örneğin, sahip bir <xref:System.Windows.Forms.TreeView.ItemDrag> olay.  
  
#### <a name="to-start-a-drag-operation"></a>Bir sürükleme işlemi başlatmak için  
  
1. İçinde <xref:System.Windows.Forms.Control.MouseDown> yeri sürükleme başlayacak, kullanımını denetlemek için olay `DoDragDrop` sürüklenmesi için veri kümesi için yöntem ve sürükleme izin verilen etkin olacaktır. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Aşağıdaki örnek, bir sürükleme işlemi başlatmak gösterilmektedir. Sürükleme başladığı denetimi bir <xref:System.Windows.Forms.Button> denetimi, sürüklenen veri olduğu temsil eden dize <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.Button> denetimi ve izin verilen efektleri kopyalama veya taşıma.  
  
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
    >  Tüm veriler, bir parametre olarak kullanılabilir `DoDragDrop` yöntemi; yukarıdaki örnekte, <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.Button> denetim kullanıldı (yerine, kodlama sabit bir değer veya bir veri kümesinden veri alma) özelliği ilişkili için gelen sürüklenen konumu ( <xref:System.Windows.Forms.Button> denetim). Sürükle ve bırak işlemleri Windows tabanlı uygulamalarınıza eklemenizi olarak bunu aklınızda bulundurun.  
  
 Bir sürükleme işlemi etkin durumdayken işleyebilirsiniz <xref:System.Windows.Forms.Control.QueryContinueDrag> "izin isteyen" olayı, sürükle işlemini devam etmek için sistemin. Bu yöntem işlenirken, ayrıca, genişletme gibi sürükleme işlemi üzerinde bir etkisi olmayacak yöntemleri çağırmak uygun bir noktasına olduğu bir <xref:System.Windows.Forms.TreeNode> içinde bir <xref:System.Windows.Forms.TreeView> imleci üzerine geldiğinde denetim.  
  
## <a name="dropping-data"></a>Veri bırakılıyor  
 Verileri bir konumdan bir Windows Form veya denetim üzerinde sürükleyerek başlamıştır sonra doğal olarak yere bırak isteyeceksiniz. İmleç, bir form veya denetim verilerini silmek için doğru şekilde yapılandırıldığı bir alanı geçtiğinde değişecektir. Bırakılan veri ayarlayarak kabul etmek için bir Windows Form veya denetim içinde herhangi bir alan yapılabilir <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği ve işleme <xref:System.Windows.Forms.Control.DragEnter> ve <xref:System.Windows.Forms.Control.DragDrop> olayları.  
  
#### <a name="to-perform-a-drop"></a>Bir bırakma gerçekleştirmek için  
  
1. Ayarlama <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği true.  
  
2. İçinde `DragEnter` burada açılan gerçekleşir, denetim için olay sürüklenen veri kabul edilebilir bir tür olduğundan emin olun (Bu durumda, <xref:System.Windows.Forms.Control.Text%2A>). Kodun ardından açılan bir değere oluştuğunda gerçekleşir etkisini ayarlar <xref:System.Windows.Forms.DragDropEffects> sabit listesi. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    >  Kendi tanımlayabilirsiniz <xref:System.Windows.Forms.DataFormats> kendi nesnesi olarak belirterek <xref:System.Object> parametresinin <xref:System.Windows.Forms.DataObject.SetData%2A> yöntemi. Bunu yaparken belirtilen bir nesne seri hale getirilebilir olduğunu denetleyin. Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.  
  
3. İçinde <xref:System.Windows.Forms.Control.DragDrop> burada açılan gerçekleşir, kullanımını denetlemek için olay <xref:System.Windows.Forms.DataObject.GetData%2A> sürüklenen verileri almak için yöntemi. Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     Aşağıdaki örnekte bir <xref:System.Windows.Forms.TextBox> (açılan gerçekleşeceği için) sürüklenen denetimi bir denetimdir. Kod kümeleri <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.TextBox> sürüklenen verilere eşit denetim.  
  
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
    >  Ayrıca, çalışabilirsiniz <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> özelliğine bağlı olarak tuşları basılı sürükle ve bırak işlemi sırasında böylece bazı efektler ortaya (örneğin, CTRL tuşuna basıldığında sürüklenen veri kopyalamak için standart olmadığı).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Panoya veri ekleme](how-to-add-data-to-the-clipboard.md)
- [Nasıl yapılır: Panodan veri alma](how-to-retrieve-data-from-the-clipboard.md)
- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
