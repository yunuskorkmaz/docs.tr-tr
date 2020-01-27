---
title: Cam çerçeveyi WPF uygulamasına genişletme
titleSuffix: ''
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
ms.openlocfilehash: b78547aa8b414c585bb2e5c9c6680ed159731bc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746538"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="1dd3a-102">Cam Çerçeveyi WPF Uygulamasında Genişletme</span><span class="sxs-lookup"><span data-stu-id="1dd3a-102">Extend Glass Frame Into a WPF Application</span></span>

<span data-ttu-id="1dd3a-103">Bu konuda, Windows Vista cam çerçevesinin bir Windows Presentation Foundation (WPF) uygulamasının istemci alanına nasıl genişletileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-103">This topic demonstrates how to extend the Windows Vista glass frame into the client area of a Windows Presentation Foundation (WPF) application.</span></span>

> [!NOTE]
> <span data-ttu-id="1dd3a-104">Bu örnek, yalnızca cam özellikli Masaüstü Pencere Yöneticisi (DWM) çalıştıran bir Windows Vista makinesinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-104">This example will only work on a Windows Vista machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> <span data-ttu-id="1dd3a-105">Windows Vista Home Basic sürümü, saydam cam efektini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-105">Windows Vista Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="1dd3a-106">Windows Vista 'nın diğer sürümlerinde genellikle saydam cam etkisi ile işlenen alanlar donuk işlenir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-106">Areas that would typically render with the transparent glass effect on other editions of Windows Vista are rendered opaque.</span></span>

## <a name="example"></a><span data-ttu-id="1dd3a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1dd3a-107">Example</span></span>

<span data-ttu-id="1dd3a-108">Aşağıdaki görüntüde, Internet Explorer 7 ' nin adres çubuğuna genişletilmiş cam çerçeve gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1dd3a-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7:</span></span>

![IE7 çerçeve adres çubuğunun arkasındaki cam çerçeveyi gösteren ekran görüntüsü.](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

<span data-ttu-id="1dd3a-110">Bir WPF uygulamasında cam çerçeveyi genişletmek için yönetilmeyen API 'ye erişim gerekir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-110">To extend the glass frame on a WPF application, access to unmanaged API is needed.</span></span> <span data-ttu-id="1dd3a-111">Aşağıdaki kod örneği, çerçeveyi istemci alanına genişletmek için gereken iki API için bir platform çağırma (PInvoke) sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-111">The following code example does a Platform Invoke (pinvoke) for the two API needed to extend the frame into the client area.</span></span> <span data-ttu-id="1dd3a-112">Bu API 'nin her biri **Clientregionapı**adlı bir sınıfta bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-112">Each of these API are declared in a class called **NonClientRegionAPI**.</span></span>

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

<span data-ttu-id="1dd3a-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) , çerçeveyi istemci alanına GENIŞLETEN bir DWM işlevidir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="1dd3a-114">İki parametre alır; pencere tutamacı ve [kenar boşluğu](/windows/win32/api/uxtheme/ns-uxtheme-margins) yapısı.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-114">It takes two parameters; a window handle and a [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) structure.</span></span> <span data-ttu-id="1dd3a-115">[Kenar boşlukları](/windows/win32/api/uxtheme/ns-uxtheme-margins) , bu karenin ne kadar ekstra çerçeveye istemci alanına genişletilmesi gerektiğini bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-115">[MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>

## <a name="example"></a><span data-ttu-id="1dd3a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="1dd3a-116">Example</span></span>

<span data-ttu-id="1dd3a-117">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) işlevini kullanmak için bir pencere tanıtıcısının alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-117">To use the [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) function, a window handle must be obtained.</span></span> <span data-ttu-id="1dd3a-118">WPF 'de, pencere tutamacı bir <xref:System.Windows.Interop.HwndSource><xref:System.Windows.Interop.HwndSource.Handle%2A> özelliğinden elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-118">In WPF, the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="1dd3a-119">Aşağıdaki örnekte, çerçeve pencerenin <xref:System.Windows.FrameworkElement.Loaded> olayında istemci alanına genişletilir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-119">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>

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

## <a name="example"></a><span data-ttu-id="1dd3a-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="1dd3a-120">Example</span></span>

<span data-ttu-id="1dd3a-121">Aşağıdaki örnek, çerçevenin istemci alanına genişletilme basit bir pencere gösterir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-121">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="1dd3a-122">Çerçeve, iki <xref:System.Windows.Controls.TextBox> nesnesini içeren üst kenarlığın arkasında genişletilir.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-122">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>

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

<span data-ttu-id="1dd3a-123">Aşağıdaki görüntüde, bir WPF uygulamasına genişletilmiş cam çerçeve gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1dd3a-123">The following image illustrates the glass frame extended into a WPF application:</span></span>

![WPF uygulamasına genişletilmiş bir cam çerçeveyi gösteren ekran görüntüsü.](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a><span data-ttu-id="1dd3a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dd3a-125">See also</span></span>

- [<span data-ttu-id="1dd3a-126">Masaüstü Pencere Yöneticisi genel bakış</span><span class="sxs-lookup"><span data-stu-id="1dd3a-126">Desktop Window Manager Overview</span></span>](/windows/desktop/dwm/dwm-overview)
- [<span data-ttu-id="1dd3a-127">Masaüstü Pencere Yöneticisi bulanıklaştırma genel bakış</span><span class="sxs-lookup"><span data-stu-id="1dd3a-127">Desktop Window Manager Blur Overview</span></span>](/windows/desktop/dwm/blur-ovw)
- [<span data-ttu-id="1dd3a-128">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="1dd3a-128">DwmExtendFrameIntoClientArea</span></span>](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
