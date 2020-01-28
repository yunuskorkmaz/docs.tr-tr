---
title: 'Nasıl yapılır: ToolStrip Taşmasını Yönetme'
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
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736151"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="26c75-102">Nasıl yapılır: Windows Forms'ta ToolStrip Taşmasını Yönetme</span><span class="sxs-lookup"><span data-stu-id="26c75-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>

<span data-ttu-id="26c75-103">Bir <xref:System.Windows.Forms.ToolStrip> denetimindeki tüm öğeler ayrılan alana uygun olmadığında, <xref:System.Windows.Forms.ToolStrip> taşma işlevselliğini etkinleştirebilir ve belirli <xref:System.Windows.Forms.ToolStripItem>s 'nin taşma davranışını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26c75-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>

<span data-ttu-id="26c75-104">Formun geçerli boyutu verilen <xref:System.Windows.Forms.ToolStrip> ayrılan daha fazla alan gerektiren <xref:System.Windows.Forms.ToolStripItem>s eklediğinizde, <xref:System.Windows.Forms.ToolStrip>üzerinde otomatik olarak bir <xref:System.Windows.Forms.ToolStripOverflowButton> görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="26c75-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="26c75-105"><xref:System.Windows.Forms.ToolStripOverflowButton> görünür ve taşma özellikli öğeler aşağı açılan taşma menüsüne taşınır.</span><span class="sxs-lookup"><span data-stu-id="26c75-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="26c75-106">Bu, <xref:System.Windows.Forms.ToolStrip> öğelerinizin farklı form boyutlarına nasıl doğru şekilde ayarlantığınızı özelleştirmenize ve önceliklendirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="26c75-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="26c75-107">Ayrıca, <xref:System.Windows.Forms.ToolStripItem.Placement%2A> ve <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> özelliklerini ve <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olayını kullanarak, öğelerinize giren öğelerin görünümünü de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="26c75-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="26c75-108">Formu Tasarım zamanında veya çalışma zamanında büyütürseniz, ana <xref:System.Windows.Forms.ToolStrip> daha fazla <xref:System.Windows.Forms.ToolStripItem>görüntülenir ve formun boyutunu azaltana kadar <xref:System.Windows.Forms.ToolStripOverflowButton> bile kaybolabilir.</span><span class="sxs-lookup"><span data-stu-id="26c75-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>

## <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="26c75-109">ToolStrip denetiminde taşmayı etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="26c75-109">To enable overflow on a ToolStrip control</span></span>

- <span data-ttu-id="26c75-110"><xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> özelliğinin <xref:System.Windows.Forms.ToolStrip>için `false` ayarlı olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="26c75-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="26c75-111">Varsayılan, `True` değeridir.</span><span class="sxs-lookup"><span data-stu-id="26c75-111">The default is `True`.</span></span>

     <span data-ttu-id="26c75-112"><xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> `True` (varsayılan), <xref:System.Windows.Forms.ToolStripItem> içeriği bir yatay <xref:System.Windows.Forms.ToolStrip> veya dikey <xref:System.Windows.Forms.ToolStrip>yüksekliğini aştığında açılan taşma menüsüne bir <xref:System.Windows.Forms.ToolStripItem> gönderilir.</span><span class="sxs-lookup"><span data-stu-id="26c75-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="26c75-113">Belirli bir ToolStripItem 'ın taşma davranışını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="26c75-113">To specify overflow behavior of a specific ToolStripItem</span></span>

- <span data-ttu-id="26c75-114"><xref:System.Windows.Forms.ToolStripItem> <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliğini istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="26c75-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="26c75-115">`Always`, `Never`ve `AsNeeded`olanakları vardır.</span><span class="sxs-lookup"><span data-stu-id="26c75-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="26c75-116">Varsayılan, `AsNeeded` değeridir.</span><span class="sxs-lookup"><span data-stu-id="26c75-116">The default is `AsNeeded`.</span></span>

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a><span data-ttu-id="26c75-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26c75-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="26c75-118">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="26c75-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="26c75-119">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="26c75-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="26c75-120">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="26c75-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
