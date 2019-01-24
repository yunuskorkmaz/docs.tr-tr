---
title: "Nasıl yapılır: Windows Forms'ta ToolStrip taşmasını yönetme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 5f26217c92aef1d568349aefb87dd5a882a0cf28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541163"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="0673b-102">Nasıl yapılır: Windows Forms'ta ToolStrip taşmasını yönetme</span><span class="sxs-lookup"><span data-stu-id="0673b-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>
<span data-ttu-id="0673b-103">Tüm öğeleri bir <xref:System.Windows.Forms.ToolStrip> denetimi ayrılan alana Sığdır değil, üzerinde taşma işlevselliğini etkinleştirmek <xref:System.Windows.Forms.ToolStrip> ve özel taşma davranışını belirlemek <xref:System.Windows.Forms.ToolStripItem>s.</span><span class="sxs-lookup"><span data-stu-id="0673b-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>  
  
 <span data-ttu-id="0673b-104">Eklediğinizde <xref:System.Windows.Forms.ToolStripItem>için ayrılan alandan daha fazla gerektiren s <xref:System.Windows.Forms.ToolStrip> formun geçerli boyutu, verilen bir <xref:System.Windows.Forms.ToolStripOverflowButton> otomatik olarak görünür <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="0673b-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="0673b-105"><xref:System.Windows.Forms.ToolStripOverflowButton> Görünür ve taşma etkin öğeleri açılan taşma menüsüne taşındı.</span><span class="sxs-lookup"><span data-stu-id="0673b-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="0673b-106">Bu sayede özelleştirme ve önceliklerini belirlemek nasıl, <xref:System.Windows.Forms.ToolStrip> öğelerini farklı form boyutları için düzgün şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0673b-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="0673b-107">Ayrıca bunlar taşma alanına kullanarak bozulduğunda öğelerinizi görünümünü değiştirebilirsiniz <xref:System.Windows.Forms.ToolStripItem.Placement%2A> ve <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> özellikleri ve <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="0673b-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="0673b-108">Formun tasarım zamanı veya çalışma zamanı daha büyütün, <xref:System.Windows.Forms.ToolStripItem>s ana üzerinde görüntülenebilir <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.ToolStripOverflowButton> formun boyutunu azaltma kadar bile Kaybolabiliyor.</span><span class="sxs-lookup"><span data-stu-id="0673b-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="0673b-109">ToolStrip denetimi overflow'da etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="0673b-109">To enable overflow on a ToolStrip control</span></span>  
  
-   <span data-ttu-id="0673b-110">Emin <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> özelliği ayarlanmamış `false` için <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="0673b-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="0673b-111">Varsayılan, `True` değeridir.</span><span class="sxs-lookup"><span data-stu-id="0673b-111">The default is `True`.</span></span>  
  
     <span data-ttu-id="0673b-112">Zaman <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> olan `True` (varsayılan), bir <xref:System.Windows.Forms.ToolStripItem> taşma açılan menüye gönderilir, içeriğini <xref:System.Windows.Forms.ToolStripItem> yatay genişliğini aşıyor <xref:System.Windows.Forms.ToolStrip> veya dikey yüksekliğini <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="0673b-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="0673b-113">Belirli bir ToolStripItem taşma davranışını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="0673b-113">To specify overflow behavior of a specific ToolStripItem</span></span>  
  
-   <span data-ttu-id="0673b-114">Ayarlama <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliği <xref:System.Windows.Forms.ToolStripItem> istediğiniz değer.</span><span class="sxs-lookup"><span data-stu-id="0673b-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="0673b-115">Olasılıklar `Always`, `Never`, ve `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="0673b-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="0673b-116">Defaultis `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="0673b-116">The defaultis `AsNeeded`.</span></span>  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0673b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0673b-117">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="0673b-118">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0673b-118">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="0673b-119">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="0673b-119">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [<span data-ttu-id="0673b-120">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="0673b-120">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
