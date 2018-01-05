---
title: "Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dca8d0f869702dee50bf851a2099317c45aa842
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a>Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme
Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.TextBox> denetimi tek satırlık metin görüntüler ve kaydırma çubukları görüntülemez. Metin boşluktan uzunsa, metin yalnızca bir parçasının görünür olur. Ayarlayarak bu varsayılan davranışı değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, ve <xref:System.Windows.Forms.TextBox.ScrollBars%2A> uygun değerlere özellikleri.  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a>TextBox denetiminde başı görüntülemek için  
  
-   Bir çok satır başı görüntülenecek <xref:System.Windows.Forms.TextBox>, kullanın <xref:System.Environment.NewLine%2A> özelliği.  
  
     Unutmayın, kaçış karakterleri yorumu (\\) dile özgüdür. Visual Basic kullanan `Chr$(13) & Chr$(10)` satır başı ve satır besleme karakter birleşimi.  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a>TextBox denetiminde birden fazla satır görüntülemek için  
  
1.  Ayarlama <xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğine `true`. Varsa <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> olan `true` (varsayılan), Denetim metni olarak bir veya daha fazla paragraf sonra görüntülenir; Aksi takdirde, bazı satırlar kırpılmış denetimi kenarında bir liste olarak görüntülenir.  
  
2.  Ayarlama <xref:System.Windows.Forms.TextBox.ScrollBars%2A> uygun bir değere özelliği.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|Bir paragraf metni olacaksa, bu değeri kullanın, denetimi neredeyse her zaman uyar. Kullanıcı, fare işaretçisini metin aynı anda görüntülemek için çok uzun olduğunda içindeki denetim hareket etmek için kullanabilirsiniz.|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|Satırları, bazıları olabilir genişliğinden daha uzun bir listesini görüntülemek istiyorsanız, bu değeri kullanın <xref:System.Windows.Forms.TextBox> denetim.|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|Liste denetimi yüksekliğini uzun olması durumunda bu değeri kullanın.|  
  
3.  Ayarlama <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> uygun bir değere özelliği.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |`false`|Satır sonu ulaşılana kadar sağa kaydırın şekilde metninin denetimde otomatik olarak, sarılır değil. Bu değer belirlediğinizde kullanmak <xref:System.Windows.Forms.ScrollBars.Horizontal> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.Both>, yukarıdaki.|  
    |`true`(varsayılan)|Yatay kaydırma çubuğu görünmez. Bu değer belirlediğinizde kullanmak <xref:System.Windows.Forms.ScrollBars.Vertical> kaydırma çubukları veya <xref:System.Windows.Forms.ScrollBars.None>, bir veya daha fazla paragraf görüntülemek için yukarıdaki.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [TextBox Denetimi](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
