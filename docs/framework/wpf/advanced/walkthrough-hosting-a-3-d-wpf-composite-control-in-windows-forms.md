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
ms.openlocfilehash: 748ab027fa8206c163578c89b94460665563cbce
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197871"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>İzlenecek yol: 3B WPF Bileşik Denetimini Windows Forms İçinde Barındırma

Bu izlenecek yol, <xref:System.Windows.Forms.Integration.ElementHost> denetimini kullanarak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bileşik denetim oluşturabileceğiniz ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerde ve formlarda nasıl barındırabileceğinizi gösterir.

Bu izlenecek yolda, iki alt denetim içeren bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> uygulayacaksınız. <xref:System.Windows.Controls.UserControl> üç boyutlu (3-b) koni görüntüler. 3-b nesneleri işleme [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)][!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] çok daha kolay. Bu nedenle, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]3-b grafik oluşturmak için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> sınıfını barındırmak mantıklı olur.

Bu izlenecek yolda gösterilen görevler şunlardır:

- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>oluşturuluyor.

- Windows Forms konak projesi oluşturuluyor.

- [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>barındırma.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>UserControl oluşturma

1. `HostingWpfUserControlInWf`adlı bir **WPF Kullanıcı denetim kitaplığı** projesi oluşturun.

2. [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]UserControl1. xaml ' i açın.

3. Oluşturulan kodu aşağıdaki kodla değiştirin:

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Bu kod, iki alt denetim içeren bir <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> tanımlar. İlk alt denetim bir <xref:System.Windows.Controls.Label?displayProperty=nameWithType> denetimidir; İkincisi, 3-b koni görüntüleyen bir <xref:System.Windows.Controls.Viewport3D> denetimidir.

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>Konak projesi oluşturma

1. Çözüme `WpfUserControlHost` adlı bir **Windows Forms App (.NET Framework)** projesi ekleyin.

2. **Çözüm Gezgini**' de, WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.

3. Aşağıdaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemelerine başvuruları ekleyin:

    - PresentationCore

    - PresentationFramework

    - WindowsBase

4. `HostingWpfUserControlInWf` projesine bir başvuru ekleyin.

5. Çözüm Gezgini, `WpfUserControlHost` projesini başlangıç projesi olarak ayarlayın.

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>UserControl barındırın

1. Windows Form Tasarımcısı Form1 ' i açın.

2. Özellikler penceresi, **Olaylar**' a tıklayın ve sonra bir olay işleyicisi oluşturmak için <xref:System.Windows.Forms.Form.Load> olayına çift tıklayın.

     Kod Düzenleyicisi, yeni oluşturulan `Form1_Load` olay işleyicisine açılır.

3. Form1.cs içindeki kodu aşağıdaki kodla değiştirin.

     `Form1_Load` olay işleyicisi `UserControl1` örneğini oluşturur ve <xref:System.Windows.Forms.Integration.ElementHost> denetimin alt denetim koleksiyonuna ekler. <xref:System.Windows.Forms.Integration.ElementHost> denetimi formun alt denetim koleksiyonuna eklenir.

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Windows Forms örnekte WPF bileşik denetimi barındırma](https://go.microsoft.com/fwlink/?LinkID=160001)
