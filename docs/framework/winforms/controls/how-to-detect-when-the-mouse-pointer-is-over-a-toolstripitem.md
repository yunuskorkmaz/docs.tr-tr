---
title: 'Nasıl yapılır: Fare İşaretçisi Bir ToolStripItem Üzerine Geldiğinde Algılama'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 09fd9f2f9b8cc44b6c04b829bf2854bea4aa8cf7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220053"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>Nasıl yapılır: Fare İşaretçisi Bir ToolStripItem Üzerine Geldiğinde Algılama
Fare işaretçisi bittiğinde algılamak için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>Fare işaretçisi bir ToolStripItem üzerine geldiğinde algılama  
  
-   Kullanım <xref:System.Windows.Forms.ToolStripItem.Selected%2A> özelliği olan öğelerin <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> olduğu `true`.  
  
     Bu, eşitlemeye sahip olmasını önler <xref:System.Windows.Forms.ToolStripItem.MouseEnter> ve <xref:System.Windows.Forms.ToolStripItem.MouseLeave> olayları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
