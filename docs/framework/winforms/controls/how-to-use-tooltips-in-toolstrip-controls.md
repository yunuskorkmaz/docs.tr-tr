---
title: 'Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939728"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma
<xref:System.Windows.Forms.ToolTip> <xref:System.Windows.Forms.ToolStrip> Denetimin özelliğiniolarak`true`ayarlayarak istediğiniz denetim için bir görüntüleyebilirsiniz. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
  
### <a name="to-display-a-tooltip"></a>Araç Ipucunu görüntüleme  
  
- Denetiminin özelliğini olarak `true`ayarlayın. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
  
     Varsayılan değeri <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> `true`, <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> ve varsayılan<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>değeridir . `false`  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>ToolStripButton araç Ipucu metni için ToolTipText özelliğini kullanmak için  
  
1. Düğmenin özelliğini olarak `true`ayarlayın. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
  
2. Düğmenin özelliğini olarak `false`ayarlayın. <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>  
  
     <xref:System.Windows.Forms.ToolStripButton> `true` Özelliği,,ve<xref:System.Windows.Forms.ToolStripSplitButton>için Varsayılanolarakolur.<xref:System.Windows.Forms.ToolStripDropDownButton> `AutoToolTip`  
  
     , Varsayılan olarak `Text` <xref:System.Windows.Forms.ToolTip> metin için özelliğini kullanır.<xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripButton> İçinde<xref:System.Windows.Forms.ToolTip>özel metin göstermek için bu yordamı kullanın.  
  
> [!NOTE]
> Veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> olarak ayarlarsanız,düğmeüzerindehiçbirmetingörünmez,ancakaraçipucugörünmeyedevameder.<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
