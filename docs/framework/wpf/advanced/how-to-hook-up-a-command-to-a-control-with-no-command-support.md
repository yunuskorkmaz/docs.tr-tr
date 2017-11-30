---
title: "Nasıl yapılır: Komut Desteği Olmadan Denetime Komut Bağlama"
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
- Control class [WPF], attaching a RoutedCommand
- classes [WPF], Control [WPF], attaching a RoutedCommand
- RoutedCommand class [WPF], attaching to a Control
- classes [WPF], RoutedCommand [WPF], attaching to a Control
ms.assetid: dad08f64-700b-46fb-ad3f-fbfee95f0dfe
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f38a6f900ee2b253708da4b63bdc2f474fa3ab1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hook-up-a-command-to-a-control-with-no-command-support"></a><span data-ttu-id="25860-102">Nasıl yapılır: Komut Desteği Olmadan Denetime Komut Bağlama</span><span class="sxs-lookup"><span data-stu-id="25860-102">How to: Hook Up a Command to a Control with No Command Support</span></span>
<span data-ttu-id="25860-103">Aşağıdaki örnek e nasıl bağlanacağını gösterir bir <xref:System.Windows.Input.RoutedCommand> için bir <xref:System.Windows.Controls.Control> değil sahip derlendiği komutu için destek.</span><span class="sxs-lookup"><span data-stu-id="25860-103">The following example shows how to hook up a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Control> which does not have built in support for the command.</span></span>  <span data-ttu-id="25860-104">Birden çok kaynak komutları tam bir örnek için bkz: [özel bağlayan örneği oluşturma](http://go.microsoft.com/fwlink/?LinkID=159980) örnek.</span><span class="sxs-lookup"><span data-stu-id="25860-104">For a complete sample which hooks up commands to multiple sources, see the [Create a Custom RoutedCommand Sample](http://go.microsoft.com/fwlink/?LinkID=159980) sample.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25860-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="25860-105">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="25860-106">Uygulama programcıları düzenli olarak karşılaştığı yaygın komutları kitaplığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="25860-106"> provides a library of common commands which application programmers encounter regularly.</span></span>  <span data-ttu-id="25860-107">Komut kitaplığı oluşturan sınıfları şunlardır: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, ve <xref:System.Windows.Documents.EditingCommands>.</span><span class="sxs-lookup"><span data-stu-id="25860-107">The classes which comprise the command library are: <xref:System.Windows.Input.ApplicationCommands>, <xref:System.Windows.Input.ComponentCommands>, <xref:System.Windows.Input.NavigationCommands>, <xref:System.Windows.Input.MediaCommands>, and <xref:System.Windows.Documents.EditingCommands>.</span></span>  
  
 <span data-ttu-id="25860-108">Statik <xref:System.Windows.Input.RoutedCommand> bu sınıfları yapan nesneleri komut mantığı sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="25860-108">The static <xref:System.Windows.Input.RoutedCommand> objects which make up these classes do not supply command logic.</span></span>  <span data-ttu-id="25860-109">Komutu için mantığı komutu ile ilişkilendirilmiş bir <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="25860-109">The logic for the command is associated with the command with a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="25860-110">Birçok denetimlerinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bazı komutlar komut kitaplığındaki desteği yerleşik.</span><span class="sxs-lookup"><span data-stu-id="25860-110">Many controls in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] have built in support for some of the commands in the command library.</span></span>  <span data-ttu-id="25860-111"><xref:System.Windows.Controls.TextBox>, örneğin, uygulama Düzenle komutların çoğu gibi destekleyen <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, ve <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.</span><span class="sxs-lookup"><span data-stu-id="25860-111"><xref:System.Windows.Controls.TextBox>, for example, supports many of the application edit commands such as <xref:System.Windows.Input.ApplicationCommands.Paste%2A>, <xref:System.Windows.Input.ApplicationCommands.Copy%2A>, <xref:System.Windows.Input.ApplicationCommands.Cut%2A>, <xref:System.Windows.Input.ApplicationCommands.Redo%2A>, and <xref:System.Windows.Input.ApplicationCommands.Undo%2A>.</span></span>  <span data-ttu-id="25860-112">Uygulama geliştiricisinin bu denetimlerle çalışmak üzere bu komutları almak için özel bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="25860-112">The application developer does not have to do anything special to get these commands to work with these controls.</span></span>  <span data-ttu-id="25860-113">Varsa <xref:System.Windows.Controls.TextBox> komut hedefi komutu çalıştırıldığında komutunu kullanarak işleyecek <xref:System.Windows.Input.CommandBinding> denetime oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="25860-113">If the <xref:System.Windows.Controls.TextBox> is the command target when the command is executed, it will handle the command using the <xref:System.Windows.Input.CommandBinding> that is built into the control.</span></span>  
  
 <span data-ttu-id="25860-114">Aşağıdaki nasıl kullanılacağını gösterir bir <xref:System.Windows.Controls.Button> komut kaynağı olarak <xref:System.Windows.Input.ApplicationCommands.Open%2A> komutu.</span><span class="sxs-lookup"><span data-stu-id="25860-114">The following shows how to use a <xref:System.Windows.Controls.Button> as the command source for the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  <span data-ttu-id="25860-115">A <xref:System.Windows.Input.CommandBinding> ilişkilendiren belirtilen oluşturulan <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ile <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="25860-115">A <xref:System.Windows.Input.CommandBinding> is created that associates the specified <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="25860-116">İlk olarak, komut kaynağı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="25860-116">First, the command source is created.</span></span>  <span data-ttu-id="25860-117">A <xref:System.Windows.Controls.Button> komut kaynağı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25860-117">A <xref:System.Windows.Controls.Button> is used as the command source.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandsource)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbuttoncommandsource)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerButtonCommandSource](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbuttoncommandsource)]  
  
 <span data-ttu-id="25860-118">Ardından, <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="25860-118">Next, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> and the <xref:System.Windows.Input.CanExecuteRoutedEventHandler> are created.</span></span>  <span data-ttu-id="25860-119"><xref:System.Windows.Input.ExecutedRoutedEventHandler> Yalnızca açılır bir <xref:System.Windows.MessageBox> komutu yürütüldüğünü belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="25860-119">The <xref:System.Windows.Input.ExecutedRoutedEventHandler> simply opens a <xref:System.Windows.MessageBox> to signify that the command executed.</span></span>  <span data-ttu-id="25860-120"><xref:System.Windows.Input.CanExecuteRoutedEventHandler> Ayarlar <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="25860-120">The <xref:System.Windows.Input.CanExecuteRoutedEventHandler> sets the <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> property to `true`.</span></span>  <span data-ttu-id="25860-121">Normal olarak, execute işleyici komutu geçerli komut hedefinde yürütüldüğünü görmek için daha sağlam denetimleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="25860-121">Normally, the can execute handler would perform more robust checks to see if the command could execute on the current command target.</span></span>  
  
 [!code-csharp[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerbothhandlers)]
 [!code-vb[commandWithHandler#CommandHandlerBothHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerbothhandlers)]  
  
 <span data-ttu-id="25860-122">Son olarak, bir <xref:System.Windows.Input.CommandBinding> kökünde oluşturulan <xref:System.Windows.Window> yönlendirilmiş olay işleyicilerini ilişkilendirir uygulamanın <xref:System.Windows.Input.ApplicationCommands.Open%2A> komutu.</span><span class="sxs-lookup"><span data-stu-id="25860-122">Finally, a <xref:System.Windows.Input.CommandBinding> is created on the root <xref:System.Windows.Window> of the application that associates the routed events handlers to the <xref:System.Windows.Input.ApplicationCommands.Open%2A> command.</span></span>  
  
 [!code-xaml[commandWithHandler#CommandHandlerCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
## <a name="see-also"></a><span data-ttu-id="25860-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25860-123">See Also</span></span>  
 [<span data-ttu-id="25860-124">Komut verme genel bakış</span><span class="sxs-lookup"><span data-stu-id="25860-124">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [<span data-ttu-id="25860-125">Komut desteği ile denetlemek için komut</span><span class="sxs-lookup"><span data-stu-id="25860-125">Hook Up a Command to a Control with Command Support</span></span>](../../../../docs/framework/wpf/advanced/how-to-hook-up-a-command-to-a-control-with-command-support.md)
