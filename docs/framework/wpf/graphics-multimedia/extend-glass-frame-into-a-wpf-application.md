---
title: Cam Çerçeveyi WPF Uygulamasında Genişletme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
ms.openlocfilehash: 11c872767b5e3595da1fb4982d3b12e0fc77db98
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238596"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="11262-102">Cam Çerçeveyi WPF Uygulamasında Genişletme</span><span class="sxs-lookup"><span data-stu-id="11262-102">Extend Glass Frame Into a WPF Application</span></span>

<span data-ttu-id="11262-103">Bu konu nasıl genişleteceğinizi gösterir [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] cam çerçeveyi bir Windows Presentation Foundation (WPF) uygulamasının istemci alanına.</span><span class="sxs-lookup"><span data-stu-id="11262-103">This topic demonstrates how to extend the [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] glass frame into the client area of a Windows Presentation Foundation (WPF) application.</span></span>

> [!NOTE]
> <span data-ttu-id="11262-104">Bu örnek yalnızca çalışır bir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] etkin cam ile Masaüstü Pencere Yöneticisi'ni (DWM) çalıştıran makine.</span><span class="sxs-lookup"><span data-stu-id="11262-104">This example will only work on a [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] <span data-ttu-id="11262-105">Home Basic sürümü saydam cam etkisi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="11262-105">Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="11262-106">Genellikle diğer sürümleri üzerinde saydam cam etkisi ile işlenen alanları [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] donuk işlenir.</span><span class="sxs-lookup"><span data-stu-id="11262-106">Areas that would typically render with the transparent glass effect on other editions of [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] are rendered opaque.</span></span>

## <a name="example"></a><span data-ttu-id="11262-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="11262-107">Example</span></span>

<span data-ttu-id="11262-108">Aşağıdaki görüntüde, adres çubuğuna, Internet Explorer'a 7 genişletilmiş cam çerçeveyi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="11262-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7:</span></span>

