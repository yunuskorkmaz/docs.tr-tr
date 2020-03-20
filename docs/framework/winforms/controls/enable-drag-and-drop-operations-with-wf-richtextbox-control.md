---
title: RichTextBox Denetimi ile Sürükle ve Bırak Işlemlerini Etkinleştir
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
ms.openlocfilehash: 27e5c18598552c465ef17f5e58069bc10e401c09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182345"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Sürükleyip Bırakma İşlemlerini Etkinleştirme
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi ile sürükle ve bırak işlemleri <xref:System.Windows.Forms.RichTextBox.DragEnter> <xref:System.Windows.Forms.RichTextBox.DragDrop> ve olayları işleyerek yapılır. Bu nedenle, sürükle ve bırak işlemleri <xref:System.Windows.Forms.RichTextBox> denetim ile son derece basittir.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>RichTextBox denetiminde sürükleme işlemlerini etkinleştirmek için  
  
1. Denetimin <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> özelliğini <xref:System.Windows.Forms.RichTextBox> `true`' ye ayarlayın.  
  
2. <xref:System.Windows.Forms.RichTextBox.DragEnter> Olayın olay işleyicisi kodu yazın. Sürüklenen `if` verilerin kabul edilebilir bir türde olduğundan emin olmak için bir deyim kullanın (bu durumda, metin). Özellik <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> numaralandırmanın <xref:System.Windows.Forms.DragDropEffects> herhangi bir değerine ayarlanabilir.  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     (Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3. <xref:System.Windows.Forms.RichTextBox.DragDrop> Olayı işlemek için kod yazın. Sürüklenen <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> verileri almak için yöntemi kullanın.  
  
     Aşağıdaki örnekte, kod, <xref:System.Windows.Forms.RichTextBox.Text%2A> denetimin <xref:System.Windows.Forms.RichTextBox> özelliğini sürüklenen verilere eşit olarak ayarlar. <xref:System.Windows.Forms.RichTextBox> Denetimde zaten metin varsa, sürüklenen metin ekleme noktasına eklenir.  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragDrop  
       Dim i As Int16
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     (Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>Uygulamanızdaki sürükle ve bırak işlevini test etmek için  
  
1. Uygulamanızı kaydedin ve oluşturun. Çalışırken WordPad'i çalıştırın.  
  
     WordPad, Windows tarafından yüklenen ve sürükle ve bırak işlemlerine izin veren bir metin düzenleyicisidir. **Başlat** düğmesine tıklayarak, **Çalıştır'ı**seçerek `WordPad` , **Çalıştır** iletişim kutusunun metin kutusuna yazarak ve sonra **Tamam'ı**tıklatarak erişilebilir.  
  
2. WordPad açıldıktan sonra, içinde bir metin dizisi yazın. Fareyi kullanarak metni seçin ve ardından seçili metni <xref:System.Windows.Forms.RichTextBox> Windows uygulamanızdaki denetime sürükleyin.  
  
     Fareyi <xref:System.Windows.Forms.RichTextBox> denetime doğrulttuğa (ve dolayısıyla olayı <xref:System.Windows.Forms.RichTextBox.DragEnter> yükselttiğinde), fare işaretçisinin değiştiğine ve <xref:System.Windows.Forms.RichTextBox> seçili metni denetime bırakabileceğinize dikkat edin.  
  
     Fare düğmesini serbest bıraktığınızda, seçili metin bırakılır <xref:System.Windows.Forms.RichTextBox.DragDrop> (diğer bir deyişle, olay yükseltilir) ve denetim in <xref:System.Windows.Forms.RichTextBox> içine eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox>
- [Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'ta Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
