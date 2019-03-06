---
title: 'Nasıl yapılır: Karma uygulamada görsel stilleri etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: 9588a2e2d839af43ffe4397303c4a45cad5af2e5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371924"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Nasıl yapılır: Karma uygulamada görsel stilleri etkinleştirme
Bu konuda nasıl etkinleştirileceği gösterilmektedir [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] görsel stillerin bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminde barındırılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı bir uygulama.  
  
 Uygulamanız çağırıyorsa <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi, çoğu, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulamanız çalıştırıldığında denetimleri görsel stilde otomatik olarak kullanır [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)]. Daha fazla bilgi için [denetimleri görsel stilde işleme](../../winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Bu konu başlığında gösterilen görevlerin tam kod listesi için bkz. [karma uygulama örneğinde görsel stilleri etkinleştirme](https://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Forms görsel stilleri Windows etkinleştirme  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Windows Forms görsel stilleri etkinleştirmek için  
  
1.  Oluşturma bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] adlı uygulama projesi `HostingWfWithVisualStyles`.  
  
2.  Çözüm Gezgini'nde, aşağıdaki derlemelere başvurular ekleyin.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
3.  Araç kutusunda çift <xref:System.Windows.Controls.Grid> simgesini yerleştirmek için bir <xref:System.Windows.Controls.Grid> tasarım yüzeyinde öğesi.  
  
4.  Özellikler penceresinde değerlerini ayarlayın <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özelliklerine **otomatik**.  
  
5.  Tasarım görünümü veya XAML görünümünde seçin <xref:System.Windows.Window>.  
  
6.  Özellikler penceresinde tıklayın **olayları** sekmesi.  
  
7.  Çift <xref:System.Windows.FrameworkElement.Loaded> olay.
  
8.  MainWindow.xaml.vb veya MainWindow.xaml.cs içinde işlemek için aşağıdaki kodu ekleyin <xref:System.Windows.FrameworkElement.Loaded> olay.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimi ile görsel stilleri boyanır.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Devre dışı Windows Forms görsel stilleri  
 Görsel stiller devre dışı bırakmak için basitçe çağrısını kaldırın <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Windows Forms görsel stiller devre dışı bırakmak için  
  
1.  MainWindow.xaml.vb veya MainWindow.xaml.cs Kod Düzenleyicisi'nde açın.  
  
2.  Çağrı yorum <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.  
  
3.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimi, varsayılan sistem stiliyle boyanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Denetimleri Görsel Stilde İşleme](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [İzlenecek yol: WPF'de Windows Forms denetimini barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
