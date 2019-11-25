---
title: "İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: e353c35e9989e5887e038371672adbb6c2d3598d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976522"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zengin özellik kümesiyle birçok denetim sağlar. Ancak, bazı durumlarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfalarınızda [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri kullanmak isteyebilirsiniz. Örneğin, varolan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinde önemli bir yatırımınız olabilir veya benzersiz işlevler sağlayan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimine sahip olabilirsiniz.

Bu izlenecek yol, kod kullanarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasında [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetiminin nasıl barındıralınacağını gösterir.

Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms denetimini barındırma](https://go.microsoft.com/fwlink/?LinkID=160057).

## <a name="prerequisites"></a>Prerequisites

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="hosting-the-windows-forms-control"></a>Windows Forms denetimini barındırma

### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox denetimini barındırmak için

1. `HostingWfInWpf`adlı bir WPF uygulaması projesi oluşturun.

2. Aşağıdaki derlemelere başvurular ekleyin.

    - WindowsFormsIntegration

    - System. Windows. Forms

3. WPF Tasarımcısında MainWindow. xaml ' i açın.

4. <xref:System.Windows.Controls.Grid> öğesi `grid1`adlandırın.

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window> öğesini seçin.

6. Özellikler penceresi, **Olaylar** sekmesine tıklayın.

7. <xref:System.Windows.FrameworkElement.Loaded> olayına çift tıklayın.

8. <xref:System.Windows.FrameworkElement.Loaded> olayını işlemek için aşağıdaki kodu ekleyin.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. Dosyanın en üstüne aşağıdaki `Imports` veya `using` ifadesini ekleyin.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri](windows-forms-controls-and-equivalent-wpf-controls.md)
- [WPF örneğinde Windows Forms denetimini barındırma](https://go.microsoft.com/fwlink/?LinkID=160057)
