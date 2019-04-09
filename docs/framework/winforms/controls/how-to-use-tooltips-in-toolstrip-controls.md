---
title: 'Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 884fb75d53e425702cdef46615a16394b835518f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076483"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma
Görüntüleyebileceğiniz bir <xref:System.Windows.Forms.ToolTip> için <xref:System.Windows.Forms.ToolStrip> denetimin ayarlayarak denetimi <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> özelliğini `true`.  
  
### <a name="to-display-a-tooltip"></a>Bir araç ipucunu görüntülemek için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> denetimin özellik `true`.  
  
     Varsayılan değer olan <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> olduğu `true`, varsayılan değeri <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> olduğu `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Tooltıptext özelliği bir ToolStripButton için araç ipucu metni kullanmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> özelliği düğmenin `true`.  
  
2.  Ayarlama <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> özelliği düğmenin `false`.  
  
     `AutoToolTip` Özelliği `true` için varsayılan olarak <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, ve <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     A <xref:System.Windows.Forms.ToolStripButton> kullanır, `Text` özelliği <xref:System.Windows.Forms.ToolTip> varsayılan metin. Özel metin görüntülemek için bu yordamı kullanın. bir <xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Ayarlarsanız <xref:System.Windows.Forms.ToolStripItemDisplayStyle> için <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>metin düğmesinde görüntülenir, ancak araç ipucu görünmeye devam eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
