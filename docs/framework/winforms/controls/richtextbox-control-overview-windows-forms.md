---
title: RichTextBox Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- RichTextBox
helpviewer_keywords:
- RichTextBox control [Windows Forms], about RichTextBox control
- text boxes [Windows Forms], about text boxes
ms.assetid: 95081194-3dd4-4b84-9545-dd373e491eca
ms.openlocfilehash: 53c4cd41cf203886c93291debc7bca4f395f9698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="richtextbox-control-overview-windows-forms"></a>RichTextBox Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi görüntüleme, girme ve biçimlendirme metin düzenleme için kullanılır. <xref:System.Windows.Forms.RichTextBox> Denetimi her şeyi yapar <xref:System.Windows.Forms.TextBox> denetimi yapar, ancak bunu ayrıca yazı tiplerini, renk ve bağlantıları görüntüleyebilir; metin ve katıştırılmış görüntüler bir dosyadan; yüklemek ve belirtilen karakterleri bulmak. <xref:System.Windows.Forms.RichTextBox> Denetimi metin düzenleme sağlamak ve Microsoft Word gibi sözcük işleme uygulamaları benzer özellikleri görüntülemek için genellikle kullanılır. Gibi <xref:System.Windows.Forms.TextBox> denetimi <xref:System.Windows.Forms.RichTextBox> denetim kaydırma çubukları; görüntüleyebilir ancak aksine <xref:System.Windows.Forms.TextBox> denetimi, varsayılan ayardır yatay ve dikey kaydırma çubukları gerektiği gibi görüntülemek için ve ek scrollbar ayarlara sahip.  
  
## <a name="working-with-the-richtextbox-control"></a>RichTextBox denetimi ile çalışma  
 İle <xref:System.Windows.Forms.TextBox> denetim, görüntülenen metin tarafından belirlenir <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliği. <xref:System.Windows.Forms.RichTextBox> Denetimi metni biçimlendirmek için çeşitli özellikler vardır. Bu özellikler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms RichTextBox denetimi için yazı tipi özniteliklerini ayarlama](../../../../docs/framework/winforms/controls/how-to-set-font-attributes-for-the-windows-forms-richtextbox-control.md) ve [nasıl yapılır: ayarlama girintileri, asılı girintileri ve madde işaretli paragrafları Windows Forms RichTextBox denetimi ile ](../../../../docs/framework/winforms/controls/set-indents-hanging-indents-bulleted-paragraphs-with-wf-richtextbox.md). Dosyaları işlemek için <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> ve <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> yöntemleri görüntülenir ve düz metin, Unicode düz metin ve zengin metin biçimi (RTF) dahil olmak üzere birden çok dosya biçimleri yazılır. Olası dosya biçimlerini listelenen <xref:System.Windows.Forms.RichTextBoxStreamType>. Kullanabileceğiniz <xref:System.Windows.Forms.RichTextBox.Find%2A> metin ya da özel karakter dizeleri bulmak için yöntem.  
  
 Aynı zamanda bir <xref:System.Windows.Forms.RichTextBox> denetimi ayarlayarak Web stili bağlantılar için <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> özelliğine `true` ve işlemek için kod yazma <xref:System.Windows.Forms.RichTextBox.LinkClicked> olay. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms RichTextBox denetimi ile Web stili bağlantılar görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-web-style-links-with-the-windows-forms-richtextbox-control.md). Bazı veya tüm denetiminde metni ayarlayarak değiştirmelerine kullanıcının engelleyebilirsiniz <xref:System.Windows.Forms.RichTextBox.SelectionProtected%2A> özelliğine `true`.  
  
 Geri alma ve düzenleme işlemlerinin çoğu yineleme bir <xref:System.Windows.Forms.RichTextBox> çağırarak denetim <xref:System.Windows.Forms.TextBoxBase.Undo%2A> ve <xref:System.Windows.Forms.RichTextBox.Redo%2A> yöntemleri. <xref:System.Windows.Forms.RichTextBox.CanRedo%2A> Yöntemi kullanıcı geri son işlem denetime uygulanabilir olup olmadığını belirlemenizi sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox Denetimi](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [TextBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)
