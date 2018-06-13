---
title: 'Nasıl yapılır: RoutedCommand Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- RoutedCommand class [WPF], creating
ms.assetid: aaf6979f-69ab-406f-979f-5766daa85fa0
ms.openlocfilehash: 75e6c435516fe2a174cf991bd41f24e1b30a212a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544121"
---
# <a name="how-to-create-a-routedcommand"></a>Nasıl yapılır: RoutedCommand Oluşturma
Bu örnek özel bir oluşturulacağını gösterir <xref:System.Windows.Input.RoutedCommand> ve özel komut oluşturarak uygulamak nasıl bir <xref:System.Windows.Input.ExecutedRoutedEventHandler> ve <xref:System.Windows.Input.CanExecuteRoutedEventHandler> ve bunlara ekleyerek bir <xref:System.Windows.Input.CommandBinding>.  Komut verme hakkında daha fazla bilgi için bkz: [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Örnek  
 Oluşturmanın ilk adımı bir <xref:System.Windows.Input.RoutedCommand> komutu tanımlama ve onun örneğini oluşturmadır.  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommanddefinition)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommanddefinition)]  
  
 Komut bir uygulamada kullanabilmek için komutun ne yaptığını tanımlayan olay işleyicileri oluşturulmalıdır  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewexecuted)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewExecuted](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewexecuted)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcanexecute)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCanExecute](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcanexecute)]  
  
 Ardından, bir <xref:System.Windows.Input.CommandBinding> komutu olay işleyicileri ile ilişkilendiren oluşturulur. <xref:System.Windows.Input.CommandBinding> Belirli bir nesne üzerinde oluşturulur.  Bu nesne kapsamını tanımlar <xref:System.Windows.Input.CommandBinding> öğe ağacındaki  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewWindowCommandBindingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewwindowcommandbindingxaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandbindingcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandbindingcodebehind)]  
  
 Son adım komutu çalıştırır.  Bir komut çağırmak için bir yol olduğu ile ilişkilendirilecek bir <xref:System.Windows.Input.ICommandSource>, gibi bir <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcustomcommandsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcustomcommandsourcecodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCustomCommandSourceCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcustomcommandsourcecodebehind)]  
  
 Düğme tıklatıldığında <xref:System.Windows.Input.RoutedCommand.Execute%2A> yöntemi özel <xref:System.Windows.Input.RoutedCommand> olarak adlandırılır.  <xref:System.Windows.Input.RoutedCommand> Başlatır <xref:System.Windows.Input.CommandManager.PreviewExecuted> ve <xref:System.Windows.Input.CommandManager.Executed> yönlendirilmiş olaylar.  Bu olaylar aramakta öğesi ağacı gezme bir <xref:System.Windows.Input.CommandBinding> bu belirli komut.  Varsa bir <xref:System.Windows.Input.CommandBinding> bulunan <xref:System.Windows.Input.ExecutedRoutedEventHandler> ile ilişkili <xref:System.Windows.Input.CommandBinding> olarak adlandırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Input.RoutedCommand>  
 [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)
