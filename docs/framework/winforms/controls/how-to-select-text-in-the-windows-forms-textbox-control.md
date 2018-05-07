---
title: 'Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme'
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
ms.openlocfilehash: 8fd1cfb0764d16b86cd639d8266d1cceff874932
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme
Windows Forms'ta program aracılığıyla metin seçebilirsiniz <xref:System.Windows.Forms.TextBox> denetim. Örneğin, belirli bir dizenin metni arar işlevi oluşturursanız, görsel olarak bulunan dizesinin konumu okuyucu uyarı metne seçebilirsiniz.  
  
### <a name="to-select-text-programmatically"></a>Program aracılığıyla metni seçmek için  
  
1.  Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> seçmek istediğiniz metnin başına özelliğine.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Özellik metin dizesi içinde ekleme noktasını belirten bir sayı, 0 ile en solundaki konumu bırakılıyor. Varsa <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliği ayarlanmış değerine eşit veya daha fazla karakter metin kutusuna, ekleme noktasını son karakter sonra yerleştirilir.  
  
2.  Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğu.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Ekleme noktasını genişliğini ayarlar sayısal bir değeri bir özelliktir. Ayar <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> bu seçilecek karakter sayısı 0 neden olan daha büyük bir sayı geçerli ekleme noktasından başlatılıyor.  
  
3.  (İsteğe bağlı) Seçili metni üzerinden erişim <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> özelliği.  
  
     Bir metin içeriğini seçer aşağıdaki kodu kutusunu denetimin <xref:System.Windows.Forms.Control.Enter> olayı oluşur. Bu örnek metin kutusu için bir değer olup olmadığını denetler <xref:System.Windows.Forms.TextBox.Text%2A> olmayan özellik `null` ya da boş bir dize. Metin kutusu odağı aldığında, metin kutusuna geçerli metin seçilir. `TextBox1_Enter` Olay işleyicisi bağlı denetimi; daha fazla bilgi için bkz: [nasıl yapılır: olay işleyicileri oluşturma çalıştırma süresi için Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Bu örnekte test etmek için metin kutusunun odaklanmış kadar SEKME tuşuna basın. Metin kutusuna tıklayın, metin seçilmemiş demektir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox Denetimi](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
