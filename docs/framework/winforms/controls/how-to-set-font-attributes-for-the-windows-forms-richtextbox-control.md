---
title: 'Nasıl yapılır: Windows Forms RichTextBox denetimi için yazı tipi özniteliklerini ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: 3793c33d378ee242656889434c7b29c415e9ec9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496211"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox denetimi için yazı tipi özniteliklerini ayarlama
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimin görüntülediği metni biçimlendirmek için çok sayıda seçeneği vardır. Seçilen karakterleri kalın, altı çizili veya italik kullanarak yapabileceğiniz <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> özelliği. Bu özellik, boyutunu ve yazı tipi seçili karakterleri değiştirmek için de kullanabilirsiniz. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Özelliği Seçilen karakterleri rengini değiştirmek etkinleştirir.  
  
### <a name="to-change-the-appearance-of-characters"></a>Karakter görünümünü değiştirmek için  
  
1.  Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> özelliğini uygun bir yazı tipi.  
  
     Yazı tipi ailesi, boyut ve yazı tipi uygulamada ayarlamak kullanıcıları etkinleştirmek için genellikle kullanacağınız <xref:System.Windows.Forms.FontDialog> bileşeni. Genel bakış için bkz. [FontDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).  
  
2.  Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> özelliğini uygun bir renk.  
  
     Bir uygulamada rengini ayarlamak kullanıcıları etkinleştirmek için genellikle kullanacağınız <xref:System.Windows.Forms.ColorDialog> bileşeni. Genel bakış için bkz. [ColorDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  Bu özellikler, yalnızca seçili metni etkiler veya hiç metin seçili değilse, metin olan ekleme noktasının geçerli konumda yazdınız. Program aracılığıyla metni seçme hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
