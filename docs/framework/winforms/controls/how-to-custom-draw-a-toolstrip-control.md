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
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme
<xref:System.Windows.Forms.ToolStrip> Denetimlerde aşağıdaki ilişkili işleme (boyama) sınıfları vardır:  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer>işletim sisteminizin görünüşünü ve stilini sağlar.  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>Microsoft Office görünümünü ve stilini sağlar.  
  
- <xref:System.Windows.Forms.ToolStripRenderer>, diğer iki işleme sınıfı için soyut temel sınıftır.  
  
 Özel çizim (sahip çizimi olarak da bilinir) a <xref:System.Windows.Forms.ToolStrip>için, işleyici sınıflarından birini geçersiz kılabilir ve işleme mantığının bir yönünü değiştirebilirsiniz.  
  
 Aşağıdaki yordamlar özel çizimin çeşitli yönlerini anlatmaktadır.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Belirtilen işleyicilere arasında geçiş yapmak için  
  
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> Özelliği<xref:System.Windows.Forms.ToolStripRenderMode> istediğiniz değere ayarlayın.  
  
     İle <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, statik <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> , uygulamanız için oluşturucuyu belirler. Diğer değerleri <xref:System.Windows.Forms.ToolStripRenderMode> , ve<xref:System.Windows.Forms.ToolStripRenderMode.Professional> <xref:System.Windows.Forms.ToolStripRenderMode.Custom> '<xref:System.Windows.Forms.ToolStripRenderMode.System>dir.  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Microsoft Office stili kenarlıklarını düz olarak değiştirmek için  
  
- Geçersiz <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>kıl, ancak temel sınıfı çağırmayın.  
  
> [!NOTE]
> , <xref:System.Windows.Forms.ToolStripRenderer> <xref:System.Windows.Forms.ToolStripSystemRenderer>Ve içinbuyönteminbirsürümüvardır.<xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
  
### <a name="to-change-the-professionalcolortable"></a>ProfessionalColorTable değiştirmek için  
  
- İstediğiniz <xref:System.Windows.Forms.ProfessionalColorTable> renkleri geçersiz kılın ve değiştirin.  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Uygulamanızdaki tüm ToolStrip denetimleri için işlemeyi değiştirmek için  
  
1. Bu özelliği <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> kullanarak, belirtilen oluşturuculara birini seçin.  
  
2. Özel <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> bir işleyici atamak için kullanın.  
  
3. <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> Öğesinin<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>varsayılan değerine ayarlandığından emin olun.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Tüm uygulamanın Microsoft Office renklerini devre dışı bırakmak için  
  
- <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> Olarak`false`ayarlayın.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Tek bir ToolStrip denetimi için Microsoft Office renkleri devre dışı bırakmak için  
  
- Aşağıdaki kod örneğine benzer bir kod kullanın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [Yerleşik Sahip Çizimi Destekli Denetimler](controls-with-built-in-owner-drawing-support.md)
- [Nasıl yapılır: Windows Forms ToolStrip denetimi için özel Oluşturucu oluşturma ve ayarlama](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
