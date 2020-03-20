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
ms.openlocfilehash: 3477e6a9eda40edeadaab9cd6d3de2f016250fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186207"
---
# <a name="commanding-overview"></a>Komut Vermeye Genel Bakış
<a name="introduction"></a>Komut, giriş işlemeyi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aygıt girişinden daha semantik düzeyde sağlayan bir giriş mekanizmasıdır. Komutlara örnek olarak birçok uygulamada bulunan **Kopyala,** **Kes**ve **Yapıştır** işlemleri verilebilir.  
  
 Bu genel bakış, hangi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]komutların hangi komutların olduğunu, hangi sınıfların komut modelinin bir parçası olduğunu ve uygulamalarınızda komutların nasıl kullanılacağını ve oluşturulmasını tanımlar.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
- [Komutlar Nelerdir?](#commands_at_10000_feet)  
  
- [WPF'de Basit Komut Örneği](#simple_command)  
  
- [WPF Komutunda Dört Ana Kavram](#Four_main_Concepts)  
  
- [Komut Kütüphanesi](#Command_Library)  
  
- [Özel Komutlar Oluşturma](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>
## <a name="what-are-commands"></a>Komutlar Nelerdir?  
 Komutların birkaç amacı vardır. İlk amaç semantik ve komutu çağıran nesneyi komutu yürüten mantıktan ayırmaktır. Bu, birden çok ve birbirinden farklı kaynakların aynı komut mantığını çağırmasına ve komut mantığının farklı hedefler için özelleştirilemesine olanak tanır. Örneğin, birçok uygulamada bulunan düzenleme işlemleri **Kopyala,** **Kes**ve **Yapıştır**, komutları kullanılarak uygulandığında farklı kullanıcı eylemleri kullanılarak çağrılabilir. Uygulama, bir düğmeyi tıklatarak, menüdeki öğeyi seçerek veya CTRL+X gibi bir anahtar kombinasyonunu kullanarak kullanıcının seçili nesneleri veya metni kesmesine izin verebilir. Komutları kullanarak, her kullanıcı eylemi türünü aynı mantığa bağlayabilirsiniz.  
  
 Komutların diğer bir amacı da bir eylemin kullanılabilir olup olmadığını belirtmektir. Bir nesneyi veya metni kesme örneğine devam etmek için, eylem yalnızca bir şey seçildiğinde anlamlıdır. Bir kullanıcı bir nesneyi veya metni hiçbir şey seçilmeden kesmeye çalışırsa, hiçbir şey olmaz. Bunu kullanıcıya göstermek için, birçok uygulama düğmeleri ve menü öğelerini devre dışı bırakıp kullanıcının bir eylem gerçekleştirmenin mümkün olup olmadığını bilmesiiçin devre dışı kalır. Bir <xref:System.Windows.Input.ICommand.CanExecute%2A> komut, yöntemi uygulayarak bir eylemin mümkün olup olmadığını gösterebilir. Bir düğme <xref:System.Windows.Input.ICommand.CanExecuteChanged> etkinliğe abone olabilir <xref:System.Windows.Input.ICommand.CanExecute%2A> ve `false` döndürürse devre dışı tutulabilir veya döndürürse <xref:System.Windows.Input.ICommand.CanExecute%2A> `true`etkinleştirilebilir.  
  
 Bir komutun anlambilimi uygulamalar ve sınıflar arasında tutarlı olabilir, ancak eylemin mantığı belirli bir nesneye özgüdür. CTRL+X tuş kombinasyonu metin sınıflarında, görüntü sınıflarında ve Web tarayıcılarında **Kesme** komutunu çağırır, ancak **Kesme** işlemini gerçekleştirmek için gerçek mantık kesme işlemini gerçekleştiren uygulama tarafından tanımlanır. A <xref:System.Windows.Input.RoutedCommand> istemcilerin mantığı uygulamasına olanak tanır. Metin nesnesi seçili metni panoya kesebilirken, görüntü nesnesi seçili görüntüyü kesebilir. Bir uygulama <xref:System.Windows.Input.CommandManager.Executed> olayı işlediğinde, komutun hedefine erişebilir ve hedefin türüne bağlı olarak uygun eylemi gerçekleştirebilir.  
  
<a name="simple_command"></a>
## <a name="simple-command-example-in-wpf"></a>WPF'de Basit Komut Örneği  
 Komutu kullanmanın en basit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yolu, komut <xref:System.Windows.Input.RoutedCommand> kitaplığı sınıflarından birinden önceden tanımlanmış bir komut kitaplığı kullanmaktır; komutu işlemek için yerel desteğe sahip bir denetim kullanın; ve bir komut çağırmak için yerel desteği olan bir denetim kullanın.  Komut, <xref:System.Windows.Input.ApplicationCommands.Paste%2A> <xref:System.Windows.Input.ApplicationCommands> sınıftaönceden tanımlanmış komutlardan biridir.  Denetim <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu işlemek için mantık yerleşiktir.  Ve <xref:System.Windows.Controls.MenuItem> sınıfın komutları çağırmak için yerel desteği var.  
  
 Aşağıdaki örnek, tıklatıldığında klavye <xref:System.Windows.Controls.MenuItem> odağı olduğunu varsayarak <xref:System.Windows.Input.ApplicationCommands.Paste%2A> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> komutu çağıracak şekilde nasıl ayarlanacağını gösterir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>
## <a name="four-main-concepts-in-wpf-commanding"></a>WPF Komutunda Dört Ana Kavram  
 Yönlendirilen komut [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modeli dört ana kavrama ayrılabilir: komut, komut kaynağı, komut hedefi ve komut bağlama:  
  
- *Komut,* yürütülecek eylemdir.  
  
- *Komut kaynağı* komutu çağıran nesnedir.  
  
- *Komut hedefi,* komutun yürütüldettiği nesnedir.  
  
- *Komut bağlama* komut uyruğa komut mantığı eşleyen nesnedir.  
  
 Önceki örnekte, <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komut komutu, <xref:System.Windows.Controls.MenuItem> komut kaynağı, komut <xref:System.Windows.Controls.TextBox> hedefi ve komut bağlama <xref:System.Windows.Controls.TextBox> denetimi tarafından sağlanır.  Bu komut hedef sınıfı olan denetim tarafından <xref:System.Windows.Input.CommandBinding> sağlanan her zaman durumda olmadığını belirtmekte yarar vardır.  Genellikle uygulama <xref:System.Windows.Input.CommandBinding> geliştiricisi tarafından oluşturulmalıdır <xref:System.Windows.Input.CommandBinding> veya komut hedefinin bir atasına iliştirilmiş olabilir.  
  
<a name="Commands"></a>
### <a name="commands"></a>Komutlar  
 Komutlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommand> arabirimi uygulanarak oluşturulur.  <xref:System.Windows.Input.ICommand>ve bir olayı, iki yöntemi <xref:System.Windows.Input.ICommand.Execute%2A> <xref:System.Windows.Input.ICommand.CanExecute%2A>ortaya <xref:System.Windows.Input.ICommand.CanExecuteChanged>çıkarır. <xref:System.Windows.Input.ICommand.Execute%2A>komutla ilişkili eylemleri gerçekleştirir. <xref:System.Windows.Input.ICommand.CanExecute%2A>komutun geçerli komut hedefinde yürütülüp yürütemeyeceğini belirler. <xref:System.Windows.Input.ICommand.CanExecuteChanged>komut işlemlerini merkezileştiren komut yöneticisi, komut kaynağında yükseltilmiş ancak komut bağlama tarafından henüz yürütülmemiş bir komutu geçersiz kılabilecek bir değişiklik algılarsa yükseltilir.  Uygulama [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.RoutedCommand> sınıfıdır ve bu genel bakışın odak noktasıdır.  
  
 Girişin ana kaynakları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fare, klavye, mürekkep ve yönlendirilmiş komutlardır.  Aygıt ayarı yönelimli girişler, bir uygulama sayfasındaki nesneleri bir giriş olayının oluştuğunu bildirmek <xref:System.Windows.RoutedEvent> için kullanır.  A <xref:System.Windows.Input.RoutedCommand> da farklı değil.  <xref:System.Windows.Input.RoutedCommand.Execute%2A> <xref:System.Windows.Input.RoutedCommand> Bir komut için uygulama mantığı içermez, daha ziyade bir nesne ile karşılaşına kadar eleman ağacı ile tünel ve kabarcık yönlendirilmiş olayları yükseltmek <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.RoutedCommand.CanExecute%2A>  Bu <xref:System.Windows.Input.CommandBinding> olayların işleyicilerini içerir ve komutu gerçekleştiren işleyicileridir.  Olay yönlendirmesi hakkında daha [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fazla bilgi için, [Yönlendirilmiş Olaylara Genel Bakış'a](routed-events-overview.md)bakın.  
  
 Bir <xref:System.Windows.Input.RoutedCommand.Execute%2A> <xref:System.Windows.Input.RoutedCommand> yöntem, komut <xref:System.Windows.Input.CommandManager.PreviewExecuted> hedefindeki <xref:System.Windows.Input.CommandManager.Executed> olayları ve olayları yükseltir.  Bir <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntem <xref:System.Windows.Input.RoutedCommand> komut <xref:System.Windows.Input.CommandManager.CanExecute> hedefi <xref:System.Windows.Input.CommandManager.PreviewCanExecute> ve olayları yükseltir.  Bu olaylar tünel ve kabarcık bu özel <xref:System.Windows.Input.CommandBinding> komutu olan bir nesne karşılaşına kadar eleman ağacı ile.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]çeşitli sınıflara yayılmış ortak yönlendirilmiş komutlar <xref:System.Windows.Input.MediaCommands> <xref:System.Windows.Input.ApplicationCommands>kümesi <xref:System.Windows.Input.NavigationCommands> <xref:System.Windows.Input.ComponentCommands>sağlar: <xref:System.Windows.Documents.EditingCommands>, , , ve .  Bu sınıflar yalnızca <xref:System.Windows.Input.RoutedCommand> komutun uygulama mantığından değil, nesnelerden oluşur.  Uygulama mantığı, komutun yürütüldettiği nesnenin sorumluluğundadır.  
  
<a name="Command_Sources"></a>
### <a name="command-sources"></a>Komut Kaynakları  
 Komut kaynağı, komutu çağıran nesnedir.  Komut kaynaklarına <xref:System.Windows.Controls.MenuItem>örnek <xref:System.Windows.Controls.Button>olarak <xref:System.Windows.Input.KeyGesture>, ve .  
  
 Komut kaynakları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] genellikle <xref:System.Windows.Input.ICommandSource> arabirimi uygular.  
  
 <xref:System.Windows.Input.ICommandSource>üç özelliği ni <xref:System.Windows.Input.ICommandSource.Command%2A> <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>ortaya <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>çıkarır: , , ve :  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A>komut kaynağı çağrıldığı zaman yürütmek için komutudur.  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>komutu yürütmek için nesnedir.  Bu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> özellik üzerinde <xref:System.Windows.Input.ICommandSource> sadece bir <xref:System.Windows.Input.ICommand> <xref:System.Windows.Input.RoutedCommand>olduğunda uygulanabilir olduğunu belirtmekte yarar vardır .  <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Bir'de <xref:System.Windows.Input.ICommandSource> ayarlanırsa ve ilgili komut <xref:System.Windows.Input.RoutedCommand>bir değilse, komut hedefi yoksayılır. Ayarlı <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> değilse, klavye odaklı eleman komut hedefi olacaktır.  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>komutu uygulayan işleyicilere bilgi aktarmak için kullanılan kullanıcı tanımlı bir veri türüdür.  
  
 Uygulayan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource> <xref:System.Windows.Controls.Primitives.ButtonBase>sınıflar , <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Input.InputBinding>ve .  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink> ve tıklatıldığında bir komut çağırır <xref:System.Windows.Input.InputBinding> ve ilişkili yapıldığında <xref:System.Windows.Input.InputGesture> bir komut çağırır.  
  
 Aşağıdaki örnekte, a <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ContextMenu> <xref:System.Windows.Input.ApplicationCommands.Properties%2A> komutu için komut kaynağı olarak nasıl kullanılacağı gösterilmektedir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Genellikle, bir komut kaynağı <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> olayı dinler.  Bu olay, komut kaynağına, komutun geçerli komut hedefinde yürütme yeteneğinin değişmiş olabileceğini bildirir.  Komut kaynağı <xref:System.Windows.Input.RoutedCommand> <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemi kullanarak geçerli durumunu sorgulayabilir.  Komut yürütülemiyorsa komut kaynağı kendisini devre dışı kılabilir.  Bunun bir örneği, <xref:System.Windows.Controls.MenuItem> bir komut yürütülemediğinde kendiliğinden ağarmasıdır.  
  
 Bir <xref:System.Windows.Input.InputGesture> komut kaynağı olarak kullanılabilir.  Giriş hareketlerinin iki türü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.KeyGesture> ve <xref:System.Windows.Input.MouseGesture>.  CtRL+C <xref:System.Windows.Input.KeyGesture> gibi bir klavye kısayolu olarak düşünebilirsiniz.  A, <xref:System.Windows.Input.KeyGesture> bir <xref:System.Windows.Input.Key> ve bir dizi <xref:System.Windows.Input.ModifierKeys>.'den oluşur.  A, <xref:System.Windows.Input.MouseGesture> bir <xref:System.Windows.Input.MouseAction> ve isteğe bağlı <xref:System.Windows.Input.ModifierKeys>bir dizi .'den oluşur.  
  
 Bir <xref:System.Windows.Input.InputGesture> komut kaynağı olarak hareket edebilmek için bir komutile ilişkilendirilmelidir. Bunu başarmanın birkaç yolu vardır.  Bir yolu kullanmaktır <xref:System.Windows.Input.InputBinding>.  
  
 Aşağıdaki örnekte, a <xref:System.Windows.Input.KeyBinding> ile <xref:System.Windows.Input.KeyGesture> a <xref:System.Windows.Input.RoutedCommand>arasında nasıl oluşturulacak gösteriliyor.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 A ile <xref:System.Windows.Input.InputGesture> ilişkilendirmek <xref:System.Windows.Input.RoutedCommand> için başka <xref:System.Windows.Input.InputGesture> bir <xref:System.Windows.Input.InputGestureCollection> yolu <xref:System.Windows.Input.RoutedCommand>üzerinde eklemektir.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Input.KeyGesture> <xref:System.Windows.Input.InputGestureCollection> <xref:System.Windows.Input.RoutedCommand>.'ün 'e nasıl bir a eklenilir  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>
### <a name="commandbinding"></a>CommandBinding  
 Bir <xref:System.Windows.Input.CommandBinding> komutu, komutu uygulayan olay işleyicileriyle ilişkilendirir.  
  
 Sınıf, <xref:System.Windows.Input.CommandBinding> bir <xref:System.Windows.Input.CommandBinding.Command%2A> özellik <xref:System.Windows.Input.CommandBinding.PreviewExecuted>ve <xref:System.Windows.Input.CommandBinding.Executed> <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, <xref:System.Windows.Input.CommandBinding.CanExecute> , ve olaylar içerir.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>ile ilişkili <xref:System.Windows.Input.CommandBinding> olan komutudur.  Olay işleyicileri <xref:System.Windows.Input.CommandBinding.PreviewExecuted> ve <xref:System.Windows.Input.CommandBinding.Executed> olaylar bağlı komut mantığını uygular.  Olay işleyicileri ekli <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> ve <xref:System.Windows.Input.CommandBinding.CanExecute> olaylar komutu geçerli komut hedefi üzerinde yürütebilir olup olmadığını belirler.  
  
 Aşağıdaki örnek, bir uygulamanın kökünde <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Window> nasıl oluşturulacak gösterilmektedir.  Komutu <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.ApplicationCommands.Open%2A> ve <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.Input.CommandBinding.CanExecute> işleyicileri ilişkilendiren.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Sonra, <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> a oluşturulur.  Açılan <xref:System.Windows.Input.ExecutedRoutedEventHandler> a <xref:System.Windows.MessageBox> komutun yürütüldedildiğini belirten bir dize görüntüler.  Özelliği <xref:System.Windows.Input.CanExecuteRoutedEventHandler> . <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> `true`  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A, <xref:System.Windows.Input.CommandBinding> uygulamanın kökü <xref:System.Windows.Window> veya denetim gibi belirli bir nesneye eklenir.  Bağlı olduğu <xref:System.Windows.Input.CommandBinding> nesne bağlama nın kapsamını tanımlar.  Örneğin, komut <xref:System.Windows.Input.CommandBinding> hedefinin atasına bağlı bir ataya <xref:System.Windows.Input.CommandBinding.Executed> olay <xref:System.Windows.Input.CommandBinding> tarafından ulaşılabilir, ancak komut hedefinin soyundan gelen bir bağlıya ulaşılamaz.  Bu, bir <xref:System.Windows.RoutedEvent> tünelin ve kabarcıkların olayı yükselten nesneden çıkışının doğrudan bir sonucudur.  
  
 <xref:System.Windows.Input.CommandBinding> Bazı durumlarda komut hedefinin kendisine, <xref:System.Windows.Controls.TextBox> sınıf ve <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, , <xref:System.Windows.Input.ApplicationCommands.Copy%2A>ve <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutlar gibi eklenir. Ancak çoğu zaman, özellikle aynı <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Window> <xref:System.Windows.Input.CommandBinding> sıyrık birden çok komut hedefi için kullanılabilse, ana veya Uygulama nesnesi gibi komut hedefinin atasına eklemek daha uygundur.  Bunlar, komuta altyapınızı oluştururken göz önünde bulundurmak isteyeceğiniz tasarım kararlarıdır.  
  
<a name="Commane_Target"></a>
### <a name="command-target"></a>Hedef Komutu  
 Komut hedefi, komutun yürütüldolduğu öğedir.  Bir, <xref:System.Windows.Input.RoutedCommand>komut hedefi ile ilgili olarak hangi yönlendirme <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandManager.CanExecute> başlar öğesidir.  Daha önce de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] belirtildiği <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> gibi, özellik <xref:System.Windows.Input.ICommandSource> sadece <xref:System.Windows.Input.ICommand> bir <xref:System.Windows.Input.RoutedCommand>.  <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> Bir'de <xref:System.Windows.Input.ICommandSource> ayarlanırsa ve ilgili komut <xref:System.Windows.Input.RoutedCommand>bir değilse, komut hedefi yoksayılır.  
  
 Komut kaynağı açıkça komut hedefini ayarlayabilir.  Komut hedefi tanımlanmamışsa, klavye odaklı öğe komut hedefi olarak kullanılır.  Komut hedefi olarak klavye odağı ile öğe kullanmanın yararlarından biri, uygulama geliştiricisi komut hedefi izlemek zorunda kalmadan birden çok hedef üzerinde bir komut çağırmak için aynı komut kaynağını kullanmasına izin verir.  Örneğin, denetimi <xref:System.Windows.Controls.MenuItem> ve <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> denetimi olan bir uygulamada Yapıştır **komutunu** çağırırsa, hedef klavye <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.PasswordBox> odağına sahip olan denetime bağlı olarak olabilir.  
  
 Aşağıdaki örnek, komut hedefinin işaretleme ve kod arkasında açıkça nasıl ayarlanır olduğunu gösterir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>
### <a name="the-commandmanager"></a>Komutan Yönetici  
 Komutla <xref:System.Windows.Input.CommandManager> ilgili bir dizi işlev eve hizmet eder.  Belirli bir öğeye ve olay işleyicilerine <xref:System.Windows.Input.CommandManager.PreviewCanExecute>ekleme <xref:System.Windows.Input.CommandManager.CanExecute> ve çıkarma <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.Input.CommandManager.Executed>için bir dizi statik yöntem sağlar.  Belirli bir sınıfa <xref:System.Windows.Input.CommandBinding> <xref:System.Windows.Input.InputBinding> kaydolmak ve nesneleri kaydetmek için bir araç sağlar.  Ayrıca, <xref:System.Windows.Input.CommandManager> <xref:System.Windows.Input.CommandManager.RequerySuggested> <xref:System.Windows.Input.ICommand.CanExecuteChanged> olay aracılığıyla, olayı yükseltmesi gereken bir komutu bildirmek için bir araç sağlar.  
  
 Yöntem <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> <xref:System.Windows.Input.CommandManager.RequerySuggested> olayı <xref:System.Windows.Input.CommandManager> yükseltmek için zorlar.  Bu, bir komutu devre dışı/ etkinleştirmesi gereken ancak <xref:System.Windows.Input.CommandManager> bunun farkında olduğu koşullar olmayan koşullar için yararlıdır.  
  
<a name="Command_Library"></a>
## <a name="command-library"></a>Komut Kütüphanesi  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]önceden tanımlanmış komutlar kümesi sağlar.  Komut kitaplığı aşağıdaki sınıflardan <xref:System.Windows.Input.ApplicationCommands> <xref:System.Windows.Input.NavigationCommands>oluşur: <xref:System.Windows.Documents.EditingCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.MediaCommands>, ve .  Bu <xref:System.Windows.Input.ApplicationCommands.Cut%2A>sınıflar , ve <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>, <xref:System.Windows.Input.MediaCommands.Pause%2A>ve .  
  
 Bu komutların çoğu varsayılan giriş bağlamaları kümesi içerir.  Örneğin, uygulamanızın kopyalama komutunu işlettiğini belirtirseniz, otomatik olarak klavye bağlama "CTRL+C" alırsınız Tablet PC kalem hareketleri ve konuşma bilgileri gibi diğer giriş aygıtları için de bağlayıcılar elde elabilirsiniz.  
  
 Çeşitli komut kitaplıklarında komutlara [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]atıfta bulunarak, genellikle statik komut özelliğini ortaya çıkaran kitaplık sınıfının sınıf adını atlayabilirsiniz. Genellikle, komut adları dizeleri olarak açık ve sahip olmak türleri komutları mantıksal bir gruplandırma sağlamak için var, ancak ayrışma için gerekli değildir. Örneğin, daha ayrıntılı `Command="Cut"` yerine `Command="ApplicationCommands.Cut"`belirtebilirsiniz. Bu komutlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] için işlemci yerleşik bir kolaylık mekanizmasıdır (daha doğrusu, bir tür <xref:System.Windows.Input.ICommand>dönüştürücü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] davranışıdır , hangi işlemci yük zamanında başvurur).  
  
<a name="creating_commands"></a>
## <a name="creating-custom-commands"></a>Özel Komutlar Oluşturma  
 Komut kitaplığı sınıflarında komutlar gereksinimlerinizi karşılamıyorsa, kendi komutlarınızı oluşturabilirsiniz.  Özel komut oluşturmanın iki yolu vardır.  Birincisi sıfırdan başlayıp <xref:System.Windows.Input.ICommand> arayüzü uygulamaktır.  Diğer yol ve daha yaygın bir yaklaşım, <xref:System.Windows.Input.RoutedCommand> bir <xref:System.Windows.Input.RoutedUICommand>veya bir oluşturmaktır.  
  
 Özel <xref:System.Windows.Input.RoutedCommand>oluşturma örneği için [bkz.](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [Girişe Genel Bakış](input-overview.md)
- [Gönderilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [ICommandSource Uygulama](how-to-implement-icommandsource.md)
- [Nasıl yapılsın: MenuItem'e Komut Ekleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [Özel RoutedCommand Örneği Oluşturma](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
