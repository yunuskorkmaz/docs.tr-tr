---
title: "İzlenecek yol: WPF'te ActiveX denetimi barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 25019444e107af2ad681e9f51adebbf01c444438
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668326"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>İzlenecek yol: WPF'te ActiveX denetimi barındırma
Tarayıcı ile Gelişmiş etkileşimi etkinleştirmek için kullanabileceğiniz [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı bir uygulama. Bu izlenecek yol, nasıl barındırabilirsiniz gösterir [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] denetim olarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası.

 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

-   Proje oluşturuluyor.

-   ActiveX denetimi oluşturma

-   WPF sayfasında ActiveX denetimi barındırma.

 Bu izlenecek yolu tamamladığınızda, nasıl kullanılacağını anlayacaksınız [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı bir uygulama.

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] Visual Studio'nun yüklü bilgisayarda yüklü.

-   Visual Studio 2010.

## <a name="creating-the-project"></a>Projeyi Oluşturma

#### <a name="to-create-and-set-up-the-project"></a>Oluşturma ve projesi kurun

1.  Adlı bir WPF uygulaması projesi oluşturmak `HostingAxInWpf`.

2.  Bir Windows Forms Denetim Kitaplığı projesi çözüme ekleyin ve projeyi adlandırın `WmpAxLib`.

3.  WmpAxLib projesinde wmp.dll adlı Windows Media Player derlemesine bir başvuru ekleyin.

4.  Açık **araç kutusu**.

5.  Sağ **araç kutusu**ve ardından **öğelerini Seç**.

6.  Tıklayın **COM bileşenlerini** sekmesinde **Windows Media Player** denetlemek ve ardından **Tamam**.

     Windows Media Player denetimi eklenir **araç kutusu**.

7.  Çözüm Gezgini'nde sağ **UserControl1** dosya ve ardından **Yeniden Adlandır**.

8.  Adla değiştirin `WmpAxControl.vb` veya `WmpAxControl.cs`dile bağlı olarak.

9. Tüm başvuruları yeniden adlandırmak için istenirse, tıklayın **Evet**.

## <a name="creating-the-activex-control"></a>ActiveX denetimi oluşturma
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] otomatik olarak oluşturduğu bir <xref:System.Windows.Forms.AxHost> sarmalayıcı sınıfı için bir [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] bir tasarım yüzeyine bir denetim eklendiğinde denetim. Aşağıdaki yordam AxInterop.WMPLib.dll yönetilen bir derleme oluşturur.

#### <a name="to-create-the-activex-control"></a>ActiveX denetimi oluşturmak için

1.  WmpAxControl.vb veya WmpAxControl.cs Windows Form Tasarımcısı'nda açın.

2.  Gelen **araç kutusu**, Windows Media Player denetimi tasarım yüzeyine ekleyin.

3.  Özellikler penceresinde, Windows Media Player denetimin değerini <xref:System.Windows.Forms.Control.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.

4.  WmpAxLib denetim kitaplığı projesi oluşturun.

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Bir WPF sayfasında ActiveX denetimi barındırma

#### <a name="to-host-the-activex-control"></a>ActiveX denetimi barındırma

1.  HostingAxInWpf projesinde, oluşturulan bir başvuru ekleyin [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] birlikte çalışma derlemesi.

     Bu derleme AxInterop.WMPLib.dll adlandırılır ve Windows Media Player denetimi aktarıldığında WmpAxLib projenin hata ayıklama klasöre eklendi.

2.  WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.

3.  Bir başvuru ekleyin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] System.Windows.Forms.dll adlı bütünleştirilmiş kod.

4.  MainWindow.xaml WPF Tasarımcısı'nda açın.

5.  Adı <xref:System.Windows.Controls.Grid> öğesi `grid1`.

     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6.  Tasarım görünümü veya XAML görünümünde seçin <xref:System.Windows.Window> öğesi.

7.  Özellikler penceresinde tıklayın **olayları** sekmesi.

8.  Çift <xref:System.Windows.FrameworkElement.Loaded> olay.

9. İşlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.

     Bu kod örneği oluşturur <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetlemek ve bir örneğini ekler `AxWindowsMediaPlayer` denetim alt öğesi olarak.

     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms bileşik denetimini barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF bileşik denetimini Windows Forms içinde barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
