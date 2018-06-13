---
title: "İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 515135893c0d6cf251977bbddc13241e8b6b60bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546835"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birçok denetimleri ile zengin özellik kümesi sağlar. Ancak, bazen kullanmak istediğiniz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerini, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sayfaları. Örneğin, varolan önemli ölçüde yatırımınız olabilir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri veya olabilir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] benzersiz işlevsellik sağlayan denetim.  
  
 Bu kılavuzda barındırmak gösterilmiştir bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> denetiminin bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kodu kullanarak sayfa.  
  
 Bu kılavuzda gösterilen görevlerin tam kod listesi için bkz: [WPF örnek bir Windows Forms denetimi barındırma](http://go.microsoft.com/fwlink/?LinkID=160057).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="hosting-the-windows-forms-control"></a>Windows Forms denetimi barındırma  
  
#### <a name="to-host-the-maskedtextbox-control"></a>MaskedTextBox denetimi barındırma  
  
1.  Adlı bir WPF uygulaması projesi oluşturduğunuzda `HostingWfInWpf`.  
  
2.  Aşağıdaki derlemeler başvurular ekleyin.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  MainWindow.xaml içinde açmak [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
4.  Ad <xref:System.Windows.Controls.Grid> öğesi `grid1`.  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  Tasarım görünümü ya da XAML görünümdeki seçmek <xref:System.Windows.Window> öğesi.  
  
6.  Özellikler penceresinde **olayları** sekmesi.  
  
7.  Çift <xref:System.Windows.FrameworkElement.Loaded> olay.  
  
8.  İşlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. Dosyanın üst kısmında, aşağıdaki ekleyin `Imports` veya `using` deyimi.  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [İzlenecek yol: XAML Kullanarak WPF İçerisinde bir Windows Forms Denetimi Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Windows Forms Denetimleri ve Eşdeğer WPF Denetimleri](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [WPF örnek bir Windows Forms denetimi barındırma](http://go.microsoft.com/fwlink/?LinkID=160057)
