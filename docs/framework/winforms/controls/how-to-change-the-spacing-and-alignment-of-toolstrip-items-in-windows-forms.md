---
title: 'Nasıl yapılır: ToolStrip öğelerinin aralıklarını ve hizalamasını değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 805fbac5fe33071006f29692d503e5c57eacd765
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746557"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Öğelerinin Aralık ve Hizalamasını Değiştirme
<xref:System.Windows.Forms.ToolStrip> denetimi, boyutlandırma, birbirleriyle ilgili <xref:System.Windows.Forms.ToolStripItem> denetimlerinin aralığı, <xref:System.Windows.Forms.ToolStrip>denetim yerleşimi ve <xref:System.Windows.Forms.ToolStrip>göreli denetimlerin boşlukları gibi düzen özelliklerini tam olarak destekler.  
  
 <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> özelliğinin varsayılan değeri `true`olduğundan, <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> özelliğini `false`olarak ayarlamadığınız takdirde denetimler otomatik olarak boyutlandırılır.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Bir ToolStripItem 'ı el ile boyutlandırma  
  
1. <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> özelliğini ilişkili denetim için `false` olarak ayarlayın.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. <xref:System.Windows.Forms.ToolStripItem.Size%2A> özelliğini ilişkili <xref:System.Windows.Forms.ToolStripItem>istediğiniz şekilde ayarlayın.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Bir ToolStripItem 'ın aralığını ayarlamak için  
  
1. İstenen değerleri piksel cinsinden, ilişkili denetimin <xref:System.Windows.Forms.ToolStripItem.Margin%2A> özelliğine ekleyin.  
  
     <xref:System.Windows.Forms.ToolStripItem.Margin%2A> özelliğinin değerleri, öğe ve bitişik öğeler arasındaki boşluğu şu sırada belirtir: Left, top, Right ve Bottom.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Bir ToolStripItem 'ı ToolStrip 'in sağ tarafına hizalamak için  
  
1. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> özelliğini ilişkili denetim için <xref:System.Windows.Forms.ToolStripItemAlignment.Right> olarak ayarlayın. Varsayılan olarak <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>, denetimleri <xref:System.Windows.Forms.ToolStrip>sol tarafına hizalayan <xref:System.Windows.Forms.ToolStripItemAlignment.Left>olarak ayarlanır.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>ToolStrip 'te ToolStrip öğelerini düzenlemek için  
  
- <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> özelliğini istediğiniz <xref:System.Windows.Forms.ToolStripLayoutStyle> değerine ayarlayın.  
  
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
- [ToolStrip Teknoloji Özeti](toolstrip-technology-summary.md)
