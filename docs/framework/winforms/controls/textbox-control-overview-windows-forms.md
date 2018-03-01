---
title: "TextBox Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d7312246c43157ca9cd6c7b41d2b110586721c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox Denetimine Genel Bakış (Windows Forms)
Windows Forms metin kutuları kullanıcıdan giriş almak veya metni görüntülemek için kullanılır. <xref:System.Windows.Forms.TextBox> Salt okunur ayrıca çalışabilmesine rağmen denetim düzenlenebilir metin için genellikle kullanılır. Metin kutuları birden çok satır görüntüleme, denetimin boyutunu metni kaydırma ve temel biçimlendirme ekleyin. <xref:System.Windows.Forms.TextBox> Denetimi görüntülenen veya denetime girilen metin için bir tek biçimi stili sağlar. Biçimlendirilmiş metin birden çok türde görüntülemek için kullanın <xref:System.Windows.Forms.RichTextBox> denetim. Daha fazla bilgi için bkz: [RichTextBox denetimine genel bakış](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>TextBox denetimi ile çalışma  
 Denetimi tarafından görüntülenen metni yer <xref:System.Windows.Forms.TextBox.Text%2A> özelliği. Varsayılan olarak, en çok 2048 karakter metin kutusuna girebilirsiniz. Ayarlarsanız <xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğine `true`, en çok 32 KB metin girin. <xref:System.Windows.Forms.TextBox.Text%2A> Özelliği, tasarım zamanında Özellikler penceresi ile çalışma zamanında kod veya kullanıcı girişi tarafından çalışma zamanında ayarlanabilir. Geçerli bir metin kutusunun içeriğini okuyarak çalışma zamanında alınabilir <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.  
  
 Aşağıdaki kod örneğinde metin denetiminde çalışma zamanında ayarlar. `InitializeMyControl` Yordamı değil yürütülecek otomatik olarak; çağrılması gerekir.  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextBox>  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox Denetimi](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
