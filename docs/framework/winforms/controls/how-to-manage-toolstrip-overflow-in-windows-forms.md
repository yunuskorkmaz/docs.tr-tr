---
title: "Nasıl yapılır: Windows Forms'ta ToolStrip Taşmasını Yönetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1ae4172dbdf82b4bd5bdd9a7f8afc1901fcfa3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="84061-102">Nasıl yapılır: Windows Forms'ta ToolStrip Taşmasını Yönetme</span><span class="sxs-lookup"><span data-stu-id="84061-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>
<span data-ttu-id="84061-103">Zaman üzerindeki tüm öğeleri bir <xref:System.Windows.Forms.ToolStrip> denetimi ayrılan alanı Sığdır değil, üzerinde taşma işlevselliğini etkinleştirmek <xref:System.Windows.Forms.ToolStrip> ve özel taşma davranışını belirleyen <xref:System.Windows.Forms.ToolStripItem>s.</span><span class="sxs-lookup"><span data-stu-id="84061-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>  
  
 <span data-ttu-id="84061-104">Eklediğinizde <xref:System.Windows.Forms.ToolStripItem>için ayrılan alandan daha fazla gerektiren s <xref:System.Windows.Forms.ToolStrip> formun geçerli boyut, verilen bir <xref:System.Windows.Forms.ToolStripOverflowButton> otomatik olarak görünür <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="84061-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="84061-105"><xref:System.Windows.Forms.ToolStripOverflowButton> Görünür ve taşma etkin öğeleri açılan taşma menüsüne taşınır.</span><span class="sxs-lookup"><span data-stu-id="84061-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="84061-106">Bu sayede özelleştirmek ve öncelik vermeniz nasıl, <xref:System.Windows.Forms.ToolStrip> öğeleri düzgün bir şekilde ayarlamak için farklı form boyutları.</span><span class="sxs-lookup"><span data-stu-id="84061-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="84061-107">Bunlar taşma alanına kullanarak düştüğünde öğelerinizi görünümünü de değiştirebilirsiniz <xref:System.Windows.Forms.ToolStripItem.Placement%2A> ve <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> özellikleri ve <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="84061-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="84061-108">Formun tasarım zamanında veya çalışma zamanında daha büyütmek varsa <xref:System.Windows.Forms.ToolStripItem>s üzerinde ana görüntülenebilir <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.ToolStripOverflowButton> formun boyutunu azaltmak kadar bile Kaybolabiliyor.</span><span class="sxs-lookup"><span data-stu-id="84061-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="84061-109">ToolStrip denetimi taşma etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="84061-109">To enable overflow on a ToolStrip control</span></span>  
  
-   <span data-ttu-id="84061-110">Emin <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> özelliği ayarlı değil `false` için <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="84061-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="84061-111">Varsayılan, `True` değeridir.</span><span class="sxs-lookup"><span data-stu-id="84061-111">The default is `True`.</span></span>  
  
     <span data-ttu-id="84061-112">Zaman <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> olan `True` (varsayılan), bir <xref:System.Windows.Forms.ToolStripItem> açılan taşma menüsüne gönderilip olduğunda içeriği <xref:System.Windows.Forms.ToolStripItem> yatay genişliğini aşıyor <xref:System.Windows.Forms.ToolStrip> veya dikey yüksekliğini <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="84061-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="84061-113">Belirli bir ToolStripItem taşma davranışını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="84061-113">To specify overflow behavior of a specific ToolStripItem</span></span>  
  
-   <span data-ttu-id="84061-114">Ayarlama <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliği <xref:System.Windows.Forms.ToolStripItem> istediğiniz değer.</span><span class="sxs-lookup"><span data-stu-id="84061-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="84061-115">Olasılıkları şunlardır `Always`, `Never`, ve `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="84061-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="84061-116">Defaultis `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="84061-116">The defaultis `AsNeeded`.</span></span>  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="84061-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84061-117">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [<span data-ttu-id="84061-118">ToolStrip denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="84061-118">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="84061-119">ToolStrip denetim mimarisi</span><span class="sxs-lookup"><span data-stu-id="84061-119">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="84061-120">ToolStrip Teknoloiji özeti</span><span class="sxs-lookup"><span data-stu-id="84061-120">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
