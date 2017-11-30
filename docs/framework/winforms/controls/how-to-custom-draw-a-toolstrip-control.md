---
title: "Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme"
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
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abb9891fb8e4dde1e94f2d8786ece299ff6579d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="ce8e4-102">Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme</span><span class="sxs-lookup"><span data-stu-id="ce8e4-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="ce8e4-103"><xref:System.Windows.Forms.ToolStrip> Denetimleriniz aşağıdaki sınıfları (boyama) işleme ilişkili:</span><span class="sxs-lookup"><span data-stu-id="ce8e4-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
-   <span data-ttu-id="ce8e4-104"><xref:System.Windows.Forms.ToolStripSystemRenderer>işletim sisteminizi stili ve görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
-   <span data-ttu-id="ce8e4-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer>Microsoft Office stili ve görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="ce8e4-106"><xref:System.Windows.Forms.ToolStripRenderer>diğer iki işleme sınıfları için Özet temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="ce8e4-107">Özel çizim (sahibi çizim da bilinir) için bir <xref:System.Windows.Forms.ToolStrip>, oluşturucu sınıflarından biri geçersiz kılma ve bir işleme mantığı yönünü değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="ce8e4-108">Aşağıdaki yordamlar, özel çizim çeşitli yönlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="ce8e4-109">Sağlanan Oluşturucu arasında geçiş yapmak için</span><span class="sxs-lookup"><span data-stu-id="ce8e4-109">To switch between the provided renderers</span></span>  
  
-   <span data-ttu-id="ce8e4-110">Ayarlama <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> özelliğine <xref:System.Windows.Forms.ToolStripRenderMode> istediğiniz değer.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="ce8e4-111">İle <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statik <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> uygulamanız için oluşturucu belirler.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="ce8e4-112">Diğer değerlerini <xref:System.Windows.Forms.ToolStripRenderMode> olan <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, ve <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="ce8e4-113">Microsoft Office – stil kenarlıkları doğrudan değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="ce8e4-113">To change the Microsoft Office–style borders to straight</span></span>  
  
-   <span data-ttu-id="ce8e4-114">Geçersiz kılma <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, ancak temel sınıfı çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce8e4-115">Bu yöntem için sürümü <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, ve <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="ce8e4-116">ProfessionalColorTable değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="ce8e4-116">To change the ProfessionalColorTable</span></span>  
  
-   <span data-ttu-id="ce8e4-117">Geçersiz kılma <xref:System.Windows.Forms.ProfessionalColorTable> ve istediğiniz renkleri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="ce8e4-118">İşleme, uygulamanızdaki tüm ToolStrip denetimleri için değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="ce8e4-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1.  <span data-ttu-id="ce8e4-119">Kullanım <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> özelliği sağlanan Oluşturucu birini seçin.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2.  <span data-ttu-id="ce8e4-120">Kullanım <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> özel Oluşturucu atamak için.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3.  <span data-ttu-id="ce8e4-121">Emin <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> varsayılan değer olarak ayarlı <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="ce8e4-122">Microsoft Office renkleri tüm uygulama için devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="ce8e4-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
-   <span data-ttu-id="ce8e4-123">Ayarlama <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> için `false`.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="ce8e4-124">Microsoft Office renklerini bir ToolStrip denetimi için devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="ce8e4-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
-   <span data-ttu-id="ce8e4-125">Aşağıdaki kod örneğine benzer bir kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-125">Use code similar to the following code example.</span></span>  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ce8e4-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce8e4-126">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 [<span data-ttu-id="ce8e4-127">Yerleşik sahip çizimi destekli denetimler</span><span class="sxs-lookup"><span data-stu-id="ce8e4-127">Controls with Built-In Owner-Drawing Support</span></span>](../../../../docs/framework/winforms/controls/controls-with-built-in-owner-drawing-support.md)  
 [<span data-ttu-id="ce8e4-128">Nasıl yapılır: oluşturun ve ToolStrip denetimi Windows Forms için özel Oluşturucu ayarlayın</span><span class="sxs-lookup"><span data-stu-id="ce8e4-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
 [<span data-ttu-id="ce8e4-129">ToolStrip denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="ce8e4-129">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
