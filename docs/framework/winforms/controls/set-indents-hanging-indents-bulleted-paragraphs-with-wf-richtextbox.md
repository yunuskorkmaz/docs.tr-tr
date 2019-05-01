---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Girintileri, Asılı Girintileri ve Madde İşaretli Paragrafları Ayarlama'
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
ms.openlocfilehash: ef579923ac2b9ea9905a60000d93f6bfc90ed5b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903025"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Girintileri, Asılı Girintileri ve Madde İşaretli Paragrafları Ayarlama
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimin görüntülediği metni biçimlendirmek için çok sayıda seçeneği vardır. Madde işaretli listeler olarak ayarlayarak seçili paragrafların biçimlendirebilirsiniz <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliği. Ayrıca <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, ve <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> girinti paragraf sol ve sağ kenarları denetimi ve diğer satırlık bir metin ile sol kenarı göre ayarlamak için özellikler.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Paragraf madde işaretli liste olarak biçimlendirmek için  
  
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
  
### <a name="to-indent-a-paragraph"></a>Paragrafın girinti  
  
1. Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> metnin sol kenarı ile denetimin sol kenarı arasındaki piksel cinsinden uzaklık temsil eden bir tamsayı özelliği.  
  
2. Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> paragraf metni ilk satırının sol kenarı ve sonraki satırları aynı öğenin sol kenarı arasındaki piksel cinsinden uzaklık temsil eden bir tamsayı özelliği. Değerini <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> özelliği ilk satırı sarmalanmış bir paragraf satırlarında için yalnızca uygulanır.  
  
3. Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> metnin sağ kenarı ile denetimin sağ kenarı arasındaki piksel cinsinden uzaklığı temsil eden bir tamsayı özelliği.  
  
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
    >  Tüm bu özellikler, seçilen metin ve sonra geçerli ekleme noktasına yazdığınız metni içeren tüm paragrafları etkiler. Örneğin, bir kullanıcı bir paragraf içinde bir sözcük seçer ve ardından girintisini ayarlar yeni ayarları bu sözcüğü içeren tüm paragrafa ve daha sonra seçili paragrafın girilen paragraflara uygulanır. Program aracılığıyla metni seçme hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
