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
ms.openlocfilehash: 251c53a8665d2eae7c3b5bb23b0a388009362dcc
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960118"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Nasıl yapılır: Karma Uygulamada Görsel Stilleri Etkinleştirme
Bu konuda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı bir uygulamada barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminde görsel stillerin nasıl etkinleştirileceği gösterilmektedir.  
  
 Uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemini çağırırsa, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinizin çoğu otomatik olarak görsel stilleri kullanır. Daha fazla bilgi için bkz. [görsel stillerle denetim işleme](../../winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Bu konuda gösterilen görevlerin tüm kod listesi için bkz. [karma uygulama örneğinde görsel stilleri etkinleştirme](https://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Windows Forms Görsel stilleri etkinleştirme  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Windows Forms Görsel stilleri etkinleştirmek için  
  
1. `HostingWfWithVisualStyles`adlı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir uygulama projesi oluşturun.  
  
2. Çözüm Gezgini, aşağıdaki derlemelere başvurular ekleyin.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. Araç kutusunda, tasarım yüzeyine bir <xref:System.Windows.Controls.Grid> öğesi yerleştirmek için <xref:System.Windows.Controls.Grid> simgesine çift tıklayın.  
  
4. Özellikler penceresi, <xref:System.Windows.FrameworkElement.Height%2A> ve <xref:System.Windows.FrameworkElement.Width%2A> özelliklerinin değerlerini **Otomatik**olarak ayarlayın.  
  
5. Tasarım görünümü veya XAML görünümünde <xref:System.Windows.Window>seçin.  
  
6. Özellikler penceresi, **Olaylar** sekmesine tıklayın.  
  
7. <xref:System.Windows.FrameworkElement.Loaded> olayına çift tıklayın.
  
8. MainWindow. xaml. vb veya MainWindow.xaml.cs içinde, <xref:System.Windows.FrameworkElement.Loaded> olayını işlemek için aşağıdaki kodu ekleyin.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Uygulamayı derleyip çalıştırmak için F5'e basın.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi görsel stillerle boyanmıştır.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Windows Forms görsel stillerini devre dışı bırakma  
 Görsel stilleri devre dışı bırakmak için <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metoduna çağrıyı kaldırmanız yeterlidir.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Windows Forms görsel stillerini devre dışı bırakmak için  
  
1. Kod düzenleyicisinde MainWindow. xaml. vb veya MainWindow.xaml.cs öğesini açın.  
  
2. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemine yapılan çağrıyı açıklama.  
  
3. Uygulamayı derleyip çalıştırmak için F5'e basın.  
  
     [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi varsayılan sistem stiliyle boyanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Denetimleri Görsel Stilde İşleme](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
