---
title: RichTextBox Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 0827c1919597e9eb85bfa41721676008b76564d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902505"
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi görüntüleme, girerek ve biçimlendirme metin düzenleme için kullanılır. <xref:System.Windows.Forms.RichTextBox> Netimi her şeyi <xref:System.Windows.Forms.TextBox> denetimi yapar, ancak ayrıca yazı tiplerini, renkleri ve bağlantılar görüntülemek; metin ve görüntüleri gömülü bir dosyadan; yüklemek ve belirtilen karakter bulun. <xref:System.Windows.Forms.RichTextBox> Denetimi genellikle metin düzenlemesini sağlar ve Microsoft Word gibi bir sözcük işleme uygulamalarını benzer özellikleri görüntülemek için kullanılır. Gibi <xref:System.Windows.Forms.TextBox> denetimi <xref:System.Windows.Forms.RichTextBox> denetimi, kaydırma çubukları; görüntüleyebilir ancak tersine <xref:System.Windows.Forms.TextBox> denetimi, varsayılan ayardır yatay ve dikey kaydırma çubukları gerektiği şekilde görüntülenecek ve ek kaydırma çubuğu ayarları vardır.  
  
## <a name="working-with-the-richtextbox-control"></a>RichTextBox denetimi ile çalışma  
 Olduğu gibi <xref:System.Windows.Forms.TextBox> denetimi görüntülenen metni tarafından belirlenir <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliği. <xref:System.Windows.Forms.RichTextBox> Denetimi metni biçimlendirmek için çeşitli özelliklere sahiptir. Bu özellikler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms RichTextBox denetimi için yazı tipi özniteliklerini ayarlama](how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) ve [nasıl yapılır: Girintileri, asılı girintileri ve madde işaretli paragrafları Windows Forms RichTextBox denetimi ile ayarlanmış](set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Dosyaları işlemek için <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> ve <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemleri görüntüleyebilir ve düz metin, Unicode düz metin ve zengin metin biçimi (RTF) dahil olmak üzere birden çok dosya biçimleri yazma. Olası dosya biçimlerini listelenen <xref:System.Windows.Forms.RichTextBoxStreamType>. Kullanabileceğiniz <xref:System.Windows.Forms.RichTextBox.Find%2A> metin veya belirli karakter dizeleri bulmak için yöntemi.  
  
 Ayrıca bir <xref:System.Windows.Forms.RichTextBox> ayarlayarak Web stili bağlantılar denetimi <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> özelliğini `true` ve işlemek için kod yazma <xref:System.Windows.Forms.RichTextBox.LinkClicked> olay. Daha fazla bilgi için [nasıl yapılır: Windows ile Web stili bağlantılar görüntüleme Forms RichTextBox denetimi](how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Kullanıcının denetimdeki metnin tümünü veya ayarlayarak değiştirmelerine engelleyebilirsiniz <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> özelliğini `true`.  
  
 Geri Al ve Yinele çoğu düzenleme işlemleri bir <xref:System.Windows.Forms.RichTextBox> çağırarak denetim <xref:System.Windows.Forms.TextBoxBase.Undo%2A> ve <xref:System.Windows.Forms.RichTextBox.Redo%2A> yöntemleri. <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> Yöntemi denetime kullanıcı geri son işlemi uygulanabilir olup olmadığını belirlemenize olanak sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
