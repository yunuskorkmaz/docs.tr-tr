---
title: 'Nasıl yapılır: ToolStrip metin ve görüntülerinin görünümünü değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: 7816e138e44554683c201895ece1f886ace8bfa6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746602"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Metni ve Resimlerinin Görünüşünü Değiştirme
Metin ve görüntülerin <xref:System.Windows.Forms.ToolStripItem> gösterilip gösterilmeyeceğini ve bunların birbirlerine ve <xref:System.Windows.Forms.ToolStrip>göre nasıl hizalandığını kontrol edebilirsiniz.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>ToolStripItem üzerinde neyin görüntülendiğini tanımlamak için  
  
- <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini istenen değere ayarlayın. `Image`, `ImageAndText`, `None`ve `Text`olanakları vardır. Varsayılan, `ImageAndText` değeridir.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Bir ToolStripItem üzerinde metin hizalamak için  
  
- <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> özelliğini istenen değere ayarlayın. Bu olanaklar, sol, orta ve sağ ile herhangi bir üst, orta ve alt bileşimdir. Varsayılan, `MiddleCenter` değeridir.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>ToolStripItem üzerinde bir görüntüyü hizalamak için  
  
- <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> özelliğini istenen değere ayarlayın. Bu olanaklar, sol, orta ve sağ ile herhangi bir üst, orta ve alt bileşimdir. Varsayılan, `MiddleLeft` değeridir.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>ToolStripItem metninin ve görüntülerinin birbirlerine göre nasıl görüntülendiğini tanımlamak için  
  
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> özelliğini istenen değere ayarlayın. `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`ve `TextBeforeImage`olanakları vardır. Varsayılan, `ImageBeforeText` değeridir.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
- [ToolStrip Denetim, Mimarisi](toolstrip-control-architecture.md)
- [ToolStrip Teknoloji Özeti](toolstrip-technology-summary.md)
