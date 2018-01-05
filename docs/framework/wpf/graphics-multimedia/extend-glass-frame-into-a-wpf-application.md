---
title: "Cam Çerçeveyi WPF Uygulamasında Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aad070bca408fc608eb000948c1b942d08f02018
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="1aa13-102">Cam Çerçeveyi WPF Uygulamasında Genişletme</span><span class="sxs-lookup"><span data-stu-id="1aa13-102">Extend Glass Frame Into a WPF Application</span></span>
<span data-ttu-id="1aa13-103">Bu konuda nasıl genişletileceğini gösterir [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] istemci alanını cam çerçeveye bir [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="1aa13-103">This topic demonstrates how to extend the [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] glass frame into the client area of a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1aa13-104">Bu örnek yalnızca çalışır bir [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] etkin cam ile Masaüstü Pencere Yöneticisi (DWM) çalıştıran makine.</span><span class="sxs-lookup"><span data-stu-id="1aa13-104">This example will only work on a [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)]<span data-ttu-id="1aa13-105">Home Basic sürümü saydam cam etkisini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1aa13-105"> Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="1aa13-106">Genellikle diğer sürümleri saydam cam etkisini ile hale getiren alanları [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] donuk işlenir.</span><span class="sxs-lookup"><span data-stu-id="1aa13-106">Areas that would typically render with the transparent glass effect on other editions of [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] are rendered opaque.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1aa13-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1aa13-107">Example</span></span>  
 <span data-ttu-id="1aa13-108">Aşağıdaki resimde adres çubuğu, Internet Explorer'a 7 genişletilmiş cam çerçeve gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1aa13-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7.</span></span>  
  
 <span data-ttu-id="1aa13-109">**Internet Explorer Adres çubuğuna arkasında genişletilmiş cam çerçeveyle.**</span><span class="sxs-lookup"><span data-stu-id="1aa13-109">**Internet Explorer with extended glass frame behind address bar.**</span></span>  
  
 <span data-ttu-id="1aa13-110">![Adres çubuğu genişletilmiş cam çerçeve IE7. ] (../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")</span><span class="sxs-lookup"><span data-stu-id="1aa13-110">![IE7 with glass frame extended behind address bar.](../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")</span></span>  
  
 <span data-ttu-id="1aa13-111">Üzerinde cam çerçeveyi genişletmek için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama, yönetilmeyen erişimi [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1aa13-111">To extend the glass frame on a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application, access to unmanaged [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] is needed.</span></span> <span data-ttu-id="1aa13-112">Aşağıdaki kod örneği iki için bir Platform Çağırma (PInvoke) yapmaz [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] çerçeve istemci alanına genişletmek için gerekli.</span><span class="sxs-lookup"><span data-stu-id="1aa13-112">The following code example does a Platform Invoke (pinvoke) for the two [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] needed to extend the frame into the client area.</span></span> <span data-ttu-id="1aa13-113">Bunların her biri [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] adlı bir sınıf içinde bildirilen **NonClientRegionAPI**.</span><span class="sxs-lookup"><span data-stu-id="1aa13-113">Each of these [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] are declared in a class called **NonClientRegionAPI**.</span></span>  
  
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
  
 <span data-ttu-id="1aa13-114">[DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) çerçeveyi istemci alanına genişleten bir DWM işlevidir.</span><span class="sxs-lookup"><span data-stu-id="1aa13-114">[DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="1aa13-115">İki parametre alır; bir pencere tanıtıcının ve [kenar BOŞLUKLARI](https://msdn.microsoft.com/library/bb773244.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="1aa13-115">It takes two parameters; a window handle and a [MARGINS](https://msdn.microsoft.com/library/bb773244.aspx) structure.</span></span> <span data-ttu-id="1aa13-116">[Kenar BOŞLUKLARI](https://msdn.microsoft.com/library/bb773244.aspx) çerçeve istemci alanına ne kadar çok genişletilmiş DWM bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1aa13-116">[MARGINS](https://msdn.microsoft.com/library/bb773244.aspx) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1aa13-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="1aa13-117">Example</span></span>  
 <span data-ttu-id="1aa13-118">Kullanılacak [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) işlevi, bir pencere tanıtıcının gerekir elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="1aa13-118">To use the [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx) function, a window handle must be obtained.</span></span> <span data-ttu-id="1aa13-119">İçinde [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bir pencere tanıtıcının elde edilebilir <xref:System.Windows.Interop.HwndSource.Handle%2A> özelliği bir <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="1aa13-119">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="1aa13-120">Aşağıdaki örnekte, çerçeve istemci alanına genişletilir <xref:System.Windows.FrameworkElement.Loaded> penceresinin olay.</span><span class="sxs-lookup"><span data-stu-id="1aa13-120">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="1aa13-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="1aa13-121">Example</span></span>  
 <span data-ttu-id="1aa13-122">Aşağıdaki örnek, çerçeve istemci alanına genişletilmiş basit bir pencereyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1aa13-122">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="1aa13-123">İki içeren üst kenarlığın arkasında genişletilen çerçeve <xref:System.Windows.Controls.TextBox> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1aa13-123">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>  
  
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
  
 <span data-ttu-id="1aa13-124">Aşağıdaki resimde uygulamasına genişletilmiş cam çerçeve gösterilir bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="1aa13-124">The following image illustrates the glass frame extended into a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application.</span></span>  
  
 <span data-ttu-id="1aa13-125">**Uygulamada bir**[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]**uygulama.** </span><span class="sxs-lookup"><span data-stu-id="1aa13-125">**Glass Frame Extended into a**  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  **Application.**</span></span>  
  
 <span data-ttu-id="1aa13-126">![Çerçevenin cam genişletilmiş WPF uygulamasına. ] (../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")</span><span class="sxs-lookup"><span data-stu-id="1aa13-126">![Glass Frame Extended into a WPF application.](../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa13-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1aa13-127">See Also</span></span>  
 [<span data-ttu-id="1aa13-128">Masaüstü Pencere Yöneticisi'ne genel bakış</span><span class="sxs-lookup"><span data-stu-id="1aa13-128">Desktop Window Manager Overview</span></span>](https://msdn.microsoft.com/library/aa969540.aspx)  
 [<span data-ttu-id="1aa13-129">Masaüstü Pencere Yöneticisi bulanık bakış</span><span class="sxs-lookup"><span data-stu-id="1aa13-129">Desktop Window Manager Blur Overview</span></span>](https://msdn.microsoft.com/library/aa969537.aspx)  
 [<span data-ttu-id="1aa13-130">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="1aa13-130">DwmExtendFrameIntoClientArea</span></span>](https://msdn.microsoft.com/library/aa969512.aspx)
