---
title: "Nasıl yapılır: RoutedCommand Oluşturma"
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
helpviewer_keywords: RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dad0cd8aaa81e6a458307ec69ec60ed369ca6b03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-routedcommand"></a><span data-ttu-id="42660-102">Nasıl yapılır: RoutedCommand Oluşturma</span><span class="sxs-lookup"><span data-stu-id="42660-102">How to: Create a RoutedCommand</span></span>
<span data-ttu-id="42660-103">Bu örnek özel bir oluşturulacağını gösterir <xref:System.Windows.Input.RoutedCommand> ve özel komut oluşturarak uygulamak nasıl bir <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve bunlara ekleyerek bir <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="42660-103">This example shows how to create a custom <xref:System.Windows.Input.RoutedCommand> and how to implement the custom command by creating a <xref:System.Windows.Input.ExecutedRoutedEventHandler> and a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and attaching them to a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="42660-104">Komut verme hakkında daha fazla bilgi için bkz: [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="42660-104">For more information on commanding, see the [Commanding Overview](../../../../docs/framework/wpf/advanced/commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42660-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="42660-105">Example</span></span>  
 <span data-ttu-id="42660-106">Oluşturmanın ilk adımı bir <xref:System.Windows.Input.RoutedCommand> komutu tanımlama ve onun örneğini oluşturmadır.</span><span class="sxs-lookup"><span data-stu-id="42660-106">The first step in creating a <xref:System.Windows.Input.RoutedCommand> is defining the command and instantiating it.</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 <span data-ttu-id="42660-107">Komut bir uygulamada kullanabilmek için komutun ne yaptığını tanımlayan olay işleyicileri oluşturulmalıdır</span><span class="sxs-lookup"><span data-stu-id="42660-107">In order to use the command in an application, event handlers which define what the command does must be created</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 <span data-ttu-id="42660-108">Ardından, bir <xref:System.Windows.Input.CommandBinding> komutu olay işleyicileri ile ilişkilendiren oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42660-108">Next, a  <xref:System.Windows.Input.CommandBinding> is created which associates the command with the event handlers.</span></span> <span data-ttu-id="42660-109"><xref:System.Windows.Input.CommandBinding> Belirli bir nesne üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42660-109">The <xref:System.Windows.Input.CommandBinding> is created on a specific object.</span></span>  <span data-ttu-id="42660-110">Bu nesne kapsamını tanımlar <xref:System.Windows.Input.CommandBinding> öğe ağacındaki</span><span class="sxs-lookup"><span data-stu-id="42660-110">This object defines the scope of the <xref:System.Windows.Input.CommandBinding> in the element tree</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 <span data-ttu-id="42660-111">Son adım komutu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="42660-111">The final step is invoking the command.</span></span>  <span data-ttu-id="42660-112">Bir komut çağırmak için bir yol olduğu ile ilişkilendirilecek bir <xref:System.Windows.Input.ICommandSource>, gibi bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="42660-112">One way to invoke a command is to associate it with a <xref:System.Windows.Input.ICommandSource>, such as a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 <span data-ttu-id="42660-113">Düğme tıklatıldığında <xref:System.Windows.Input.RoutedCommand.Execute%2A> yöntemi özel <xref:System.Windows.Input.RoutedCommand> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="42660-113">When the Button is clicked, the <xref:System.Windows.Input.RoutedCommand.Execute%2A> method on the custom <xref:System.Windows.Input.RoutedCommand> is called.</span></span>  <span data-ttu-id="42660-114"><xref:System.Windows.Input.RoutedCommand> Başlatır <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> yönlendirilmiş olaylar.</span><span class="sxs-lookup"><span data-stu-id="42660-114">The <xref:System.Windows.Input.RoutedCommand> raises the <xref:System.Windows.Input.CommandManager.PreviewExecuted> and <xref:System.Windows.Input.CommandManager.Executed> routed events.</span></span>  <span data-ttu-id="42660-115">Bu olaylar aramakta öğesi ağacı gezme bir <xref:System.Windows.Input.CommandBinding> bu belirli komut.</span><span class="sxs-lookup"><span data-stu-id="42660-115">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for this particular command.</span></span>  <span data-ttu-id="42660-116">Varsa bir <xref:System.Windows.Input.CommandBinding> bulunan <xref:System.Windows.Input.ExecutedRoutedEventHandler> ile ilişkili <xref:System.Windows.Input.CommandBinding> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="42660-116">If a <xref:System.Windows.Input.CommandBinding> is found, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> associated with <xref:System.Windows.Input.CommandBinding> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42660-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42660-117">See Also</span></span>  
 <xref:System.Windows.Input.RoutedCommand>  
 [<span data-ttu-id="42660-118">Komut verme genel bakış</span><span class="sxs-lookup"><span data-stu-id="42660-118">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)
