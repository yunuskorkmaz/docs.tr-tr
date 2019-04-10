---
title: 'İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: e5b98a33f29759a81ba1cbc1fefbd45c0e5bf736
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330174"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma

Bu izlenecek yol nasıl oluşturacağınızı gösterir. bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetleyebilir ve bunu ana [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri ve formları kullanarak <xref:System.Windows.Forms.Integration.ElementHost> denetimi.

Bu izlenecek yolda, uygulayan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> , iki alt denetimler de içerir. <xref:System.Windows.Controls.UserControl> Üç boyutlu (3B) koni görüntüler. 3B nesneleri oluşturma ile çok daha kolay [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] daha ile [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Bu nedenle, konağa mantıklı bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> 3B grafikleri oluşturmak için sınıf [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

-   Oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

-   Windows Forms konak projesi oluşturma.

-   Barındırma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>UserControl oluşturma

1. Oluşturma bir **WPF kullanıcı denetimi Kitaplığı** adlı proje `HostingWpfUserControlInWf`.

2. İçinde UserControl1.xaml açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

3. Oluşturulan kodu aşağıdaki kodla değiştirin:

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Bu kodu tanımlayan bir <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> , iki alt denetimler de içerir. İlk alt denetim bir <xref:System.Windows.Controls.Label?displayProperty=nameWithType> denetimi; ikinci olduğu bir <xref:System.Windows.Controls.Viewport3D> 3B koni görüntüleyen denetim.

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>Ana proje oluşturma

1. Ekleme bir **WPF uygulaması (.NET Framework)** adlı proje `WpfUserControlHost` çözüm. Daha fazla bilgi için [izlenecek yol: İlk WPF Masaüstü Uygulamam](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

2. İçinde **Çözüm Gezgini**, WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.

3. Aşağıdaki başvuruları ekleyin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler:

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

4. Bir başvuru ekleyin `HostingWpfUserControlInWf` proje.

5. Çözüm Gezgini içinde ayarlamak `WpfUserControlHost` projesini başlangıç projesi olarak.

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>UserControl barındırın

1. Windows Form Tasarımcısı'nda Form1'i açın.

2. Özellikler penceresinde tıklayın **olayları**ve çift tıklatarak <xref:System.Windows.Forms.Form.Load> bir olay işleyicisi oluşturmak için olay.

     Yeni oluşturulan kod düzenleyicisi açılır `Form1_Load` olay işleyicisi.

3. Form1.cs içindeki kodu aşağıdaki kodla değiştirin.

     `Form1_Load` Olay işleyicisi bir örneğini oluşturur `UserControl1` ve onu ekler <xref:System.Windows.Forms.Integration.ElementHost> denetimin alt denetimler koleksiyonu. <xref:System.Windows.Forms.Integration.ElementHost> Denetimi, form alt denetimler koleksiyonuna eklenir.

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Windows Forms örneğinde bir WPF bileşik denetimini barındırma](https://go.microsoft.com/fwlink/?LinkID=160001)