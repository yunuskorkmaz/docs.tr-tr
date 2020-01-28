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
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Taşmasını Yönetme

Bir <xref:System.Windows.Forms.ToolStrip> denetimindeki tüm öğeler ayrılan alana uygun olmadığında, <xref:System.Windows.Forms.ToolStrip> taşma işlevselliğini etkinleştirebilir ve belirli <xref:System.Windows.Forms.ToolStripItem>s 'nin taşma davranışını belirleyebilirsiniz.

Formun geçerli boyutu verilen <xref:System.Windows.Forms.ToolStrip> ayrılan daha fazla alan gerektiren <xref:System.Windows.Forms.ToolStripItem>s eklediğinizde, <xref:System.Windows.Forms.ToolStrip>üzerinde otomatik olarak bir <xref:System.Windows.Forms.ToolStripOverflowButton> görüntülenir. <xref:System.Windows.Forms.ToolStripOverflowButton> görünür ve taşma özellikli öğeler aşağı açılan taşma menüsüne taşınır. Bu, <xref:System.Windows.Forms.ToolStrip> öğelerinizin farklı form boyutlarına nasıl doğru şekilde ayarlantığınızı özelleştirmenize ve önceliklendirmenize olanak tanır. Ayrıca, <xref:System.Windows.Forms.ToolStripItem.Placement%2A> ve <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> özelliklerini ve <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olayını kullanarak, öğelerinize giren öğelerin görünümünü de değiştirebilirsiniz. Formu Tasarım zamanında veya çalışma zamanında büyütürseniz, ana <xref:System.Windows.Forms.ToolStrip> daha fazla <xref:System.Windows.Forms.ToolStripItem>görüntülenir ve formun boyutunu azaltana kadar <xref:System.Windows.Forms.ToolStripOverflowButton> bile kaybolabilir.

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>ToolStrip denetiminde taşmayı etkinleştirmek için

- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> özelliğinin <xref:System.Windows.Forms.ToolStrip>için `false` ayarlı olmadığından emin olun. Varsayılan, `True` değeridir.

     <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> `True` (varsayılan), <xref:System.Windows.Forms.ToolStripItem> içeriği bir yatay <xref:System.Windows.Forms.ToolStrip> veya dikey <xref:System.Windows.Forms.ToolStrip>yüksekliğini aştığında açılan taşma menüsüne bir <xref:System.Windows.Forms.ToolStripItem> gönderilir.

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Belirli bir ToolStripItem 'ın taşma davranışını belirtmek için

- <xref:System.Windows.Forms.ToolStripItem> <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliğini istenen değere ayarlayın. `Always`, `Never`ve `AsNeeded`olanakları vardır. Varsayılan, `AsNeeded` değeridir.

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
- [ToolStrip Denetim, Mimarisi](toolstrip-control-architecture.md)
- [ToolStrip Teknoloji Özeti](toolstrip-technology-summary.md)
