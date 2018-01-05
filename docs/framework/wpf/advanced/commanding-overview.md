---
title: "Komut Vermeye Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1af7d9dba986c3775dc3625d1e7a874f6b26c97d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="commanding-overview"></a>Komut Vermeye Genel Bakış
<a name="introduction"></a>Kumanda bir giriş mekanizmasıdır içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] giriş cihaz giriş'den fazla anlamsal düzeyde işlenmesini sağlar. Komut örneklerindendir **kopya**, **Kes**, ve **Yapıştır** işlemleri birçok uygulama üzerinde bulunamadı.  
  
 Bu genel bakışta komutları bulunan tanımlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], hangi sınıfların komut verme modelinin bir parçası olduğunu ve uygulamalarınızda kullanın ve oluşturmak nasıl komutları.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
-   [Komutlar nelerdir?](#commands_at_10000_feet)  
  
-   [WPF içindeki basit komut örneği](#simple_command)  
  
-   [WPF kumanda dört ana kavramlar](#Four_main_Concepts)  
  
-   [Komut kitaplığı](#Command_Library)  
  
-   [Özel komutlar oluşturma](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>   
## <a name="what-are-commands"></a>Komutlar nelerdir?  
 Komutların birkaç amacı vardır. İlk amacı semantiğini ve komutu yürütür mantığı komuttan çağırır nesne ayrı sağlamaktır. Bu çoklu ve aynı komut mantığı ve çağrılacak ayrık kaynaklara farklı hedefler için özelleştirilmek üzere komut mantığı olanak sağlar. Örneğin, düzenleme işlemleri **kopya**, **Kes**, ve **Yapıştır**, birçok uygulamada bulunduğu çağrılabilir olmaları durumunda farklı kullanıcı eylemleri kullanılarak komutları kullanılarak uygulanır. Bir uygulama bir kullanıcı ya da menüde bir öğeyi seçerek veya CTRL + X gibi bir tuş bileşimini kullanarak bir düğmeye tıklayarak seçilen nesneler veya metin kesme sağlayabilir. Komutları kullanarak, her bir kullanıcı eylemi türü aynı mantığı bağlayabilirsiniz.  
  
 Bir eylemin kullanılabilir olup olmadığını belirtmek için komutları başka bir amacı budur. Bir şey seçildiğinde bir nesneyi veya metni kesme örneği devam etmek için eylem yalnızca anlamlıdır. Bir kullanıcı herhangi bir şeyi seçmeden bir nesne veya metni kesme çalışırsa, hiçbir şey olmaz. Böylece bir eylem gerçekleştirmeniz mümkün olup olmadığını kullanıcının bildiği bu kullanıcıya belirtmek için birçok uygulama düğmelerini ve menü öğelerini devre dışı bırakın. Bir komut uygulayarak bir eylem mümkün olup olmadığını belirtebilir <xref:System.Windows.Input.ICommand.CanExecute%2A> yöntemi. Düğme için abone olabilirsiniz <xref:System.Windows.Input.ICommand.CanExecuteChanged> olay ve devre dışı <xref:System.Windows.Input.ICommand.CanExecute%2A> döndürür `false` veya etkinleştirilmesi <xref:System.Windows.Input.ICommand.CanExecute%2A> döndürür `true`.  
  
 Bir komut semantiği uygulamaları ve sınıflar arasında tutarlı olabilir, ancak eylemin mantığı üzerinde işlem belirli nesne için belirli. CTRL + X çağırır tuş bileşimini **Kes** metin sınıfları, görüntü sınıfları ve Web tarayıcıları, ancak gerçekleştirmek için gerçek mantığı komutunu **Kes** işlemi gerçekleştiren uygulama tarafından tanımlanan kesme. A <xref:System.Windows.Input.RoutedCommand> istemcilerin mantığı uygulamasını sağlar. Bir resim nesnesi seçilen görüntü Kes ancak bir metin nesnesi panoya seçili metni keser. Ne zaman bir uygulamayı işleme <xref:System.Windows.Input.CommandManager.Executed> olay komut hedefinin erişimi olduğundan ve hedefin türüne bağlı olarak uygun eylemi alabilir.  
  
<a name="simple_command"></a>   
## <a name="simple-command-example-in-wpf"></a>WPF içindeki basit komut örneği  
 Bir komutu kullanmak için en basit yolu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] önceden tanımlanmış bir kullanmaktır <xref:System.Windows.Input.RoutedCommand> komut kitaplığı sınıflarının; birinden; komutu işlemek için yerel destek sahip bir denetim ve bir komut çağırmadan için yerel destek sahip bir denetimini kullanın.  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> Komuttur içindeki önceden tanımlanmış komutlarından birini <xref:System.Windows.Input.ApplicationCommands> sınıfı.  <xref:System.Windows.Controls.TextBox> Denetim işleme mantığı içinde yerleşik <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutu.  Ve <xref:System.Windows.Controls.MenuItem> sınıfı komutları çağırma için yerel destek sahiptir.  
  
 Aşağıdaki örnekte nasıl ayarlanacağını gösterir bir <xref:System.Windows.Controls.MenuItem> böylece tıklandığında çağırma <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutunu bir <xref:System.Windows.Controls.TextBox>olduğunu varsayarak <xref:System.Windows.Controls.TextBox> klavye odağını sahiptir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>   
## <a name="four-main-concepts-in-wpf-commanding"></a>WPF kumanda dört ana kavramlar  
 Yönlendirilmiş komut modelinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dört ana kavrama ayrılabilir: komut, komut kaynağı, komut hedefi ve komut bağlama:  
  
-   *Komutu* yürütülecek eylem.  
  
-   *Komut kaynağı* komutu çağıran nesnesidir.  
  
-   *Komut hedefi* komut üzerinde yürütülmekte olan nesnesidir.  
  
-   *Komut bağlama* komut mantığını komuta eşleştiren nesnesidir.  
  
 Önceki örnekte, <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komuttur komutu <xref:System.Windows.Controls.MenuItem> komutu kaynak <xref:System.Windows.Controls.TextBox> komut hedefidir ve komut bağlama tarafından sağlanan <xref:System.Windows.Controls.TextBox> denetim.  Bu, her zaman çalışması olmadığını önemlidir, <xref:System.Windows.Input.CommandBinding> komutu hedef sınıf denetimi tarafından sağlanır.  Genellikle <xref:System.Windows.Input.CommandBinding> uygulama geliştiricisi tarafından oluşturulmalıdır veya <xref:System.Windows.Input.CommandBinding> için komut hedefinin bir üst öğesine bağlı.  
  
<a name="Commands"></a>   
### <a name="commands"></a>Komutlar  
 İçindeki komutlar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama tarafından oluşturulan <xref:System.Windows.Input.ICommand> arabirimi.  <xref:System.Windows.Input.ICommand>iki yöntem sunar <xref:System.Windows.Input.ICommand.Execute%2A>, ve <xref:System.Windows.Input.ICommand.CanExecute%2A>ve bir olay <xref:System.Windows.Input.ICommand.CanExecuteChanged>. <xref:System.Windows.Input.ICommand.Execute%2A>komut ile ilişkili eylemleri gerçekleştirir. <xref:System.Windows.Input.ICommand.CanExecute%2A>Geçerli komut hedefinde komutun yürütülüp yürütülmeyeceğini belirler. <xref:System.Windows.Input.ICommand.CanExecuteChanged>komut verme işlemlerini merkezi hale getirir komutu Yöneticisi oluşturuldu, ancak henüz komut bağlama tarafından yürütülen komutu kılmak komut kaynağı bir değişiklik algılarsa tetiklenir.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Uyarlamasını <xref:System.Windows.Input.ICommand> olan <xref:System.Windows.Input.RoutedCommand> sınıfı ve odak noktası, bu genel bakış.  
  
 Giriş ana kaynakları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fare, klavye, mürekkep ve yönlendirilen komutlardır.  Daha fazla aygıt odaklı girişleri kullanın bir <xref:System.Windows.RoutedEvent> giriş olayı oluştu bir uygulama sayfasını nesneleri bildirir.  A <xref:System.Windows.Input.RoutedCommand> farklı değildir.  <xref:System.Windows.Input.RoutedCommand.Execute%2A> Ve <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemlerinin bir <xref:System.Windows.Input.RoutedCommand> komutu için uygulama mantığını içermesi gerekmez, ancak yerine tünel yönlendirilmiş olaylar yükseltmek ve bir nesneyle karşılaştıkları kadar öğe ağacı üzerinden Kabarcık bir <xref:System.Windows.Input.CommandBinding>.  <xref:System.Windows.Input.CommandBinding> Bu olayları için işleyiciler içerir ve komut gerçekleştiren işleyicileri olur.  İçindeki olay yönlendirme hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 <xref:System.Windows.Input.RoutedCommand.Execute%2A> Yöntemi bir <xref:System.Windows.Input.RoutedCommand> başlatır <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> komut hedefi olaylarına.  <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> Yöntemi bir <xref:System.Windows.Input.RoutedCommand> başlatır <xref:System.Windows.Input.CommandManager.CanExecute> ve <xref:System.Windows.Input.CommandManager.PreviewCanExecute> komut hedefi olaylarına.  Bu olaylar tünel ve kabarcık sahip olan bir nesne karşılaştıkları kadar öğe ağacı üzerinden bir <xref:System.Windows.Input.CommandBinding> o belirli komut için.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ortak yönlendirilmiş komutlar kümesi birkaç sınıf arasında yayılan kaynakları: <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.ComponentCommands>, ve <xref:System.Windows.Documents.EditingCommands>.  Bu sınıfların yalnızca oluşur <xref:System.Windows.Input.RoutedCommand> nesneleri ve değil uygulama mantığı komutu.  Uygulama mantığı üzerinde komut üzerinde yürütülmekte olan nesne sorumluluğundadır.  
  
<a name="Command_Sources"></a>   
### <a name="command-sources"></a>Komut kaynakları  
 Bir komutu kaynağı komutu çağıran nesnedir.  Komut kaynakları örnekleri <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.Button>, ve <xref:System.Windows.Input.KeyGesture>.  
  
 İçindeki komut kaynakları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] genellikle uygulama <xref:System.Windows.Input.ICommandSource> arabirimi.  
  
 <xref:System.Windows.Input.ICommandSource>üç özellik sunar: <xref:System.Windows.Input.ICommandSource.Command%2A>, <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>, ve <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>:  
  
-   <xref:System.Windows.Input.ICommandSource.Command%2A>komut kaynağı çağrıldığında çalıştırılacak komuttur.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>komutu yürütmek üzerinde nesnedir.  Uygulamasında dikkate değerdir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> özelliği <xref:System.Windows.Input.ICommandSource> yalnızca uygun olduğunda <xref:System.Windows.Input.ICommand> olan bir <xref:System.Windows.Input.RoutedCommand>.  Varsa <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> üzerinde ayarlanmış bir <xref:System.Windows.Input.ICommandSource> ve karşılık gelen komutunu değil bir <xref:System.Windows.Input.RoutedCommand>, komut hedefi göz ardı edilir. Varsa <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> ayarlanmazsa klavye odağını öğeyle komut hedefi olacaktır.  
  
-   <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>işleyicilere bilgi geçirmek için kullanılan kullanıcı tanımlı veri türü komutu uygular.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sınıfları uygulayan <xref:System.Windows.Input.ICommandSource> olan <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Documents.Hyperlink>, ve <xref:System.Windows.Input.InputBinding>.  <xref:System.Windows.Controls.Primitives.ButtonBase>, <xref:System.Windows.Controls.MenuItem>, ve <xref:System.Windows.Documents.Hyperlink> bunlar tıklatıldığında ve bir komut çağırma <xref:System.Windows.Input.InputBinding> bir komutu çalıştırır, <xref:System.Windows.Input.InputGesture> ilişkili ile bu gerçekleştirilir.  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Windows.Controls.MenuItem> içinde bir <xref:System.Windows.Controls.ContextMenu> için komut kaynağı olarak <xref:System.Windows.Input.ApplicationCommands.Properties%2A> komutu.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 Genellikle, bir komut kaynağı için dinler <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> olay.  Bu olay, geçerli komut hedefinde yürütülecek komut yeteneklerini değişmiş olabilir komut kaynağı bildirir.  Komut kaynak geçerli durumunu sorgulayabilirsiniz <xref:System.Windows.Input.RoutedCommand> kullanarak <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> yöntemi.  Komutu yürütülemiyor komut kaynağı ardından kendisini devre dışı bırakabilirsiniz.  Bunun bir örneği bir <xref:System.Windows.Controls.MenuItem> kendisini grileştirmesi bir komut yürütülürken olamaz.  
  
 Bir <xref:System.Windows.Input.InputGesture> komut kaynağı olarak kullanılabilir.  İki tür giriş hareketleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] olan <xref:System.Windows.Input.KeyGesture> ve <xref:System.Windows.Input.MouseGesture>.  Düşünebilirsiniz bir <xref:System.Windows.Input.KeyGesture> CTRL + C gibi bir klavye kısayolu.  A <xref:System.Windows.Input.KeyGesture> oluşur bir <xref:System.Windows.Input.Key> ve bir dizi <xref:System.Windows.Input.ModifierKeys>.  A <xref:System.Windows.Input.MouseGesture> oluşur bir <xref:System.Windows.Input.MouseAction> ve isteğe bağlı bir dizi <xref:System.Windows.Input.ModifierKeys>.  
  
 Sırayla bir <xref:System.Windows.Input.InputGesture> komut kaynağı olarak görev yapması için bu komutu ile ilişkilendirilmiş olması gerekir. Bunu yapmanın birkaç yolu vardır.  Tek yönlü kullanmaktır bir <xref:System.Windows.Input.InputBinding>.  
  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Input.KeyBinding> arasında bir <xref:System.Windows.Input.KeyGesture> ve <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 İlişkilendirmek için başka bir yolu bir <xref:System.Windows.Input.InputGesture> için bir <xref:System.Windows.Input.RoutedCommand> eklemektir <xref:System.Windows.Input.InputGesture> için <xref:System.Windows.Input.InputGestureCollection> üzerinde <xref:System.Windows.Input.RoutedCommand>.  
  
 Aşağıdaki örnekte nasıl ekleneceğini gösterir bir <xref:System.Windows.Input.KeyGesture> için <xref:System.Windows.Input.InputGestureCollection> , bir <xref:System.Windows.Input.RoutedCommand>.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>   
### <a name="commandbinding"></a>CommandBinding  
 A <xref:System.Windows.Input.CommandBinding> bir komutu komutu işleyen olay işleyicileri ile ilişkilendirir.  
  
 <xref:System.Windows.Input.CommandBinding> Sınıfı içeren bir <xref:System.Windows.Input.CommandBinding.Command%2A> özelliği ve <xref:System.Windows.Input.CommandBinding.PreviewExecuted>, <xref:System.Windows.Input.CommandBinding.Executed>, <xref:System.Windows.Input.CommandBinding.PreviewCanExecute>, ve <xref:System.Windows.Input.CommandBinding.CanExecute> olaylar.  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A>Bu komut, <xref:System.Windows.Input.CommandBinding> ile ilişkili.  Bağlı olan olay işleyicileri <xref:System.Windows.Input.CommandBinding.PreviewExecuted> ve <xref:System.Windows.Input.CommandBinding.Executed> olayları komut mantığını uygular.  Olay işleyicileri bağlı <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> ve <xref:System.Windows.Input.CommandBinding.CanExecute> olayları belirlemek komutu geçerli komut hedefinde yürütülüp yürütülmeyeceğini.  
  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Input.CommandBinding> kökündeki <xref:System.Windows.Window> bir uygulama.  <xref:System.Windows.Input.CommandBinding> İlişkilendirir <xref:System.Windows.Input.ApplicationCommands.Open%2A> komutunu <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandBinding.CanExecute> işleyicileri.  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 Ardından, <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> oluşturulur.  <xref:System.Windows.Input.ExecutedRoutedEventHandler> Açılır bir <xref:System.Windows.MessageBox> komutu yürütüldü söyleyen bir dizeyi görüntüler.  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> Ayarlar <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> özelliğine `true`.  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 A <xref:System.Windows.Input.CommandBinding> kök gibi belirli bir nesneye iliştirilmiş <xref:System.Windows.Window> uygulama veya bir denetimin.  Nesne, <xref:System.Windows.Input.CommandBinding> tanımlar bağlama kapsamını bağlı.  Örneğin, bir <xref:System.Windows.Input.CommandBinding> bağlı komutu, bir üst öğesi için hedef tarafından erişilebildiğini <xref:System.Windows.Input.CommandBinding.Executed> olay, ancak bir <xref:System.Windows.Input.CommandBinding> bağlı komutunun alt öğesi için hedef ulaşılamıyor.  Bu şekilde doğrudan bir sonucu olan bir <xref:System.Windows.RoutedEvent> tünel ve balonları nesnesinden olayını başlatır.  
  
 Bazı durumlarda <xref:System.Windows.Input.CommandBinding> ile gibi komut hedefinin kendisine bağlı <xref:System.Windows.Controls.TextBox> sınıfı ve <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, ve <xref:System.Windows.Input.ApplicationCommands.Paste%2A> komutları. Genellikle ancak eklemek daha kullanışlı <xref:System.Windows.Input.CommandBinding> ana gibi komut hedefinin bir üst için <xref:System.Windows.Window> veya uygulama nesnesi özellikle de aynı <xref:System.Windows.Input.CommandBinding> birden çok komut hedefleri için kullanılabilir.  Komut verme altyapınızı oluştururken düşünmek isteyebilirsiniz tasarım kararları bunlar.  
  
<a name="Commane_Target"></a>   
### <a name="command-target"></a>Komut hedefi  
 Komut hedefi komutu yürütüldüğü öğedir.  Yönlendirilmesinin bir <xref:System.Windows.Input.RoutedCommand>, komut hedefi hangi yönlendirmesini adresindeki öğedir <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandManager.CanExecute> başlatır.  Önceden, belirtilen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> özelliği <xref:System.Windows.Input.ICommandSource> yalnızca uygun olduğunda <xref:System.Windows.Input.ICommand> olan bir <xref:System.Windows.Input.RoutedCommand>.  Varsa <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> üzerinde ayarlanmış bir <xref:System.Windows.Input.ICommandSource> ve karşılık gelen komutunu değil bir <xref:System.Windows.Input.RoutedCommand>, komut hedefi göz ardı edilir.  
  
 Komut kaynağı açıkça komut hedefi ayarlayabilirsiniz.  Komut hedefi tanımlı değil, klavye odağını öğeyle komut hedefi olarak kullanılır.  Öğe ile klavye odağı komut hedefi olarak kullanmanın avantajları komut hedefi izlemek zorunda kalmadan çoklu hedefler üzerinde komutu çağırmak için aynı komut kaynağını kullanmak uygulama geliştiricisi izin verdiğini biridir.  Örneğin, varsa bir <xref:System.Windows.Controls.MenuItem> çağırır **Yapıştır** olan bir uygulama komutunu bir <xref:System.Windows.Controls.TextBox> denetim ve <xref:System.Windows.Controls.PasswordBox> denetimi, hedef olabilir ya da <xref:System.Windows.Controls.TextBox> veya <xref:System.Windows.Controls.PasswordBox> seçtiğinize bağlı olarak klavye odağı denetimi vardır.  
  
 Aşağıdaki örnek açıkça komut hedefi biçimlendirme ve arka plan kodu nasıl ayarlanacağını gösterir.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>   
### <a name="the-commandmanager"></a>CommandManager  
 <xref:System.Windows.Input.CommandManager> İlgili işlevleri bir komut bir dizi görevi görür.  Ekleme ve kaldırma için statik yöntemler kümesi sağlar <xref:System.Windows.Input.CommandManager.PreviewExecuted>, <xref:System.Windows.Input.CommandManager.Executed>, <xref:System.Windows.Input.CommandManager.PreviewCanExecute>, ve <xref:System.Windows.Input.CommandManager.CanExecute> olay işleyicileri için ve belirli bir öğe.  Kaydetmek için bir yol sağlar <xref:System.Windows.Input.CommandBinding> ve <xref:System.Windows.Input.InputBinding> nesneleri belirli bir sınıf üzerine.  <xref:System.Windows.Input.CommandManager> Da aracılığıyla bir yolu sağlar <xref:System.Windows.Input.CommandManager.RequerySuggested> oluşturması gerektiğini komutu bildirmek için olay <xref:System.Windows.Input.ICommand.CanExecuteChanged> olay.  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> Yöntemi zorlar <xref:System.Windows.Input.CommandManager> yükseltmek için <xref:System.Windows.Input.CommandManager.RequerySuggested> olay.  Bu işlem için gereken koşullar faydalı olur devre dışı bırak/etkinleştir komutu ancak olmayan koşulları <xref:System.Windows.Input.CommandManager> bilmektedir.  
  
<a name="Command_Library"></a>   
## <a name="command-library"></a>Komut kitaplığı  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]önceden tanımlanmış komut kümesini sağlar.  Komut kitaplığı aşağıdaki sınıflardan oluşur: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, <xref:System.Windows.Documents.EditingCommands>ve <xref:System.Windows.Input.ComponentCommands>.  Bu sınıfların gibi komutları sağlar <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.NavigationCommands.BrowseBack%2A> ve <xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>, <xref:System.Windows.Input.MediaCommands.Play%2A>, <xref:System.Windows.Input.MediaCommands.Stop%2A>, ve <xref:System.Windows.Input.MediaCommands.Pause%2A>.  
  
 Bu komutların çoğu, varsayılan giriş bağlamaları kümesi içerir.  Belirtirseniz, uygulamanızın copy komutu işlediğinde, otomatik olarak "CTRL + C" bağlama klavye alın örneğin, ayrıca diğer giriş aygıtları için bağlamaları gibi elde edersiniz [!INCLUDE[TLA2#tla_tpc](../../../../includes/tla2sharptla-tpc-md.md)] kalem hareketleri ve konuşma bilgi.  
  
 Başvuru yaptığınızda kullanarak çeşitli komutu kitaplık komutlarda [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], genellikle statik komut özelliğini sunan kitaplık sınıfının sınıf adını atlayabilirsiniz. Genellikle, komut adlarının dize olarak anlaşılır ve sahibi olan türler komutları mantıksal bir gruplandırmasını sağlar ancak Kesinleştirme için gerekli değildir. Örneğin, belirtebilirsiniz `Command="Cut"` daha ayrıntılı yerine `Command="ApplicationCommands.Cut"`. İçinde yerleşik olan bir kolaylık mekanizması budur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci komutlar için (daha kesin bir türü dönüştürücü davranışını olan <xref:System.Windows.Input.ICommand>, hangi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] yükleme zamanında işlemci başvurduğu).  
  
<a name="creating_commands"></a>   
## <a name="creating-custom-commands"></a>Özel komutlar oluşturma  
 Komut kitaplığı sınıflarının komutlar gereksinimlerinizi karşılamazsa, kendi komutları oluşturabilirsiniz.  Özel bir komut oluşturmak için iki yolu vardır.  Sıfırdan başlamak ve uygulamak için ilk olduğu <xref:System.Windows.Input.ICommand> arabirimi.  Diğer bir yol daha genel yaklaşım ise oluşturmak için bir <xref:System.Windows.Input.RoutedCommand> veya <xref:System.Windows.Input.RoutedUICommand>.  
  
 Özel oluşturma örneği <xref:System.Windows.Input.RoutedCommand>, bkz: [özel bağlayan örneği oluşturma](http://go.microsoft.com/fwlink/?LinkID=159980).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Input.RoutedCommand>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Input.InputBinding>  
 <xref:System.Windows.Input.CommandManager>  
 [Girişe Genel Bakış](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [ICommandSource Uygulama](../../../../docs/framework/wpf/advanced/how-to-implement-icommandsource.md)  
 [Nasıl yapılır: bir MenuItem komut ekleme](http://msdn.microsoft.com/en-us/013d68a0-5373-4a68-bd91-5de574307370)  
 [Özel bağlayan örneği oluşturma](http://go.microsoft.com/fwlink/?LinkID=159980)
