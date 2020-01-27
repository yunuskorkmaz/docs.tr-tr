---
title: TextBox Denetimine Genel Bakış
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
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742799"
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox Denetimine Genel Bakış (Windows Forms)
Windows Forms metin kutuları, kullanıcıdan giriş almak veya metin göstermek için kullanılır. <xref:System.Windows.Forms.TextBox> denetimi genellikle düzenlenebilir metin için kullanılır, ancak salt okunabilir hale getirilebilir. Metin kutuları birden çok satır görüntüleyebilir, metni denetimin boyutuna kaydırabilirler ve temel biçimlendirme ekleyebilir. <xref:System.Windows.Forms.TextBox> denetimi, görüntülenmiş veya denetime girilen metin için tek bir biçim stili sağlar. Birden çok biçimli metin türünü göstermek için <xref:System.Windows.Forms.RichTextBox> denetimini kullanın. Daha fazla bilgi için bkz. [RichTextBox denetimine genel bakış](richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>TextBox denetimiyle çalışma  
 Denetim tarafından görünen metin, <xref:System.Windows.Forms.TextBox.Text%2A> özelliğinde bulunur. Varsayılan olarak, bir metin kutusuna en fazla 2048 karakter girebilirsiniz. <xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğini `true`olarak ayarlarsanız, 32 KB 'a kadar metin girebilirsiniz. <xref:System.Windows.Forms.TextBox.Text%2A> özelliği, tasarım zamanında Özellikler penceresiyle, koddaki çalışma zamanında veya çalışma zamanında Kullanıcı girişiyle ayarlanabilir. Bir metin kutusunun geçerli içeriği, <xref:System.Windows.Forms.TextBox.Text%2A> özelliği okunarak çalışma zamanında alınabilir.  
  
 Aşağıdaki kod örneği, çalışma zamanında denetimindeki metni ayarlar. `InitializeMyControl` yordamı otomatik olarak yürütülmez; çağrılması gerekir.  
  
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
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
