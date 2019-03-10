---
title: "Nasıl yapılır: Windows Forms'ta çalışma zamanında ToolStrip öğelerinin yeniden sıralanmasını etkinleştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
ms.openlocfilehash: 0800acc955ff8cf9efa7bc183f10d2b5cc87aac6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713727"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="96de1-102">Nasıl yapılır: Windows Forms'ta çalışma zamanında ToolStrip öğelerinin yeniden sıralanmasını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="96de1-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="96de1-103">Kullanıcının yeniden etkinleştirebilirsiniz <xref:System.Windows.Forms.ToolStripItem> denetimlerini <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="96de1-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="96de1-104">Çalışma zamanında ToolStripItem yeniden etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="96de1-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
-   <span data-ttu-id="96de1-105">Ayarlama <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="96de1-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="96de1-106">Varsayılan olarak, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="96de1-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="96de1-107">Çalışma zamanında kullanıcı ALT tuşunu ve sürüklemek için sol fare düğmesini tutar bir <xref:System.Windows.Forms.ToolStripItem> farklı bir konuma <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="96de1-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="96de1-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96de1-108">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [<span data-ttu-id="96de1-109">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="96de1-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="96de1-110">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="96de1-110">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="96de1-111">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="96de1-111">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
