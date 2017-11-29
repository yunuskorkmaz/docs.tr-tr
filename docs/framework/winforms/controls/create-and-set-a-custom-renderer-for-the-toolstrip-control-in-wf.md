---
title: "Nasıl yapılır: Windows Forms'ta ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f63ff0a7336ae80ce5652cf3e4c6c7dd409882a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama
<xref:System.Windows.Forms.ToolStrip>denetimleri, temalar ve stiller kolay destek verin. Ya da ayarlayarak tamamen özel görünüm ve davranış (Görünüm) gerçekleştirebilirsiniz <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliği veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özel Oluşturucu özelliğine.  
  
 Her kişi için işleyiciler atayabilirsiniz <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, veya <xref:System.Windows.Forms.StatusStrip> denetim veya kullanabilirsiniz <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> ayarlayarak tüm nesneleri etkilemek için özellik <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> özelliğine <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>döndürür <xref:System.Windows.Forms.ToolStripRenderMode.Custom> yalnızca değerini <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> değil `null`.  
  
### <a name="to-create-a-custom-renderer"></a>Özel oluşturucu oluşturmak için  
  
1.  Genişletme <xref:System.Windows.Forms.ToolStripRenderer> sınıfı.  
  
2.  Uygulama istenen özel işleme kılarak uygun *üzerinde...* üyeler  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Geçerli oluşturucusu olması için özel Oluşturucu ayarlamak için  
  
1.  Bir özel Oluşturucu ayarlamak için <xref:System.Windows.Forms.ToolStrip>ayarlayın <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özel Oluşturucu özelliğine.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  Veya tümü için özel Oluşturucu ayarlamak için <xref:System.Windows.Forms.ToolStrip> uygulamanızda bulunan sınıflar: ayarlamak <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> kümesi ve özel Oluşturucu özelliğine <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğine <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>  
 [ToolStrip denetimine genel bakış](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip denetim mimarisi](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip Teknoloiji özeti](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
