---
title: 'Nasıl yapılır: ToolStrip denetimi için özel Oluşturucu oluşturma ve ayarlama'
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
ms.openlocfilehash: ad5ced42754fba6a714452220dd824c4f54fb5e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743414"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama
<xref:System.Windows.Forms.ToolStrip> denetimleri, temalara ve stillere kolay destek verir. <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliğini ya da <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliğini özel bir işleyiciye ayarlayarak tamamen özel görünüm ve davranış (göz atın) elde edebilirsiniz.  
  
 Her bireysel <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>veya <xref:System.Windows.Forms.StatusStrip> denetimine işlem atayabilir veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> özelliğini <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> olarak ayarlayarak tüm nesneleri etkilemek için <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>özelliğini kullanabilirsiniz.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>, yalnızca <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> değeri `null`değilse <xref:System.Windows.Forms.ToolStripRenderMode.Custom> döndürür.  
  
### <a name="to-create-a-custom-renderer"></a>Özel bir işleyici oluşturmak için  
  
1. <xref:System.Windows.Forms.ToolStripRenderer> sınıfını genişletin.  
  
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
  
1. Bir <xref:System.Windows.Forms.ToolStrip>için özel oluşturucuyu ayarlamak için, <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliğini özel Oluşturucu olarak ayarlayın.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Veya uygulamanızda bulunan tüm <xref:System.Windows.Forms.ToolStrip> sınıfları için özel oluşturucuyu ayarlamak için: <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliğini özel Oluşturucu olarak ayarlayın ve <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğini <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>olarak ayarlayın.  
  
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
