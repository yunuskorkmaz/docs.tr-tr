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
ms.openlocfilehash: 95ba276f3b2682d5b5bcaaa49916e856eb580632
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537693"
---
# <a name="how-to-set-indents-hanging-indents-and-bulleted-paragraphs-with-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Girintileri, Asılı Girintileri ve Madde İşaretli Paragrafları Ayarlama
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi görüntülediği metni biçimlendirme için birçok seçenek vardır. Ayarlayarak seçili paragrafları madde işaretli listeler olarak biçimlendirebilirsiniz <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliği. Aynı zamanda <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A>, <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A>, ve <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> paragrafları sol ve sağ kenarlarının denetimi ve diğer satırlar metnin sol kenarı göre girinti ayarlamak için özellikleri.  
  
### <a name="to-format-a-paragraph-as-a-bulleted-list"></a>Madde işaretli bir liste olarak bir paragraf biçimlendirme  
  
1.  Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliğine `true`.  
  
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
  
1.  Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionIndent%2A> denetimi sol kenarı ve metnin sol köşesinde arasındaki piksel cinsinden uzaklık temsil eden bir tamsayı özelliği.  
  
2.  Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> paragraf içindeki metnin ilk satırın sol kenarı ve sonraki satırların aynı paragrafta sol kenarı arasındaki piksel cinsinden uzaklığı temsil eden bir tamsayı özelliği. Değeri <xref:System.Windows.Forms.RichTextBox.SelectionHangingIndent%2A> özelliği yalnızca uygulanır altına ilk satır Sarmalanan bir paragraf satırlarında.  
  
3.  Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionRightIndent%2A> denetimin sağ kenarı ve metnin sağ köşesine arasındaki piksel cinsinden uzaklığı temsil eden bir tamsayı özelliği.  
  
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
    >  Bu özellikleri seçili metin ve sonra geçerli ekleme noktasını yazılan metni içeren tüm paragrafları etkiler. Örneğin, bir kullanıcı bir paragraf içinde bir sözcük seçer ve girinti ayarlar, yeni ayarları bu sözcüğünü içeren tüm paragrafı ve ayrıca daha sonra seçili paragrafın girilen paragrafları uygulanır. Program aracılığıyla metni seçme hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.TextBoxBase.Select%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox Denetimi](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
