---
title: "İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe2b54123e117f21f3bda7bc78bc9c5b45fc9ae3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>İzlenecek yol: Windows Forms'ta Sürükle ve Bırak İşlemi Gerçekleştirme
Windows tabanlı uygulamalar içinde sürükle ve bırak işlemleri için bir dizi olay, özellikle işlemelidir <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, ve <xref:System.Windows.Forms.Control.DragDrop> olaylar. Kullanılabilir bilgilerle olay bağımsız değişkenleri bu olayların çalışarak sürükle ve bırak işlemleri kolayca kolaylaştırabilir.  
  
## <a name="dragging-data"></a>Veriler sürükleme  
 Tüm sürükle ve bırak işlemleri sürükleyerek ile başlar. Sürükleme işlemi başladığında, toplanacak veri sağlayan İşlevler uygulanan <xref:System.Windows.Forms.Control.DoDragDrop%2A> yöntemi.  
  
 Aşağıdaki örnekte, <xref:System.Windows.Forms.Control.MouseDown> olay en sezgisel olduğundan sürükleme işlemi başlatmak için kullanılır (fare düğmesini basılı çoğu sürükle ve bırak işlemleri başlamak). Bununla birlikte, herhangi bir olayın bir Sürükle ve bırak yordamı başlatmak için kullanılabilecek unutmayın.  
  
> [!NOTE]
>  Bazı denetimler özel sürükleme özgü olaylar sahiptir. <xref:System.Windows.Forms.ListView> Ve <xref:System.Windows.Forms.TreeView> denetimleri, örneğin, sahip bir <xref:System.Windows.Forms.TreeView.ItemDrag> olay.  
  
#### <a name="to-start-a-drag-operation"></a>Sürükleme işlemi başlatmak için  
  
1.  İçinde <xref:System.Windows.Forms.Control.MouseDown> yere sürükleyin başlayacak, kullanımını denetlemek için olay `DoDragDrop` sürüklenen için veri kümesi için yöntem ve sürükleyerek izin verilen etkili olacaktır. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Data%2A> ve <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Aşağıdaki örnek, bir sürükleme işlemi başlatmak gösterilmiştir. Sürükle başladığı denetimi bir <xref:System.Windows.Forms.Button> denetimi sürüklenen veri olduğu temsil eden dize <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.Button> denetim ve izin verilen efektleri kopyalama veya taşıma.  
  
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
    >  Herhangi bir veriyi bir parametresi olarak kullanılabilir `DoDragDrop` yöntemi; yukarıdaki örnekte <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.Button> denetimi (yerine, kodlama sabit bir değer veya bir veri kümesinden veri alma) kullanıldı özelliği ilişkili nedeniyle gelen sürüklenen konumu ( <xref:System.Windows.Forms.Button> denetim). Windows tabanlı uygulamalarınıza sürükle ve bırak işlemleri içerecek şekilde bunu göz önünde bulundurun.  
  
 Sürükleme işlemi etkin durumdayken işleyebilir <xref:System.Windows.Forms.Control.QueryContinueDrag> "izin isteyen" olay sürükleme işlemi devam etmek için sistemi. Bu yöntem işlenirken, ayrıca, genişletme gibi sürükleme işlemi üzerinde bir etkisi olmaz yöntemleri çağırmak uygun bir noktasına olmasından bir <xref:System.Windows.Forms.TreeNode> içinde bir <xref:System.Windows.Forms.TreeView> zaman imleç üzerinde gezinen denetim.  
  
## <a name="dropping-data"></a>Veri bırakma  
 Bir Windows Form veya denetim bir konumdan veri sürükleme başlamıştır sonra doğal olarak herhangi bir yerde bırakma isteyeceksiniz. Bir form veya veri bırakma için doğru yapılandırıldığını denetim alanı kestiği yapıldığında imleci değişir. Windows Form veya denetim içinde herhangi bir alan ayarlayarak bırakılan verileri kabul etmek için yapılan <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği ve işleme <xref:System.Windows.Forms.Control.DragEnter> ve <xref:System.Windows.Forms.Control.DragDrop> olaylar.  
  
#### <a name="to-perform-a-drop"></a>Bir açılan gerçekleştirmek için  
  
1.  Ayarlama <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliğinin true.  
  
2.  İçinde `DragEnter` burada açılan oluşur, denetim olayı sürüklenen verileri kabul edilebilir bir türde olduğundan emin olun (Bu durumda, <xref:System.Windows.Forms.Control.Text%2A>). Kod sonra açılan bir değere oluştuğunda olacağını etkisi ayarlar <xref:System.Windows.Forms.DragDropEffects> numaralandırması. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    >  Kendi tanımlayabilirsiniz <xref:System.Windows.Forms.DataFormats> kendi nesnesi olarak belirterek <xref:System.Object> parametresinin <xref:System.Windows.Forms.DataObject.SetData%2A> yöntemi. Emin, bunu yaparken belirtilen nesne seri hale getirilebilir olduğundan emin olun. Daha fazla bilgi için bkz. <xref:System.Runtime.Serialization.ISerializable>.  
  
3.  İçinde <xref:System.Windows.Forms.Control.DragDrop> burada açılan oluşur, kullanımını denetlemek için olay <xref:System.Windows.Forms.DataObject.GetData%2A> sürüklenen veri alma yöntemi. Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     Aşağıdaki örnekte bir <xref:System.Windows.Forms.TextBox> denetimidir (açılan gerçekleşeceği için) sürüklenen denetim. Kod kümeleri <xref:System.Windows.Forms.Control.Text%2A> özelliği <xref:System.Windows.Forms.TextBox> sürüklenen veri eşit denetim.  
  
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
    >  Ayrıca, birlikte çalışabilir <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> özelliği, bağlı olarak tuşlarını basılı sürükle ve bırak işlemi sırasında bazı efektler gerçekleşmesini (örneğin, CTRL tuşuna basıldığında sürüklenen verileri kopyalamak için standart öyledir).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: panoya veri ekleme](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Nasıl yapılır: panodan veri alma](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Sürükle ve bırak işlemleri ve Pano desteği](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
