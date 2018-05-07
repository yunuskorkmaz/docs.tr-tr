---
title: 'Nasıl yapılır: Karma Uygulamada Görsel Stilleri Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 2d714ad020f2f7b6a6343c8f8e3901b59dfd23a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Nasıl yapılır: Karma Uygulamada Görsel Stilleri Etkinleştirme
Bu konuda nasıl etkinleştirileceği gösterilmiştir [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] görsel stilleri bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminde barındırılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı.  
  
 Uygulamanızı çağırırsa <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi, çoğu, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri otomatik olarak kullanacağınız görsel stiller uygulamanızı çalıştırıldığında [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]. Daha fazla bilgi için bkz: [denetimleri görsel stilde işleme](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Bu konu başlığı altında gösterilen görevlerin tam kod listesi için bkz: [etkinleştirme görsel stiller karma uygulama örnekteki](http://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Windows etkinleştirme Forms görsel stilleri  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Windows Forms görsel stilleri etkinleştirmek için  
  
1.  Oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] adlı uygulama projesi `HostingWfWithVisualStyles`.  
  
2.  Çözüm Gezgini'nde, aşağıdaki derlemeler başvurular ekleyin.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Araç kutusunda çift <xref:System.Windows.Controls.Grid> yerleştirmek için simge bir <xref:System.Windows.Controls.Grid> tasarım yüzeyine öğesi.  
  
4.  Özellikler penceresinde değerlerini ayarlayın <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özelliklerine **otomatik**.  
  
5.  Tasarım görünümü ya da XAML görünümdeki seçmek <xref:System.Windows.Window>.  
  
6.  Özellikler penceresinde **olayları** sekmesi.  
  
7.  Çift <xref:System.Windows.FrameworkElement.Loaded> olay.
  
8.  MainWindow.xaml.vb veya MainWindow.xaml.cs işlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetim görsel stiller ile boyanır.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Windows devre dışı bırakma Forms görsel stilleri  
 Görsel stiller devre dışı bırakmak için basitçe çağrısı kaldırmak <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Windows Forms görsel stilleri devre dışı bırakmak için  
  
1.  MainWindow.xaml.vb veya MainWindow.xaml.cs kod düzenleyicisinde açın.  
  
2.  Açıklama çağrısı çıkışı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.  
  
3.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimi, varsayılan sistem stili ile boyanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Denetimleri Görsel Stilde İşleme](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
