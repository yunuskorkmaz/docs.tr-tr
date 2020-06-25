---
title: 'İzlenecek yol: sürükle ve bırak işlemi gerçekleştirme'
description: En özellikle DragEnter, DragLeave ve DragDrop olaylarını bir dizi olayı işleyerek Windows Forms bir sürükle ve bırak işlemi gerçekleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 83bfda875e2fdec3981bbcb8f8f7be00db342440
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325822"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme
Windows tabanlı uygulamalarda sürükle ve bırak işlemleri gerçekleştirmek için, bir dizi olayı, özellikle, <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragLeave> ve olaylarını işlemeniz gerekir <xref:System.Windows.Forms.Control.DragDrop> . Bu olayların olay bağımsız değişkenlerinde bulunan bilgilerle çalışarak, sürükle ve bırak işlemlerini kolayca kolaylaştırabilirsiniz.  
  
## <a name="dragging-data"></a>Verileri sürükleme  
 Tüm sürükle ve bırak işlemleri sürüklemeye başlar. Sürükleme başladığında verilerin toplanmasına olanak sağlayan işlevsellik, yöntemi içinde uygulanır <xref:System.Windows.Forms.Control.DoDragDrop%2A> .  
  
 Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> en sezgisel olan (sürükleme ve bırakma eylemleri fare düğmesi basılı olarak başlar), sürükleme işlemini başlatmak için olay kullanılır. Ancak, bir sürükle ve bırak yordamını başlatmak için herhangi bir olayın kullanılabileceğini unutmayın.  
  
> [!NOTE]
> Belirli denetimlerin özel sürüklemeye özgü olayları vardır. <xref:System.Windows.Forms.ListView>Ve <xref:System.Windows.Forms.TreeView> denetimleri, örneğin, bir <xref:System.Windows.Forms.TreeView.ItemDrag> olayıdır.  
  
#### <a name="to-start-a-drag-operation"></a>Bir sürükleme işlemini başlatmak için  
  
1. <xref:System.Windows.Forms.Control.MouseDown>Sürüklediğiniz denetimin başlayacağı olayda, `DoDragDrop` verileri sürüklenecektir ve izin verilen efekt sürüklemeye sahip olacak şekilde ayarlamak için yöntemini kullanın. Daha fazla bilgi için <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> bölümlerine bakın.  
  
     Aşağıdaki örnek, bir sürükleme işleminin nasıl başlatılacağı gösterilmektedir. Sürükleme işleminin başladığı denetim bir <xref:System.Windows.Forms.Button> denetimdir, sürüklediğiniz veri denetimin özelliğini temsil eden dizedir <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button> ve izin verilen etkiler kopyalama veya taşıma olur.  
  
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
    > Herhangi bir veri, yöntemde parametre olarak kullanılabilir `DoDragDrop` ; Yukarıdaki örnekte <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.Button> denetimin özelliği kullanılmıştır (bir değer kodlanması veya bir veri kümesinden veri almak yerine), özellik sürüklediğiniz konumla ilişkili olduğundan ( <xref:System.Windows.Forms.Button> Denetim). Windows tabanlı uygulamalarınıza sürükle ve bırak işlemleri eklediğinizde bunu göz önünde bulundurun.  
  
 Bir sürükleme işlemi etkin olsa da, <xref:System.Windows.Forms.Control.QueryContinueDrag> sürükleme işlemine devam etmek için sistemin "izin sorar" olayını işleyebilirsiniz. Bu yöntemi işlerken, <xref:System.Windows.Forms.TreeNode> imleç üzerine geldiğinde bir denetimde genişletme gibi, sürükleme işleminde bir etkisi olan yöntemleri çağırdığınızda de uygun bir nokta vardır <xref:System.Windows.Forms.TreeView> .  
  
## <a name="dropping-data"></a>Verileri bırakma  
 Bir Windows formundaki veya denetimindeki bir konumdan veri sürüklemeye başladıktan sonra doğal olarak bir yere bırakmak istersiniz. İmleç, veri bırakma için doğru şekilde yapılandırılmış bir formun veya denetimin bir alanını aştığında değişecektir. Bir Windows form veya denetim içindeki herhangi bir alan, özelliği ayarlayarak ve olayları işleyerek bırakılan verileri kabul etmek için yapılabilir <xref:System.Windows.Forms.Control.AllowDrop%2A> <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> .  
  
#### <a name="to-perform-a-drop"></a>Bir bırakma işlemi gerçekleştirmek için  
  
1. <xref:System.Windows.Forms.Control.AllowDrop%2A>Özelliği true olarak ayarlayın.  
  
2. `DragEnter`Bırakma işleminin gerçekleşeceği denetim olayında, sürüklenen verilerin kabul edilebilir bir tür (Bu durumda) olduğundan emin olun <xref:System.Windows.Forms.Control.Text%2A> . Kod daha sonra, Numaralandırmadaki bir değere bırakma gerçekleştiğinde gerçekleşecek etkiyi ayarlar <xref:System.Windows.Forms.DragDropEffects> . Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > <xref:System.Windows.Forms.DataFormats>Yöntemin parametresi olarak kendi nesneniz belirterek kendi uygulamanızı tanımlayabilirsiniz <xref:System.Object> <xref:System.Windows.Forms.DataObject.SetData%2A> . Bunu yaparken, belirtilen nesnenin seri hale getirilebilir olduğundan emin olun. Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.  
  
3. <xref:System.Windows.Forms.Control.DragDrop>Bırakma işleminin gerçekleşeceği denetim olayında, <xref:System.Windows.Forms.DataObject.GetData%2A> sürüklediğiniz verileri almak için yöntemini kullanın. Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     Aşağıdaki örnekte, bir <xref:System.Windows.Forms.TextBox> Denetim Sürüklenmekte olan denetimdir (bırakma gerçekleşir). Kod, <xref:System.Windows.Forms.Control.Text%2A> <xref:System.Windows.Forms.TextBox> denetimin özelliğini sürüklenen verilere eşit olarak ayarlar.  
  
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
    > Ayrıca, özelliği ile birlikte çalışarak, <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> sürükle ve bırak işlemi sırasında tuşlara bağlı olarak belirli etkileri oluşur (örneğin, CTRL tuşuna basıldığında sürüklenen verileri kopyalamak standart olur).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Panoya Veri Ekleme](how-to-add-data-to-the-clipboard.md)
- [Nasıl yapılır: Panodan Veri Alma](how-to-retrieve-data-from-the-clipboard.md)
- [Sürükle ve Bırak İşlemleri ve Pano Desteği](drag-and-drop-operations-and-clipboard-support.md)
