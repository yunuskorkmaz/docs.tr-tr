---
title: "İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma"
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
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5af705509d30f7dfd50ade0c07aca242deff4dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma
Bu kılavuz, nasıl oluşturabileceğinizi gösterir bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim ve içinde ana bilgisayar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ve kullanarak forms <xref:System.Windows.Forms.Integration.ElementHost> denetim.  
  
 Bu kılavuzda, uygulayacak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> iki alt denetimleri içerir. <xref:System.Windows.Controls.UserControl> Üç boyutlu (3-b) koni görüntüler. 3-b nesneleri işleme ile çok daha kolay [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fazla ile [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Bu nedenle, bu konağa mantıklı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 3B grafik oluşturmak için sınıf [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.  
  
-   Windows Forms konak projesi oluşturma.  
  
-   Barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.  
  
 Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [3-b WPF bileşik denetim Windows Forms örnekteki barındırma](http://go.microsoft.com/fwlink/?LinkID=160001).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
<a name="To_Create_the_UserControl"></a>   
## <a name="creating-the-usercontrol"></a>UserControl oluşturma  
  
#### <a name="to-create-the-usercontrol"></a>UserControl oluşturmak için  
  
1.  Adlı bir WPF kullanıcı denetimi kitaplığı projesi oluşturun `HostingWpfUserControlInWf`.  
  
2.  ' Da UserControl1.xaml'i açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
3.  Oluşturulan kodu aşağıdaki kodla değiştirin.  
  
     Bu kodu tanımlayan bir <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> iki alt denetimleri içerir. İlk alt denetim bir <xref:System.Windows.Controls.Label?displayProperty=nameWithType> denetim; ikinci olan bir <xref:System.Windows.Controls.Viewport3D> 3-b koni görüntüleyen denetim.  
  
     [!code-xaml[HostingWpfUserControlInWf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
<a name="To_Create_the_Windows_Forms_Host_Project"></a>   
## <a name="creating-the-windows-forms-host-project"></a>Windows Forms konak projesi oluşturma  
  
#### <a name="to-create-the-host-project"></a>Konak projesi oluşturmak için  
  
1.  Adlı bir Windows uygulaması projesi eklemek `WpfUserControlHost` çözüme. Daha fazla bilgi için bkz: [nasıl yapılır: yeni bir WPF uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
2.  Çözüm Gezgininde WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine başvuru ekleyin.  
  
3.  Aşağıdaki başvurular ekleyin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler:  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
4.  Bir başvuru ekleyin `HostingWpfUserControlInWf` projesi.  
  
5.  Çözüm Gezgininde ayarlayın `WpfUserControlHost` projesini başlangıç projesi olacak şekilde.  
  
<a name="To_Host_the_Windows_Presentation_Foundation"></a>   
## <a name="hosting-the-windows-presentation-foundation-usercontrol"></a>Windows Presentation Foundation UserControl barındırma  
  
#### <a name="to-host-the-usercontrol"></a>UserControl barındırmak için  
  
1.  Windows Forms Tasarımcısı'nda Form1 açın.  
  
2.  Özellikler penceresinde **olayları**, çift tıklayın ve ardından <xref:System.Windows.Forms.Form.Load> olay olay işleyicisi oluşturun.  
  
     Kod Düzenleyicisi yeni oluşturulan açar `Form1_Load` olay işleyicisi.  
  
3.  Form1.cs içindeki kodu aşağıdaki kodla değiştirin.  
  
     `Form1_Load` Olay işleyicisi oluşturur örneği `UserControl1` ve yönlendirir ekler <xref:System.Windows.Forms.Integration.ElementHost> denetimin alt denetimler koleksiyonu. <xref:System.Windows.Forms.Integration.ElementHost> Denetimi formun alt denetimler koleksiyonuna eklenir.  
  
     [!code-csharp[HostingWpfUserControlInWf#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]  
  
4.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [İzlenecek yol: Windows Forms içerisinde WPF bileşik denetimi barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [İzlenecek yol: bir Windows Forms Bileşik Denetimi WPF barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Windows Forms örnek bir WPF bileşik denetimi barındırma](http://go.microsoft.com/fwlink/?LinkID=160001)
