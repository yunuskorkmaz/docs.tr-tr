---
title: XAML kullanarak WPF 'de Windows Forms denetimi barındırma
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 99c077801a26043e17e0d51ecc0a97b9608784c0
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095066"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zengin özellik kümesiyle birçok denetim sağlar. Ancak, bazı durumlarda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfalarınızda Windows Forms denetimleri kullanmak isteyebilirsiniz. Örneğin, varolan Windows Forms Denetimlerinde önemli bir yatırımınız olabilir veya benzersiz işlevler sağlayan bir Windows Forms denetimine sahip olabilirsiniz.  
  
 Bu izlenecek yol, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfasında Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetiminin nasıl barındırılacağını gösterir.  
  
 Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [XAML örneği kullanarak WPF 'de Windows Forms denetimini barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).
  
## <a name="prerequisites"></a>Önkoşullar  

Bu yönergeyi tamamlamak için Visual Studio gerekir.  
  
## <a name="hosting-the-windows-forms-control"></a>Windows Forms denetimini barındırma  
  
#### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox denetimini barındırmak için  
  
1. `HostingWfInWpfWithXaml`adlı bir WPF uygulaması projesi oluşturun.  
  
2. Aşağıdaki derlemelere başvurular ekleyin.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. WPF Tasarımcısında MainWindow. xaml ' i açın.  
  
4. <xref:System.Windows.Window> öğesinde, aşağıdaki ad alanı eşlemesini ekleyin. `wf` ad alanı eşlemesi, Windows Forms denetimini içeren derlemeye bir başvuru oluşturur.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. <xref:System.Windows.Controls.Grid> öğesinde aşağıdaki XAML 'yi ekleyin.  
  
     <xref:System.Windows.Forms.MaskedTextBox> denetimi, <xref:System.Windows.Forms.Integration.WindowsFormsHost> denetiminin bir alt öğesi olarak oluşturulur.  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. Uygulamayı derleyip çalıştırmak için F5'e basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri](windows-forms-controls-and-equivalent-wpf-controls.md)
- [XAML örneğini kullanarak WPF 'de Windows Forms denetimini barındırma](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml)
