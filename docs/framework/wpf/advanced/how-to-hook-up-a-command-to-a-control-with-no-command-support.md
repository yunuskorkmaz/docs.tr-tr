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
ms.openlocfilehash: 5f963c871ed9b600586c32403a288eadd6e9daec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725382"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Nasıl yapılır: Komut Desteği Olmadan Denetime Komut Bağlama
Aşağıdaki örnek e nasıl bağlanacağını gösterir. bir <xref:System.Windows.Input.RoutedCommand> için bir <xref:System.Windows.Controls.Control> hangi değil olması için yerleşik desteğe komutu.  Komutları için birden çok kaynaktan eksiksiz bir örnek için bkz. [örnek bir özel RoutedCommand oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) örnek.  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] düzenli olarak uygulama programcıların karşılaştığı yaygın komutları içeren bir kitaplık sağlar.  Komut kitaplığı oluşturan sınıfları: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, ve <xref:System.Windows.Documents.EditingCommands>.  
  
 Statik <xref:System.Windows.Input.RoutedCommand> bu sınıfları oluşturan nesneleri komut mantıksal sağlamaz.  Mantıksal komutu için komut ile ilişkili bir <xref:System.Windows.Input.CommandBinding>.  Birçok denetimlerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desteklemek için bazı komutlar komutu Kitaplığı'nda yerleşik olarak.  <xref:System.Windows.Controls.TextBox>, örneğin, birçok uygulama Düzenle komutu gibi destekleyen <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, ve <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.  Uygulama geliştiricisinin bu denetimleri ile çalışmak için bu komutları almak için özel bir şey yapmanız gerekmez.  Varsa <xref:System.Windows.Controls.TextBox> komut hedefi komut yürütüldüğünde, komutunu kullanarak işleyecek <xref:System.Windows.Input.CommandBinding> denetime oluşturulur.  
  
 Aşağıdakileri nasıl kullanılacağını gösterir. bir <xref:System.Windows.Controls.Button> komut kaynağı olarak <xref:System.Windows.Input.ApplicationCommands.Open%2A> komutu.  A <xref:System.Windows.Input.CommandBinding> ilişkilendiren belirtilen oluşturulan <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ile <xref:System.Windows.Input.RoutedCommand>.  
  
 İlk olarak, komut kaynağı oluşturulur.  A <xref:System.Windows.Controls.Button> komut kaynağı olarak kullanılır.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 Ardından, <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> oluşturulur.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Yalnızca açılır bir <xref:System.Windows.MessageBox> komutu yürütüldüğünü belirtmek için.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Ayarlar <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> özelliğini `true`.  Normal olarak, execute işleyici komutun geçerli komut hedefi üzerinde yürütüldüğünü görmek için daha güçlü denetimler gerçekleştirir.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Son olarak, bir <xref:System.Windows.Input.CommandBinding> kökünde oluşturulan <xref:System.Windows.Window> yönlendirilmiş olay işleyicilerini ilişkilendirir uygulamanın <xref:System.Windows.Input.ApplicationCommands.Open%2A> komutu.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)
- [Komut Destekli Denetime Komut Bağlama](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
