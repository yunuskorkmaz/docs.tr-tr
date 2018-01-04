---
title: "Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d81a1936d8a6159c6225a12f712c546fe9beeb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Nasıl yapılır: ToolStrip Denetiminde ToolTips Kullanma
Görüntüleyebileceğiniz bir <xref:System.Windows.Forms.ToolTip> için <xref:System.Windows.Forms.ToolStrip> istediğiniz denetimin ayarlayarak denetimi <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> özelliğine `true`.  
  
### <a name="to-display-a-tooltip"></a>Bir araç ipucunu görüntüleyebilirsiniz  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> denetiminin özelliği `true`.  
  
     Varsayılan değer olan <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> olan `true`ve varsayılan değerini <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> ve <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> olan `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Tooltıptext özelliği bir ToolStripButton için araç ipucu metni kullanmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> düğme özelliğinin `true`.  
  
2.  Ayarlama <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> düğme özelliğinin `false`.  
  
     `AutoToolTip` Özelliği `true` için varsayılan olarak <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, ve <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     A <xref:System.Windows.Forms.ToolStripButton> kullanan kendi `Text` özelliği için <xref:System.Windows.Forms.ToolTip> varsayılan metin. Özel metin olarak görüntülemek için bu yordamı kullanın bir <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Ayarlarsanız <xref:System.Windows.Forms.ToolStripItemDisplayStyle> için <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> veya <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>metin düğmesi görünür, ancak araç ipucu görünmeye devam eder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
