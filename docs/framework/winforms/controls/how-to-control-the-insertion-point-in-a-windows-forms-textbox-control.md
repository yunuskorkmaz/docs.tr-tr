---
title: 'Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme'
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
ms.openlocfilehash: 1fa6e8a3642086f81d0a62502d801ec6ade9b3d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110722"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme
Bir Windows Forms olduğunda <xref:System.Windows.Forms.TextBox> denetim ilk odağı aldığında, varolan herhangi bir metni sola metin kutusu içinde varsayılan ekleme. Kullanıcı, klavye veya fare ile ekleme noktasını taşıyabilirsiniz. Metin kutusu kaybeder ve ardından odak kazandıktan, ekleme noktasını yerde kullanıcı son uygulanan olacaktır.  
  
 Bazı durumlarda, bu davranış kullanıcıya disconcerting olabilir. Kullanıcı, bir sözcükteki uygulama işleme, sonra var olan tüm metin görüntülenecek yeni karakter bekleyebilirsiniz. Bir veri giriş uygulaması, kullanıcının herhangi bir mevcut giriş değiştirmek için yeni karakter bekleyebilirsiniz. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Ve <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özellikler amacınıza uygun davranışını değiştirmek etkinleştirir.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>TextBox denetiminde ekleme noktasını denetlemek için  
  
1.  Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliğini uygun bir değer. Sıfır, ekleme noktasını ilk karakterin hemen soluna yerleştirir.  
  
2.  (İsteğe bağlı) Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğu.  
  
     Aşağıdaki kod, her zaman 0 olarak ekleme noktasını döndürür. `TextBox1_Enter` Olay işleyicisi bağlı denetime; daha fazla bilgi için bkz: [Windows Forms'ta olay işleyicileri oluşturma](../creating-event-handlers-in-windows-forms.md).  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a>Ekleme noktasını varsayılan olarak görünür hale getirme  
 <xref:System.Windows.Forms.TextBox> Noktasını, varsayılan olarak yeni bir form yalnızca Eğer görülebilir <xref:System.Windows.Forms.TextBox> denetimidir sekme sırasının ilk. Yalnızca size, aksi durumda, ekleme noktasını görünür <xref:System.Windows.Forms.TextBox> klavye veya fare odağı.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Metin kutusu ekleme noktasının varsayılan olarak yeni bir form üzerinde görünür yapmak için  
  
-   Ayarlama <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.Control.TabIndex%2A> özelliğini `0`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
