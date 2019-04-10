---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Sürükleyip Bırakma İşlemlerini Etkinleştirme'
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
ms.openlocfilehash: 5c60fe411fcbf6257c8aaacf1f7400c11c150ddc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310284"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Sürükleyip Bırakma İşlemlerini Etkinleştirme
Windows Forms ile sürükle ve bırak işlemleri <xref:System.Windows.Forms.RichTextBox> denetim işleyerek yapılır <xref:System.Windows.Forms.RichTextBox.DragEnter> ve <xref:System.Windows.Forms.RichTextBox.DragDrop> olayları. Bu nedenle, sürükle ve bırak işlemleri ile son derece basit <xref:System.Windows.Forms.RichTextBox> denetimi.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>RichTextBox denetiminde sürükleme işlemleri etkinleştirmek için  
  
1. Ayarlama <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> özelliği <xref:System.Windows.Forms.RichTextBox> denetimini `true`.  
  
2. Olay işleyicisinde kodu yazma <xref:System.Windows.Forms.RichTextBox.DragEnter> olay. Kullanım bir `if` deyimini sürüklenen verilerin (Bu durumda, metin) kabul edilebilir bir tür olduğundan emin olun. <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> Özelliği herhangi bir değere ayarlanabilir <xref:System.Windows.Forms.DragDropEffects> sabit listesi.  
  
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
  
     (Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
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
  
3. İşlemek için kod yazma <xref:System.Windows.Forms.RichTextBox.DragDrop> olay. Kullanım <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> sürüklenen verileri almak için yöntemi.  
  
     Kod aşağıdaki örnekte ayarlar <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliği <xref:System.Windows.Forms.RichTextBox> sürüklenen verilere eşit denetim. Zaten varsa metinde <xref:System.Windows.Forms.RichTextBox> sürüklenen metin denetimi ekleme noktasına eklenir.  
  
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
  
     (Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>Sürükle ve bırak işlevi uygulamanızı test etmek için  
  
1. Kaydet ve uygulamanızı oluşturun. Çalışır durumdayken WordPad çalıştırın.  
  
     WordPad sürükle ve bırak işlemleri sağlayan Windows tarafından yüklenen bir metin düzenleyicidir. Tıklayarak erişilebilir durumda **Başlat** düğmesi, seçerek **çalıştırmak**yazarak `WordPad` metin kutusunda **çalıştırmak** iletişim kutusunu ve ardından  **Tamam**.  
  
2. WordPad açıldıktan sonra bir metin dizesi yazın. Fareyi kullanarak, metni seçin ve ardından seçili metin üzerine sürükleyin <xref:System.Windows.Forms.RichTextBox> Windows uygulamanızda denetimi.  
  
     Fareyi üzerine geldiğinizde dikkat <xref:System.Windows.Forms.RichTextBox> denetimi (ve sonuç olarak, yükseltme <xref:System.Windows.Forms.RichTextBox.DragEnter> olay), fare işaretçisini değişiklikleri ve seçilen metne bırakabilirsiniz <xref:System.Windows.Forms.RichTextBox> denetimi.  
  
     Fare düğmesini bıraktığınızda, seçili metni bırakılır (diğer bir deyişle, <xref:System.Windows.Forms.RichTextBox.DragDrop> olayı) ve içinde eklenen <xref:System.Windows.Forms.RichTextBox> denetimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox>
- [Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'ta Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
