---
title: 'Nasıl yapılır: RoutedCommand Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: d433658a3039c262d2f682eff09df646d978018c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776486"
---
# <a name="how-to-create-a-routedcommand"></a>Nasıl yapılır: RoutedCommand Oluşturma
Bu örnekte, özel bir oluşturma işlemi gösterilmektedir <xref:System.Windows.Input.RoutedCommand> ve özel komut oluşturarak uygulamak nasıl bir <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve bunlara ekleyerek bir <xref:System.Windows.Input.CommandBinding>.  Komut vermeye genel ile ilgili daha fazla bilgi için bkz: [komut vermeye genel genel bakış](commanding-overview.md).  
  
## <a name="example"></a>Örnek  
 Oluşturmanın ilk adımı bir <xref:System.Windows.Input.RoutedCommand> komutunu tanımlama ve onu örnekleme.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 Komut bir uygulamada kullanmak için komutun ne yaptığını tanımlayan olay işleyicileri oluşturulmalıdır  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 Ardından, bir <xref:System.Windows.Input.CommandBinding> komutu olay işleyicileri ile ilişkilendiren oluşturulur. <xref:System.Windows.Input.CommandBinding> Belirli bir nesne üzerinde oluşturulur.  Bu nesne kapsamını tanımlar <xref:System.Windows.Input.CommandBinding> öğe ağacında  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 Son adım komutu çalıştırır.  Bir komutu çağırmak için bir yol olan ile ilişkilendirmek istediğiniz bir <xref:System.Windows.Input.ICommandSource>, gibi bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 Düğme tıklandığında <xref:System.Windows.Input.RoutedCommand.Execute%2A> özel metodunda <xref:System.Windows.Input.RoutedCommand> çağrılır.  <xref:System.Windows.Input.RoutedCommand> Başlatır <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> yönlendirilmiş olaylar.  Bu olayları aranırken öğesi ağacı gezme bir <xref:System.Windows.Input.CommandBinding> bu belirli komutu.  Varsa bir <xref:System.Windows.Input.CommandBinding> bulunursa <xref:System.Windows.Input.ExecutedRoutedEventHandler> ilişkili <xref:System.Windows.Input.CommandBinding> çağrılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Input.RoutedCommand>
- [Komut Vermeye Genel Bakış](commanding-overview.md)
