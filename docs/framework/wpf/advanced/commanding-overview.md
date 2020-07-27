---
title: Komut Vermeye Genel Bakış
description: Windows Presentation Foundation ' de bir giriş mekanizması, cihaz girişinden daha anlamsal bir düzeyde giriş işlemesi sağlayan bir komut verme hakkında bilgi edinin.
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
ms.openlocfilehash: 4f7d12fbf0de9b1546f15061ab7eb1318378bbbb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168122"
---
# <a name="commanding-overview"></a>Komut Vermeye Genel Bakış
<a name="introduction"></a>Komut verme, içinde, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] cihaz girişinden daha anlamlı bir düzeyde giriş işleme sağlayan bir giriş mekanizmasıdır. Komutların örnekleri, birçok uygulamada bulunan **kopyalama**, **kesme**ve **Yapıştırma** operasyonlardır.  
  
 Bu genel bakış, hangi komutların içinde olduğunu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , hangi sınıfların komut veren modelin bir parçası olduğunu ve uygulamalarınızda komutları nasıl kullanacağınızı ve oluşturulacağını tanımlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Komutlar nelerdir?](#commands_at_10000_feet)  
  
- [WPF 'de basit komut örneği](#simple_command)  
  
- [WPF komutlama 'da dört ana kavram](#Four_main_Concepts)  
  
- [Komut kitaplığı](#Command_Library)  
  
- [Özel komutlar oluşturma](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>
## <a name="what-are-commands"></a>Komutlar nelerdir?  
 Komutların çeşitli amaçları vardır. İlk amaç, komutu yürüten mantığdan bir komutu çağıran semantiğini ve nesneyi ayıramaktır. Bu, birden çok ve farklı kaynağın aynı komut mantığını çağırmasına olanak sağlar ve komut mantığının farklı hedefler için özelleştirilme olanağı sağlar. Örneğin, birçok uygulamada bulunan Düzenle işlemleri **kopyalama**, **kesme**ve **Yapıştırma**işlemleri, komutlar kullanılarak uygulandıklarında farklı Kullanıcı eylemleri kullanılarak çağrılabilir. Bir uygulama, bir düğmeye tıklayarak, menüdeki bir öğeyi seçerek veya CTRL + X gibi bir anahtar birleşimi kullanarak, bir kullanıcının seçili nesneleri veya metni kesmesine izin verebilir. Komutları kullanarak her bir kullanıcı eylemi türünü aynı mantığa bağlayabilirsiniz.  
  
 Komutların başka bir amacı, bir eylemin kullanılabilir olup olmadığını gösterir. Bir nesne veya metin kesme örneğine devam etmek için, eylem yalnızca bir öğe seçildiğinde anlamlıdır. Bir Kullanıcı herhangi bir şeyi seçmeden bir nesne veya metin kesmeye çalışırsa hiçbir şey olmaz. Bunu kullanıcıya göstermek için, birçok uygulama düğme ve menü öğelerini devre dışı bırakır, böylece Kullanıcı bir eylem gerçekleştirmek için mümkün olup olmadığını bilir. Bir komut, yöntemi uygulayarak bir eylemin mümkün olup olmadığını belirtebilir <xref:System.Windows.Input.ICommand.CanExecute%2A> . Bir düğme olaya abone olabilir <xref:System.Windows.Input.ICommand.CanExecuteChanged> ve döndürüyorsa <xref:System.Windows.Input.ICommand.CanExecute%2A> , dönerse veya etkinleştirilirse devre dışı bırakılabilir `false` <xref:System.Windows.Input.ICommand.CanExecute%2A> `true` .  
  
 Bir komutun semantiği uygulamalar ve sınıflar arasında tutarlı olabilir, ancak eylemin mantığı üzerinde işlem yapılan belirli bir nesneye özgüdür. CTRL + X tuş birleşimi metin sınıflarında, resim sınıflarında ve Web tarayıcılarında **Kes** komutunu çağırır, ancak **kesme** işlemini gerçekleştirmeye yönelik gerçek mantık, kesmeyi gerçekleştiren uygulama tarafından tanımlanır. , <xref:System.Windows.Input.RoutedCommand> İstemcilerinin mantığı uygulamasına olanak sağlar. Bir metin nesnesi seçili metni panoya kesebilir, ancak bir resim nesnesi seçili görüntüyü kesebilir. Bir uygulama <xref:System.Windows.Input.CommandManager.Executed> olayı işlediğinde, komutun hedefine erişimi vardır ve hedefin türüne bağlı olarak uygun eylemi gerçekleştirebilir.  
  
<a name="simple_command"></a>
## <a name="simple-command-example-in-wpf"></a>WPF 'de basit komut örneği  
 ' De bir komut kullanmanın en basit yolu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komut kitaplığı sınıflarından birini önceden tanımlamış bir şekilde kullanmaktır <xref:System.Windows.Input.RoutedCommand> ; komutu işlemek için yerel desteğe sahip bir denetim kullanın ve bir komutu çağırmak için yerel desteğe sahip bir denetim kullanın.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A>Komut, sınıfındaki önceden tanımlanmış komutlardan biridir <xref:System.Windows.Input.ApplicationCommands> .  <xref:System.Windows.Controls.TextBox>Denetim, komutu işlemek için yerleşik mantığa sahiptir <xref:System.Windows.Input.ApplicationCommands.Paste%2A> .  Ve <xref:System.Windows.Controls.MenuItem> sınıfı komutları çağırmak için yerel destek içerir.  
  
 Aşağıdaki örnek, bir, <xref:System.Windows.Controls.MenuItem> tıklatılınca, <xref:System.Windows.Input.ApplicationCommands.Paste%2A> <xref:System.Windows.Controls.TextBox> klavye odağına sahip olduğunu varsayarak bir üzerinde komutunu çağıracağı için nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>
## <a name="four-main-concepts-in-wpf-commanding"></a>WPF komutlama 'da dört ana kavram  
 İçindeki yönlendirilmiş komut modeli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört ana kavram halinde ayrılabilir: komut, komut kaynağı, komut hedefi ve komut bağlama:  
  
- *Komut* yürütülecek eylemdir.  
  
- *Komut kaynağı* , komutunu çağıran nesnedir.  
  
- *Komut hedefi* , komutun yürütüldüğü nesnedir.  
  
- Komut *bağlama* komutu, komut mantığını komutla eşleyen nesnedir.  
  
 Önceki örnekte, komut komutu, komut kaynağıdır, komut <xref:System.Windows.Input.ApplicationCommands.Paste%2A> hedefi ise <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.TextBox> ve komut bağlaması denetim tarafından sağlanır <xref:System.Windows.Controls.TextBox> .  Her zaman, <xref:System.Windows.Input.CommandBinding> komut hedef sınıfı olan denetim tarafından sağlanmıştı.  Genellikle <xref:System.Windows.Input.CommandBinding> uygulama geliştiricisi tarafından oluşturulması gerekir veya <xref:System.Windows.Input.CommandBinding> komut hedefinin bir üst öğesine eklenmiş olabilir.  
  
<a name="Commands"></a>
### <a name="commands"></a>Komutlar  
 İçindeki komutlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , arabirimini uygulayarak oluşturulur <xref:System.Windows.Input.ICommand> .  <xref:System.Windows.Input.ICommand>iki yöntem, <xref:System.Windows.Input.ICommand.Execute%2A> , ve <xref:System.Windows.Input.ICommand.CanExecute%2A> ve bir olay gösterir <xref:System.Windows.Input.ICommand.CanExecuteChanged> . <xref:System.Windows.Input.ICommand.Execute%2A>komutuyla ilişkili eylemleri gerçekleştirir. <xref:System.Windows.Input.ICommand.CanExecute%2A>komutun geçerli komut hedefinde yürütülüp yürütülmeyeceğini belirler. <xref:System.Windows.Input.ICommand.CanExecuteChanged>komutlama işlemlerini merkezileştiren komut Yöneticisi komut kaynağında yükseltilen ancak henüz çalıştırılmayan bir komutu geçersiz kılabilecek bir değişikliği algılarsa, tetiklenir.  Uygulamasının [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sınıfı, <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.RoutedCommand> ve bu genel bakışın odaklanmasıdır.  
  
 İçindeki giriş kaynakları, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fare, klavye, mürekkep ve yönlendirilmiş komutlardır.  Cihaza yönelik daha fazla giriş, bir <xref:System.Windows.RoutedEvent> giriş olayının gerçekleştiği bir uygulama sayfasında nesneleri bilgilendirmek için bir kullanır.  <xref:System.Windows.Input.RoutedCommand>, Farklı değildir.  <xref:System.Windows.Input.RoutedCommand.Execute%2A>Ve <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemleri, <xref:System.Windows.Input.RoutedCommand> komutu için uygulama mantığını içermez, ancak bir nesnesi ile karşılaşana kadar, öğe ağacı aracılığıyla tünel ve balon oluşturan yönlendirilmiş olayları yükseltir <xref:System.Windows.Input.CommandBinding> .  , <xref:System.Windows.Input.CommandBinding> Bu olaylar için işleyicileri içerir ve komutu gerçekleştiren işleyicileridir.  İçindeki olay yönlendirme hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bkz. [yönlendirilmiş olaylara genel bakış](routed-events-overview.md).  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A>Bir üzerindeki yöntemi <xref:System.Windows.Input.RoutedCommand> , <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.Input.CommandManager.Executed> komut hedefi üzerindeki ve olaylarını oluşturur.  İçindeki <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemi <xref:System.Windows.Input.RoutedCommand> , <xref:System.Windows.Input.CommandManager.CanExecute> <xref:System.Windows.Input.CommandManager.PreviewCanExecute> komut hedefi üzerindeki ve olaylarını oluşturur.  Bu olaylar, belirli bir komuta ait olan bir nesneyle karşılaşana kadar öğe ağacı aracılığıyla tünel ve kabarcık <xref:System.Windows.Input.CommandBinding> .  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]birçok sınıfa yayılan ortak bir yönlendirilmiş komutlar kümesi sağlar: <xref:System.Windows.Input.MediaCommands> ,,, <xref:System.Windows.Input.ApplicationCommands> <xref:System.Windows.Input.NavigationCommands> <xref:System.Windows.Input.ComponentCommands> ve <xref:System.Windows.Documents.EditingCommands> .  Bu sınıflar, <xref:System.Windows.Input.RoutedCommand> komutun uygulama mantığını değil yalnızca nesnelerden oluşur.  Uygulama mantığı, üzerinde komutun yürütüldüğü nesnenin sorumluluğundadır.  
  
<a name="Command_Sources"></a>
### <a name="command-sources"></a>Komut kaynakları  
 Komut kaynağı, komutunu çağıran nesnedir.  Komut kaynakları örnekleri, ve ' dir <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.Button> <xref:System.Windows.Input.KeyGesture> .  
  
 İçindeki komut kaynakları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] genellikle arabirimini uygular <xref:System.Windows.Input.ICommandSource> .  
  
 <xref:System.Windows.Input.ICommandSource>üç özellik sunar: <xref:System.Windows.Input.ICommandSource.Command%2A> , <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> ve <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> :  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A>komut kaynağı çağrıldığında yürütülecek komut.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, komutun yürütüleceği nesnedir.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Üzerinde özelliğinin <xref:System.Windows.Input.ICommandSource> yalnızca bir olduğu durumlarda geçerli olduğunu belirtmekte bir değer verilir <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.RoutedCommand> .  , <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Bir üzerinde ayarlanırsa <xref:System.Windows.Input.ICommandSource> ve karşılık gelen komut bir değilse <xref:System.Windows.Input.RoutedCommand> , komut hedefi yok sayılır. <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>Ayarlanmamışsa, klavye odaklı öğe komut hedefi olacaktır.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>, komutu uygulayan işleyicilere bilgi geçirmek için kullanılan Kullanıcı tanımlı bir veri türüdür.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Uygulayan sınıflar,, <xref:System.Windows.Input.ICommandSource> ve ' dir <xref:System.Windows.Controls.Primitives.ButtonBase> <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Input.InputBinding> .  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem> , ve <xref:System.Windows.Documents.Hyperlink> tıklandığında bir komutu çağırır ve bununla ilişkili olduğunda bir komutu <xref:System.Windows.Input.InputBinding> çağırır <xref:System.Windows.Input.InputGesture> .  
  
 Aşağıdaki örnek, <xref:System.Windows.Controls.MenuItem> komutu için bir komut kaynağı olarak bir olarak ' ın nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ContextMenu> <xref:System.Windows.Input.ApplicationCommands.Properties%2A> .  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Genellikle, bir komut kaynağı <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> olayı dinler.  Bu olay komut kaynağını, komutun geçerli komut hedefinde yürütme yeteneğinin değiştiğini bildirir.  Komut kaynağı yöntemini kullanarak geçerli durumunu sorgulayabilir <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> .  Komut yürütülemez ise, komut kaynağı kendisini devre dışı bırakabilir.  Bu bir örnek, bir <xref:System.Windows.Controls.MenuItem> komut yürütümediğinde kendinden gri bir örnektir.  
  
 Bir <xref:System.Windows.Input.InputGesture> komut kaynağı olarak kullanılabilir.  ' De iki tür giriş hareketi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vardır <xref:System.Windows.Input.KeyGesture> <xref:System.Windows.Input.MouseGesture> .  <xref:System.Windows.Input.KeyGesture>CTRL + C gibi bir klavye kısayolu olarak düşünebilirsiniz.  <xref:System.Windows.Input.KeyGesture>, Bir <xref:System.Windows.Input.Key> ve kümesinden oluşur <xref:System.Windows.Input.ModifierKeys> .  <xref:System.Windows.Input.MouseGesture>, <xref:System.Windows.Input.MouseAction> Ve isteğe bağlı bir kümesinden oluşur <xref:System.Windows.Input.ModifierKeys> .  
  
 Bir <xref:System.Windows.Input.InputGesture> komut kaynağı olarak davranması için, bir komutla ilişkilendirilmesi gerekir. Bunu yapmanın birkaç yolu vardır.  Tek bir yöntem kullanmaktır <xref:System.Windows.Input.InputBinding> .  
  
 Aşağıdaki örnek, ve arasında bir oluşturma yöntemi gösterir <xref:System.Windows.Input.KeyBinding> <xref:System.Windows.Input.KeyGesture> <xref:System.Windows.Input.RoutedCommand> .  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 Bir ile ilişkilendirmenin bir diğer yolu, <xref:System.Windows.Input.InputGesture> <xref:System.Windows.Input.RoutedCommand> üzerine öğesine eklemektir <xref:System.Windows.Input.InputGesture> <xref:System.Windows.Input.InputGestureCollection> <xref:System.Windows.Input.RoutedCommand> .  
  
 Aşağıdaki örnek, ' a ' öğesine nasıl ekleneceğini gösterir <xref:System.Windows.Input.KeyGesture> <xref:System.Windows.Input.InputGestureCollection> <xref:System.Windows.Input.RoutedCommand> .  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>
### <a name="commandbinding"></a>CommandBinding  
 <xref:System.Windows.Input.CommandBinding>, Komutu uygulayan olay işleyicileriyle bir komutu ilişkilendirir.  
  
 <xref:System.Windows.Input.CommandBinding>Sınıfı bir <xref:System.Windows.Input.CommandBinding.Command%2A> özelliği,,,, <xref:System.Windows.Input.CommandBinding.PreviewExecuted> <xref:System.Windows.Input.CommandBinding.Executed> <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> ve olaylarını içerir <xref:System.Windows.Input.CommandBinding.CanExecute> .  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>, ilişkili olduğu komuttur <xref:System.Windows.Input.CommandBinding> .  Ve olaylarına eklenen olay işleyicileri <xref:System.Windows.Input.CommandBinding.PreviewExecuted> <xref:System.Windows.Input.CommandBinding.Executed> komut mantığını uygular.  Ve olaylarına eklenen olay işleyicileri, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> <xref:System.Windows.Input.CommandBinding.CanExecute> komutun geçerli komut hedefinde yürütülüp yürütülmeyeceğini tespit edebilir.  
  
 Aşağıdaki örnek, bir uygulamanın kökünde nasıl oluşturulacağını gösterir <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Window> .  , <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.ApplicationCommands.Open%2A> Komutunu <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandBinding.CanExecute> işleyicileri ilişkilendirir.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Ardından, <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> oluşturulur.  , <xref:System.Windows.Input.ExecutedRoutedEventHandler> <xref:System.Windows.MessageBox> Komutun yürütüldüğünü söyleyen bir dize görüntüleyen bir açar.  , <xref:System.Windows.Input.CanExecuteRoutedEventHandler> <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> Özelliğini olarak ayarlar `true` .  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 <xref:System.Windows.Input.CommandBinding>, <xref:System.Windows.Window> Uygulamanın kökü veya bir denetim gibi belirli bir nesneye iliştirilir.  Öğesinin eklendiği nesne, <xref:System.Windows.Input.CommandBinding> bağlamanın kapsamını tanımlar.  Örneğin, <xref:System.Windows.Input.CommandBinding> komut hedefinin bir üst öğesine iliştirilmiş bir olay tarafından erişilebilir <xref:System.Windows.Input.CommandBinding.Executed> , ancak <xref:System.Windows.Input.CommandBinding> komut hedefinin alt öğesine eklenmiş bir öğeye ulaşılamıyor.  Bu, <xref:System.Windows.RoutedEvent> olayı oluşturan nesneden gelen tünellerin ve kabarcıkların doğrudan bir sonucudur.  
  
 Bazı durumlarda, <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Controls.TextBox> sınıfı ve <xref:System.Windows.Input.ApplicationCommands.Cut%2A> ,, <xref:System.Windows.Input.ApplicationCommands.Copy%2A> ve komutlarıyla birlikte komut hedefine iliştirilir <xref:System.Windows.Input.ApplicationCommands.Paste%2A> . Genellikle, <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Window> özellikle de aynı <xref:System.Windows.Input.CommandBinding> Çoklu komut hedefleri için kullanılabilir olması halinde, bir ana veya uygulama nesnesi gibi komut hedefinin bir üst öğesine eklenmesi daha uygundur.  Bunlar, komutlama altyapınızı oluştururken göz önünde bulundurmanız gereken tasarım kararlardır.  
  
<a name="Commane_Target"></a>
### <a name="command-target"></a>Komut hedefi  
 Komut hedefi, komutun yürütüldüğü öğedir.  Bir öğesine gelince <xref:System.Windows.Input.RoutedCommand> , komut hedefi, <xref:System.Windows.Input.CommandManager.Executed> ve ' ın yönlendirmenin başladığı öğedir <xref:System.Windows.Input.CommandManager.CanExecute> .  Daha önce belirtildiği gibi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> üzerindeki özelliğinde <xref:System.Windows.Input.ICommandSource> yalnızca bir olduğunda geçerlidir <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.RoutedCommand> .  , <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Bir üzerinde ayarlanırsa <xref:System.Windows.Input.ICommandSource> ve karşılık gelen komut bir değilse <xref:System.Windows.Input.RoutedCommand> , komut hedefi yok sayılır.  
  
 Komut kaynağı, komut hedefini açık bir şekilde ayarlayabilir.  Komut hedefi tanımlanmamışsa, klavye odaklı öğe komut hedefi olarak kullanılacaktır.  Komut hedefi olarak, öğesini klavye odağıyla birlikte kullanmanın avantajlarından biri, uygulama geliştiricisinin komut hedefini izlemek zorunda kalmadan birden çok hedefte bir komutu çağırmak için aynı komut kaynağını kullanmasına izin verir.  Örneğin, bir, bir denetim <xref:System.Windows.Controls.MenuItem> ve denetim içeren bir uygulamada **Yapıştır** komutunu çağırmışsa <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> , hedef, <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.PasswordBox> hangi denetimde klavye odağına sahip olduğuna bağlı olarak ya da olabilir.  
  
 Aşağıdaki örnek, biçimlendirme ve arka plan kodunda komut hedefinin açıkça nasıl ayarlanacağını gösterir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>
### <a name="the-commandmanager"></a>CommandManager  
 , <xref:System.Windows.Input.CommandManager> Bir dizi komutla ilgili işlevi sunar.  <xref:System.Windows.Input.CommandManager.PreviewExecuted>Belirli bir öğeden,, <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.Input.CommandManager.PreviewCanExecute> ve <xref:System.Windows.Input.CommandManager.CanExecute> olay işleyicileri eklemek ve kaldırmak için bir statik yöntemler kümesi sağlar.  Belirli bir sınıfa kaydolmak ve nesneler için bir yol sağlar <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.InputBinding> .  Ayrıca, olayı <xref:System.Windows.Input.CommandManager> <xref:System.Windows.Input.CommandManager.RequerySuggested> ne zaman tetiklemeli bir komuta bildirimde bulunan olay aracılığıyla bir yol sağlar <xref:System.Windows.Input.ICommand.CanExecuteChanged> .  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A>Yöntemi <xref:System.Windows.Input.CommandManager> olayını oluşturmaya zorlar <xref:System.Windows.Input.CommandManager.RequerySuggested> .  Bu, bir komutu devre dışı bırakmak/etkinleştirmek zorunda olan ancak durumunu algılayan koşullar için yararlıdır <xref:System.Windows.Input.CommandManager> .  
  
<a name="Command_Library"></a>
## <a name="command-library"></a>Komut kitaplığı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]önceden tanımlanmış bir komutlar kümesi sağlar.  Komut kitaplığı, aşağıdaki sınıflardan oluşur: <xref:System.Windows.Input.ApplicationCommands> ,,, <xref:System.Windows.Input.NavigationCommands> <xref:System.Windows.Input.MediaCommands> <xref:System.Windows.Documents.EditingCommands> ve <xref:System.Windows.Input.ComponentCommands> .  Bu sınıflar, ve,, ve gibi komutları sağlar <xref:System.Windows.Input.ApplicationCommands.Cut%2A> <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A> <xref:System.Windows.Input.MediaCommands.Play%2A> <xref:System.Windows.Input.MediaCommands.Stop%2A> <xref:System.Windows.Input.MediaCommands.Pause%2A> .  
  
 Bu komutların birçoğu, varsayılan giriş bağlamaları kümesini içerir.  Örneğin, uygulamanızın kopyalama komutunu işlediğini belirtirseniz, otomatik olarak "CTRL + C" klavye bağlamasını alırsınız. Ayrıca, Tablet PC kalem hareketleri ve konuşma bilgileri gibi diğer giriş cihazlarına yönelik bağlamaları da alırsınız.  
  
 Kullanarak çeşitli komut kitaplıklarında komutlara başvurduğunuzda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , genellikle statik komut özelliğini sunan kitaplık sınıfının sınıf adını atlayabilirsiniz. Genellikle, komut adları dizeler olarak anlaşılır ve sahip olan türler, bir komut mantıksal gruplandırması sağlamak için vardır ancak Kesinleştirme için gerekli değildir. Örneğin, daha ayrıntılı yerine belirtebilirsiniz `Command="Cut"` `Command="ApplicationCommands.Cut"` . Bu, komutları için işlemcinin içinde yerleşik olarak bulunan kullanışlı bir mekanizmadır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . (daha kesin olarak, <xref:System.Windows.Input.ICommand> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin yükleme zamanında başvurduğu bir tür dönüştürücü davranışıdır).  
  
<a name="creating_commands"></a>
## <a name="creating-custom-commands"></a>Özel komutlar oluşturma  
 Komut kitaplığı sınıflardaki komutlar gereksinimlerinizi karşılamıyorsa, kendi komutlarınızı oluşturabilirsiniz.  Özel bir komut oluşturmanın iki yolu vardır.  Birincisi, baştan başlayıp <xref:System.Windows.Input.ICommand> arabirimini uygulamaktır.  Diğer bir yöntem ve daha yaygın yaklaşım, <xref:System.Windows.Input.RoutedCommand> veya oluşturmaktır <xref:System.Windows.Input.RoutedUICommand> .  
  
 Özel bir oluşturma örneği için <xref:System.Windows.Input.RoutedCommand> bkz. özel bir [RoutedCommand örneği oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Girişe Genel Bakış](input-overview.md)
- [Gönderilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [ICommandSource Uygulama](how-to-implement-icommandsource.md)
- [Nasıl yapılır: MenuItem 'a komut ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Özel bir RoutedCommand örneği oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
