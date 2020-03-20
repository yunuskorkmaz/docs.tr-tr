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
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Nasıl yapılır: Bir ToolStrip Denetimini Özel Olarak Çizme
Denetimler <xref:System.Windows.Forms.ToolStrip> aşağıdaki ilişkili işleme (boyama) sınıfları vardır:  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer>işletim sisteminizin görünümünü ve stilini sağlar.  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>Microsoft Office'in görünümünü ve stilini sağlar.  
  
- <xref:System.Windows.Forms.ToolStripRenderer>diğer iki işleme sınıfının soyut taban sınıfıdır.  
  
 Özel çizmek için (ayrıca sahibi <xref:System.Windows.Forms.ToolStrip>çizmek olarak da bilinir) a, işleyici sınıflarından birini geçersiz kılmak ve işleme mantığının bir yönünü değiştirebilirsiniz.  
  
 Aşağıdaki yordamlar özel çizim çeşitli yönlerini açıklar.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Sağlanan işleyiciler arasında geçiş yapmak için  
  
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> Özelliği istediğiniz değere <xref:System.Windows.Forms.ToolStripRenderMode> ayarlayın.  
  
     <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>Ile , <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> statik uygulamanızın işleyicibelirler. Diğer değerler <xref:System.Windows.Forms.ToolStripRenderMode> , <xref:System.Windows.Forms.ToolStripRenderMode.Custom> <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, <xref:System.Windows.Forms.ToolStripRenderMode.System>ve .  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Microsoft Office stili kenarlıkları düz olarak değiştirmek için  
  
- Geçersiz <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>kılma, ancak taban sınıf aramayın.  
  
> [!NOTE]
> Bu yöntemin bir sürümü <xref:System.Windows.Forms.ToolStripRenderer> <xref:System.Windows.Forms.ToolStripSystemRenderer>vardır <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, , , ve .  
  
### <a name="to-change-the-professionalcolortable"></a>ProfessionalColorTable'ı değiştirmek için  
  
- Geçersiz <xref:System.Windows.Forms.ProfessionalColorTable> kılın ve istediğiniz renkleri değiştirin.  
  
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
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Uygulamanızdaki tüm ToolStrip denetimleri için oluşturmayı değiştirmek için  
  
1. Sağlanan <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> işleyicilerden birini seçmek için özelliği kullanın.  
  
2. Özel <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> bir işleyici atamak için kullanın.  
  
3. <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>Varsayılan değere ayarlandığından <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> emin olun.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Tüm uygulama için Microsoft Office renklerini kapatmak için  
  
- `false`Ayarlayın. <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Tek bir ToolStrip denetimi için Microsoft Office renklerini kapatmak için  
  
- Aşağıdaki kod örneğine benzer kod kullanın.  
  
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
- [Nasıl yapılır: Windows Forms'da ToolStrip Denetimi için Özel Oluşturucu Oluşturma ve Ayarlama](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [ToolStrip Denetimine Genel Bakış](toolstrip-control-overview-windows-forms.md)
