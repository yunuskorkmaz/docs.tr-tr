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
ms.openlocfilehash: 24304b64b4214f9c15006e4f6cf35fac0bd0ced1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480084"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip taşmasını yönetme

Tüm öğeleri bir <xref:System.Windows.Forms.ToolStrip> denetimi ayrılan alana Sığdır değil, üzerinde taşma işlevselliğini etkinleştirmek <xref:System.Windows.Forms.ToolStrip> ve özel taşma davranışını belirlemek <xref:System.Windows.Forms.ToolStripItem>s.

Eklediğinizde <xref:System.Windows.Forms.ToolStripItem>için ayrılan alandan daha fazla gerektiren s <xref:System.Windows.Forms.ToolStrip> formun geçerli boyutu, verilen bir <xref:System.Windows.Forms.ToolStripOverflowButton> otomatik olarak görünür <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.ToolStripOverflowButton> Görünür ve taşma etkin öğeleri açılan taşma menüsüne taşındı. Bu sayede özelleştirme ve önceliklerini belirlemek nasıl, <xref:System.Windows.Forms.ToolStrip> öğelerini farklı form boyutları için düzgün şekilde ayarlayın. Ayrıca bunlar taşma alanına kullanarak bozulduğunda öğelerinizi görünümünü değiştirebilirsiniz <xref:System.Windows.Forms.ToolStripItem.Placement%2A> ve <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> özellikleri ve <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olay. Formun tasarım zamanı veya çalışma zamanı daha büyütün, <xref:System.Windows.Forms.ToolStripItem>s ana üzerinde görüntülenebilir <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.ToolStripOverflowButton> formun boyutunu azaltma kadar bile Kaybolabiliyor.

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>ToolStrip denetimi overflow'da etkinleştirmek için

- Emin <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> özelliği ayarlanmamış `false` için <xref:System.Windows.Forms.ToolStrip>. Varsayılan, `True` değeridir.

     Zaman <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> olan `True` (varsayılan), bir <xref:System.Windows.Forms.ToolStripItem> taşma açılan menüye gönderilir, içeriğini <xref:System.Windows.Forms.ToolStripItem> yatay genişliğini aşıyor <xref:System.Windows.Forms.ToolStrip> veya dikey yüksekliğini <xref:System.Windows.Forms.ToolStrip>.

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Belirli bir ToolStripItem taşma davranışını belirtmek için

- Ayarlama <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliği <xref:System.Windows.Forms.ToolStripItem> istediğiniz değer. Olasılıklar `Always`, `Never`, ve `AsNeeded`. Varsayılan, `AsNeeded` değeridir.

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
- [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
- [ToolStrip Denetim, Mimarisi](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
- [ToolStrip Teknoloji Özeti](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
