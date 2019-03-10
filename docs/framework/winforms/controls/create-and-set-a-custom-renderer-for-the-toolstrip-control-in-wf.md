---
title: "Nasıl yapılır: Windows Forms'ta ToolStrip denetimi için özel Oluşturucu Oluşturma ve"
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
ms.openlocfilehash: 379cb8862ce5dda5cfffc625cc72906cf6a2c305
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721014"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="dc682-102">Nasıl yapılır: Windows Forms'ta ToolStrip denetimi için özel Oluşturucu Oluşturma ve</span><span class="sxs-lookup"><span data-stu-id="dc682-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="dc682-103"><xref:System.Windows.Forms.ToolStrip> denetimleri, temalar ve stilleri kolay desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc682-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="dc682-104">Tamamen özel görünümünü ve davranışını (Görünüm) ya da ayarlayarak elde edebileceğiniz <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliği veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliğini özel Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="dc682-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="dc682-105">Oluşturucular için her bir kişinin atayabilirsiniz <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, veya <xref:System.Windows.Forms.StatusStrip> denetimi veya kullanabileceğiniz <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> özelliğini ayarlayarak tüm nesneleri etkileyecek şekilde <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc682-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc682-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> döndürür <xref:System.Windows.Forms.ToolStripRenderMode.Custom> yalnızca değerini <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> değil `null`.</span><span class="sxs-lookup"><span data-stu-id="dc682-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="dc682-107">Özel oluşturucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="dc682-107">To create a custom renderer</span></span>  
  
1.  <span data-ttu-id="dc682-108">Genişletme <xref:System.Windows.Forms.ToolStripRenderer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dc682-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2.  <span data-ttu-id="dc682-109">Uygulamak istediğiniz özel işleme geçersiz kılarak uygun *üzerinde...*</span><span class="sxs-lookup"><span data-stu-id="dc682-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="dc682-110">üyeler</span><span class="sxs-lookup"><span data-stu-id="dc682-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="dc682-111">İşleyicinin geçerli olması için özel Oluşturucu ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="dc682-111">To set the custom renderer to be the current renderer</span></span>  
  
1.  <span data-ttu-id="dc682-112">Bir özel Oluşturucu ayarlanacak <xref:System.Windows.Forms.ToolStrip>ayarlayın <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliğini özel Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="dc682-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  <span data-ttu-id="dc682-113">Veya tüm özel Oluşturucu ayarlanacak <xref:System.Windows.Forms.ToolStrip> , uygulamanızda bulunan sınıfları: Ayarlama <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliğini ayarlama ve özel Oluşturucu <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğini <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="dc682-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dc682-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc682-114">See also</span></span>
- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="dc682-115">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dc682-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="dc682-116">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="dc682-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="dc682-117">ToolStrip Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="dc682-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
