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
ms.openlocfilehash: d7a00f2508769534e49c965d098dbacb01a1f189
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843538"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Cam Çerçeveyi WPF Uygulamasında Genişletme

Bu konu nasıl genişleteceğinizi gösterir [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] cam çerçeveyi bir Windows Presentation Foundation (WPF) uygulamasının istemci alanına.

> [!NOTE]
> Bu örnek yalnızca çalışır bir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] etkin cam ile Masaüstü Pencere Yöneticisi'ni (DWM) çalıştıran makine. [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Home Basic sürümü saydam cam etkisi desteklemez. Genellikle diğer sürümleri üzerinde saydam cam etkisi ile işlenen alanları [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] donuk işlenir.

## <a name="example"></a>Örnek

Aşağıdaki görüntüde, adres çubuğuna, Internet Explorer'a 7 genişletilmiş cam çerçeveyi gösterir.

**Internet Explorer Adres çubuğuna arkasındaki genişletilmiş cam çerçeveyi ile.**

![Cam çerçeveyi adres çubuğuna genişletilmiş IE7. ](./media/ie7glasstopbar.PNG "IE7glasstopbar")

Üzerinde cam çerçeveyi genişletmek için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama erişimi yönetilmeyen [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] gereklidir. Aşağıdaki kod örneği iki bir Platform Çağırma (PInvoke) yapmaz [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] istemci alanına çerçeveyi genişletmek için gerekli. Bunların her biri [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] adlı bir sınıfta bildirilen **NonClientRegionAPI**.

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

[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) çerçevenin istemci alanına genişleten DWM işlevdir. İki parametre alır; bir pencere tutucu ve [kenar BOŞLUKLARI](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) yapısı. [Kenar BOŞLUKLARI](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) DWM çerçevenin istemci alanına ne kadar çok genişletilmiş söylemek için kullanılır.

## <a name="example"></a>Örnek

Kullanılacak [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) işlevi, bir pencere tutucu gerekir elde edilebilir. İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], pencere işleyicisi örneğinden alınabilen <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği bir <xref:System.Windows.Interop.HwndSource>. Aşağıdaki örnekte, çerçevenin istemci alanını genişletilir <xref:System.Windows.FrameworkElement.Loaded> penceresinin olay.

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

## <a name="example"></a>Örnek

Aşağıdaki örnek, çerçevenin istemci alanını genişletilir basit bir pencere gösterir. İki içeren üst kenarlık genişletilen çerçeve <xref:System.Windows.Controls.TextBox> nesneleri.

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

Aşağıdaki görüntüde gösterilmiştir uygulamasına genişletilmiş cam çerçeveyi bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama.

**Uygulamada bir**[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]**uygulama.**

![Cam çerçeveyi WPF uygulamasına genişletilmiş. ](./media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")

## <a name="see-also"></a>Ayrıca bkz.

- [Masaüstü Pencere Yöneticisi'ne genel bakış](/windows/desktop/dwm/dwm-overview)
- [Masaüstü Pencere Yöneticisi Bulanıklaştırma genel bakış](/windows/desktop/dwm/blur-ovw)
- [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
