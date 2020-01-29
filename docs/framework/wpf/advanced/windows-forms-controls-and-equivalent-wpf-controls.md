---
title: Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: 7f531b60d8b31181688f3d0a6753b234ffc6c7dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735211"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a><span data-ttu-id="27890-102">Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri</span><span class="sxs-lookup"><span data-stu-id="27890-102">Windows Forms Controls and Equivalent WPF Controls</span></span>
<span data-ttu-id="27890-103">Birçok [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminin eşdeğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetimleri vardır ancak bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]eşdeğerleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="27890-103">Many [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls, but some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have no equivalents in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="27890-104">Bu konu, iki teknoloji tarafından sunulan denetim türlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="27890-104">This topic compares control types provided by the two technologies.</span></span>  
  
 <span data-ttu-id="27890-105">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulamalarınızda eşdeğerleri olmayan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri barındırmak için her zaman karşılıklı çalışma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27890-105">You can always use interoperation to host [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls that do not have equivalents in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
 <span data-ttu-id="27890-106">Aşağıdaki tabloda, hangi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinin ve bileşenlerin eşdeğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim işlevselliğine sahip olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="27890-106">The following table shows which [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and components have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control functionality.</span></span>  
  
|<span data-ttu-id="27890-107">Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="27890-107">Windows Forms control</span></span>|<span data-ttu-id="27890-108">WPF denk denetimi</span><span class="sxs-lookup"><span data-stu-id="27890-108">WPF equivalent control</span></span>|<span data-ttu-id="27890-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27890-109">Remarks</span></span>|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|<span data-ttu-id="27890-110">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-110">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<span data-ttu-id="27890-111">birleşim ile <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="27890-111"><xref:System.Windows.Controls.ListBox> with composition.</span></span>||  
|<xref:System.Windows.Forms.ColorDialog>|<span data-ttu-id="27890-112">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-112">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<span data-ttu-id="27890-113"><xref:System.Windows.Controls.ComboBox> otomatik tamamlamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="27890-113"><xref:System.Windows.Controls.ComboBox> does not support auto-complete.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<span data-ttu-id="27890-114"><xref:System.Windows.Controls.TextBox> ve iki <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="27890-114"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.ErrorProvider>|<span data-ttu-id="27890-115">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-115">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<span data-ttu-id="27890-116"><xref:System.Windows.Controls.WrapPanel> veya <xref:System.Windows.Controls.StackPanel></span><span class="sxs-lookup"><span data-stu-id="27890-116"><xref:System.Windows.Controls.WrapPanel> or <xref:System.Windows.Controls.StackPanel></span></span>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|<span data-ttu-id="27890-117">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-117">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FontDialog>|<span data-ttu-id="27890-118">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-118">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<span data-ttu-id="27890-119"><xref:System.Windows.Window> alt pencereleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="27890-119"><xref:System.Windows.Window> does not support child windows.</span></span>|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|<span data-ttu-id="27890-120">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-120">No equivalent control.</span></span>|<span data-ttu-id="27890-121">F1 yardımı yok.</span><span class="sxs-lookup"><span data-stu-id="27890-121">No F1 Help.</span></span> <span data-ttu-id="27890-122">"Bu nedir?" yardımı araç Ipuçlarında değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="27890-122">"What's This" Help is replaced by ToolTips.</span></span>|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="27890-123">Kaydırma, kapsayıcı denetimlerinde yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="27890-123">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.ImageList>|<span data-ttu-id="27890-124">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-124">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|<span data-ttu-id="27890-125">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-125">No equivalent control.</span></span>|<span data-ttu-id="27890-126">Akış içeriği içindeki köprüleri barındırmak için <xref:System.Windows.Documents.Hyperlink> sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27890-126">You can use the <xref:System.Windows.Documents.Hyperlink> class to host hyperlinks within flow content.</span></span>|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<span data-ttu-id="27890-127"><xref:System.Windows.Controls.ListView> denetimi salt okunurdur Ayrıntılar görünümü sağlar.</span><span class="sxs-lookup"><span data-stu-id="27890-127">The <xref:System.Windows.Controls.ListView> control provides a read-only details view.</span></span>|  
|<xref:System.Windows.Forms.MaskedTextBox>|<span data-ttu-id="27890-128">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-128">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<span data-ttu-id="27890-129"><xref:System.Windows.Controls.Menu> denetim stili, <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> sınıfının davranışını ve görünümünü yaklaşık olarak değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="27890-129"><xref:System.Windows.Controls.Menu> control styling can approximate the behavior and appearance of the <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> class.</span></span>|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|<span data-ttu-id="27890-130">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-130">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.NumericUpDown>|<span data-ttu-id="27890-131"><xref:System.Windows.Controls.TextBox> ve iki <xref:System.Windows.Controls.Primitives.RepeatButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="27890-131"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<span data-ttu-id="27890-132"><xref:Microsoft.Win32.OpenFileDialog> sınıfı, Win32 denetiminin etrafındaki bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sarmalayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="27890-132">The <xref:Microsoft.Win32.OpenFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the Win32 control.</span></span>|  
|<xref:System.Windows.Forms.PageSetupDialog>|<span data-ttu-id="27890-133">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-133">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|<span data-ttu-id="27890-134">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-134">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|<span data-ttu-id="27890-135">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-135">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|<span data-ttu-id="27890-136">Denk denetim yok.</span><span class="sxs-lookup"><span data-stu-id="27890-136">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<span data-ttu-id="27890-137"><xref:Microsoft.Win32.SaveFileDialog> sınıfı, Win32 denetiminin etrafındaki bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sarmalayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="27890-137">The <xref:Microsoft.Win32.SaveFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the Win32 control.</span></span>|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="27890-138">birleşim ile <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="27890-138"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="27890-139">birleşim ile <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="27890-139"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<span data-ttu-id="27890-140">birleşim ile <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="27890-140"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripPanel>|<span data-ttu-id="27890-141">birleşim ile <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="27890-141"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="27890-142">Kaydırma, kapsayıcı denetimlerinde yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="27890-142">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.WebBrowser>|<span data-ttu-id="27890-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="27890-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span></span>|<span data-ttu-id="27890-144"><xref:System.Windows.Controls.Frame> denetim HTML sayfalarını barındırabilirler.</span><span class="sxs-lookup"><span data-stu-id="27890-144">The <xref:System.Windows.Controls.Frame> control can host HTML pages.</span></span><br /><br /> <span data-ttu-id="27890-145">.NET Framework 3,5 SP1 'den başlayarak, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> denetim HTML sayfalarını barındırabilir ve ayrıca <xref:System.Windows.Controls.Frame> denetimini geri alabilir.</span><span class="sxs-lookup"><span data-stu-id="27890-145">Starting in the .NET Framework 3.5 SP1, the <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> control can host HTML pages and also backs the <xref:System.Windows.Controls.Frame> control.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27890-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27890-146">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- <span data-ttu-id="27890-147">[Windows Forms geliştiricileri için WPF Tasarımcısı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="27890-147">[WPF Designer for Windows Forms Developers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))</span></span>
- [<span data-ttu-id="27890-148">İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma</span><span class="sxs-lookup"><span data-stu-id="27890-148">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="27890-149">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="27890-149">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="27890-150">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="27890-150">Migration and Interoperability</span></span>](migration-and-interoperability.md)
