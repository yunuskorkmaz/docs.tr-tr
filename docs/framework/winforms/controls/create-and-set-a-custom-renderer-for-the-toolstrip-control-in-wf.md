---
title: "Nasıl yapılır: Windows Forms'da ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama"
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
ms.openlocfilehash: c354ace3a7d3ce43f549dd1295a85fbee004eb22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929735"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Nasıl yapılır: Windows Forms'da ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama
<xref:System.Windows.Forms.ToolStrip>denetimler, temalara ve stillere kolay destek verir. <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> Özelliği<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> ya da özelliği özel bir işleyiciye ayarlayarak tamamen özel görünüm ve davranış elde edebilirsiniz (göz atın).  
  
 Her <xref:System.Windows.Forms.ToolStrip>kişiye <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> ,,<xref:System.Windows.Forms.ToolStripManager.Renderer%2A> veya denetime<xref:System.Windows.Forms.StatusStrip> işlem atayabilir veya özelliği ' e<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>ayarlayarak tüm nesneleri etkilemek için özelliğini kullanabilirsiniz. <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>yalnızca <xref:System.Windows.Forms.ToolStripRenderMode.Custom> değeri<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> değilse döndürür`null`.  
  
### <a name="to-create-a-custom-renderer"></a>Özel bir işleyici oluşturmak için  
  
1. <xref:System.Windows.Forms.ToolStripRenderer> Sınıfı genişletin.  
  
2. Uygun üzerine yazarak istenen özel işlemeyi uygulayın *...* üyeler  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Özel oluşturucuyu geçerli işleyici olacak şekilde ayarlamak için  
  
1. Özel Oluşturucuyu bir <xref:System.Windows.Forms.ToolStrip>için ayarlamak için, <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliği özel işleyiciye ayarlayın.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Veya uygulamanızda bulunan tüm <xref:System.Windows.Forms.ToolStrip> sınıflar için özel oluşturucuyu ayarlamak için: Özelliği özel Oluşturucu olarak ayarlayın ve <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğini olarak <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>ayarlayın. <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>  
  
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
- [ToolStrip Teknoloji Özeti](toolstrip-technology-summary.md)
