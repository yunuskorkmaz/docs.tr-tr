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
ms.openlocfilehash: a702456895cfdbd44a58059befefb69deee5afa3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636204"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Cam Çerçeveyi WPF Uygulamasında Genişletme

Bu konuda, Windows Vista cam çerçevesinin bir Windows Presentation Foundation (WPF) uygulamasının istemci alanına nasıl genişletileceği gösterilmektedir.

> [!NOTE]
> Bu örnek, yalnızca cam özellikli Masaüstü Pencere Yöneticisi (DWM) çalıştıran bir Windows Vista makinesinde çalışır. Windows Vista Home Basic sürümü, saydam cam efektini desteklemez. Windows Vista 'nın diğer sürümlerinde genellikle saydam cam etkisi ile işlenen alanlar donuk işlenir.

## <a name="example"></a>Örnek

Aşağıdaki görüntüde, Internet Explorer 7 ' nin adres çubuğuna genişletilmiş cam çerçeve gösterilmektedir:

![IE7 çerçeve adres çubuğunun arkasındaki cam çerçeveyi gösteren ekran görüntüsü.](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

Bir WPF uygulamasında cam çerçeveyi genişletmek için yönetilmeyen API 'ye erişim gerekir. Aşağıdaki kod örneği, çerçeveyi istemci alanına genişletmek için gereken iki API için bir platform çağırma (PInvoke) sağlar. Bu API 'nin her biri **Clientregionapı**adlı bir sınıfta bildirilmiştir.

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

[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) , çerçeveyi istemci alanına GENIŞLETEN bir DWM işlevidir. İki parametre alır; pencere tutamacı ve [kenar boşluğu](/windows/win32/api/uxtheme/ns-uxtheme-margins) yapısı. [Kenar boşlukları](/windows/win32/api/uxtheme/ns-uxtheme-margins) , bu karenin ne kadar ekstra çerçeveye istemci alanına genişletilmesi gerektiğini bildirmek için kullanılır.

## <a name="example"></a>Örnek

[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) işlevini kullanmak için bir pencere tanıtıcısının alınması gerekir. WPF 'de, pencere tutamacı bir <xref:System.Windows.Interop.HwndSource><xref:System.Windows.Interop.HwndSource.Handle%2A> özelliğinden elde edilebilir. Aşağıdaki örnekte, çerçeve pencerenin <xref:System.Windows.FrameworkElement.Loaded> olayında istemci alanına genişletilir.

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

Aşağıdaki örnek, çerçevenin istemci alanına genişletilme basit bir pencere gösterir. Çerçeve, iki <xref:System.Windows.Controls.TextBox> nesnesini içeren üst kenarlığın arkasında genişletilir.

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

Aşağıdaki görüntüde, bir WPF uygulamasına genişletilmiş cam çerçeve gösterilmektedir:

![WPF uygulamasına genişletilmiş bir cam çerçeveyi gösteren ekran görüntüsü.](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Masaüstü Pencere Yöneticisi genel bakış](/windows/desktop/dwm/dwm-overview)
- [Masaüstü Pencere Yöneticisi bulanıklaştırma genel bakış](/windows/desktop/dwm/blur-ovw)
- [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
