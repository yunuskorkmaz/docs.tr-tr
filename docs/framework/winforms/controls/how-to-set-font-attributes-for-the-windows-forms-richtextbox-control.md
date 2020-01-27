---
title: RichTextBox denetimi için yazı tipi özniteliklerini ayarlama
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
ms.openlocfilehash: f27256c155223df576ee3c42e6bf65270c870b0f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744858"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, görüntülediği metni biçimlendirmek için çeşitli seçeneklere sahiptir. <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> özelliğini kullanarak seçili karakterleri kalın, altı çizili veya italik yapabilirsiniz. Bu özelliği, seçilen karakterlerin boyutunu ve yazı tipini değiştirmek için de kullanabilirsiniz. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> özelliği, seçilen karakterlerin rengini değiştirmenize olanak sağlar.  
  
### <a name="to-change-the-appearance-of-characters"></a>Karakterlerin görünüşünü değiştirmek için  
  
1. <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> özelliğini uygun bir yazı tipine ayarlayın.  
  
     Kullanıcıların bir uygulamadaki yazı tipi ailesini, boyutunu ve yazı tipini ayarlayacağından, genellikle <xref:System.Windows.Forms.FontDialog> bileşenini kullanırsınız. Genel bakış için bkz. [FontDialog bileşenine genel bakış](fontdialog-component-overview-windows-forms.md).  
  
2. <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> özelliğini uygun bir renk olarak ayarlayın.  
  
     Kullanıcıların bir uygulamada renk ayarlaması için, genellikle <xref:System.Windows.Forms.ColorDialog> bileşenini kullanırsınız. Genel bakış için bkz. [ColorDialog Bileşenine Genel Bakış](colordialog-component-overview-windows-forms.md).  
  
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
    > Bu özellikler yalnızca seçili metni etkiler veya hiçbir metin seçilmezse, ekleme noktasının geçerli konumuna yazılan metni. Program aracılığıyla metin seçme hakkında bilgi için bkz. <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
