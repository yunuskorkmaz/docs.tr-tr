---
title: WPF 'te ActiveX denetimi barındırma
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: f2d9345eaaba7b85a217e6b230ae202f27ad3af8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742618"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>İzlenecek yol: WPF'te ActiveX Denetimi Barındırma
Tarayıcılarla geliştirilmiş etkileşimi etkinleştirmek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulamanızda Microsoft ActiveX denetimlerini kullanabilirsiniz. Bu izlenecek yol, Microsoft Windows Media Player bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasında denetim olarak nasıl barındırabileceğinizi gösterir.

 Bu izlenecek yolda gösterilen görevler şunlardır:

- Proje oluşturuluyor.

- ActiveX denetimi oluşturuluyor.

- Bir WPF sayfasında ActiveX denetimini barındırma.

 Bu yönergeyi tamamladığınızda, Microsoft ActiveX denetimlerini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulamanızda nasıl kullanacağınızı anlamış olursunuz.

## <a name="prerequisites"></a>Prerequisites
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Microsoft Windows Media Player, Visual Studio 'Nun yüklü olduğu bilgisayarda yüklüdür.

- Visual Studio 2010.

## <a name="creating-the-project"></a>Projeyi Oluşturma

### <a name="to-create-and-set-up-the-project"></a>Projeyi oluşturmak ve ayarlamak için

1. `HostingAxInWpf`adlı bir WPF uygulaması projesi oluşturun.

2. Çözüme bir Windows Forms denetim kitaplığı projesi ekleyin ve proje `WmpAxLib`adlandırın.

3. WmpAxLib projesinde, WMP. dll adlı Windows Media Player derlemesine bir başvuru ekleyin.

4. **Araç kutusunu**açın.

5. **Araç kutusuna**sağ tıklayın ve ardından **öğeleri seç**' e tıklayın.

6. **Com bileşenleri** sekmesine tıklayın, **Windows Media Player** denetimini seçin ve ardından **Tamam**' a tıklayın.

     Windows Media Player denetimi **araç kutusuna**eklenir.

7. Çözüm Gezgini, **UserControl1** dosyasına sağ tıklayın ve ardından **Yeniden Adlandır**' a tıklayın.

8. `WmpAxControl.vb` veya `WmpAxControl.cs`dile bağlı olarak adı değiştirin.

9. Tüm başvuruları yeniden adlandırmanız istenirse, **Evet**' e tıklayın.

## <a name="creating-the-activex-control"></a>ActiveX denetimi oluşturma
Visual Studio, denetim tasarım yüzeyine eklendiğinde Microsoft ActiveX denetimi için otomatik olarak bir <xref:System.Windows.Forms.AxHost> sarmalayıcı sınıfı oluşturur. Aşağıdaki yordam, AxInterop. WMPLib. dll adlı bir yönetilen derleme oluşturur.

### <a name="to-create-the-activex-control"></a>ActiveX denetimi oluşturmak için

1. Windows Form Tasarımcısı WmpAxControl. vb veya WmpAxControl.cs öğesini açın.

2. **Araç kutusundan**, tasarım yüzeyine Windows Media Player denetimini ekleyin.

3. Özellikler penceresi, Windows Media Player denetiminin <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin değerini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.

4. WmpAxLib denetim kitaplığı projesi oluşturun.

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Bir WPF sayfasında ActiveX denetimini barındırma

### <a name="to-host-the-activex-control"></a>ActiveX denetimini barındırmak için

1. HostingAxInWpf projesinde, oluşturulan ActiveX birlikte çalışabilirlik derlemesine bir başvuru ekleyin.

     Bu derleme, AxInterop. WMPLib. dll olarak adlandırılır ve Windows Media Player denetimini içeri aktardığınızda WmpAxLib projesinin hata ayıklama klasörüne eklenmiştir.

2. WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.

3. System. Windows. Forms. dll adlı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] derlemesine bir başvuru ekleyin.

4. WPF Tasarımcısında MainWindow. xaml ' i açın.

5. <xref:System.Windows.Controls.Grid> öğesi `grid1`adlandırın.

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window> öğesini seçin.

7. Özellikler penceresi, **Olaylar** sekmesine tıklayın.

8. <xref:System.Windows.FrameworkElement.Loaded> olayına çift tıklayın.

9. <xref:System.Windows.FrameworkElement.Loaded> olayını işlemek için aşağıdaki kodu ekleyin.

     Bu kod, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminin bir örneğini oluşturur ve `AxWindowsMediaPlayer` denetiminin alt öğesi olarak bir örneğini ekler.

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
