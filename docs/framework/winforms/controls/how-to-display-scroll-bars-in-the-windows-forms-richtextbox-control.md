---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetiminde Kaydırma Çubukları Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 152706cee511e4bca1dd324a652e8077b1f8548a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312663"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetiminde Kaydırma Çubukları Görüntüleme
Varsayılan olarak, Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi gerektiği gibi yatay ve dikey kaydırma çubukları görüntülenir. Yedi olası değerleri vardır <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> özelliği <xref:System.Windows.Forms.RichTextBox> denetimi, aşağıdaki tabloda açıklanmıştır.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>RichTextBox denetiminde kaydırma çubukları görüntülemek için  
  
1. Ayarlama <xref:System.Windows.Forms.RichTextBox.Multiline%2A> özelliğini `true`. Hiçbir tür yatay kaydırma çubuğu dahil olmak üzere, görüntüler, <xref:System.Windows.Forms.RichTextBox.Multiline%2A> özelliği `false`.  
  
2. Ayarlama <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> uygun bir değere <xref:System.Windows.Forms.RichTextBoxScrollBars> sabit listesi.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (varsayılan)|Yalnızca metin genişlik veya denetim uzunluğunu aşarsa, yatay veya dikey kaydırma çubukları veya her ikisi de görüntüler.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Hiçbir zaman herhangi bir türde kaydırma çubuğu görüntüler.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Bir yatay kaydırma çubuğu yalnızca metin denetim genişliği aştığında görüntüler. (Bunun gerçekleşmesi <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği ayarlanmalıdır `false`.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Bir dikey kaydırma çubuğu yalnızca metin denetimin yüksekliği aştığında görüntüler.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|Yatay kaydırma ne zaman görüntüler <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği `false`. Metin denetim genişliği geçmediği zaman kaydırma çubuğu gri görünür.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Her zaman bir dikey kaydırma çubuğu görüntülenir. Metin denetimi uzunluğunu aşan değil kaydırma çubuğu gri görünür.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Her zaman bir dikey kaydırma çubuğu görüntüler. Yatay kaydırma ne zaman görüntüler <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği `false`. Kaydırma çubuklarının metin genişlik veya denetim uzunluğunu aşmadığından gri görünür.|  
  
3. Ayarlama <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliğini uygun bir değer.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |`false`|Denetimdeki metnin, denetiminin genişliğini satır sonu ulaşılana kadar sağa doğru kayar şekilde sığacak şekilde otomatik olarak ayarlanmaz. Yukarıda yatay kaydırma çubuklarını veya her ikisi de seçerseniz, bu değeri kullanın.|  
    |`true` (varsayılan)|Denetimdeki metnin, denetiminin genişliğini sığacak şekilde otomatik olarak ayarlanır. Yatay kaydırma çubuğu görüntülenmez. Dikey kaydırma çubukları veya hiçbiri, yukarıdaki bir veya daha fazla paragraflar görüntülenecek seçerseniz, bu değeri kullanın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
