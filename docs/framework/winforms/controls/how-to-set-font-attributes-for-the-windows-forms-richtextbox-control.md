---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama'
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
ms.openlocfilehash: 7c4c9362bb5a32bd8d5afc2b1edeb935d505fd19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533649"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi görüntülediği metni biçimlendirme için birçok seçenek vardır. Seçilen karakterleri kalın, altı çizili ya da italik kullanarak yapabileceğiniz <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> özelliği. Bu özellik, boyutunu ve Seçilen karakterlerin yazı tipini değiştirmek için de kullanabilirsiniz. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Özelliği, seçilen karakterleri rengini değiştirmek sağlar.  
  
### <a name="to-change-the-appearance-of-characters"></a>Karakterlerin görünümünü değiştirmek için  
  
1.  Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> uygun bir font özelliği.  
  
     Yazı tipi ailesi, boyutu ve yazı tipi bir uygulamada ayarlamak kullanıcıların etkinleştirmek için genellikle kullanacağınız <xref:System.Windows.Forms.FontDialog> bileşeni. Genel bir bakış için bkz: [FontDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/fontdialog-component-overview-windows-forms.md).  
  
2.  Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> uygun bir renk özelliğine.  
  
     Bir uygulamada rengini ayarlamak kullanıcıların etkinleştirmek için genellikle kullanacağınız <xref:System.Windows.Forms.ColorDialog> bileşeni. Genel bir bakış için bkz: [ColorDialog bileşenine genel bakış](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md).  
  
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
    >  Bu özellikler, yalnızca seçili metni etkiler veya metin seçtiyseniz olan metin ekleme noktasını geçerli konumda belirtilmiş. Program aracılığıyla metni seçme hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox Denetimi](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
