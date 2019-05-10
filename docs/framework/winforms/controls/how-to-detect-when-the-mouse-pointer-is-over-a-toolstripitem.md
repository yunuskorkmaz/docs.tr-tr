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
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="f882f-102">Nasıl yapılır: Fare İşaretçisi Bir ToolStripItem Üzerine Geldiğinde Algılama</span><span class="sxs-lookup"><span data-stu-id="f882f-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="f882f-103">Fare işaretçisi bittiğinde algılamak için aşağıdaki yordamı kullanın. bir <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="f882f-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="f882f-104">Fare işaretçisi bir ToolStripItem üzerine geldiğinde algılama</span><span class="sxs-lookup"><span data-stu-id="f882f-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
- <span data-ttu-id="f882f-105">Kullanım <xref:System.Windows.Forms.ToolStripItem.Selected%2A> özelliği olan öğelerin <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> olduğu `true`.</span><span class="sxs-lookup"><span data-stu-id="f882f-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="f882f-106">Bu, eşitlemeye sahip olmasını önler <xref:System.Windows.Forms.ToolStripItem.MouseEnter> ve <xref:System.Windows.Forms.ToolStripItem.MouseLeave> olayları.</span><span class="sxs-lookup"><span data-stu-id="f882f-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f882f-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f882f-107">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [<span data-ttu-id="f882f-108">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f882f-108">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
