---
title: "Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme"
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
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8de64ac28fe57e3c448c671859053fad4aae3b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme
Windows Forms zaman <xref:System.Windows.Forms.TextBox> denetim odağı ilk alır, varolan herhangi bir metni sola metin kutusu içinde varsayılan ekleme. Kullanıcı klavye veya fare ekleme noktasını taşıyabilirsiniz. Metin kutusu kaybeder ve odak yeniden kazanabilmesi ekleme noktasını yerlerde kullanıcı son onu yerleştirilen olacaktır.  
  
 Bazı durumlarda, bu davranış kullanıcıya disconcerting olabilir. Word uygulaması işleme, kullanıcı sonra varolan herhangi bir metni görünmesi yeni karakterler bekleyebilirsiniz. Bir veri girişi uygulamasında kullanıcı varolan bir girişi değiştirmek için yeni karakterler bekleyebilirsiniz. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Ve <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özellikleri amacınıza uygun olarak davranışını değiştirmek etkinleştirin.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>TextBox denetiminde ekleme noktasını denetlemek için  
  
1.  Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> uygun bir değere özelliği. Ekleme noktasını ilk karakterin hemen soluna sıfır yerleştirir.  
  
2.  (İsteğe bağlı) Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğu.  
  
     Aşağıdaki kod ekleme noktasını her zaman 0 olarak döndürür. `TextBox1_Enter` Olay işleyicisi bağlı denetimi; daha fazla bilgi için bkz: [Windows Forms'ta olay işleyicileri oluşturma](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
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
 <xref:System.Windows.Forms.TextBox> Ekleme noktasını, varsayılan olarak yeni bir form yalnızca IF görülebilir <xref:System.Windows.Forms.TextBox> denetimidir sekme sırasındaki ilk. Ekleme noktasını yalnızca size Aksi takdirde görünür <xref:System.Windows.Forms.TextBox> klavye veya fare odaktaki.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Metin kutusu noktasını yeni bir form üzerinde varsayılan olarak görünür yapmak için  
  
-   Ayarlama <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.Control.TabIndex%2A> özelliğine `0`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox Denetimi](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
