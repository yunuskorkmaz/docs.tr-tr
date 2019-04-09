---
title: Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: abfcb9f5398a6a8d264985543df585bea93a0446
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075281"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a><span data-ttu-id="a05b1-102">Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri</span><span class="sxs-lookup"><span data-stu-id="a05b1-102">Windows Forms Controls and Equivalent WPF Controls</span></span>
<span data-ttu-id="a05b1-103">Birçok [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminiz eşdeğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kontrol eder, ancak bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri olmayan eşdeğerleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a05b1-103">Many [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls, but some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have no equivalents in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="a05b1-104">Bu konu iki teknoloji tarafından sağlanan denetim türlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="a05b1-104">This topic compares control types provided by the two technologies.</span></span>  
  
 <span data-ttu-id="a05b1-105">Birlikte çalışabilirlik barındırmak için her zaman kullanabileceğiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] eşdeğerleri olmayan denetimleri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="a05b1-105">You can always use interoperation to host [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls that do not have equivalents in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
 <span data-ttu-id="a05b1-106">Aşağıdaki tabloda gösterir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ve bileşenleri sahip eşdeğer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] denetim işlevi.</span><span class="sxs-lookup"><span data-stu-id="a05b1-106">The following table shows which [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and components have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control functionality.</span></span>  
  
|<span data-ttu-id="a05b1-107">Windows Forms denetimi</span><span class="sxs-lookup"><span data-stu-id="a05b1-107">Windows Forms control</span></span>|<span data-ttu-id="a05b1-108">Eşdeğer WPF denetimi</span><span class="sxs-lookup"><span data-stu-id="a05b1-108">WPF equivalent control</span></span>|<span data-ttu-id="a05b1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a05b1-109">Remarks</span></span>|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|<span data-ttu-id="a05b1-110">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-110">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<xref:System.Windows.Controls.ListBox> <span data-ttu-id="a05b1-111">ile oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a05b1-111">with composition.</span></span>||  
|<xref:System.Windows.Forms.ColorDialog>|<span data-ttu-id="a05b1-112">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-112">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<xref:System.Windows.Controls.ComboBox> <span data-ttu-id="a05b1-113">Otomatik Tamamlama desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a05b1-113">does not support auto-complete.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<xref:System.Windows.Controls.TextBox> <span data-ttu-id="a05b1-114">ve iki <xref:System.Windows.Controls.Primitives.RepeatButton> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a05b1-114">and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.ErrorProvider>|<span data-ttu-id="a05b1-115">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-115">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<xref:System.Windows.Controls.WrapPanel> <span data-ttu-id="a05b1-116">veya</span><span class="sxs-lookup"><span data-stu-id="a05b1-116">or</span></span> <xref:System.Windows.Controls.StackPanel>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|<span data-ttu-id="a05b1-117">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-117">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FontDialog>|<span data-ttu-id="a05b1-118">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-118">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<xref:System.Windows.Window> <span data-ttu-id="a05b1-119">alt öğe pencerelerini desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="a05b1-119">does not support child windows.</span></span>|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|<span data-ttu-id="a05b1-120">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-120">No equivalent control.</span></span>|<span data-ttu-id="a05b1-121">F1 Yardım yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-121">No F1 Help.</span></span> <span data-ttu-id="a05b1-122">"Şudur" Yardım araç ipuçları değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="a05b1-122">"What's This" Help is replaced by ToolTips.</span></span>|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="a05b1-123">Kaydırma kapsayıcı denetimlere yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="a05b1-123">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.ImageList>|<span data-ttu-id="a05b1-124">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-124">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|<span data-ttu-id="a05b1-125">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-125">No equivalent control.</span></span>|<span data-ttu-id="a05b1-126">Kullanabileceğiniz <xref:System.Windows.Documents.Hyperlink> köprüler akış içeriği barındırmanıza sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a05b1-126">You can use the <xref:System.Windows.Documents.Hyperlink> class to host hyperlinks within flow content.</span></span>|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<span data-ttu-id="a05b1-127"><xref:System.Windows.Controls.ListView> Denetimi salt okunur Ayrıntıları görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="a05b1-127">The <xref:System.Windows.Controls.ListView> control provides a read-only details view.</span></span>|  
|<xref:System.Windows.Forms.MaskedTextBox>|<span data-ttu-id="a05b1-128">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-128">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<xref:System.Windows.Controls.Menu> <span data-ttu-id="a05b1-129">Denetim stili yaklaşık görünümünü ve davranışını <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a05b1-129">control styling can approximate the behavior and appearance of the <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> class.</span></span>|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|<span data-ttu-id="a05b1-130">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-130">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.NumericUpDown>|<xref:System.Windows.Controls.TextBox> <span data-ttu-id="a05b1-131">ve iki <xref:System.Windows.Controls.Primitives.RepeatButton> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a05b1-131">and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<span data-ttu-id="a05b1-132"><xref:Microsoft.Win32.OpenFileDialog> Sınıfı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çevresinde sarmalayıcı [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetimi.</span><span class="sxs-lookup"><span data-stu-id="a05b1-132">The <xref:Microsoft.Win32.OpenFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.PageSetupDialog>|<span data-ttu-id="a05b1-133">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-133">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|<span data-ttu-id="a05b1-134">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-134">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|<span data-ttu-id="a05b1-135">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-135">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|<span data-ttu-id="a05b1-136">Eşdeğer denetim yok.</span><span class="sxs-lookup"><span data-stu-id="a05b1-136">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<span data-ttu-id="a05b1-137"><xref:Microsoft.Win32.SaveFileDialog> Sınıfı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çevresinde sarmalayıcı [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] denetimi.</span><span class="sxs-lookup"><span data-stu-id="a05b1-137">The <xref:Microsoft.Win32.SaveFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<xref:System.Windows.Controls.ToolBar> <span data-ttu-id="a05b1-138">ile oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a05b1-138">with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<xref:System.Windows.Controls.ToolBar> <span data-ttu-id="a05b1-139">ile oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a05b1-139">with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<xref:System.Windows.Controls.ToolBar> <span data-ttu-id="a05b1-140">ile oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a05b1-140">with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripPanel>|<xref:System.Windows.Controls.ToolBar> <span data-ttu-id="a05b1-141">ile oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a05b1-141">with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="a05b1-142">Kaydırma kapsayıcı denetimlere yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="a05b1-142">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.WebBrowser>|<xref:System.Windows.Controls.Frame><span data-ttu-id="a05b1-143">,</span><span class="sxs-lookup"><span data-stu-id="a05b1-143">,</span></span> <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType>|<span data-ttu-id="a05b1-144"><xref:System.Windows.Controls.Frame> Denetimi, HTML sayfaları barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="a05b1-144">The <xref:System.Windows.Controls.Frame> control can host HTML pages.</span></span><br /><br /> <span data-ttu-id="a05b1-145">İtibariyle [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> denetimi, HTML sayfaları ve de telefonla geri barındırabilir <xref:System.Windows.Controls.Frame> denetimi.</span><span class="sxs-lookup"><span data-stu-id="a05b1-145">Starting in the [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], the <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> control can host HTML pages and also backs the <xref:System.Windows.Controls.Frame> control.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a05b1-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a05b1-146">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="a05b1-147">Windows için WPF Tasarımcısı geliştiriciler formlar</span><span class="sxs-lookup"><span data-stu-id="a05b1-147">WPF Designer for Windows Forms Developers</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))
- [<span data-ttu-id="a05b1-148">İzlenecek yol: WPF içinde Windows Forms Denetimi Barındırma</span><span class="sxs-lookup"><span data-stu-id="a05b1-148">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="a05b1-149">İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma</span><span class="sxs-lookup"><span data-stu-id="a05b1-149">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="a05b1-150">Geçiş ve Birlikte Çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="a05b1-150">Migration and Interoperability</span></span>](migration-and-interoperability.md)