![Cam çerçeveyi IE7 adres çubuğuna genişletilmiş gösteren ekran görüntüsü.](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

<span data-ttu-id="11262-110">Üzerinde cam çerçeveyi genişletmek için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulaması yönetilmeyen API erişimi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="11262-110">To extend the glass frame on a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application, access to unmanaged API is needed.</span></span> <span data-ttu-id="11262-111">Aşağıdaki kod örneği, istemci alanına çerçeveyi genişletmek için gereken iki API için Platform Çağırma (PInvoke) desteklemez.</span><span class="sxs-lookup"><span data-stu-id="11262-111">The following code example does a Platform Invoke (pinvoke) for the two API needed to extend the frame into the client area.</span></span> <span data-ttu-id="11262-112">Bu API'nin her adlı bir sınıf içinde bildirildiğinde **NonClientRegionAPI**.</span><span class="sxs-lookup"><span data-stu-id="11262-112">Each of these API are declared in a class called **NonClientRegionAPI**.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential)]
public struct MARGINS
{
    public int cxLeftWidth;      // width of left border that retains its size
    public int cxRightWidth;     // width of right border that retains its size
    public int cyTopHeight;      // height of top border that retains its size
    public int cyBottomHeight;   // height of bottom border that retains its size
};

[DllImport("DwmApi.dll")]
public static extern int DwmExtendFrameIntoClientArea(
    IntPtr hwnd,
    ref MARGINS pMarInset);
```

```vb
<StructLayout(LayoutKind.Sequential)>
Public Structure MARGINS
    Public cxLeftWidth As Integer ' width of left border that retains its size
    Public cxRightWidth As Integer ' width of right border that retains its size
    Public cyTopHeight As Integer ' height of top border that retains its size
    Public cyBottomHeight As Integer ' height of bottom border that retains its size
End Structure

<DllImport("DwmApi.dll")>
Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer
End Function
```

<span data-ttu-id="11262-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) çerçevenin istemci alanına genişleten DWM işlevdir.</span><span class="sxs-lookup"><span data-stu-id="11262-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="11262-114">İki parametre alır; bir pencere tutucu ve [kenar BOŞLUKLARI](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) yapısı.</span><span class="sxs-lookup"><span data-stu-id="11262-114">It takes two parameters; a window handle and a [MARGINS](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) structure.</span></span> <span data-ttu-id="11262-115">[Kenar BOŞLUKLARI](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) DWM çerçevenin istemci alanına ne kadar çok genişletilmiş söylemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11262-115">[MARGINS](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>

## <a name="example"></a><span data-ttu-id="11262-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="11262-116">Example</span></span>

<span data-ttu-id="11262-117">Kullanılacak [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) işlevi, bir pencere tutucu gerekir elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="11262-117">To use the [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) function, a window handle must be obtained.</span></span> <span data-ttu-id="11262-118">İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], pencere işleyicisi örneğinden alınabilen <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği bir <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="11262-118">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="11262-119">Aşağıdaki örnekte, çerçevenin istemci alanını genişletilir <xref:System.Windows.FrameworkElement.Loaded> penceresinin olay.</span><span class="sxs-lookup"><span data-stu-id="11262-119">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>

```csharp
void OnLoaded(object sender, RoutedEventArgs e)
{
   try
   {
      // Obtain the window handle for WPF application
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);

      // Get System Dpi
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);
      float DesktopDpiX = desktop.DpiX;
      float DesktopDpiY = desktop.DpiY;

      // Set Margins
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();

      // Extend glass frame into client area
      // Note that the default desktop Dpi is 96dpi. The  margins are
      // adjusted for the system Dpi.
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));

      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);
      //
      if (hr < 0)
      {
         //DwmExtendFrameIntoClientArea Failed
      }
   }
   // If not Vista, paint background white.
   catch (DllNotFoundException)
   {
      Application.Current.MainWindow.Background = Brushes.White;
   }
}
```

## <a name="example"></a><span data-ttu-id="11262-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="11262-120">Example</span></span>

<span data-ttu-id="11262-121">Aşağıdaki örnek, çerçevenin istemci alanını genişletilir basit bir pencere gösterir.</span><span class="sxs-lookup"><span data-stu-id="11262-121">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="11262-122">İki içeren üst kenarlık genişletilen çerçeve <xref:System.Windows.Controls.TextBox> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="11262-122">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>

```xaml
<Window x:Class="SDKSample.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Extended Glass in WPF" Height="300" Width="400"
    Loaded="OnLoaded" Background="Transparent"
    >
  <Grid ShowGridLines="True">
    <DockPanel Name="mainDock">
      <!-- The border is used to compute the rendered height with margins.
           topBar contents will be displayed on the extended glass frame.-->
      <Border Name="topBar" DockPanel.Dock="Top" >
        <Grid Name="grid">
          <Grid.ColumnDefinitions>
            <ColumnDefinition MinWidth="100" Width="*"/>
            <ColumnDefinition Width="Auto"/>
          </Grid.ColumnDefinitions>
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>
        </Grid>
      </Border>
      <Grid DockPanel.Dock="Top" >
        <Grid.ColumnDefinitions>
          <ColumnDefinition/>
        </Grid.ColumnDefinitions>
        <TextBox Grid.Column="0" AcceptsReturn="True"/>
      </Grid>
    </DockPanel>
  </Grid>
</Window>
```

<span data-ttu-id="11262-123">Aşağıdaki görüntüde gösterilmiştir uygulamasına genişletilmiş cam çerçeveyi bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama:</span><span class="sxs-lookup"><span data-stu-id="11262-123">The following image illustrates the glass frame extended into a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application:</span></span>

![Cam çerçeveyi WPF uygulamasında genişletilmiş gösteren ekran görüntüsü.](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a><span data-ttu-id="11262-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11262-125">See also</span></span>

- [<span data-ttu-id="11262-126">Masaüstü Pencere Yöneticisi'ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="11262-126">Desktop Window Manager Overview</span></span>](/windows/desktop/dwm/dwm-overview)
- [<span data-ttu-id="11262-127">Masaüstü Pencere Yöneticisi Bulanıklaştırma genel bakış</span><span class="sxs-lookup"><span data-stu-id="11262-127">Desktop Window Manager Blur Overview</span></span>](/windows/desktop/dwm/blur-ovw)
- [<span data-ttu-id="11262-128">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="11262-128">DwmExtendFrameIntoClientArea</span></span>](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
