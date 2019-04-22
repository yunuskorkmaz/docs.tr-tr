---
title: TextBox Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
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
ms.openlocfilehash: a91b67df1071c79707bb20a68efb4d5e6f083ae0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162143"
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox Denetimine Genel Bakış (Windows Forms)
Windows Forms metin kutuları, kullanıcıdan giriş almak veya metni görüntülemek için kullanılır. <xref:System.Windows.Forms.TextBox> Salt okunur ayrıca çalışabilmesine rağmen denetim düzenlenebilir metin için genellikle kullanılır. Metin kutuları, birden çok satır görüntüleme, denetimin boyutunu metni kaydırma ve temel biçimlendirmeler ekleyin. <xref:System.Windows.Forms.TextBox> Denetim görüntülenen veya denetimine girilen metni için bir tek biçim stili sağlar. Birden çok biçimli metin görüntülemek için kullanın <xref:System.Windows.Forms.RichTextBox> denetimi. Daha fazla bilgi için [RichTextBox denetimine genel bakış](richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>TextBox denetimi ile çalışma  
 Denetimi tarafından görüntülenen metni bulunan <xref:System.Windows.Forms.TextBox.Text%2A> özelliği. Varsayılan olarak, en çok 2048 karakter metin kutusuna girebilirsiniz. Ayarlarsanız <xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğini `true`, en fazla 32 KB metin girebilirsiniz. <xref:System.Windows.Forms.TextBox.Text%2A> Özelliği, çalışma zamanında çalışma zamanında kodu veya kullanıcı girişi ile Özellikler penceresinde, tasarım zamanında ayarlanabilir. Geçerli bir metin kutusunun içeriğini okuyarak çalışma zamanında alınabilir <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.  
  
 Aşağıdaki kod örneği, çalışma zamanında denetiminde metin ayarlar. `InitializeMyControl` Yordamı değil yürütülecek otomatik olarak; çağrılması gerekir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- [Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt okunur metin kutusu oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Dizeye tırnak işaretleri koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde birden çok satır görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
