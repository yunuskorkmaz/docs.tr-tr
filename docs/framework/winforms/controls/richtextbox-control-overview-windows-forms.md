---
title: RichTextBox Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0d40967d97622b23e9dcb07e861f190327e6baba
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742401"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi, biçimlendirme ile metin görüntülemek, girmek ve işlemek için kullanılır. <xref:System.Windows.Forms.RichTextBox> denetimi <xref:System.Windows.Forms.TextBox> denetiminin yaptığı her şeyi yapar, ancak yazı tiplerini, renkleri ve bağlantıları da görüntüleyebilir; dosyadan metin ve katıştırılmış görüntüleri yükleme; ve belirtilen karakterleri bulur. <xref:System.Windows.Forms.RichTextBox> denetimi genellikle, Microsoft Word gibi Word işleme uygulamalarına benzer şekilde metin işleme ve görüntüleme özellikleri sağlamak için kullanılır. <xref:System.Windows.Forms.TextBox> denetimi gibi, <xref:System.Windows.Forms.RichTextBox> denetimi de kaydırma çubuklarını görüntüleyebilir; Ancak <xref:System.Windows.Forms.TextBox> denetiminin aksine, varsayılan ayarı hem yatay hem de dikey kaydırma çubuklarını gerektiği şekilde görüntülemektir ve ek kaydırma çubuğu ayarlarına sahiptir.  
  
## <a name="working-with-the-richtextbox-control"></a>RichTextBox denetimiyle çalışma  
 <xref:System.Windows.Forms.TextBox> denetiminde olduğu gibi, görünen metin <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliği tarafından ayarlanır. <xref:System.Windows.Forms.RichTextBox> denetim, metni biçimlendirmek için çok sayıda özelliğe sahiptir. Bu özellikler hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms RichTextBox denetimi Için yazı tipi özniteliklerini ayarlama](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) ve [nasıl yapılır: Windows Forms RichTextBox denetimiyle girintileri, asılı girintileri ve madde işaretli paragrafları ayarlama](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Dosyaları değiştirmek için, <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> ve <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemleri düz metin, Unicode düz metin ve zengin metin biçimi (RTF) gibi birden çok dosya biçimini görüntüleyebilir ve yazabilir. Olası dosya biçimleri <xref:System.Windows.Forms.RichTextBoxStreamType>listelenmiştir. Metin veya belirli karakter dizelerini bulmak için <xref:System.Windows.Forms.RichTextBox.Find%2A> yöntemini kullanabilirsiniz.  
  
 Ayrıca, <xref:System.Windows.Forms.RichTextBox.LinkClicked> olayını işlemek için <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> özelliğini `true` ve kod yazarak, Web stili bağlantıları için <xref:System.Windows.Forms.RichTextBox> denetimi de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms RichTextBox denetimiyle Web stili bağlantıları görüntüleme](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Kullanıcının denetimdeki metnin bir kısmını veya tamamını <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> özelliğini `true`olarak ayarlayarak engelleyebilirsiniz.  
  
 <xref:System.Windows.Forms.TextBoxBase.Undo%2A> ve <xref:System.Windows.Forms.RichTextBox.Redo%2A> yöntemlerini çağırarak <xref:System.Windows.Forms.RichTextBox> denetiminde birçok düzenleme işlemini geri alabilir ve yineleyebilirsiniz. <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> yöntemi, kullanıcının geri aldığı son işlemin denetime yeniden uygulanabilir olup olmadığını belirlemenizi sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
