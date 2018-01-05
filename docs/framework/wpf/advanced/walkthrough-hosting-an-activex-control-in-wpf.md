---
title: "İzlenecek yol: WPF'te ActiveX Denetimi Barındırma"
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
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6980097c074e10efae7fc6ee77c6c9835c3b1b00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>İzlenecek yol: WPF'te ActiveX Denetimi Barındırma
Tarayıcılarla geliştirilmiş etkileşimi etkinleştirmek için kullanabileceğiniz [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı. Bu anlatımda nasıl barındırabilir gösterilir [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] bir denetim olarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfası.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Projeyi oluşturma.  
  
-   ActiveX denetimi oluşturma.  
  
-   WPF sayfasında ActiveX denetimi barındırma.  
  
 Bu kılavuzu tamamladıktan sonra nasıl kullanılacağını anlayabileceği [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]bilgisayarda yüklü olduğu [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yüklenir.  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
  
#### <a name="to-create-and-set-up-the-project"></a>Oluşturun ve projeyi ayarlamak için  
  
1.  Adlı bir WPF uygulaması projesi oluşturduğunuzda `HostingAxInWpf`.  
  
2.  Bir Windows Forms Denetim Kitaplığı proje çözüme ekleyin ve proje adı `WmpAxLib`.  
  
3.  WmpAxLib projesinde wmp.dll adlı Windows Media Player derlemesine başvuru ekleyin.  
  
4.  Açık **araç**.  
  
5.  Sağ **araç**ve ardından **öğeleri Seç**.  
  
6.  Tıklatın **COM bileşenlerini** sekmesine **Windows Media Player** denetlemek ve ardından **Tamam**.  
  
     Windows Media Player denetim eklenir **araç**.  
  
7.  Çözüm Gezgini'nde sağ **UserControl1** dosya ve ardından **yeniden adlandırma**.  
  
8.  Adına değiştirme `WmpAxControl.vb` veya `WmpAxControl.cs`dil bağlı olarak.  
  
9. Tüm başvuruları yeniden adlandırma istenirse tıklatın **Evet**.  
  
## <a name="creating-the-activex-control"></a>ActiveX denetimi oluşturma  
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]otomatik olarak oluşturan bir <xref:System.Windows.Forms.AxHost> sarmalayıcı sınıfı için bir [!INCLUDE[TLA#tla_actx](../../../../includes/tlasharptla-actx-md.md)] denetimi tasarım yüzeyine eklendiğinde denetim. Aşağıdaki yordam AxInterop.WMPLib.dll yönetilen bir bütünleştirilmiş kod oluşturur.  
  
#### <a name="to-create-the-activex-control"></a>ActiveX denetimi oluşturulamıyor  
  
1.  Windows Forms Tasarımcısı'nda WmpAxControl.vb veya WmpAxControl.cs açın.  
  
2.  Gelen **araç**, Windows Media Player denetimi tasarım yüzeyine ekleyin.  
  
3.  Özellikler penceresinde Windows Media Player denetimin değerini <xref:System.Windows.Forms.Control.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.  
  
4.  WmpAxLib denetim kitaplığı projesi oluşturun.  
  
## <a name="hosting-the-activex-control-on-a-wpf-page"></a>WPF sayfasında ActiveX denetimi barındırma  
  
#### <a name="to-host-the-activex-control"></a>ActiveX denetimi barındırma  
  
1.  HostingAxInWpf projesinde oluşturulan bir başvuru ekleyin [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] birlikte çalışabilirlik derleme.  
  
     Bu derleme AxInterop.WMPLib.dll adlandırılır ve Windows Media Player denetimi aktarıldığında WmpAxLib projesinin Debug klasörüne eklendi.  
  
2.  WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine başvuru ekleyin.  
  
3.  Bir başvuru ekleyin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] System.Windows.Forms.dll adlı derleme.  
  
4.  WPF Tasarımcısı'nda MainWindow.xaml açın.  
  
5.  Ad <xref:System.Windows.Controls.Grid> öğesi `grid1`.  
  
     [!code-xaml[HostingAxInWpf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]  
  
6.  Tasarım görünümü ya da XAML görünümdeki seçmek <xref:System.Windows.Window> öğesi.  
  
7.  Özellikler penceresinde **olayları** sekmesi.  
  
8.  Çift <xref:System.Windows.FrameworkElement.Loaded> olay.  
  
9. İşlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.  
  
     Bu kod örneği oluşturur <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetlemek ve bir örneğini ekler `AxWindowsMediaPlayer` alt öğesi olarak denetim.  
  
     [!code-csharp[HostingAxInWpf#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
