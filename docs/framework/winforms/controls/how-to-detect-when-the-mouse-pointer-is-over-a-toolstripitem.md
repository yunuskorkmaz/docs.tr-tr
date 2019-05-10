---
title: 'Nasıl yapılır: Fare İşaretçisi Bir ToolStripItem Üzerine Geldiğinde Algılama'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: f01a9acb3a566be40d65fb075c8487d4e9cb6e73
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623635"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>Nasıl yapılır: Fare İşaretçisi Bir ToolStripItem Üzerine Geldiğinde Algılama
Fare işaretçisi bittiğinde algılamak için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>Fare işaretçisi bir ToolStripItem üzerine geldiğinde algılama  
  
- Kullanım <xref:System.Windows.Forms.ToolStripItem.Selected%2A> özelliği olan öğelerin <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> olduğu `true`.  
  
     Bu, eşitlemeye sahip olmasını önler <xref:System.Windows.Forms.ToolStripItem.MouseEnter> ve <xref:System.Windows.Forms.ToolStripItem.MouseLeave> olayları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
