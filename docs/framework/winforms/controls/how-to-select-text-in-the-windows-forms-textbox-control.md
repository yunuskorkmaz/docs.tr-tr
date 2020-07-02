---
title: TextBox denetiminde metin Seç
description: Windows Forms metin kutusu denetiminde metni programlı olarak seçme hakkında bilgi edinin. Ayrıca, bulunan dizenin konumunun okuyucuyu görsel olarak uyarma hakkında bilgi edinin.
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
ms.openlocfilehash: b8fdaff76461c4d6766dfc6afaef5e814d982834
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621567"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme
Windows Forms denetiminde metin programlama yoluyla seçebilirsiniz <xref:System.Windows.Forms.TextBox> . Örneğin, belirli bir dize için metin arayan bir işlev oluşturursanız, bulunan dizenin konumunun okuyucuyu görsel olarak uyarmak için metni seçebilirsiniz.  
  
### <a name="to-select-text-programmatically"></a>Metni programlı olarak seçmek için  
  
1. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>Özelliğini seçmek istediğiniz metnin başlangıcına ayarlayın.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>Özelliği, ekleme noktasını metin dizesi içinde gösteren ve 0 ' ın en sol konumu olacak şekilde belirten bir sayıdır. Özellik, <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> metin kutusundaki karakter sayısına eşit veya ondan daha büyük bir değere ayarlandıysa, ekleme noktası son karakterden sonra yerleştirilir.  
  
2. <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>Özelliğini seçmek istediğiniz metnin uzunluğuna ayarlayın.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>Özelliği, ekleme noktasının genişliğini ayarlayan sayısal bir değerdir. <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>0 ' dan büyük bir sayıya ayarlamak, geçerli ekleme noktasından başlayarak, bu sayıda karakteri seçilmesine neden olur.  
  
3. Seçim Seçili metne özelliği aracılığıyla erişin <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> .  
  
     Aşağıdaki kod, denetimin olayı gerçekleştiğinde bir metin kutusunun içeriğini seçer <xref:System.Windows.Forms.Control.Enter> . Bu örnek, metin kutusunun <xref:System.Windows.Forms.TextBox.Text%2A> `null` veya boş bir dize olmayan özellik için bir değer olup olmadığını denetler. Metin kutusu odağı aldığında, metin kutusundaki geçerli metin seçilidir. `TextBox1_Enter`Olay işleyicisi denetime bağlanmalıdır; daha fazla bilgi için bkz. [nasıl yapılır: çalışma zamanında olay işleyicileri oluşturma Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
