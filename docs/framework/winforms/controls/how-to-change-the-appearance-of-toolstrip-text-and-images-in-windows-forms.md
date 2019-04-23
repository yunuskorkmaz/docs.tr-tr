---
title: "Nasıl yapılır: Windows Forms'da ToolStrip Metni ve Resimlerinin Görünüşünü Değiştirme"
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
ms.openlocfilehash: 5c326c8f6a56c934d317305f85f4c88e95e75f8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088489"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Nasıl yapılır: Windows Forms'da ToolStrip Metni ve Resimlerinin Görünüşünü Değiştirme
Metin ve görüntüleri üzerinde görüntülenip görüntülenmeyeceğini denetleyebileceğiniz bir <xref:System.Windows.Forms.ToolStripItem> ve nasıl birbirlerine göreli hizalandığını ve <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Üzerinde ToolStripItem görüntülenenleri tanımlamak için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini istediğiniz değer. Olasılıklar `Image`, `ImageAndText`, `None`, ve `Text`. Varsayılan, `ImageAndText` değeridir.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>ToolStripItem metni hizalama  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> özelliğini istediğiniz değer. Olasılıkları üstünde, Orta ve alt sol, Orta ve sağ ile herhangi bir birleşimini şunlardır. Varsayılan, `MiddleCenter` değeridir.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Görüntünün üzerinde ToolStripItem hizalamak için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> özelliğini istediğiniz değer. Olasılıkları üstünde, Orta ve alt sol, Orta ve sağ ile herhangi bir birleşimini şunlardır. Varsayılan, `MiddleLeft` değeridir.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>ToolStripItem metin ve görüntüleri birbirine göre nasıl görüntüleneceğini tanımlamak için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> özelliğini istediğiniz değer. Olasılıklar `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, ve `TextBeforeImage`. Varsayılan, `ImageBeforeText` değeridir.  
  
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
