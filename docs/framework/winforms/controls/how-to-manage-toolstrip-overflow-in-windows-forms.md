---
title: "Nasıl yapılır: Windows Forms'ta ToolStrip Taşmasını Yönetme"
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
ms.openlocfilehash: 32bbc06320f0dc7f096a4b9021bebfbefedaf8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534898"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Taşmasını Yönetme
Zaman üzerindeki tüm öğeleri bir <xref:System.Windows.Forms.ToolStrip> denetimi ayrılan alanı Sığdır değil, üzerinde taşma işlevselliğini etkinleştirmek <xref:System.Windows.Forms.ToolStrip> ve özel taşma davranışını belirleyen <xref:System.Windows.Forms.ToolStripItem>s.  
  
 Eklediğinizde <xref:System.Windows.Forms.ToolStripItem>için ayrılan alandan daha fazla gerektiren s <xref:System.Windows.Forms.ToolStrip> formun geçerli boyut, verilen bir <xref:System.Windows.Forms.ToolStripOverflowButton> otomatik olarak görünür <xref:System.Windows.Forms.ToolStrip>. <xref:System.Windows.Forms.ToolStripOverflowButton> Görünür ve taşma etkin öğeleri açılan taşma menüsüne taşınır. Bu sayede özelleştirmek ve öncelik vermeniz nasıl, <xref:System.Windows.Forms.ToolStrip> öğeleri düzgün bir şekilde ayarlamak için farklı form boyutları. Bunlar taşma alanına kullanarak düştüğünde öğelerinizi görünümünü de değiştirebilirsiniz <xref:System.Windows.Forms.ToolStripItem.Placement%2A> ve <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> özellikleri ve <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> olay. Formun tasarım zamanında veya çalışma zamanında daha büyütmek varsa <xref:System.Windows.Forms.ToolStripItem>s üzerinde ana görüntülenebilir <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.ToolStripOverflowButton> formun boyutunu azaltmak kadar bile Kaybolabiliyor.  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a>ToolStrip denetimi taşma etkinleştirmek için  
  
-   Emin <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> özelliği ayarlı değil `false` için <xref:System.Windows.Forms.ToolStrip>. Varsayılan, `True` değeridir.  
  
     Zaman <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> olan `True` (varsayılan), bir <xref:System.Windows.Forms.ToolStripItem> açılan taşma menüsüne gönderilip olduğunda içeriği <xref:System.Windows.Forms.ToolStripItem> yatay genişliğini aşıyor <xref:System.Windows.Forms.ToolStrip> veya dikey yüksekliğini <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Belirli bir ToolStripItem taşma davranışını belirtmek için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> özelliği <xref:System.Windows.Forms.ToolStripItem> istediğiniz değer. Olasılıkları şunlardır `Always`, `Never`, ve `AsNeeded`. Defaultis `AsNeeded`.  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip Denetim, Mimarisi](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip Teknoloji Özeti](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
