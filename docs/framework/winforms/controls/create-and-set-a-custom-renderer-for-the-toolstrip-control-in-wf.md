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
ms.openlocfilehash: d8a85edf8c001b19191fdfd74d1f9ebdf87024ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195494"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="8b2f1-102">Nasıl yapılır: Windows Forms'da ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="8b2f1-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<xref:System.Windows.Forms.ToolStrip> <span data-ttu-id="8b2f1-103">denetimleri, temalar ve stilleri kolay desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-103">controls give easy support to themes and styles.</span></span> <span data-ttu-id="8b2f1-104">Tamamen özel görünümünü ve davranışını (Görünüm) ya da ayarlayarak elde edebileceğiniz <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliği veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliğini özel Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="8b2f1-105">Oluşturucular için her bir kişinin atayabilirsiniz <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, veya <xref:System.Windows.Forms.StatusStrip> denetimi veya kullanabileceğiniz <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> özelliğini ayarlayarak tüm nesneleri etkileyecek şekilde <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> <span data-ttu-id="8b2f1-106">döndürür <xref:System.Windows.Forms.ToolStripRenderMode.Custom> yalnızca değerini <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> değil `null`.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-106">returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="8b2f1-107">Özel oluşturucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b2f1-107">To create a custom renderer</span></span>  
  
1.  <span data-ttu-id="8b2f1-108">Genişletme <xref:System.Windows.Forms.ToolStripRenderer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2.  <span data-ttu-id="8b2f1-109">Uygulamak istediğiniz özel işleme geçersiz kılarak uygun *üzerinde...*</span><span class="sxs-lookup"><span data-stu-id="8b2f1-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="8b2f1-110">üyeler</span><span class="sxs-lookup"><span data-stu-id="8b2f1-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="8b2f1-111">İşleyicinin geçerli olması için özel Oluşturucu ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8b2f1-111">To set the custom renderer to be the current renderer</span></span>  
  
1.  <span data-ttu-id="8b2f1-112">Bir özel Oluşturucu ayarlanacak <xref:System.Windows.Forms.ToolStrip>ayarlayın <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> özelliğini özel Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  <span data-ttu-id="8b2f1-113">Veya tüm özel Oluşturucu ayarlanacak <xref:System.Windows.Forms.ToolStrip> , uygulamanızda bulunan sınıfları: Ayarlama <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliğini ayarlama ve özel Oluşturucu <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğini <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8b2f1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b2f1-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="8b2f1-115">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8b2f1-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="8b2f1-116">ToolStrip Denetim Mimarisi</span><span class="sxs-lookup"><span data-stu-id="8b2f1-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="8b2f1-117">ToolStrip Teknoloiji Özeti</span><span class="sxs-lookup"><span data-stu-id="8b2f1-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
