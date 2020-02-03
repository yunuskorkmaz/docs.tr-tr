---
title: RichTextBox denetiminde kaydırma çubuklarını görüntüleme
ms.date: 03/30/2017
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
ms.openlocfilehash: 2185b572ef20765043d3df3dbfd8bf5b21cfac28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745553"
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetiminde Kaydırma Çubukları Görüntüleme
Varsayılan olarak Windows Forms <xref:System.Windows.Forms.RichTextBox> denetim, yatay ve dikey kaydırma çubuklarını gerektiği şekilde görüntüler. Aşağıdaki tabloda açıklanan <xref:System.Windows.Forms.RichTextBox> denetiminin <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> özelliği için yedi olası değer vardır.  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a>Bir RichTextBox denetiminde kaydırma çubuklarını görüntüleme  
  
1. <xref:System.Windows.Forms.RichTextBox.Multiline%2A> özelliğini `true`olarak ayarlayın. <xref:System.Windows.Forms.RichTextBox.Multiline%2A> özelliği `false`olarak ayarlanırsa yatay dahil olmak üzere kaydırma çubuğu türü görüntülenmez.  
  
2. <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> özelliğini <xref:System.Windows.Forms.RichTextBoxScrollBars> sabit listesinin uygun bir değeri olarak ayarlayın.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (varsayılan)|Yalnızca metin denetimin genişliğini veya uzunluğunu aştığında yatay veya dikey kaydırma çubuklarını veya her ikisini birden görüntüler.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|Hiçbir tür kaydırma çubuğunu görüntülemez.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|Yalnızca metin denetimin genişliğini aştığında bir yatay kaydırma çubuğu görüntüler. (Bunun gerçekleşmesi için <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliğinin `false`olarak ayarlanması gerekir.)|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|Yalnızca metin denetimin yüksekliğini aştığında dikey kaydırma çubuğunu görüntüler.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|<xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği `false`olarak ayarlandığında bir yatay kaydırma çubuğu görüntüler. Metin denetimin genişliğini aşmazsa kaydırma çubuğu soluk görünür.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|Her zaman dikey bir kaydırma çubuğu görüntüler. Metin denetimin uzunluğunu aşmazsa kaydırma çubuğu soluk görünür.|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|Her zaman dikey bir kaydırma çubuğu görüntüler. <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliği `false`olarak ayarlandığında bir yatay kaydırma çubuğu görüntüler. Metin, denetimin genişliğini veya uzunluğunu aşmazsa, kaydırma çubukları gri görünür.|  
  
3. <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> özelliğini uygun bir değer olarak ayarlayın.  
  
    |Değer|Açıklama|  
    |-----------|-----------------|  
    |`false`|Denetimdeki metin, denetimin genişliğine uyacak şekilde otomatik olarak düzeltilmez, bu nedenle, bir satır sonuna ulaşılana kadar sağa kayacaktır. Yukarıdaki yatay kaydırma çubuklarını veya her ikisini de seçtiyseniz bu değeri kullanın.|  
    |`true` (varsayılan)|Denetimdeki metin, denetimin genişliğine uyacak şekilde otomatik olarak ayarlanır. Yatay kaydırma çubuğu görünmez. Bir veya daha fazla paragraf göstermek için yukarıdaki dikey kaydırma çubuklarını veya hiçbirini seçtiyseniz bu değeri kullanın.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBoxScrollBars>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
