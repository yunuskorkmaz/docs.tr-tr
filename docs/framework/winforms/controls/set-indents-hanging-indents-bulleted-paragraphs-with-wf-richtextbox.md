---
title: RichTextBox denetimi ile girintileri, asılı girintileri ve madde Işaretli paragrafları ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], setting indents
- .rtf files [Windows Forms], formatting in RichTextBox control
- examples [Windows Forms], text boxes
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting indents and bullets
- text boxes [Windows Forms], bullets
ms.assetid: abfb40e6-5642-4691-8ec1-9d9ae91688dc
ms.openlocfilehash: 4dcd5691f328eac6d94675c50ed41a7d7cc36596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743008"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Girintileri, Asılı Girintileri ve Madde İşaretli Paragrafları Ayarlama
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, görüntülediği metni biçimlendirmek için çeşitli seçeneklere sahiptir. <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliğini ayarlayarak seçili paragrafları madde işaretli listeler olarak biçimlendirebilirsiniz. <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>ve <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> özelliklerini, denetimin sol ve sağ kenarlarına ve diğer metin satırlarının sol kenarına göre ayarlamak için de kullanabilirsiniz.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Paragrafı madde işaretli liste olarak biçimlendirmek için  
  
1. Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliğini `true`.  
  
    ```vb  
    RichTextBox1.SelectionBullet = True  
    ```  
  
    ```csharp  
    richTextBox1.SelectionBullet = true;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionBullet = true;  
    ```  
  
### <a name="to-indent-a-paragraph"></a>Paragrafı girintilemek için  
  
1. <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> özelliğini, denetimin sol kenarı ve metnin sol kenarı arasında piksel cinsinden uzaklığı temsil eden bir tamsayı olarak ayarlayın.  
  
2. <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> özelliğini, paragraftaki metnin sol kenarı ve aynı paragraftaki sonraki satırların sol kenarı arasındaki mesafeyi temsil eden bir tamsayı olarak ayarlayın. <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> özelliğinin değeri yalnızca, ilk satırın altına kaydırılmış olan bir paragraftaki satırlar için geçerlidir.  
  
3. <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> özelliğini, denetimin sağ kenarı ve metnin sağ kenarı arasındaki mesafeyi temsil eden bir tamsayı olarak ayarlayın.  
  
    ```vb  
    RichTextBox1.SelectionIndent = 8  
    RichTextBox1.SelectionHangingIndent = 3  
    RichTextBox1.SelectionRightIndent = 12  
    ```  
  
    ```csharp  
    richTextBox1.SelectionIndent = 8;  
    richTextBox1.SelectionHangingIndent = 3;  
    richTextBox1.SelectionRightIndent = 12;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionIndent = 8;  
    richTextBox1->SelectionHangingIndent = 3;  
    richTextBox1->SelectionRightIndent = 12;  
    ```  
  
    > [!NOTE]
    > Tüm bu özellikler, seçili metni içeren paragrafları ve ayrıca geçerli ekleme noktasının ardından yazılan metni etkiler. Örneğin, bir Kullanıcı bir paragraf içinde bir kelime seçip Girintiyi ayarladığında, yeni ayarlar, bu sözcüğü içeren tüm paragrafa ve ayrıca seçili paragraftan sonra daha sonra girilmiş olan paragraflara uygulanır. Program aracılığıyla metin seçme hakkında daha fazla bilgi için bkz. <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
