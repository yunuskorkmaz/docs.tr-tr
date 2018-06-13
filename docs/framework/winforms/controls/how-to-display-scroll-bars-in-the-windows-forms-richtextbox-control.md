---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetiminde Kaydırma Çubukları Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 5588aad5b2e38716c628947c6e06365e7053eb5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532749"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetiminde Kaydırma Çubukları Görüntüleme
Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi gerektiği gibi yatay ve dikey kaydırma çubukları görüntüler. Yedi olası değerler için <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> özelliği <xref:System.Windows.Forms.RichTextBox> aşağıdaki tabloda açıklanan denetim.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>RichTextBox denetiminde kaydırma çubukları görüntülemek için  
  
1.  Ayarlama <xref:System.Windows.Forms.RichTextBox.Multiline%2A> özelliğine `true`. Tür yatay kaydırma çubuğu dahil olmak üzere, görüntüler, <xref:System.Windows.Forms.RichTextBox.Multiline%2A> özelliği ayarlanmış `false`.  
  
2.  Ayarlama <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> uygun bir değerde özelliğine <xref:System.Windows.Forms.RichTextBoxScrollBars> numaralandırması.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (varsayılan)|Yalnızca metin genişliğini veya denetim uzunluğunu aştığında yatay veya dikey kaydırma çubukları veya her ikisini de görüntüler.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Hiçbir zaman kaydırma çubuğunun herhangi bir türde görüntüler.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Yalnızca metin denetiminin genişliğini aştığında çubuğu yatay kaydırma görüntüler. (Bunun gerçekleşmesi <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği ayarlanmalıdır `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Yalnızca metin denetimin yüksekliğini aştığında çubuğu dikey bir kaydırma görüntüler.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Yatay kaydırma ne zaman görüntüler <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği ayarlanmış `false`. Metin denetimi genişliğini aşmayan zaman kaydırma çubuğu soluk görüntülenir.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Her zaman bir dikey kaydırma çubuğu görüntüler. Metin denetim uzunluğunu aşan değil kaydırma çubuğu soluk görüntülenir.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Her zaman dikey kaydırma çubuğu görüntüler. Yatay kaydırma ne zaman görüntüler <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği ayarlanmış `false`. Kaydırma çubukları metin genişliğini veya denetim uzunluğunu aşmayan gri görünür.|  
  
3.  Ayarlama <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> uygun bir değere özelliği.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |`false`|Denetimdeki metnin satır sonu ulaşılana kadar sağa kaydırın şekilde denetiminin genişliğini sığması için otomatik olarak ayarlanmaz. Yukarıdaki yatay kaydırma çubuklarını veya her ikisini de seçerseniz, bu değeri kullanın.|  
    |`true` (varsayılan)|Denetimdeki metnin denetiminin genişliğini sığması için otomatik olarak düzeltilir. Yatay kaydırma çubuğu görünmez. Dikey kaydırma çubuklarını veya hiçbiri, yukarıda, bir veya daha fazla paragraf görüntülemek için seçtiğiniz zaman bu değeri kullanın.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox Denetimi](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
