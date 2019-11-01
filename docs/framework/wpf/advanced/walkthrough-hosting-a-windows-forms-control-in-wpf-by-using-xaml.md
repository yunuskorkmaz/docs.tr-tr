---
title: 'İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma'
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 10596f3ec89a5dc8bb7c20274b697d2592ad93d5
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197883"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zengin özellik kümesiyle birçok denetim sağlar. Ancak, bazı durumlarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfalarınızda [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri kullanmak isteyebilirsiniz. Örneğin, varolan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinde önemli bir yatırımınız olabilir veya benzersiz işlevler sağlayan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimine sahip olabilirsiniz.  
  
 Bu izlenecek yol, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasında Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetiminin nasıl barındırılacağını gösterir.  
  
 Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [XAML örneği kullanarak WPF 'de Windows Forms denetimini barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).
  
## <a name="prerequisites"></a>Prerequisites  

Bu yönergeyi tamamlamak için Visual Studio gerekir.  
  
## <a name="hosting-the-windows-forms-control"></a>Windows Forms denetimini barındırma  
  
#### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox denetimini barındırmak için  
  
1. `HostingWfInWpfWithXaml`adlı bir WPF uygulaması projesi oluşturun.  
  
2. Aşağıdaki derlemelere başvurular ekleyin.  
  
    - WindowsFormsIntegration  
  
    - System. Windows. Forms  
  
3. [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]MainWindow. xaml ' i açın.  
  
4. <xref:System.Windows.Window> öğesinde, aşağıdaki ad alanı eşlemesini ekleyin. `wf` ad alanı eşlemesi, Windows Forms denetimini içeren derlemeye bir başvuru oluşturur.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <xref:System.Windows.Controls.Grid> öğesinde aşağıdaki XAML 'yi ekleyin.  
  
     <xref:System.Windows.Forms.MaskedTextBox> denetimi, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminin bir alt öğesi olarak oluşturulur.  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri](windows-forms-controls-and-equivalent-wpf-controls.md)
- [XAML örneğini kullanarak WPF 'de Windows Forms denetimini barındırma](https://go.microsoft.com/fwlink/?LinkID=160000)
