---
title: 'Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme'
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
ms.openlocfilehash: 893782e041b1397fe0598394b69575a5c9e53806
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625390"
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme
Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.TextBox> denetimi tek satırlık metin görüntüler ve kaydırma çubukları görüntülemez. Metin boşluktan uzunsa, metnin yalnızca bir kısmını görülebilir. Ayarlayarak bu varsayılan davranışı değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, ve <xref:System.Windows.Forms.TextBox.ScrollBars%2A> özellikleri uygun değerlere.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>TextBox denetiminde başı görüntülemek için  
  
- Bir çok satır başı görüntülenecek <xref:System.Windows.Forms.TextBox>, kullanın <xref:System.Environment.NewLine%2A> özelliği.  
  
     Unutmayın, kaçış karakterleri yorumunu (\\) dile özgüdür. Visual Basic kullanan `Chr$(13) & Chr$(10)` satır başı ve satır besleme karakter birleşimi.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>Çok satırlı TextBox denetiminde görüntülemek için  
  
1. Ayarlama <xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğini `true`. Varsa <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> olduğu `true` (varsayılan), denetimdeki metin olarak bir veya daha fazla paragraflar sonra görünür; Aksi takdirde, bazı satırlar kırpılmış denetim ucuna, bir liste olarak görünür.  
  
2. Ayarlama <xref:System.Windows.Forms.TextBox.ScrollBars%2A> özelliğini uygun bir değer.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Paragraf metni olacaksa, bu değeri kullanın, Denetim neredeyse her zaman uyar. Kullanıcı, fare işaretçisini metnin tümünü tek seferde görüntülemek için çok uzun olursa denetim içinde hareket etmek için kullanabilirsiniz.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Satırları, bazıları da olabilir genişliğini uzun bir listesini görüntülemek istiyorsanız, bu değeri kullanın <xref:System.Windows.Forms.TextBox> denetimi.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Listenin denetimin yüksekliği uzun olması durumunda bu değeri kullanın.|  
  
3. Ayarlama <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliğini uygun bir değer.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |`false`|Satır sonu ulaşılana kadar sağa doğru kayar şekilde metin denetiminde otomatik olarak, sarmalanır değil. Seçerseniz, bu değeri kullanın <xref:System.Windows.Forms.ScrollBars.Horizontal> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.Both>, yukarıdaki.|  
    |`true` (varsayılan)|Yatay kaydırma çubuğu görüntülenmez. Seçerseniz, bu değeri kullanın <xref:System.Windows.Forms.ScrollBars.Vertical> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.None>, bir veya daha fazla paragraflar görüntülemek için yukarıdaki.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Salt okunur metin kutusu oluşturma](how-to-create-a-read-only-text-box-windows-forms.md)
- [Nasıl yapılır: Dizeye tırnak işaretleri koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
