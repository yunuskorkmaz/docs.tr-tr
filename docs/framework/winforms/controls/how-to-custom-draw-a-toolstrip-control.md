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
ms.openlocfilehash: 810a680a1a9d9065e80ed87453a728fe628a953d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935363"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="595b7-102">Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme</span><span class="sxs-lookup"><span data-stu-id="595b7-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="595b7-103"><xref:System.Windows.Forms.ToolStrip> Denetimlerde aşağıdaki ilişkili işleme (boyama) sınıfları vardır:</span><span class="sxs-lookup"><span data-stu-id="595b7-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
- <span data-ttu-id="595b7-104"><xref:System.Windows.Forms.ToolStripSystemRenderer>işletim sisteminizin görünüşünü ve stilini sağlar.</span><span class="sxs-lookup"><span data-stu-id="595b7-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
- <span data-ttu-id="595b7-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer>Microsoft Office görünümünü ve stilini sağlar.</span><span class="sxs-lookup"><span data-stu-id="595b7-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
- <span data-ttu-id="595b7-106"><xref:System.Windows.Forms.ToolStripRenderer>, diğer iki işleme sınıfı için soyut temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="595b7-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="595b7-107">Özel çizim (sahip çizimi olarak da bilinir) a <xref:System.Windows.Forms.ToolStrip>için, işleyici sınıflarından birini geçersiz kılabilir ve işleme mantığının bir yönünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="595b7-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="595b7-108">Aşağıdaki yordamlar özel çizimin çeşitli yönlerini anlatmaktadır.</span><span class="sxs-lookup"><span data-stu-id="595b7-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="595b7-109">Belirtilen işleyicilere arasında geçiş yapmak için</span><span class="sxs-lookup"><span data-stu-id="595b7-109">To switch between the provided renderers</span></span>  
  
- <span data-ttu-id="595b7-110"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> Özelliği<xref:System.Windows.Forms.ToolStripRenderMode> istediğiniz değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="595b7-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="595b7-111">İle <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statik <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> , uygulamanız için oluşturucuyu belirler.</span><span class="sxs-lookup"><span data-stu-id="595b7-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="595b7-112">Diğer değerleri <xref:System.Windows.Forms.ToolStripRenderMode> , ve<xref:System.Windows.Forms.ToolStripRenderMode.Professional> <xref:System.Windows.Forms.ToolStripRenderMode.Custom> '<xref:System.Windows.Forms.ToolStripRenderMode.System>dir.</span><span class="sxs-lookup"><span data-stu-id="595b7-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="595b7-113">Microsoft Office stili kenarlıklarını düz olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="595b7-113">To change the Microsoft Office–style borders to straight</span></span>  
  
- <span data-ttu-id="595b7-114">Geçersiz <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>kıl, ancak temel sınıfı çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="595b7-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="595b7-115">, <xref:System.Windows.Forms.ToolStripRenderer> <xref:System.Windows.Forms.ToolStripSystemRenderer>Ve içinbuyönteminbirsürümüvardır.<xref:System.Windows.Forms.ToolStripProfessionalRenderer></span><span class="sxs-lookup"><span data-stu-id="595b7-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="595b7-116">ProfessionalColorTable değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="595b7-116">To change the ProfessionalColorTable</span></span>  
  
- <span data-ttu-id="595b7-117">İstediğiniz <xref:System.Windows.Forms.ProfessionalColorTable> renkleri geçersiz kılın ve değiştirin.</span><span class="sxs-lookup"><span data-stu-id="595b7-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="595b7-118">Uygulamanızdaki tüm ToolStrip denetimleri için işlemeyi değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="595b7-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1. <span data-ttu-id="595b7-119">Bu özelliği <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> kullanarak, belirtilen oluşturuculara birini seçin.</span><span class="sxs-lookup"><span data-stu-id="595b7-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2. <span data-ttu-id="595b7-120">Özel <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> bir işleyici atamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="595b7-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3. <span data-ttu-id="595b7-121"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> Öğesinin<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>varsayılan değerine ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="595b7-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="595b7-122">Tüm uygulamanın Microsoft Office renklerini devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="595b7-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
- <span data-ttu-id="595b7-123"><xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> Olarak`false`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="595b7-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="595b7-124">Tek bir ToolStrip denetimi için Microsoft Office renkleri devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="595b7-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
- <span data-ttu-id="595b7-125">Aşağıdaki kod örneğine benzer bir kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="595b7-125">Use code similar to the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="595b7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="595b7-126">See also</span></span>

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [<span data-ttu-id="595b7-127">Yerleşik Sahip Çizimi Destekli Denetimler</span><span class="sxs-lookup"><span data-stu-id="595b7-127">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="595b7-128">Nasıl yapılır: Windows Forms ToolStrip denetimi için özel Oluşturucu oluşturma ve ayarlama</span><span class="sxs-lookup"><span data-stu-id="595b7-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [<span data-ttu-id="595b7-129">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="595b7-129">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
