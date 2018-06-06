---
title: 'Nasıl yapılır: Komut Desteği Olmadan Denetime Komut Bağlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
ms.openlocfilehash: e6ef78cd7e1578745f0bde5c0e9e799bb5e641a9
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805613"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Nasıl yapılır: Komut Desteği Olmadan Denetime Komut Bağlama
Aşağıdaki örnek e nasıl bağlanacağını gösterir bir <xref:System.Windows.Input.RoutedCommand> için bir <xref:System.Windows.Controls.Control> değil sahip derlendiği komutu için destek.  Birden çok kaynak komutları tam bir örnek için bkz: [özel bağlayan örneği oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) örnek.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Uygulama programcıları düzenli olarak karşılaştığı yaygın komutları kitaplığını sağlar.  Komut kitaplığı oluşturan sınıfları şunlardır: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, ve <xref:System.Windows.Documents.EditingCommands>.  
  
 Statik <xref:System.Windows.Input.RoutedCommand> bu sınıfları yapan nesneleri komut mantığı sağlamaz.  Komutu için mantığı komutu ile ilişkilendirilmiş bir <xref:System.Windows.Input.CommandBinding>.  Birçok denetimlerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bazı komutlar komut kitaplığındaki desteği yerleşik.  <xref:System.Windows.Controls.TextBox>, örneğin, uygulama Düzenle komutların çoğu gibi destekleyen <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, ve <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Uygulama geliştiricisinin bu denetimlerle çalışmak üzere bu komutları almak için özel bir şey yapmanız gerekmez.  Varsa <xref:System.Windows.Controls.TextBox> komut hedefi komutu çalıştırıldığında komutunu kullanarak işleyecek <xref:System.Windows.Input.CommandBinding> denetime oluşturulur.  
  
 Aşağıdaki nasıl kullanılacağını gösterir bir <xref:System.Windows.Controls.Button> komut kaynağı olarak <xref:System.Windows.Input.ApplicationCommands.Open%2A> komutu.  A <xref:System.Windows.Input.CommandBinding> ilişkilendiren belirtilen oluşturulan <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ile <xref:System.Windows.Input.RoutedCommand>.  
  
 İlk olarak, komut kaynağı oluşturulur.  A <xref:System.Windows.Controls.Button> komut kaynağı olarak kullanılır.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Ardından, <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> oluşturulur.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Yalnızca açılır bir <xref:System.Windows.MessageBox> komutu yürütüldüğünü belirtmek için.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Ayarlar <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> özelliğine `true`.  Normal olarak, execute işleyici komutu geçerli komut hedefinde yürütüldüğünü görmek için daha sağlam denetimleri gerçekleştirir.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Son olarak, bir <xref:System.Windows.Input.CommandBinding> kökünde oluşturulan <xref:System.Windows.Window> yönlendirilmiş olay işleyicilerini ilişkilendirir uygulamanın <xref:System.Windows.Input.ApplicationCommands.Open%2A> komutu.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [Komut Destekli Denetime Komut Bağlama](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
