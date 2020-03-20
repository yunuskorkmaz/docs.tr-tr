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
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="b121d-102">Nasıl yapılır: Windows Forms'ta ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="b121d-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="b121d-103"><xref:System.Windows.Forms.ToolStrip>kontroller temalara ve stiller kolay destek verir.</span><span class="sxs-lookup"><span data-stu-id="b121d-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="b121d-104"><xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> Özelliği veya <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özelliği özel bir işleyiciye ayarlayarak tamamen özel görünüm ve davranış (görünüm ve his) elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b121d-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="b121d-105">Her bireye <xref:System.Windows.Forms.ToolStrip>, , <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>veya <xref:System.Windows.Forms.StatusStrip> denetime görüntüleyiciatlayabilir <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> veya <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> özelliği ' ye ayarlayarak <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>tüm nesneleri etkilemek için özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b121d-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b121d-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>değeri <xref:System.Windows.Forms.ToolStripRenderMode.Custom> değilse `null`yalnızca <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> döndürür.</span><span class="sxs-lookup"><span data-stu-id="b121d-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="b121d-107">Özel bir işleyici oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b121d-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="b121d-108">Sınıfı <xref:System.Windows.Forms.ToolStripRenderer> genişletin.</span><span class="sxs-lookup"><span data-stu-id="b121d-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="b121d-109">Uygun On geçersiz kılarak istenilen özel işleme *uygulayın...*</span><span class="sxs-lookup"><span data-stu-id="b121d-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="b121d-110">üyeler</span><span class="sxs-lookup"><span data-stu-id="b121d-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="b121d-111">Özel işleyiciyi geçerli işleyici olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b121d-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="b121d-112">Özel işleyiciyi bir <xref:System.Windows.Forms.ToolStrip>tanesine <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> ayarlamak için, özelliği özel işleyiciye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b121d-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="b121d-113">Veya uygulamanızda bulunan <xref:System.Windows.Forms.ToolStrip> tüm sınıflar için özel işleyiciyi ayarlamak için: <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> Özelliği <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özel <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>işleyiciye ayarlayın ve özelliği 'ne ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b121d-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b121d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b121d-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="b121d-115">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b121d-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="b121d-116">ToolStrip Denetim, Mimarisi</span><span class="sxs-lookup"><span data-stu-id="b121d-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="b121d-117">ToolStrip Teknoloiji Özeti</span><span class="sxs-lookup"><span data-stu-id="b121d-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
