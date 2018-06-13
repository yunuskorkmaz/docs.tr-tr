---
title: "Nasıl yapılır: Windows Forms'ta ToolStrip Öğelerinin Aralık ve Hizalamasını Değiştirme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 7951a545fd8cbd0ae30907922551216161171a8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531270"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Öğelerinin Aralık ve Hizalamasını Değiştirme
<xref:System.Windows.Forms.ToolStrip> Denetimi boyutlandırma, aralığını gibi yerleşim özellikleri tam olarak destekler <xref:System.Windows.Forms.ToolStripItem> denetimleri birbirlerine göre denetimlerin düzenlenmesi üzerinde <xref:System.Windows.Forms.ToolStrip>ve denetimleri göreli aralığını <xref:System.Windows.Forms.ToolStrip>.  
  
 İçin varsayılan değeri <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> özelliği `true`, denetimleri boyutta otomatik olarak ayarladığınız sürece <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> özelliğine `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>El ile bir ToolStripItem boyut için  
  
1.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> özelliğine `false` ilişkili denetimi için.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.Size%2A> özelliği ilişkili için istediğiniz şekilde <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>ToolStripItem aralığını ayarlamak için  
  
1.  Piksel cinsinden istenen değerleri takın <xref:System.Windows.Forms.ToolStripItem.Margin%2A> ilişkili denetiminin özelliği.  
  
     Değerlerini <xref:System.Windows.Forms.ToolStripItem.Margin%2A> özelliği, bu sırada öğesi ve bitişik öğeleri arasındaki aralığı belirtin: sol, üst, sağ ve alt.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>ToolStrip sağ tarafında bir ToolStripItem hizalamak için  
  
1.  Ayarlama <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> özelliğine <xref:System.Windows.Forms.ToolStripItemAlignment.Right> ilişkili denetimi için. Varsayılan olarak, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> ayarlanır <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, sol tarafındaki denetimlere hizalar <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>ToolStrip öğelerinin şeridindeki düzenlemek için  
  
-   Ayarlama <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> özellik değerine <xref:System.Windows.Forms.ToolStripLayoutStyle> istediğiniz.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [ToolStrip Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip Denetim, Mimarisi](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip Teknoloji Özeti](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
