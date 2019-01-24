---
title: 'Nasıl yapılır: Fare işaretçisi bir ToolStripItem üzerine geldiğinde algılama'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 20fbc91773f431fc68f606f8aa9f24f4c0cc06bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539603"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>Nasıl yapılır: Fare işaretçisi bir ToolStripItem üzerine geldiğinde algılama
Fare işaretçisi bittiğinde algılamak için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>Fare işaretçisi bir ToolStripItem üzerine geldiğinde algılama  
  
-   Kullanım <xref:System.Windows.Forms.ToolStripItem.Selected%2A> özelliği olan öğelerin <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> olduğu `true`.  
  
     Bu, eşitlemeye sahip olmasını önler <xref:System.Windows.Forms.ToolStripItem.MouseEnter> ve <xref:System.Windows.Forms.ToolStripItem.MouseLeave> olayları.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
