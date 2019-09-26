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
ms.openlocfilehash: 3ae45c9a9e33a3cb53ada6e1e5430ae0f9e6c198
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "71263300"
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a>Nasıl yapılır: Komut Desteği Olmadan Denetime Komut Bağlama
Aşağıdaki örnek, komutu için yerleşik desteği olmayan bir <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Controls.Control> öğesine nasıl bağlanacağını göstermektedir.  Birden çok kaynağa komutları bağlayan bir örnek için, bkz. [özel RoutedCommand örnek örneği oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand) .  
  
## <a name="example"></a>Örnek  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]uygulama programcılarının düzenli olarak karşılaştığı yaygın komutlar içeren bir kitaplık sağlar.  Komut kitaplığını oluşturan sınıflar şunlardır: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands> <xref:System.Windows.Input.MediaCommands>, ve <xref:System.Windows.Documents.EditingCommands>.  
  
 Bu sınıfları <xref:System.Windows.Input.RoutedCommand> oluşturan statik nesneler komut mantığı sağlamaz.  Komutun mantığı, komutuyla <xref:System.Windows.Input.CommandBinding>ilişkilendirilir.  İçindeki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] birçok denetim, komut kitaplığındaki bazı komutlar için yerleşik desteğe sahiptir.  <xref:System.Windows.Controls.TextBox>Örneğin,,,, ve <xref:System.Windows.Input.ApplicationCommands.Paste%2A> <xref:System.Windows.Input.ApplicationCommands.Cut%2A> <xref:System.Windows.Input.ApplicationCommands.Redo%2A> <xref:System.Windows.Input.ApplicationCommands.Copy%2A> gibi<xref:System.Windows.Input.ApplicationCommands.Undo%2A>birçok uygulama düzenleme komutunu destekler.  Uygulama geliştiricisinin bu denetimlerle çalışmak üzere bu komutları almak için özel bir şey yapması gerekmez.  Komut yürütüldüğünde komut hedefi ise, denetimde yerleşik <xref:System.Windows.Input.CommandBinding> olan öğesini kullanarak komutu işler. <xref:System.Windows.Controls.TextBox>  
  
 Aşağıda <xref:System.Windows.Controls.Button> komut<xref:System.Windows.Input.ApplicationCommands.Open%2A> için komut kaynağı olarak nasıl kullanılacağı gösterilmektedir.  , <xref:System.Windows.Input.CommandBinding> İle<xref:System.Windows.Input.CanExecuteRoutedEventHandler> belirtilen <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve ile<xref:System.Windows.Input.RoutedCommand>ilişkilendiren bir oluşturulur.  
  
 İlk olarak, komut kaynağı oluşturulur.  <xref:System.Windows.Controls.Button> Komut kaynağı olarak kullanılır.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 <xref:System.Windows.Input.ExecutedRoutedEventHandler> Ardından ,<xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve oluşturulur.  Komutun yürütüldüğünü belirtmek için <xref:System.Windows.MessageBox> yalnızcabiraçar.<xref:System.Windows.Input.ExecutedRoutedEventHandler>  , <xref:System.Windows.Input.CanExecuteRoutedEventHandler> <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> Özelliğini olarak`true`ayarlar.  Normal olarak, işlem, komutun geçerli komut hedefinde yürütülüp yürütülmeyeceğini görmek için daha güçlü denetimler gerçekleştirir.  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 Son olarak, <xref:System.Windows.Input.CommandBinding> bir uygulamanın kökünde <xref:System.Windows.Window> , <xref:System.Windows.Input.ApplicationCommands.Open%2A> yönlendirilmiş olaylar işleyicilerini komutuyla ilişkilendiren bir oluşturulur.  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Komut Vermeye Genel Bakış](commanding-overview.md)
- [Komut Destekli Denetime Komut Bağlama](how-to-hook-up-a-command-to-a-control-with-command-support.md)
