---
title: 'Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme'
ms.date: 03/30/2017
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
ms.openlocfilehash: a9f603efdb4b4a5f68154da9c6a8bd05b55b8f46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182219"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="38573-102">Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme</span><span class="sxs-lookup"><span data-stu-id="38573-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="38573-103">Denetimler <xref:System.Windows.Forms.ToolStrip> aşağıdaki ilişkili işleme (boyama) sınıfları vardır:</span><span class="sxs-lookup"><span data-stu-id="38573-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
- <span data-ttu-id="38573-104"><xref:System.Windows.Forms.ToolStripSystemRenderer>işletim sisteminizin görünümünü ve stilini sağlar.</span><span class="sxs-lookup"><span data-stu-id="38573-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
- <span data-ttu-id="38573-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer>Microsoft Office'in görünümünü ve stilini sağlar.</span><span class="sxs-lookup"><span data-stu-id="38573-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
- <span data-ttu-id="38573-106"><xref:System.Windows.Forms.ToolStripRenderer>diğer iki işleme sınıfının soyut taban sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="38573-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="38573-107">Özel çizmek için (ayrıca sahibi <xref:System.Windows.Forms.ToolStrip>çizmek olarak da bilinir) a, işleyici sınıflarından birini geçersiz kılmak ve işleme mantığının bir yönünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38573-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="38573-108">Aşağıdaki yordamlar özel çizim çeşitli yönlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="38573-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="38573-109">Sağlanan işleyiciler arasında geçiş yapmak için</span><span class="sxs-lookup"><span data-stu-id="38573-109">To switch between the provided renderers</span></span>  
  
- <span data-ttu-id="38573-110"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> Özelliği istediğiniz değere <xref:System.Windows.Forms.ToolStripRenderMode> ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="38573-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="38573-111"><xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>Ile , <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> statik uygulamanızın işleyicibelirler.</span><span class="sxs-lookup"><span data-stu-id="38573-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="38573-112">Diğer değerler <xref:System.Windows.Forms.ToolStripRenderMode> , <xref:System.Windows.Forms.ToolStripRenderMode.Custom> <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, <xref:System.Windows.Forms.ToolStripRenderMode.System>ve .</span><span class="sxs-lookup"><span data-stu-id="38573-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="38573-113">Microsoft Office stili kenarlıkları düz olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="38573-113">To change the Microsoft Office–style borders to straight</span></span>  
  
- <span data-ttu-id="38573-114">Geçersiz <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>kılma, ancak taban sınıf aramayın.</span><span class="sxs-lookup"><span data-stu-id="38573-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38573-115">Bu yöntemin bir sürümü <xref:System.Windows.Forms.ToolStripRenderer> <xref:System.Windows.Forms.ToolStripSystemRenderer>vardır <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, , , ve .</span><span class="sxs-lookup"><span data-stu-id="38573-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="38573-116">ProfessionalColorTable'ı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="38573-116">To change the ProfessionalColorTable</span></span>  
  
- <span data-ttu-id="38573-117">Geçersiz <xref:System.Windows.Forms.ProfessionalColorTable> kılın ve istediğiniz renkleri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="38573-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="38573-118">Uygulamanızdaki tüm ToolStrip denetimleri için oluşturmayı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="38573-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1. <span data-ttu-id="38573-119">Sağlanan <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> işleyicilerden birini seçmek için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="38573-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2. <span data-ttu-id="38573-120">Özel <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> bir işleyici atamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="38573-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3. <span data-ttu-id="38573-121"><xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>Varsayılan değere ayarlandığından <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> emin olun.</span><span class="sxs-lookup"><span data-stu-id="38573-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="38573-122">Tüm uygulama için Microsoft Office renklerini kapatmak için</span><span class="sxs-lookup"><span data-stu-id="38573-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
- <span data-ttu-id="38573-123">`false`Ayarlayın. <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="38573-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="38573-124">Tek bir ToolStrip denetimi için Microsoft Office renklerini kapatmak için</span><span class="sxs-lookup"><span data-stu-id="38573-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
- <span data-ttu-id="38573-125">Aşağıdaki kod örneğine benzer kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="38573-125">Use code similar to the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38573-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38573-126">See also</span></span>

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [<span data-ttu-id="38573-127">Yerleşik Sahip Çizimi Destekli Denetimler</span><span class="sxs-lookup"><span data-stu-id="38573-127">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="38573-128">Nasıl yapılır: Windows Forms'da ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama</span><span class="sxs-lookup"><span data-stu-id="38573-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [<span data-ttu-id="38573-129">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="38573-129">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
