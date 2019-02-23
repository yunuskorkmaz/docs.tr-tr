---
title: Komut Vermeye Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interfaces [WPF], ICommandSource
- command library [WPF]
- commands [WPF], definition of
- CommandBindings [WPF]
- ICommandSource interfaces [WPF]
- commanding [WPF]
- CommandManager [WPF]
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
ms.openlocfilehash: 5273850c9fec731c5f11e101d218532d06632263
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748433"
---
# <a name="commanding-overview"></a>Komut Vermeye Genel Bakış
<a name="introduction"></a> Komut vermeye genel olan bir giriş mekanizmasında [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] cihaz girişi daha fazla anlam düzeyinde işleme giriş sağlar. Komut örneklerindendir **kopyalama**, **Kes**, ve **Yapıştır** operations birçok uygulama üzerinde bulunamadı.  
  
 Bu genel bakışta komutları bulunan tanımlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]hangi sınıfların komut verme modelin bir parçasıdır ve uygulamalarınızda kullanmak ve oluşturmak üzere nasıl komutları.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Komutları nelerdir?](#commands_at_10000_feet)  
  
-   [WPF basit komut örneği](#simple_command)  
  
-   [WPF komut vermeye genel dört ana kavramlar](#Four_main_Concepts)  
  
-   [Komut kitaplığı](#Command_Library)  
  
-   [Özel komutlar oluşturma](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Komutları nelerdir?  
 Komutları birkaç amacı vardır. İlk amacı, semantiği ve komutu yürütür mantıksal bir komutu çağıran nesnesi ayırmaktır. Bu birden çok ve aynı komutu mantığı ve onu çağırmak için farklı kaynaklarda komut mantığının farklı hedefler için özelleştirilmesine olanak sağlar. Örneğin, düzenleme işlemleri **kopyalama**, **Kes**, ve **Yapıştır**, birçok uygulamada, bulunduğu çağrılacak olmaları durumunda farklı kullanıcı eylemlerini kullanarak komutlar kullanılarak uygulanır. Bir uygulama, bir kullanıcı ya da menüsündeki bir öğeyi seçerek ya da CTRL + X gibi bir tuş bileşimini kullanarak bir düğmeye tıklayarak, seçili nesneler veya metin kesmek izin verebilir. Komutlarını kullanarak aynı mantığı her bir kullanıcı eylemi türü bağlayabilirsiniz.  
  
 Komutların başka bir amaç, bir eylemin kullanılabilir olup olmadığını belirtmektir. Seçildiğinde bir nesne veya metin kesme örneği devam etmek için eylem yalnızca mantıklıdır. Bir kullanıcı, bir nesne veya metin herhangi bir şeyi zorunda kalmadan kesmek çalışırsa, hiçbir şey olmaz. Kullanıcı bir eylem gerçekleştirmek mümkün olup olmadığını bilebilmesi bu kullanıcıya göstermek için birçok uygulama düğmeleri ve menü öğelerini devre dışı bırakın. Bir komut uygulayarak bir eylem mümkün olup olmadığını belirtebilir <xref:System.Windows.Input.ICommand.CanExecute%2A> yöntemi. Bir düğme için abone olabilirsiniz <xref:System.Windows.Input.ICommand.CanExecuteChanged> olay ve devre dışı <xref:System.Windows.Input.ICommand.CanExecute%2A> döndürür `false` veya beklemedeyse <xref:System.Windows.Input.ICommand.CanExecute%2A> döndürür `true`.  
  
 Bir komut semantiği uygulamalarınız ve sınıflar arasında tutarlı olabilir, ancak eylemin mantığı izlemede belirli nesneye özeldir. CTRL + X çağırır tuş bileşimi **Kes** metin sınıfları, görüntü sınıfları ve Web tarayıcıları, ancak gerçek mantığını gerçekleştirmek için komut **Kes** işlemi gerçekleştirir uygulama tarafından tanımlanır Kes. A <xref:System.Windows.Input.RoutedCommand> mantığını uygulamak istemcileri etkinleştirir. Bir resim nesnesi seçili görüntü keserken bir metin nesnesi panoya seçili metni keser. Bir uygulamanın ne zaman işler <xref:System.Windows.Input.CommandManager.Executed> olay, komut hedefinin erişebilir ve hedef türüne bağlı olarak uygun eylemi alabilir.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>WPF basit komut örneği  
 En basit yolu, bir komut kullanın [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] önceden tanımlanmış bir kullanmaktır <xref:System.Windows.Input.RoutedCommand> komutu kitaplığı sınıflarını; birinden; komutunu işlemek için yerel desteği olan bir denetim ve bir komut çağırmadan için yerel desteği olan bir denetim kullanmak.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> Komut önceden tanımlanmış komutlar biridir <xref:System.Windows.Input.ApplicationCommands> sınıfı.  <xref:System.Windows.Controls.TextBox> Denetim işleme mantığı yerleşik <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu.  Ve <xref:System.Windows.Controls.MenuItem> sınıfında komutları çağırmak için yerel destek.  
  
 Aşağıdaki örnek nasıl ayarlanacağını gösterir. bir <xref:System.Windows.Controls.MenuItem> tıklandığında böylece çağırma <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutunu bir <xref:System.Windows.Controls.TextBox>olduğunu varsayarak <xref:System.Windows.Controls.TextBox> klavye girintisine sahip.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>WPF komut vermeye genel dört ana kavramlar  
 Yönlendirilmiş komut modelde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört ana kavrama bölünebilir: komut, komut kaynağı, komut hedefinde ve komut bağlama:  
  
-   *Komut* yürütülecek eylem.  
  
-   *Komut kaynak* komutu çağıran nesnesidir.  
  
-   *Komut hedefi* komutu üzerinde yürütülmekte olan nesnesidir.  
  
-   *Komutu bağlama* komutu komut mantığını eşleştiren nesnesidir.  
  
 Önceki örnekte, <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komuttur komut <xref:System.Windows.Controls.MenuItem> komut kaynak <xref:System.Windows.Controls.TextBox> komut hedefi ve komut bağlama tarafından sağlanan <xref:System.Windows.Controls.TextBox> denetimi.  Her zaman böyle olmadığını hatalarının ayıklanabileceğini belirtmekte yarar, <xref:System.Windows.Input.CommandBinding> komut hedef sınıf denetimi tarafından sağlanır.  Oldukça sık <xref:System.Windows.Input.CommandBinding> uygulama geliştiricisi tarafından oluşturulan veya <xref:System.Windows.Input.CommandBinding> komut hedefinin bir üst düğüme bağlı.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Komutlar  
 İçindeki komutlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulayarak oluşturulur <xref:System.Windows.Input.ICommand> arabirimi.  <xref:System.Windows.Input.ICommand> iki yöntem sunar <xref:System.Windows.Input.ICommand.Execute%2A>, ve <xref:System.Windows.Input.ICommand.CanExecute%2A>ve bir olay <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A> komutu ile ilişkili olan eylemleri gerçekleştirir. <xref:System.Windows.Input.ICommand.CanExecute%2A> komutun geçerli komut hedefinde yürütülüp yürütülmeyeceğini belirler. <xref:System.Windows.Input.ICommand.CanExecuteChanged> komut verme işlemlerini merkezileştirir komut Yöneticisi oluşturuldu, ancak henüz komut bağlama tarafından yürütülen komutu geçersiz komut kaynağı bir değişiklik algılarsa ortaya çıkar.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulaması <xref:System.Windows.Input.ICommand> olduğu <xref:System.Windows.Input.RoutedCommand> sınıfı ve odak noktası, bu genel bakış.  
  
 Ana giriş kaynakları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fare, klavye, mürekkep ve yönlendirilmiş komutları.  Daha fazla aygıt odaklı girişlerini kullan bir <xref:System.Windows.RoutedEvent> Giriş bir olay gerçekleştiğinde bir uygulama sayfasındaki nesneleri bildirir.  A <xref:System.Windows.Input.RoutedCommand> farklı değildir.  <xref:System.Windows.Input.RoutedCommand.Execute%2A> Ve <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemlerinin bir <xref:System.Windows.Input.RoutedCommand> komutu için uygulama mantığı içermez, ancak bunun yerine tünel yönlendirilmiş olay ve sahip bir nesne karşılaştıkları kadar öğe ağacı üzerinden Kabarcık bir <xref:System.Windows.Input.CommandBinding>.  <xref:System.Windows.Input.CommandBinding> Bu olayları için işleyiciler içerir ve komut gerçekleştiren işleyicileri.  Olay yönlendirme hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A> Metodunda bir <xref:System.Windows.Input.RoutedCommand> başlatır <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> komut hedefi üzerinde olayları.  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> Metodunda bir <xref:System.Windows.Input.RoutedCommand> başlatır <xref:System.Windows.Input.CommandManager.CanExecute> ve <xref:System.Windows.Input.CommandManager.PreviewCanExecute> komut hedefi üzerinde olayları.  Bu olayları tüneli ve kabarcık sahip olan bir nesne karşılaştıkları kadar öğe ağacı aracılığıyla bir <xref:System.Windows.Input.CommandBinding> bu komuta için.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir dizi ortak yönlendirilmiş komutlar yayılmış birkaç sınıf arasında kaynakları: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands>, ve <xref:System.Windows.Documents.EditingCommands>.  Bu sınıflar yalnızca oluşur <xref:System.Windows.Input.RoutedCommand> nesneleri ve uygulama mantığı komut değil.  Uygulama mantığı üzerinde komutu üzerinde yürütülmekte olduğu nesne sorumluluğundadır.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Komut kaynakları  
 Komut kaynak komutu çağıran bir nesnedir.  Komut kaynakları örnekler <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button>, ve <xref:System.Windows.Input.KeyGesture>.  
  
 Komutuyla kaynakları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] genellikle uygulama <xref:System.Windows.Input.ICommandSource> arabirimi.  
  
 <xref:System.Windows.Input.ICommandSource> üç özellik sunar: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, ve <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A> Komut kaynak çağrıldığında yürütülecek komutudur.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Komutun yürütüleceği üzerinde nesnedir.  Uygulamasında hatalarının ayıklanabileceğini belirtmekte yarar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> özelliği <xref:System.Windows.Input.ICommandSource> yalnızca uygun olduğunda <xref:System.Windows.Input.ICommand> olduğu bir <xref:System.Windows.Input.RoutedCommand>.  Varsa <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> üzerinde ayarlanmış bir <xref:System.Windows.Input.ICommandSource> ve karşılık gelen komutun değil bir <xref:System.Windows.Input.RoutedCommand>, komut hedefinde yok sayılır. Varsa <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> ayarlanmazsa klavye odağı öğeyle komut hedefi olacaktır.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> bir kullanıcı tanımlı veri türü bilgilerini işleyicilerine geçirmek için kullanılan komut uygular.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uygulayan sınıflar <xref:System.Windows.Input.ICommandSource> olan <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>, ve <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, ve <xref:System.Windows.Documents.Hyperlink> komutu tıklandığında ve bir çağırma <xref:System.Windows.Input.InputBinding> komutu çağırır olduğunda <xref:System.Windows.Input.InputGesture> ilişkili ile bunu gerçekleştirilir.  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Controls.MenuItem> içinde bir <xref:System.Windows.Controls.ContextMenu> komut kaynağı olarak <xref:System.Windows.Input.ApplicationCommands.Properties%2A> komutu.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Komut kaynak genellikle dinleyeceği <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> olay.  Bu olay, komutun geçerli komut hedefi üzerinde yürütme yeteneği değişmiş olan komut kaynak bildirir.  Komut kaynak geçerli durumunu sorgulayabilirsiniz <xref:System.Windows.Input.RoutedCommand> kullanarak <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemi.  Komut yürütülemiyor komut kaynak sonra kendini devre dışı bırakabilirsiniz.  Bunun bir örneği bir <xref:System.Windows.Controls.MenuItem> kendisi grileştirmesi komut zaman yürütülemiyor.  
  
 Bir <xref:System.Windows.Input.InputGesture> komut kaynağı olarak kullanılabilir.  İki tür giriş hareketleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olan <xref:System.Windows.Input.KeyGesture> ve <xref:System.Windows.Input.MouseGesture>.  Kadar aklınıza gelebilecek bir <xref:System.Windows.Input.KeyGesture> gibi CTRL + C klavye kısayolu olarak.  A <xref:System.Windows.Input.KeyGesture> oluşur bir <xref:System.Windows.Input.Key> ve bir dizi <xref:System.Windows.Input.ModifierKeys>.  A <xref:System.Windows.Input.MouseGesture> oluşur bir <xref:System.Windows.Input.MouseAction> ve isteğe bağlı bir dizi <xref:System.Windows.Input.ModifierKeys>.  
  
 Sırayla bir <xref:System.Windows.Input.InputGesture> komut kaynağı olarak çalışmak için bir komut ile ilişkili olmalıdır. Bunu yapmanın birkaç yolu vardır.  Kullanılacak bir yolu olan bir <xref:System.Windows.Input.InputBinding>.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Input.KeyBinding> arasında bir <xref:System.Windows.Input.KeyGesture> ve <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Başka bir şekilde ilişkilendirmek için bir <xref:System.Windows.Input.InputGesture> için bir <xref:System.Windows.Input.RoutedCommand> eklemektir <xref:System.Windows.Input.InputGesture> için <xref:System.Windows.Input.InputGestureCollection> üzerinde <xref:System.Windows.Input.RoutedCommand>.  
  
 Aşağıdaki örnek nasıl ekleneceğini gösterir. bir <xref:System.Windows.Input.KeyGesture> için <xref:System.Windows.Input.InputGestureCollection> , bir <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 A <xref:System.Windows.Input.CommandBinding> komutu komut uygulayan olay işleyicileri ile ilişkilendirir.  
  
 <xref:System.Windows.Input.CommandBinding> Sınıfı içeren bir <xref:System.Windows.Input.CommandBinding.Command%2A> özelliği ve <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, ve <xref:System.Windows.Input.CommandBinding.CanExecute> olayları.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> Bu komut, <xref:System.Windows.Input.CommandBinding> ile ilişkili.  Ekli olay işleyicileri <xref:System.Windows.Input.CommandBinding.PreviewExecuted> ve <xref:System.Windows.Input.CommandBinding.Executed> olayları komut mantığını uygular.  Olay işleyicilerinin <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> ve <xref:System.Windows.Input.CommandBinding.CanExecute> olayları, komutun geçerli komut hedefinde yürütülüp yürütülmeyeceğini belirlemek.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Input.CommandBinding> kök <xref:System.Windows.Window> bir uygulama.  <xref:System.Windows.Input.CommandBinding> İlişkilendirir <xref:System.Windows.Input.ApplicationCommands.Open%2A> komutunu <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandBinding.CanExecute> işleyicileri.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Ardından, <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> oluşturulur.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Açılır bir <xref:System.Windows.MessageBox> komutu yürüttüğünü belirten bir dize görüntüler.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Ayarlar <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> özelliğini `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> kök gibi belirli bir nesneye iliştirilmiş <xref:System.Windows.Window> uygulama veya bir denetim.  Nesne, <xref:System.Windows.Input.CommandBinding> bağlama kapsamını tanımlar için eklenir.  Örneğin, bir <xref:System.Windows.Input.CommandBinding> bağlı komutu öğesinin üst öğesi için hedef tarafından erişilebilen <xref:System.Windows.Input.CommandBinding.Executed> olay, ancak bir <xref:System.Windows.Input.CommandBinding> ekli komut hedefinin için hedef ulaşılamıyor.  Bu şekilde doğrudan bir sonucu olan bir <xref:System.Windows.RoutedEvent> tüneller ve kabarcıklar nesnesinden olayını başlatır.  
  
 Bazı durumlarda <xref:System.Windows.Input.CommandBinding> ile olduğu gibi komut hedefinin kendisine bağlı <xref:System.Windows.Controls.TextBox> sınıfı ve <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, ve <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutları. Genellikle eklemek daha kullanışlı olan <xref:System.Windows.Input.CommandBinding> ana gibi komut hedefinin bir üst için <xref:System.Windows.Window> veya uygulama nesnesi, özellikle de aynı <xref:System.Windows.Input.CommandBinding> birden çok komut hedefleri için kullanılabilir.  Bunlar, tasarım kararlarını komut verme altyapınızı oluştururken dikkate almak istersiniz.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Komut hedefi  
 Komut hedefi üzerinde komutu yürütülmeden öğesidir.  Yönlendirilmesinin bir <xref:System.Windows.Input.RoutedCommand>, komut hedefinde hangi yönlendirme sırasında öğedir <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandManager.CanExecute> başlatır.  Daha önce de belirtildiği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> özelliği <xref:System.Windows.Input.ICommandSource> yalnızca uygun olduğunda <xref:System.Windows.Input.ICommand> olduğu bir <xref:System.Windows.Input.RoutedCommand>.  Varsa <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> üzerinde ayarlanmış bir <xref:System.Windows.Input.ICommandSource> ve karşılık gelen komutun değil bir <xref:System.Windows.Input.RoutedCommand>, komut hedefinde yok sayılır.  
  
 Komut kaynak komut hedefi açıkça ayarlayabilirsiniz.  Komut hedefi tanımlı değil, klavye odaklı öğe komut hedefi olarak kullanılır.  Öğe klavye odağı ile komut hedefi olarak kullanmanın avantajlarından biri, bu komut hedefi izlemek zorunda kalmadan birden çok hedef komutu çağırmak için aynı komutu kaynağı kullanmak uygulama geliştiricisinin olanak sağlamasıdır.  Örneğin, bir <xref:System.Windows.Controls.MenuItem> çağırır **Yapıştır** olan bir uygulama komutunu bir <xref:System.Windows.Controls.TextBox> denetimi ve bir <xref:System.Windows.Controls.PasswordBox> denetimi, hedef ya da olabilir <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.PasswordBox> hangisini seçtiğinize bağlı olarak Denetim, klavye girintisine sahip.  
  
 Aşağıdaki örnek, biçimlendirme ve arka plan kod komut hedefi açıkça ayarlamak gösterilmektedir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>The CommandManager  
 <xref:System.Windows.Input.CommandManager> İlgili işlevler bir dizi komut görev yapar.  Ekleme ve kaldırma için statik yöntemler kümesi sağlar <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>, ve <xref:System.Windows.Input.CommandManager.CanExecute> olay işleyicileri için ve belirli bir öğe.  Kaydetmek için bir yol sağlar <xref:System.Windows.Input.CommandBinding> ve <xref:System.Windows.Input.InputBinding> nesnelerin üzerine belirli bir sınıf.  <xref:System.Windows.Input.CommandManager> Ayrıca aracılığıyla bir yol sağlar <xref:System.Windows.Input.CommandManager.RequerySuggested> bunu tetiklemelidir komutu bildirmek için olay <xref:System.Windows.Input.ICommand.CanExecuteChanged> olay.  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> Yöntemi zorlar <xref:System.Windows.Input.CommandManager> yükseltmenizi <xref:System.Windows.Input.CommandManager.RequerySuggested> olay.  Gereken koşullar için kullanışlıdır devre dışı bırak/etkinleştir komutu ancak olmayan koşulları <xref:System.Windows.Input.CommandManager> farkındadır.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Komut kitaplığı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] önceden tanımlanmış komut kümesini sağlar.  Komut kitaplığı aşağıdaki sınıftan oluşur: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands>ve <xref:System.Windows.Input.ComponentCommands>.  Bu sınıflar gibi komutları sağlar <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> ve <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>, ve <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Bu komutların birçoğu, varsayılan giriş bağlamaları kümesini içerir.  Belirtirseniz, uygulamanızı kopyalama komutu işleyen, otomatik olarak "CTRL + C" bağlama klavye alma gibi de bağlamaları giriş diğer cihazlar gibi elde [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] kalem işlerse.  
  
 Komutları kullanarak çeşitli komutu kitaplıklara başvurduğunuzda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], statik komut özelliği gösteren kitaplık sınıf sınıf adı genellikle atlayabilirsiniz. Genellikle dize olarak komut adlarını kesindir ve sahip olan türler komutları mantıksal bir gruplandırmasını sağlar ancak Kesinleştirme için gerekli değildir. Örneğin, belirtebilirsiniz `Command="Cut"` daha ayrıntılı yerine `Command="ApplicationCommands.Cut"`. İçinde yerleşik olan bir kolaylık mekanizma budur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] komutları için işlemci (bir tür dönüştürücüsü davranışını daha kesin olduğu <xref:System.Windows.Input.ICommand>, hangi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci başvuruları yükleme zamanında).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Özel komutlar oluşturma  
 Komut kitaplığı sınıflarını komutlar gereksinimlerinizi karşılamıyorsa, kendi komutları oluşturabilirsiniz.  Özel komut oluşturmanın iki yolu vardır.  İlk baştan başlamak ve uygulamak için olan <xref:System.Windows.Input.ICommand> arabirimi.  Başka bir şekilde ve daha yaygın bir yaklaşım olan oluşturmak için bir <xref:System.Windows.Input.RoutedCommand> veya <xref:System.Windows.Input.RoutedUICommand>.  
  
 Özel bir oluşturma örneği için <xref:System.Windows.Input.RoutedCommand>, bkz: [örnek bir özel RoutedCommand oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [ICommandSource Uygulama](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)
- [Nasıl yapılır: MenuItem için bir komut ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Örnek bir özel RoutedCommand oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
