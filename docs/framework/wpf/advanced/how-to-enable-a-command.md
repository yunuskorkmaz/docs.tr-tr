---
title: "Nasıl yapılır: Komutu Etkinleştirme"
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
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b27f8544a44a252eb1a1afd6e096f303360c14e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-a-command"></a><span data-ttu-id="e3c01-102">Nasıl yapılır: Komutu Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e3c01-102">How to: Enable a Command</span></span>
<span data-ttu-id="e3c01-103">Aşağıdaki örnekte, komut verme kullanımı gösterilmiştir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3c01-103">The following example demonstrates how to use commanding in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  <span data-ttu-id="e3c01-104">Bu örnek ile nasıl ilişkilendirildiğini gösterir bir <xref:System.Windows.Input.RoutedCommand> için bir <xref:System.Windows.Controls.Button>, oluşturma bir <xref:System.Windows.Input.CommandBinding>ve uygulayan olay işleyicileri oluşturma <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="e3c01-104">The example shows how to associate a <xref:System.Windows.Input.RoutedCommand> to a <xref:System.Windows.Controls.Button>, create a <xref:System.Windows.Input.CommandBinding>, and create the event handlers which implement the <xref:System.Windows.Input.RoutedCommand>.</span></span>  <span data-ttu-id="e3c01-105">Komut verme hakkında daha fazla bilgi için bkz: [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e3c01-105">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3c01-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3c01-106">Example</span></span>  
 <span data-ttu-id="e3c01-107">Kodun ilk bölümü oluşturur [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], oluşan ve bir <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.StackPanel>ve oluşturan bir <xref:System.Windows.Input.CommandBinding> komut işleyicileri ile ilişkilendirir <xref:System.Windows.Input.RoutedCommand>.</span><span class="sxs-lookup"><span data-stu-id="e3c01-107">The first section of code creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], which consists of a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.StackPanel>, and creates a <xref:System.Windows.Input.CommandBinding> that associates the command handlers with the <xref:System.Windows.Input.RoutedCommand>.</span></span>  
  
 <span data-ttu-id="e3c01-108"><xref:System.Windows.Input.ICommandSource.Command%2A> Özelliği <xref:System.Windows.Controls.Button> ile ilişkili <xref:System.Windows.Input.ApplicationCommands.Close%2A> komutu.</span><span class="sxs-lookup"><span data-stu-id="e3c01-108">The <xref:System.Windows.Input.ICommandSource.Command%2A> property of the <xref:System.Windows.Controls.Button> is associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="e3c01-109"><xref:System.Windows.Input.CommandBinding> Eklenen <xref:System.Windows.Input.CommandBindingCollection> kök <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="e3c01-109">The <xref:System.Windows.Input.CommandBinding> is added to the <xref:System.Windows.Input.CommandBindingCollection> of the root <xref:System.Windows.Window>.</span></span> <span data-ttu-id="e3c01-110"><xref:System.Windows.Input.CommandBinding.Executed> Ve <xref:System.Windows.Input.CommandBinding.CanExecute> olay işleyicileri bu bağlama eklenmiş ve ilişkili <xref:System.Windows.Input.ApplicationCommands.Close%2A> komutu.</span><span class="sxs-lookup"><span data-stu-id="e3c01-110">The <xref:System.Windows.Input.CommandBinding.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers are attached to this binding and associated with the <xref:System.Windows.Input.ApplicationCommands.Close%2A> command.</span></span>  
  
 <span data-ttu-id="e3c01-111">Olmadan <xref:System.Windows.Input.CommandBinding> komut mantığı, yalnızca komut çağırma mekanizması vardır.</span><span class="sxs-lookup"><span data-stu-id="e3c01-111">Without the <xref:System.Windows.Input.CommandBinding> there is no command logic, only a mechanism to invoke the command.</span></span>  <span data-ttu-id="e3c01-112">Zaman <xref:System.Windows.Controls.Button> tıklandığında, <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> ve ardından komut hedefi üzerinde ortaya <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span><span class="sxs-lookup"><span data-stu-id="e3c01-112">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> is raised on the command target followed by the <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.</span></span>  <span data-ttu-id="e3c01-113">Bu olaylar aramakta öğesi ağacı gezme bir <xref:System.Windows.Input.CommandBinding> o belirli komut için.</span><span class="sxs-lookup"><span data-stu-id="e3c01-113">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for that particular command.</span></span>  <span data-ttu-id="e3c01-114">Çünkü dikkate değerdir <xref:System.Windows.RoutedEvent> tünel ve kabarcık öğe ağacı üzerinden, bakım gerekir alınması where <xref:System.Windows.Input.CommandBinding> yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e3c01-114">It is worth noting that because <xref:System.Windows.RoutedEvent> tunnel and bubble through the element tree, care must be taken in where the <xref:System.Windows.Input.CommandBinding> is put.</span></span>   <span data-ttu-id="e3c01-115">Varsa <xref:System.Windows.Input.CommandBinding> komut hedefi veya rotası üzerinde değil başka bir düğüme bir eşdüzeyi açıktır <xref:System.Windows.RoutedEvent>, <xref:System.Windows.Input.CommandBinding> değil erişilir.</span><span class="sxs-lookup"><span data-stu-id="e3c01-115">If the <xref:System.Windows.Input.CommandBinding> is on a sibling of the command target or another node that is not on the route of the <xref:System.Windows.RoutedEvent>, the <xref:System.Windows.Input.CommandBinding> will not be accessed.</span></span>  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 <span data-ttu-id="e3c01-116">Kod uygular, sonraki bölümünde bulunan <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandBinding.CanExecute> olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="e3c01-116">The next section of code implements the <xref:System.Windows.Input.CommandManager.Executed> and <xref:System.Windows.Input.CommandBinding.CanExecute> event handlers.</span></span>  
  
 <span data-ttu-id="e3c01-117"><xref:System.Windows.Input.CommandManager.Executed> İşleyicisi açık dosyayı kapatmak için bir yöntem çağırır.</span><span class="sxs-lookup"><span data-stu-id="e3c01-117">The <xref:System.Windows.Input.CommandManager.Executed> handler calls a method to close the open file.</span></span>  <span data-ttu-id="e3c01-118"><xref:System.Windows.Input.CommandBinding.CanExecute> İşleyicisi bir dosyanın açık olup olmadığını belirlemek için bir yöntem çağırır.</span><span class="sxs-lookup"><span data-stu-id="e3c01-118">The <xref:System.Windows.Input.CommandBinding.CanExecute> handler calls a method to determine whether a file is open.</span></span>  <span data-ttu-id="e3c01-119">Bir dosya açıksa <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> ayarlanır `true`; Aksi takdirde ayarlanır `false`.</span><span class="sxs-lookup"><span data-stu-id="e3c01-119">If a file is open, <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> is set to `true`; otherwise, it is set to `false`.</span></span>  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a><span data-ttu-id="e3c01-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3c01-120">See Also</span></span>  
 [<span data-ttu-id="e3c01-121">Komut Vermeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e3c01-121">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
