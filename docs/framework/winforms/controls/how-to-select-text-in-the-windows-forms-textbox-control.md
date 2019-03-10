---
title: 'Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç'
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
ms.openlocfilehash: acb5434911b569b0a663f47ec5de04db13b436d3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722298"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç
Windows Forms'ta program aracılığıyla metin seçebilirsiniz <xref:System.Windows.Forms.TextBox> denetimi. Örneğin, belirli bir dizenin metnini arayan bir işlev oluşturma, görsel olarak bulunan dizenin konumu okuyucu uyarı metni seçebilirsiniz.  
  
### <a name="to-select-text-programmatically"></a>Program aracılığıyla metni seçmek için  
  
1.  Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özellik başına seçmek istediğiniz metin.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Özelliği metin dizesinin içinde ekleme noktasını gösteren bir sayı ise, en soldaki konumu 0 ile oluşturuluyor. Varsa <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliği ayarlanmışsa değerine eşit veya bundan karakter sayısından metin kutusuna, ekleme noktasının son karakterden sonra yerleştirilir.  
  
2.  Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğu.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Noktasını genişliğini ayarlar sayısal bir değer bir özelliktir. Ayarı <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> , seçilecek karakter sayısı 0 neden olan daha büyük bir sayı geçerli ekleme noktasından başlatılıyor.  
  
3.  (İsteğe bağlı) Seçili metni aracılığıyla erişim <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> özelliği.  
  
     Bir metin içeriğini seçer aşağıdaki kodu kutusunu denetimin <xref:System.Windows.Forms.Control.Enter> olayı oluşur. Bu örnekte, metin kutusu için bir değer olup olmadığını denetler <xref:System.Windows.Forms.TextBox.Text%2A> olmayan özellik `null` ya da boş bir dize. Geçerli metin metin kutusundaki metin kutusu odağı aldığında seçilir. `TextBox1_Enter` Olay işleyicisi bağlı denetime; daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms için çalışma zamanında olay işleyicileri oluşturma](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Bu örnekte test etmek için metin kutusu odağı sahip oluncaya kadar SEKME tuşuna basın. Metin kutusuna tıklayın, metin seçilmemiş demektir.  
  
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
- [Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt okunur metin kutusu oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Dizeye tırnak işaretleri koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde birden çok satır görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
