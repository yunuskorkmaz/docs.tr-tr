---
title: 'Nasıl yapılır: Fare İşaretçisi Bir ToolStripItem Üzerine Geldiğinde Algılama'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 15a7562efd9a86a029754610ffd9e77c372d1ac2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530503"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>Nasıl yapılır: Fare İşaretçisi Bir ToolStripItem Üzerine Geldiğinde Algılama
Fare işaretçisini üzerinden olduğunda algılamak için aşağıdaki yordamı kullanın bir <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>Fare işaretçisi bir ToolStripItem üzerine geldiğinde algılamak için  
  
-   Kullanım <xref:System.Windows.Forms.ToolStripItem.Selected%2A> özelliği, öğeleri için <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> olan `true`.  
  
     Bu, eşitleme zorunda kalmaktan engelleyecek <xref:System.Windows.Forms.ToolStripItem.MouseEnter> ve <xref:System.Windows.Forms.ToolStripItem.MouseLeave> olaylar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
