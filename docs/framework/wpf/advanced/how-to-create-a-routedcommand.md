---
title: 'Nasıl yapılır: RoutedCommand Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: 73a5337cae61a38e10f3ddd7dbe654d7fae616b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735746"
---
# <a name="how-to-create-a-routedcommand"></a>Nasıl yapılır: RoutedCommand Oluşturma
Bu örnekte, özel bir oluşturma işlemi gösterilmektedir <xref:System.Windows.Input.RoutedCommand> ve özel komut oluşturarak uygulamak nasıl bir <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve bunlara ekleyerek bir <xref:System.Windows.Input.CommandBinding>.  Komut vermeye genel ile ilgili daha fazla bilgi için bkz: [komut vermeye genel genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Örnek  
 Oluşturmanın ilk adımı bir <xref:System.Windows.Input.RoutedCommand> komutunu tanımlama ve onu örnekleme.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 Komut bir uygulamada kullanmak için komutun ne yaptığını tanımlayan olay işleyicileri oluşturulmalıdır  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 Ardından, bir <xref:System.Windows.Input.CommandBinding> komutu olay işleyicileri ile ilişkilendiren oluşturulur. <xref:System.Windows.Input.CommandBinding> Belirli bir nesne üzerinde oluşturulur.  Bu nesne kapsamını tanımlar <xref:System.Windows.Input.CommandBinding> öğe ağacında  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 Son adım komutu çalıştırır.  Bir komutu çağırmak için bir yol olan ile ilişkilendirmek istediğiniz bir <xref:System.Windows.Input.ICommandSource>, gibi bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 Düğme tıklandığında <xref:System.Windows.Input.RoutedCommand.Execute%2A> özel metodunda <xref:System.Windows.Input.RoutedCommand> çağrılır.  <xref:System.Windows.Input.RoutedCommand> Başlatır <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> yönlendirilmiş olaylar.  Bu olayları aranırken öğesi ağacı gezme bir <xref:System.Windows.Input.CommandBinding> bu belirli komutu.  Varsa bir <xref:System.Windows.Input.CommandBinding> bulunursa <xref:System.Windows.Input.ExecutedRoutedEventHandler> ilişkili <xref:System.Windows.Input.CommandBinding> çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Input.RoutedCommand>
- [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)
