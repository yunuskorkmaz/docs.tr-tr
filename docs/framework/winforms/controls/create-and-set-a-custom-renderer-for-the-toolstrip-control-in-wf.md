---
title: 'Nasıl yapılı: ToolStrip Denetimi için Özel Bir Görüntüleyici Oluşturma ve Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: 49db0d785155f19b7220ac64011eaf4253aaa7e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182397"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama
<xref:System.Windows.Forms.ToolStrip>kontroller temalara ve stiller kolay destek verir. <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> Özelliği veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliği özel bir işleyiciye ayarlayarak tamamen özel görünüm ve davranış (görünüm ve his) elde edebilirsiniz.  
  
 Her bireye <xref:System.Windows.Forms.ToolStrip>, , <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>veya <xref:System.Windows.Forms.StatusStrip> denetime görüntüleyiciatlayabilir <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> veya <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> özelliği ' ye ayarlayarak <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>tüm nesneleri etkilemek için özelliği kullanabilirsiniz.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>değeri <xref:System.Windows.Forms.ToolStripRenderMode.Custom> değilse `null`yalnızca <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> döndürür.  
  
### <a name="to-create-a-custom-renderer"></a>Özel bir işleyici oluşturmak için  
  
1. Sınıfı <xref:System.Windows.Forms.ToolStripRenderer> genişletin.  
  
2. Uygun On geçersiz kılarak istenilen özel işleme *uygulayın...* üyeler  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Özel işleyiciyi geçerli işleyici olarak ayarlamak için  
  
1. Özel işleyiciyi bir <xref:System.Windows.Forms.ToolStrip>tanesine <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> ayarlamak için, özelliği özel işleyiciye ayarlayın.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Veya uygulamanızda bulunan <xref:System.Windows.Forms.ToolStrip> tüm sınıflar için özel işleyiciyi ayarlamak için: <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> Özelliği <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özel <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>işleyiciye ayarlayın ve özelliği 'ne ayarlayın.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
- [ToolStrip Denetim, Mimarisi](toolstrip-control-architecture.md)
- [ToolStrip Teknoloiji Özeti](toolstrip-technology-summary.md)
