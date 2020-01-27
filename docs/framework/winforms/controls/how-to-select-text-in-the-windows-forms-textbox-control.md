---
title: TextBox denetiminde metin Seç
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 8a32e40f14ddae6f8ddcaa6d62337329df6fde26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745309"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme
Windows Forms <xref:System.Windows.Forms.TextBox> denetiminde metin programlama yoluyla seçebilirsiniz. Örneğin, belirli bir dize için metin arayan bir işlev oluşturursanız, bulunan dizenin konumunun okuyucuyu görsel olarak uyarmak için metni seçebilirsiniz.  
  
### <a name="to-select-text-programmatically"></a>Metni programlı olarak seçmek için  
  
1. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliğini seçmek istediğiniz metnin başlangıcına ayarlayın.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliği, ekleme noktasını metin dizesi içinde gösteren ve 0 ' ın en sol konumu olacak şekilde belirten bir sayıdır. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliği, metin kutusundaki karakter sayısına eşit veya daha büyük bir değere ayarlandıysa, ekleme noktası son karakterden sonra yerleştirilir.  
  
2. <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğuna ayarlayın.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliği, ekleme noktasının genişliğini ayarlayan sayısal bir değerdir. <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 0 ' dan büyük bir sayıya ayarlamak, geçerli ekleme noktasından başlayarak bu sayıda karakteri seçilmesine neden olur.  
  
3. Seçim Seçilen metne <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> özelliği aracılığıyla erişin.  
  
     Aşağıdaki kod, denetimin <xref:System.Windows.Forms.Control.Enter> olayı gerçekleştiğinde bir metin kutusunun içeriğini seçer. Bu örnek, metin kutusunun `null` veya boş bir dize olmayan <xref:System.Windows.Forms.TextBox.Text%2A> özelliği için bir değere sahip olup olmadığını denetler. Metin kutusu odağı aldığında, metin kutusundaki geçerli metin seçilidir. `TextBox1_Enter` olay işleyicisi denetime bağlanmalıdır; daha fazla bilgi için bkz. [nasıl yapılır: çalışma zamanında olay Işleyicileri oluşturma Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Bu örneği test etmek için, metin kutusu odaklanana kadar SEKME tuşuna basın. Metin kutusuna tıkladığınızda metin seçili değildir.  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
