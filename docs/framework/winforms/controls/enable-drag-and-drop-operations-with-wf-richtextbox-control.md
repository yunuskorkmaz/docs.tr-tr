---
title: RichTextBox denetimiyle sürükle ve bırak Işlemlerini etkinleştir
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
ms.openlocfilehash: 3c17560dee012912aea2938654f1dc4dc56e0725
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745813"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Sürükleyip Bırakma İşlemlerini Etkinleştirme
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi ile sürükleyip bırakma işlemleri, <xref:System.Windows.Forms.RichTextBox.DragEnter> ve <xref:System.Windows.Forms.RichTextBox.DragDrop> olayları işlenerek yapılır. Bu nedenle, sürükle ve bırak işlemleri <xref:System.Windows.Forms.RichTextBox> denetimiyle son derece basittir.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>RichTextBox denetiminde sürükleme işlemlerini etkinleştirmek için  
  
1. <xref:System.Windows.Forms.RichTextBox> denetiminin <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> özelliğini `true`olarak ayarlayın.  
  
2. <xref:System.Windows.Forms.RichTextBox.DragEnter> olayının olay işleyicisine kod yazın. Sürüklenen verilerin kabul edilebilir bir tür (Bu örnekte, metin) olduğundan emin olmak için bir `if` ifadesini kullanın. <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> özelliği <xref:System.Windows.Forms.DragDropEffects> Numaralandırmadaki herhangi bir değere ayarlanabilir.  
  
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
  
     (Görsel C# ve görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
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
  
3. <xref:System.Windows.Forms.RichTextBox.DragDrop> olayını işlemek için kod yazın. Sürüklediğiniz verileri almak için <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> yöntemini kullanın.  
  
     Aşağıdaki örnekte kod, <xref:System.Windows.Forms.RichTextBox> denetiminin <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliğini sürüklenen verilere eşit olarak ayarlar. <xref:System.Windows.Forms.RichTextBox> denetiminde zaten metin varsa, sürüklenen metin ekleme noktasına eklenir.  
  
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
  
     (Görsel C# ve görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
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
  
1. Uygulamanızı kaydedin ve oluşturun. Çalışırken WordPad ' i çalıştırın.  
  
     WordPad, sürükle ve bırak işlemlerine izin veren Windows tarafından yüklenen bir metin düzenleyicisidir. **Başlat** düğmesine tıklayıp **Çalıştır**' ı seçip **çalıştır** iletişim kutusunun metin kutusuna `WordPad` yazarak ve ardından **Tamam**' a tıklayarak erişilebilir.  
  
2. WordPad açıldıktan sonra içine bir metin dizesi yazın. Fareyi kullanarak metni seçin ve ardından seçili metni Windows uygulamanızda <xref:System.Windows.Forms.RichTextBox> denetimine sürükleyin.  
  
     Fareyi <xref:System.Windows.Forms.RichTextBox> denetimine işaret ettiğinizde (ve sonuç olarak <xref:System.Windows.Forms.RichTextBox.DragEnter> olayını yükselttiğinizde), fare işaretçisi değiştiğinde ve seçili metni <xref:System.Windows.Forms.RichTextBox> denetimine bırakabilirsiniz.  
  
     Fare düğmesini serbest bırakırsanız, seçilen metin bırakılır (yani <xref:System.Windows.Forms.RichTextBox.DragDrop> olayı tetiklenir) ve <xref:System.Windows.Forms.RichTextBox> denetimine eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox>
- [Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
