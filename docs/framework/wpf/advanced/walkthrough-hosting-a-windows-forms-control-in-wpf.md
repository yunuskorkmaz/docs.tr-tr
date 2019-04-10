---
title: 'İzlenecek yol: WPF içinde Windows Forms Denetimi Barındırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 4e9b42738ff661425b05a63f2a5e5790c5cbd84b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311922"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>İzlenecek yol: WPF içinde Windows Forms Denetimi Barındırma

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pek çok denetimi ile zengin özellik kümesi sağlar. Ancak, bazen kullanmak isteyebilirsiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfaları. Örneğin, var olan önemli bir yatırım olabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri veya olabilir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] benzersiz işlevsellik sağlayan denetimi.

Bu izlenecek yol size nasıl barındıracağınızı gösterir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetimi bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu kullanarak sayfa.

Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [WPF Örneği'nde bir Windows Forms denetimi barındırma](https://go.microsoft.com/fwlink/?LinkID=160057).

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için Visual Studio ihtiyacınız vardır.

## <a name="hosting-the-windows-forms-control"></a>Windows Forms denetimi barındırma

### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox denetimi barındırma

1. Adlı bir WPF uygulaması projesi oluşturmak `HostingWfInWpf`.

2. Aşağıdaki derlemelere başvurular ekleyin.

    -   WindowsFormsIntegration

    -   System.Windows.Forms

3. İçinde MainWindow.xaml açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

4. Adı <xref:System.Windows.Controls.Grid> öğesi `grid1`.

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. Tasarım görünümü veya XAML görünümünde seçin <xref:System.Windows.Window> öğesi.

6. Özellikler penceresinde tıklayın **olayları** sekmesi.

7. Çift <xref:System.Windows.FrameworkElement.Loaded> olay.

8. İşlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. Dosyasının en üstüne aşağıdakileri ekleyin `Imports` veya `using` deyimi.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Tuşuna **F5** oluşturun ve uygulamayı çalıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Bir WPF Örneği'nde Windows Forms denetimi barındırma](https://go.microsoft.com/fwlink/?LinkID=160057)
