---
title: 'Nasıl yapılır: RoutedCommand Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: 4119a762bd0db63108d08a9db9367e367adb6b58
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372093"
---
# <a name="how-to-create-a-routedcommand"></a><span data-ttu-id="eae9c-102">Nasıl yapılır: RoutedCommand Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eae9c-102">How to: Create a RoutedCommand</span></span>
<span data-ttu-id="eae9c-103">Bu örnekte, özel bir oluşturma işlemi gösterilmektedir <xref:System.Windows.Input.RoutedCommand> ve özel komut oluşturarak uygulamak nasıl bir <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve bunlara ekleyerek bir <xref:System.Windows.Input.CommandBinding>.</span><span class="sxs-lookup"><span data-stu-id="eae9c-103">This example shows how to create a custom <xref:System.Windows.Input.RoutedCommand> and how to implement the custom command by creating a <xref:System.Windows.Input.ExecutedRoutedEventHandler> and a <xref:System.Windows.Input.CanExecuteRoutedEventHandler> and attaching them to a <xref:System.Windows.Input.CommandBinding>.</span></span>  <span data-ttu-id="eae9c-104">Komut vermeye genel ile ilgili daha fazla bilgi için bkz: [komut vermeye genel genel bakış](commanding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eae9c-104">For more information on commanding, see the [Commanding Overview](commanding-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eae9c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="eae9c-105">Example</span></span>  
 <span data-ttu-id="eae9c-106">Oluşturmanın ilk adımı bir <xref:System.Windows.Input.RoutedCommand> komutunu tanımlama ve onu örnekleme.</span><span class="sxs-lookup"><span data-stu-id="eae9c-106">The first step in creating a <xref:System.Windows.Input.RoutedCommand> is defining the command and instantiating it.</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 <span data-ttu-id="eae9c-107">Komut bir uygulamada kullanmak için komutun ne yaptığını tanımlayan olay işleyicileri oluşturulmalıdır</span><span class="sxs-lookup"><span data-stu-id="eae9c-107">In order to use the command in an application, event handlers which define what the command does must be created</span></span>  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 <span data-ttu-id="eae9c-108">Ardından, bir <xref:System.Windows.Input.CommandBinding> komutu olay işleyicileri ile ilişkilendiren oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="eae9c-108">Next, a  <xref:System.Windows.Input.CommandBinding> is created which associates the command with the event handlers.</span></span> <span data-ttu-id="eae9c-109"><xref:System.Windows.Input.CommandBinding> Belirli bir nesne üzerinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="eae9c-109">The <xref:System.Windows.Input.CommandBinding> is created on a specific object.</span></span>  <span data-ttu-id="eae9c-110">Bu nesne kapsamını tanımlar <xref:System.Windows.Input.CommandBinding> öğe ağacında</span><span class="sxs-lookup"><span data-stu-id="eae9c-110">This object defines the scope of the <xref:System.Windows.Input.CommandBinding> in the element tree</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 <span data-ttu-id="eae9c-111">Son adım komutu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="eae9c-111">The final step is invoking the command.</span></span>  <span data-ttu-id="eae9c-112">Bir komutu çağırmak için bir yol olan ile ilişkilendirmek istediğiniz bir <xref:System.Windows.Input.ICommandSource>, gibi bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="eae9c-112">One way to invoke a command is to associate it with a <xref:System.Windows.Input.ICommandSource>, such as a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 <span data-ttu-id="eae9c-113">Düğme tıklandığında <xref:System.Windows.Input.RoutedCommand.Execute%2A> özel metodunda <xref:System.Windows.Input.RoutedCommand> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="eae9c-113">When the Button is clicked, the <xref:System.Windows.Input.RoutedCommand.Execute%2A> method on the custom <xref:System.Windows.Input.RoutedCommand> is called.</span></span>  <span data-ttu-id="eae9c-114"><xref:System.Windows.Input.RoutedCommand> Başlatır <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> yönlendirilmiş olaylar.</span><span class="sxs-lookup"><span data-stu-id="eae9c-114">The <xref:System.Windows.Input.RoutedCommand> raises the <xref:System.Windows.Input.CommandManager.PreviewExecuted> and <xref:System.Windows.Input.CommandManager.Executed> routed events.</span></span>  <span data-ttu-id="eae9c-115">Bu olayları aranırken öğesi ağacı gezme bir <xref:System.Windows.Input.CommandBinding> bu belirli komutu.</span><span class="sxs-lookup"><span data-stu-id="eae9c-115">These events traverse the element tree looking for a <xref:System.Windows.Input.CommandBinding> for this particular command.</span></span>  <span data-ttu-id="eae9c-116">Varsa bir <xref:System.Windows.Input.CommandBinding> bulunursa <xref:System.Windows.Input.ExecutedRoutedEventHandler> ilişkili <xref:System.Windows.Input.CommandBinding> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="eae9c-116">If a <xref:System.Windows.Input.CommandBinding> is found, the <xref:System.Windows.Input.ExecutedRoutedEventHandler> associated with <xref:System.Windows.Input.CommandBinding> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae9c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eae9c-117">See also</span></span>
- <xref:System.Windows.Input.RoutedCommand>
- [<span data-ttu-id="eae9c-118">Komut Vermeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eae9c-118">Commanding Overview</span></span>](commanding-overview.md)
