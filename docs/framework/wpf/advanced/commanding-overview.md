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
ms.openlocfilehash: 192fe629493947ffe4e0aa8ade417b7701ff95b4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004601"
---
# <a name="commanding-overview"></a>Komut Vermeye Genel Bakış
<a name="introduction"></a>Komut verme, cihaz girişinden daha anlamlı bir düzeyde giriş işleme sağlayan [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içindeki bir giriş mekanizmasıdır. Komutların örnekleri, birçok uygulamada bulunan **kopyalama**, **kesme**ve **Yapıştırma** operasyonlardır.  
  
 Bu genel bakış, hangi komutların [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]olduğunu, hangi sınıfların komut veren modelin bir parçası olduğunu ve uygulamalarınızda komutları nasıl kullanacağınızı ve oluşturulacağını tanımlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Komutlar nelerdir?](#commands_at_10000_feet)  
  
- [WPF 'de basit komut örneği](#simple_command)  
  
- [WPF komutlama 'da dört ana kavram](#Four_main_Concepts)  
  
- [Komut kitaplığı](#Command_Library)  
  
- [Özel komutlar oluşturma](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Komutlar nelerdir?  
 Komutların çeşitli amaçları vardır. İlk amaç, komutu yürüten mantığdan bir komutu çağıran semantiğini ve nesneyi ayıramaktır. Bu, birden çok ve farklı kaynağın aynı komut mantığını çağırmasına olanak sağlar ve komut mantığının farklı hedefler için özelleştirilme olanağı sağlar. Örneğin, birçok uygulamada bulunan Düzenle işlemleri **kopyalama**, **kesme**ve **Yapıştırma**işlemleri, komutlar kullanılarak uygulandıklarında farklı Kullanıcı eylemleri kullanılarak çağrılabilir. Bir uygulama, bir düğmeye tıklayarak, menüdeki bir öğeyi seçerek veya CTRL + X gibi bir anahtar birleşimi kullanarak, bir kullanıcının seçili nesneleri veya metni kesmesine izin verebilir. Komutları kullanarak her bir kullanıcı eylemi türünü aynı mantığa bağlayabilirsiniz.  
  
 Komutların başka bir amacı, bir eylemin kullanılabilir olup olmadığını gösterir. Bir nesne veya metin kesme örneğine devam etmek için, eylem yalnızca bir öğe seçildiğinde anlamlıdır. Bir Kullanıcı herhangi bir şeyi seçmeden bir nesne veya metin kesmeye çalışırsa hiçbir şey olmaz. Bunu kullanıcıya göstermek için, birçok uygulama düğme ve menü öğelerini devre dışı bırakır, böylece Kullanıcı bir eylem gerçekleştirmek için mümkün olup olmadığını bilir. Bir komut <xref:System.Windows.Input.ICommand.CanExecute%2A> yöntemi uygulayarak bir eylemin mümkün olup olmadığını belirtebilir. Bir düğme <xref:System.Windows.Input.ICommand.CanExecuteChanged> olayına abone olabilir ve <xref:System.Windows.Input.ICommand.CanExecute%2A> `false` döndürürse veya <xref:System.Windows.Input.ICommand.CanExecute%2A> `true`döndürürse etkinleştirilebilir.  
  
 Bir komutun semantiği uygulamalar ve sınıflar arasında tutarlı olabilir, ancak eylemin mantığı üzerinde işlem yapılan belirli bir nesneye özgüdür. CTRL + X tuş birleşimi metin sınıflarında, resim sınıflarında ve Web tarayıcılarında **Kes** komutunu çağırır, ancak **kesme** işlemini gerçekleştirmeye yönelik gerçek mantık, kesmeyi gerçekleştiren uygulama tarafından tanımlanır. <xref:System.Windows.Input.RoutedCommand>, istemcilerin mantığı uygulamasına olanak sağlar. Bir metin nesnesi seçili metni panoya kesebilir, ancak bir resim nesnesi seçili görüntüyü kesebilir. Bir uygulama <xref:System.Windows.Input.CommandManager.Executed> olayını işlediğinde, komutun hedefine erişimi vardır ve hedefin türüne bağlı olarak uygun eylemi gerçekleştirebilir.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>WPF 'de basit komut örneği  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bir komutu kullanmanın en kolay yolu, komut kitaplığı sınıflarından biri önceden tanımlanmış bir <xref:System.Windows.Input.RoutedCommand> kullanmaktır; komutu işlemek için yerel desteğe sahip bir denetim kullanın; ve bir komutu çağırmak için yerel destek içeren bir denetim kullanın.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu, <xref:System.Windows.Input.ApplicationCommands> sınıfındaki önceden tanımlanmış komutlardan biridir.  <xref:System.Windows.Controls.TextBox> denetimi <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu işlemek için yerleşik mantığa sahiptir.  Ve <xref:System.Windows.Controls.MenuItem> sınıfı komutları çağırmak için yerel destek içerir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.MenuItem>, tıklandığı zaman bir <xref:System.Windows.Controls.TextBox><xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutunu çağırarak, <xref:System.Windows.Controls.TextBox> klavye odağına sahip olduğunu varsayarak, bir ayarlamayı gösterir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>WPF komutlama 'da dört ana kavram  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yönlendirilen komut modeli dört ana kavram halinde ayrılabilir: komut, komut kaynağı, komut hedefi ve komut bağlama:  
  
- *Komut* yürütülecek eylemdir.  
  
- *Komut kaynağı* , komutunu çağıran nesnedir.  
  
- *Komut hedefi* , komutun yürütüldüğü nesnedir.  
  
- Komut *bağlama* komutu, komut mantığını komutla eşleyen nesnedir.  
  
 Önceki örnekte, <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu komuttur, <xref:System.Windows.Controls.MenuItem> komut kaynağıdır, <xref:System.Windows.Controls.TextBox> komut hedefidir ve komut bağlaması <xref:System.Windows.Controls.TextBox> denetimi tarafından sağlanır.  Her zaman, <xref:System.Windows.Input.CommandBinding> komut hedef sınıfı olan denetim tarafından sağlanmıştı.  <xref:System.Windows.Input.CommandBinding> uygulama geliştiricisi tarafından oluşturulması gerekir veya <xref:System.Windows.Input.CommandBinding> komut hedefinin bir üst öğesine eklenmiş olabilir.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Komutlar  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komutları <xref:System.Windows.Input.ICommand> arabirimini uygulayarak oluşturulur.  <xref:System.Windows.Input.ICommand> iki yöntem, <xref:System.Windows.Input.ICommand.Execute%2A>ve <xref:System.Windows.Input.ICommand.CanExecute%2A>ve bir olay <xref:System.Windows.Input.ICommand.CanExecuteChanged>sunar. <xref:System.Windows.Input.ICommand.Execute%2A> komutla ilişkili eylemleri gerçekleştirir. <xref:System.Windows.Input.ICommand.CanExecute%2A>, komutun geçerli komut hedefinde yürütülüp yürütülmeyeceğini belirler. verme işlemini merkezileştiren komut Yöneticisi komut kaynağında yükseltilen ancak henüz çalıştırılmayan bir komutu geçersiz kılabilecek bir değişikliği algılarsa, <xref:System.Windows.Input.ICommand.CanExecuteChanged> tetiklenir.  <xref:System.Windows.Input.ICommand> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama <xref:System.Windows.Input.RoutedCommand> sınıftır ve bu genel bakışın odaklanmasıdır.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] giriş ana kaynakları, fare, klavye, mürekkep ve yönlendirilmiş komutlardır.  Cihaz odaklı daha fazla giriş, bir giriş olayının gerçekleştiği bir uygulama sayfasındaki nesneleri bilgilendirmek için bir <xref:System.Windows.RoutedEvent> kullanır.  <xref:System.Windows.Input.RoutedCommand> farklı değildir.  Bir <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> ve <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemleri, komut için uygulama mantığını içermez, ancak nesne ağacı aracılığıyla bir <xref:System.Windows.Input.CommandBinding>ile karşılaşana kadar tünel ve balon oluşturan yönlendirilmiş olayları yükseltir.  <xref:System.Windows.Input.CommandBinding>, bu olaylar için işleyicileri içerir ve komutu gerçekleştiren işleyicileridir.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]'de olay yönlendirme hakkında daha fazla bilgi için bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 Bir <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.Execute%2A> yöntemi, <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> olaylarını komut hedefi üzerinde oluşturur.  Bir <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemi, komut hedefi üzerinde <xref:System.Windows.Input.CommandManager.CanExecute> ve <xref:System.Windows.Input.CommandManager.PreviewCanExecute> olaylarını oluşturur.  Bu olaylar, belirli bir komut için <xref:System.Windows.Input.CommandBinding> olan bir nesneyle karşılaşana kadar, öğe ağacı aracılığıyla tünel ve kabarcık.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], birkaç sınıfa yayılan ortak bir yönlendirilmiş komutlar kümesi sağlar: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands>ve <xref:System.Windows.Documents.EditingCommands>.  Bu sınıflar, komutun uygulama mantığını değil yalnızca <xref:System.Windows.Input.RoutedCommand> nesnelerinden oluşur.  Uygulama mantığı, üzerinde komutun yürütüldüğü nesnenin sorumluluğundadır.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Komut kaynakları  
 Komut kaynağı, komutunu çağıran nesnedir.  Komut kaynaklarına örnek olarak <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button>ve <xref:System.Windows.Input.KeyGesture>verilebilir.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] içindeki komut kaynakları genellikle <xref:System.Windows.Input.ICommandSource> arabirimini uygular.  
  
 <xref:System.Windows.Input.ICommandSource> üç özellik sunar: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>ve <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A>, komut kaynağı çağrıldığında yürütülecek komuttur.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, komutun yürütüleceği nesnedir.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], <xref:System.Windows.Input.ICommandSource> <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> özelliğinin yalnızca <xref:System.Windows.Input.ICommand> bir <xref:System.Windows.Input.RoutedCommand>olduğunda geçerli olduğunu belirtmekte bir değer.  <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> bir <xref:System.Windows.Input.ICommandSource> ayarlanırsa ve karşılık gelen komut bir <xref:System.Windows.Input.RoutedCommand>değilse, komut hedefi yok sayılır. <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> ayarlanmamışsa, klavye odaklı öğe komut hedefi olacaktır.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, komutu uygulayan işleyicilere bilgi geçirmek için kullanılan Kullanıcı tanımlı bir veri türüdür.  
  
 <xref:System.Windows.Input.ICommandSource> uygulayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfları <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>ve <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>ve <xref:System.Windows.Documents.Hyperlink> tıklandığı zaman bir komutu çağırır ve onunla ilişkili <xref:System.Windows.Input.InputGesture> gerçekleştirildiğinde bir komut çağırılır <xref:System.Windows.Input.InputBinding>.  
  
 Aşağıdaki örnek, <xref:System.Windows.Input.ApplicationCommands.Properties%2A> komutu için komut kaynağı olarak bir <xref:System.Windows.Controls.ContextMenu> <xref:System.Windows.Controls.MenuItem> nasıl kullanacağınızı gösterir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Genellikle, bir komut kaynağı <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> olayını dinleyecektir.  Bu olay komut kaynağını, komutun geçerli komut hedefinde yürütme yeteneğinin değiştiğini bildirir.  Komut kaynağı, <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemini kullanarak <xref:System.Windows.Input.RoutedCommand> geçerli durumunu sorgulayabilir.  Komut yürütülemez ise, komut kaynağı kendisini devre dışı bırakabilir.  Bu, bir komut yürütümediğinde bir <xref:System.Windows.Controls.MenuItem> gri tonlamalı bir örnektir.  
  
 Bir <xref:System.Windows.Input.InputGesture>, komut kaynağı olarak kullanılabilir.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] iki tür giriş hareketi <xref:System.Windows.Input.KeyGesture> ve <xref:System.Windows.Input.MouseGesture>.  Bir <xref:System.Windows.Input.KeyGesture> CTRL + C gibi bir klavye kısayolu olarak düşünebilirsiniz.  <xref:System.Windows.Input.KeyGesture>, bir <xref:System.Windows.Input.Key> ve <xref:System.Windows.Input.ModifierKeys>kümesinden oluşur.  <xref:System.Windows.Input.MouseGesture>, <xref:System.Windows.Input.MouseAction> ve isteğe bağlı bir <xref:System.Windows.Input.ModifierKeys>kümesinden oluşur.  
  
 Bir <xref:System.Windows.Input.InputGesture> komut kaynağı olarak davranması için bir komutla ilişkilendirilmesi gerekir. Bunu yapmanın birkaç yolu vardır.  Bir yol <xref:System.Windows.Input.InputBinding>kullanmaktır.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Input.KeyGesture> ve <xref:System.Windows.Input.RoutedCommand>arasında <xref:System.Windows.Input.KeyBinding> oluşturmayı gösterir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Bir <xref:System.Windows.Input.InputGesture> <xref:System.Windows.Input.RoutedCommand> ilişkilendirmenin bir diğer yolu da <xref:System.Windows.Input.InputGesture> <xref:System.Windows.Input.RoutedCommand><xref:System.Windows.Input.InputGestureCollection> eklemektir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Input.RoutedCommand><xref:System.Windows.Input.InputGestureCollection> <xref:System.Windows.Input.KeyGesture> nasıl ekleneceğini gösterir.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 Bir <xref:System.Windows.Input.CommandBinding> komutu uygulayan olay işleyicileriyle bir komutu ilişkilendirir.  
  
 <xref:System.Windows.Input.CommandBinding> sınıfı bir <xref:System.Windows.Input.CommandBinding.Command%2A> özelliği ve <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>ve <xref:System.Windows.Input.CommandBinding.CanExecute> olaylarını içerir.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>, <xref:System.Windows.Input.CommandBinding> ilişkilendirildiği komuttur.  <xref:System.Windows.Input.CommandBinding.PreviewExecuted> ve <xref:System.Windows.Input.CommandBinding.Executed> olaylarına eklenen olay işleyicileri komut mantığını uygular.  <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> ve <xref:System.Windows.Input.CommandBinding.CanExecute> olaylarına eklenen olay işleyicileri, komutun geçerli komut hedefinde yürütülüp yürütülmeyeceğini tespit edebilir.  
  
 Aşağıdaki örnek, bir uygulamanın kök <xref:System.Windows.Window> <xref:System.Windows.Input.CommandBinding> nasıl oluşturulacağını gösterir.  <xref:System.Windows.Input.CommandBinding>, <xref:System.Windows.Input.ApplicationCommands.Open%2A> komutunu <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandBinding.CanExecute> işleyicileriyle ilişkilendirir.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Sonra, <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve bir <xref:System.Windows.Input.CanExecuteRoutedEventHandler> oluşturulur.  <xref:System.Windows.Input.ExecutedRoutedEventHandler>, komutun yürütüldüğünü söyleyen bir dize görüntüleyen bir <xref:System.Windows.MessageBox> açar.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler>, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> özelliğini `true`olarak ayarlar.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 <xref:System.Windows.Input.CommandBinding>, uygulamanın kök <xref:System.Windows.Window> veya bir denetim gibi belirli bir nesneye iliştirilir.  <xref:System.Windows.Input.CommandBinding> eklendiği nesne, bağlamanın kapsamını tanımlar.  Örneğin, komut hedefinin üst öğesine eklenmiş bir <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.CommandBinding.Executed> olayı tarafından erişilebilir, ancak komut hedefinin alt öğesine eklenmiş bir <xref:System.Windows.Input.CommandBinding> ulaşılamıyor.  Bu, olayı oluşturan nesneden bir <xref:System.Windows.RoutedEvent> tünellerinin ve kabarcıkların doğrudan bir sonucudur.  
  
 Bazı durumlarda <xref:System.Windows.Input.CommandBinding>, <xref:System.Windows.Controls.TextBox> sınıfı ve <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>ve <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutlarıyla birlikte komut hedefine iliştirilir. Ancak, özellikle de aynı <xref:System.Windows.Input.CommandBinding> birden çok komut hedefi için kullanılabilir ise, ana <xref:System.Windows.Window> veya uygulama nesnesi gibi komut hedefinin üst öğesine <xref:System.Windows.Input.CommandBinding> iliştirmek daha uygundur.  Bunlar, komutlama altyapınızı oluştururken göz önünde bulundurmanız gereken tasarım kararlardır.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Komut hedefi  
 Komut hedefi, komutun yürütüldüğü öğedir.  Bir <xref:System.Windows.Input.RoutedCommand>söz konusu olduğunda, komut hedefi, <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandManager.CanExecute> yönlendirmenin başladığı öğedir.  Daha önce belirtildiği gibi, <xref:System.Windows.Input.ICommandSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> özelliği yalnızca <xref:System.Windows.Input.ICommand> bir <xref:System.Windows.Input.RoutedCommand>olduğunda geçerlidir.  <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> bir <xref:System.Windows.Input.ICommandSource> ayarlanırsa ve karşılık gelen komut bir <xref:System.Windows.Input.RoutedCommand>değilse, komut hedefi yok sayılır.  
  
 Komut kaynağı, komut hedefini açık bir şekilde ayarlayabilir.  Komut hedefi tanımlanmamışsa, klavye odaklı öğe komut hedefi olarak kullanılacaktır.  Komut hedefi olarak, öğesini klavye odağıyla birlikte kullanmanın avantajlarından biri, uygulama geliştiricisinin komut hedefini izlemek zorunda kalmadan birden çok hedefte bir komutu çağırmak için aynı komut kaynağını kullanmasına izin verir.  Örneğin, bir <xref:System.Windows.Controls.MenuItem>, bir <xref:System.Windows.Controls.TextBox> denetimine ve bir <xref:System.Windows.Controls.PasswordBox> denetimine sahip bir uygulamada **Paste** komutunu çağırmışsa, hedef <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.PasswordBox>, klavye odağına sahip olan denetime bağlı olarak olabilir.  
  
 Aşağıdaki örnek, biçimlendirme ve arka plan kodunda komut hedefinin açıkça nasıl ayarlanacağını gösterir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>CommandManager  
 <xref:System.Windows.Input.CommandManager>, bir dizi komutla ilgili işlevi sunar.  <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>ve <xref:System.Windows.Input.CommandManager.CanExecute> olay işleyicilerini belirli bir öğeden eklemek ve kaldırmak için bir statik yöntemler kümesi sağlar.  Belirli bir sınıfa <xref:System.Windows.Input.CommandBinding> ve <xref:System.Windows.Input.InputBinding> nesneleri kaydetmek için bir yol sağlar.  <xref:System.Windows.Input.CommandManager> Ayrıca, <xref:System.Windows.Input.CommandManager.RequerySuggested> olay aracılığıyla <xref:System.Windows.Input.ICommand.CanExecuteChanged> olayını oluşturması gerektiğinde bir komuta bildirimde bulunan bir yol sağlar.  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> yöntemi, <xref:System.Windows.Input.CommandManager> <xref:System.Windows.Input.CommandManager.RequerySuggested> olayını oluşturmaya zorlar.  Bu, bir komutu devre dışı bırakmak/etkinleştirmek zorunda olan ancak <xref:System.Windows.Input.CommandManager> farkında olmayan koşullar için yararlıdır.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Komut kitaplığı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], önceden tanımlanmış bir komutlar kümesi sağlar.  Komut kitaplığı şu sınıflardan oluşur: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands>ve <xref:System.Windows.Input.ComponentCommands>.  Bu sınıflar <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> ve <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>ve <xref:System.Windows.Input.MediaCommands.Pause%2A>gibi komutları sağlar.  
  
 Bu komutların birçoğu, varsayılan giriş bağlamaları kümesini içerir.  Örneğin, uygulamanızın kopyalama komutunu işlediğini belirtirseniz, otomatik olarak "CTRL + C" klavye bağlamasını alırsınız. Ayrıca, Tablet PC kalem hareketleri ve konuşma bilgileri gibi diğer giriş cihazlarına yönelik bağlamaları da alırsınız.  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]kullanarak çeşitli komut kitaplıklarında komutlara başvurduğunuzda, genellikle statik komut özelliğini kullanıma sunan kitaplık sınıfının sınıf adını atlayabilirsiniz. Genellikle, komut adları dizeler olarak anlaşılır ve sahip olan türler, bir komut mantıksal gruplandırması sağlamak için vardır ancak Kesinleştirme için gerekli değildir. Örneğin, daha ayrıntılı `Command="ApplicationCommands.Cut"`yerine `Command="Cut"` belirtebilirsiniz. Bu, komutlar için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisinde yerleşik bir mekanizmadır (daha kesin olarak, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin yükleme zamanında başvurduğu <xref:System.Windows.Input.ICommand>tür dönüştürücü davranışıdır).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Özel komutlar oluşturma  
 Komut kitaplığı sınıflardaki komutlar gereksinimlerinizi karşılamıyorsa, kendi komutlarınızı oluşturabilirsiniz.  Özel bir komut oluşturmanın iki yolu vardır.  İlki sıfırdan başlayıp <xref:System.Windows.Input.ICommand> arabirimini uygulamaktır.  Diğer bir yöntem ve daha yaygın yaklaşım, bir <xref:System.Windows.Input.RoutedCommand> veya <xref:System.Windows.Input.RoutedUICommand>oluşturmaktır.  
  
 Özel bir <xref:System.Windows.Input.RoutedCommand>oluşturma örneği için bkz. [özel bir RoutedCommand örneği oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Girişe Genel Bakış](input-overview.md)
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [ICommandSource Uygulama](how-to-implement-icommandsource.md)
- [Nasıl yapılır: MenuItem 'a komut ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Özel bir RoutedCommand örneği oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
