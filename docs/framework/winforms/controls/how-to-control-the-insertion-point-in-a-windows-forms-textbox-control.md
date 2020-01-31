---
title: TextBox denetimindeki ekleme noktasını denetleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: fd4803820921f0c922a4ce885f809abee8fd4c6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742211"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme
Bir Windows Forms <xref:System.Windows.Forms.TextBox> denetimi ilk olarak odağı aldığında, metin kutusundaki varsayılan ekleme varolan metnin solunda yer alır. Kullanıcı ekleme noktasını klavye veya fare ile taşıyabilir. Metin kutusu kaybediyor ve sonra odağı kaybederse, ekleme noktası kullanıcının en son yerleştirmiş olduğu her yerde olur.  
  
 Bazı durumlarda, bu davranış kullanıcıya disconcerting olabilir. Bir sözcük işleme uygulamasında, Kullanıcı yeni karakterlerin mevcut metinden sonra görünmesini bekleyebilir. Bir veri girişi uygulamasında, Kullanıcı var olan herhangi bir girdinin yerine yeni karakterlerin değiştirilmesini bekleyebilir. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> ve <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özellikleri, davranışını amacınıza uyacak şekilde değiştirmenize olanak sağlar.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>TextBox denetiminde ekleme noktasını denetlemek için  
  
1. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliğini uygun bir değer olarak ayarlayın. Sıfır, ekleme noktasını ilk karakterin soluna hemen koyar.  
  
2. Seçim <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğuna ayarlayın.  
  
     Aşağıdaki kod her zaman ekleme noktasını 0 olarak döndürür. `TextBox1_Enter` olay işleyicisi denetime bağlanmalıdır; daha fazla bilgi için bkz. [Windows Forms olay Işleyicileri oluşturma](../creating-event-handlers-in-windows-forms.md).  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a>Ekleme noktasının varsayılan olarak görünmesini sağlama  
 <xref:System.Windows.Forms.TextBox> ekleme noktası, varsayılan olarak yeni bir formda görünür ve yalnızca <xref:System.Windows.Forms.TextBox> denetimi sekme sıraucundadır. Aksi halde, ekleme noktası yalnızca <xref:System.Windows.Forms.TextBox> klavye veya fare ile odağı verirseniz görünür.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Metin kutusu ekleme noktasını yeni bir formda varsayılan olarak görünür hale getirmek için  
  
- <xref:System.Windows.Forms.TextBox> denetiminin <xref:System.Windows.Forms.Control.TabIndex%2A> özelliğini `0`olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
