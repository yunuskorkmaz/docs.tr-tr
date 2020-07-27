---
title: WPF 'de Windows Forms denetimi barındırma
description: Zengin bir özellik kümesiyle çok sayıda denetim sağlayan Windows Presentation Foundation Windows Forms denetimlerini nasıl barındıralabileceğinizi öğrenin.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164972"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>İzlenecek yol: WPF içinde Windows Forms Denetimi Barındırma

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zengin özellik kümesine sahip birçok denetim sağlar. Ancak, bazen sayfalarınızda Windows Forms denetimlerini kullanmak isteyebilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Örneğin, varolan Windows Forms Denetimlerinde önemli bir yatırımınız olabilir veya benzersiz işlevler sağlayan bir Windows Forms denetimine sahip olabilirsiniz.

Bu izlenecek yol, <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> kod kullanarak sayfada bir Windows Forms denetiminin nasıl barındıralınacağını gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .

Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms denetimini barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).

## <a name="prerequisites"></a>Ön koşullar

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="hosting-the-windows-forms-control"></a>Windows Forms denetimini barındırma

### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox denetimini barındırmak için

1. Adlı bir WPF uygulaması projesi oluşturun `HostingWfInWpf` .

2. Aşağıdaki derlemelere başvurular ekleyin.

    - WindowsFormsIntegration

    - System. Windows. Forms

3. WPF Tasarımcısında MainWindow. xaml ' i açın.

4. Öğeyi adlandırın <xref:System.Windows.Controls.Grid> `grid1` .

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window> öğesini seçin.

6. Özellikler penceresi, **Olaylar** sekmesine tıklayın.

7. Olaya çift tıklayın <xref:System.Windows.FrameworkElement.Loaded> .

8. Olayı işlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> .

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
- [WPF örneğinde Windows Forms denetimini barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
