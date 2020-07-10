---
title: TextBox denetiminde birden çok satırı görüntüleme
description: Çoklu satır, WordWrap ve kaydırma çubuğu özelliklerini ayarlayarak Windows Forms metin kutusu denetiminde birden çok satırı görüntülemeyi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
ms.openlocfilehash: e40d720bcd56366f4f06bfe2e2d347aaf9aa9d6c
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174477"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme
Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.TextBox> Denetim tek satırlık bir metin görüntüler ve kaydırma çubuklarını görüntülemez. Metin, kullanılabilir alandan uzunsa metnin yalnızca bir kısmı görünür olur. <xref:System.Windows.Forms.TextBox.Multiline%2A>,, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> Ve özelliklerini uygun değerlere ayarlayarak bu varsayılan davranışı değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.ScrollBars%2A> .  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>TextBox denetiminde bir satır başı görüntüleme  
  
- Bir satır başını çok satırlı olarak göstermek için <xref:System.Windows.Forms.TextBox> <xref:System.Environment.NewLine%2A> özelliğini kullanın.  
  
     Kaçış karakterlerinin () yorumlamasının \\ dile özgü olduğunu unutmayın. Visual Basic `Chr$(13) & Chr$(10)` , satır başı ve satır besleme karakter bileşimi için kullanır.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>TextBox denetiminde birden çok satırı görüntülemek için  
  
1. <xref:System.Windows.Forms.TextBox.Multiline%2A>Özelliğini olarak ayarlayın `true` . <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>İse `true` (varsayılan), denetimdeki metin bir veya daha fazla paragraf olarak görünür; Aksi takdirde, bazı satırların denetimin kenarında kırpıldığı bir liste olarak görüntülenir.  
  
2. <xref:System.Windows.Forms.TextBox.ScrollBars%2A>Özelliği uygun bir değere ayarlayın.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Bu değeri, metin neredeyse her zaman denetime uyan bir paragraf olacak şekilde kullanın. Kullanıcı, metnin tek seferde görüntülenemeyecek kadar uzun olması halinde, denetimin içinde gezinmek için fare işaretçisini kullanabilir.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Bazıları denetimin genişliğinden daha uzun olabilecek bir satır listesini göstermek istiyorsanız bu değeri kullanın <xref:System.Windows.Forms.TextBox> .|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Liste, denetimin yüksekliğinden daha uzun olabileceğinden bu değeri kullanın.|  
  
3. <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>Özelliği uygun bir değere ayarlayın.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |`false`|Denetimdeki metin otomatik olarak kaydırılmaz, bu nedenle bir satır sonuna ulaşıncaya kadar sağa kayacaktır. Bu değeri <xref:System.Windows.Forms.ScrollBars.Horizontal> , kaydırma çubukları <xref:System.Windows.Forms.ScrollBars.Both> ' nı veya üstünü seçtiyseniz kullanın.|  
    |`true`varsayılanını|Yatay kaydırma çubuğu görünmez. <xref:System.Windows.Forms.ScrollBars.Vertical> <xref:System.Windows.Forms.ScrollBars.None> Bir veya daha fazla paragraf göstermek için, kaydırma çubukları veya yukarıdaki ' u seçerseniz bu değeri kullanın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
