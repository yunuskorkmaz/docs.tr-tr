---
title: 'Nasıl yapilir: ToolStrip Öğelerinin Aralığını ve Hizalamasını Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 550ac1660a077e8d766a01bfa8d102c07f0fbfeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182238"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Öğelerinin Aralık ve Hizalamasını Değiştirme
Denetim, <xref:System.Windows.Forms.ToolStrip> boyutlandırma, denetimlerin birbirine göre aralıkları, <xref:System.Windows.Forms.ToolStripItem> denetimlerin <xref:System.Windows.Forms.ToolStrip>düzenlenmesi ve denetimlerin belirli olması gibi düzen özelliklerini tam <xref:System.Windows.Forms.ToolStrip>olarak destekler.  
  
 Özelliğin <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> varsayılan değeri `true`olduğundan, <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> özelliği `false`'ne ayarlamadığınız sürece denetimler otomatik olarak boyutlandırılır.  
  
### <a name="to-manually-size-a-toolstripitem"></a>ToolStripItem'i el ile boyutlandırmak için  
  
1. İlişkili <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> denetim `false` için özelliği ayarlayın.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <xref:System.Windows.Forms.ToolStripItem.Size%2A> Özelliği ilişkili <xref:System.Windows.Forms.ToolStripItem>için istediğiniz şekilde ayarlayın.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>ToolStripItem'in aralığını ayarlamak için  
  
1. İstenilen değerleri pikselolarak ilişkili <xref:System.Windows.Forms.ToolStripItem.Margin%2A> denetimin özelliğine ekleyin.  
  
     <xref:System.Windows.Forms.ToolStripItem.Margin%2A> Özelliğin değerleri bu sırada madde ve bitişik öğeler arasındaki aralığı belirtir: Sol, Üst, Sağ ve Alt.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>ToolStripItem'i ToolStrip'in sağ tarafına hizalamak için  
  
1. İlişkili <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> denetim <xref:System.Windows.Forms.ToolStripItemAlignment.Right> için özelliği ayarlayın. Varsayılan olarak, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> denetimleri sol tarafa hizalayan <xref:System.Windows.Forms.ToolStripItemAlignment.Left> <xref:System.Windows.Forms.ToolStrip>, olarak ayarlanır.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>ToolStrip'teki ToolStrip öğelerini düzenlemek için  
  
- <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> Özelliği istediğiniz değere <xref:System.Windows.Forms.ToolStripLayoutStyle> ayarlayın.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
- [ToolStrip Denetim, Mimarisi](toolstrip-control-architecture.md)
- [ToolStrip Teknoloiji Özeti](toolstrip-technology-summary.md)
