---
title: 'Nasıl yapılır: Komutu Etkinleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CommandBindings [WPF]
- commanding [WPF]
ms.assetid: d8016266-58d9-48f7-8298-a86b7ed49fbd
ms.openlocfilehash: 81ae2e46c4fdd8b46e2b72b9a1430437ebfe97b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545288"
---
# <a name="how-to-enable-a-command"></a>Nasıl yapılır: Komutu Etkinleştirme
Aşağıdaki örnekte, komut verme kullanımı gösterilmiştir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Bu örnek ile nasıl ilişkilendirildiğini gösterir bir <xref:System.Windows.Input.RoutedCommand> için bir <xref:System.Windows.Controls.Button>, oluşturma bir <xref:System.Windows.Input.CommandBinding>ve uygulayan olay işleyicileri oluşturma <xref:System.Windows.Input.RoutedCommand>.  Komut verme hakkında daha fazla bilgi için bkz: [kumanda genel bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
## <a name="example"></a>Örnek  
 Kodun ilk bölümü oluşturur [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], oluşan ve bir <xref:System.Windows.Controls.Button> ve <xref:System.Windows.Controls.StackPanel>ve oluşturan bir <xref:System.Windows.Input.CommandBinding> komut işleyicileri ile ilişkilendirir <xref:System.Windows.Input.RoutedCommand>.  
  
 <xref:System.Windows.Input.ICommandSource.Command%2A> Özelliği <xref:System.Windows.Controls.Button> ile ilişkili <xref:System.Windows.Input.ApplicationCommands.Close%2A> komutu.  
  
 <xref:System.Windows.Input.CommandBinding> Eklenen <xref:System.Windows.Input.CommandBindingCollection> kök <xref:System.Windows.Window>. <xref:System.Windows.Input.CommandBinding.Executed> Ve <xref:System.Windows.Input.CommandBinding.CanExecute> olay işleyicileri bu bağlama eklenmiş ve ilişkili <xref:System.Windows.Input.ApplicationCommands.Close%2A> komutu.  
  
 Olmadan <xref:System.Windows.Input.CommandBinding> komut mantığı, yalnızca komut çağırma mekanizması vardır.  Zaman <xref:System.Windows.Controls.Button> tıklandığında, <xref:System.Windows.Input.CommandManager.PreviewExecuted> <xref:System.Windows.RoutedEvent> ve ardından komut hedefi üzerinde ortaya <xref:System.Windows.Input.CommandManager.Executed> <xref:System.Windows.RoutedEvent>.  Bu olaylar aramakta öğesi ağacı gezme bir <xref:System.Windows.Input.CommandBinding> o belirli komut için.  Çünkü dikkate değerdir <xref:System.Windows.RoutedEvent> tünel ve kabarcık öğe ağacı üzerinden, bakım gerekir alınması where <xref:System.Windows.Input.CommandBinding> yerleştirilir.   Varsa <xref:System.Windows.Input.CommandBinding> komut hedefi veya rotası üzerinde değil başka bir düğüme bir eşdüzeyi açıktır <xref:System.Windows.RoutedEvent>, <xref:System.Windows.Input.CommandBinding> değil erişilir.  
  
 [!code-xaml[EnableCloseCommand#CloseCommandBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml#closecommandbinding)]  
  
 [!code-csharp[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandbindingcodebehind)]
 [!code-vb[EnableCloseCommand#CloseCommandBindingCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandbindingcodebehind)]  
  
 Kod uygular, sonraki bölümünde bulunan <xref:System.Windows.Input.CommandManager.Executed> ve <xref:System.Windows.Input.CommandBinding.CanExecute> olay işleyicileri.  
  
 <xref:System.Windows.Input.CommandManager.Executed> İşleyicisi açık dosyayı kapatmak için bir yöntem çağırır.  <xref:System.Windows.Input.CommandBinding.CanExecute> İşleyicisi bir dosyanın açık olup olmadığını belirlemek için bir yöntem çağırır.  Bir dosya açıksa <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> ayarlanır `true`; Aksi takdirde ayarlanır `false`.  
  
 [!code-csharp[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnableCloseCommand/CSharp/Window1.xaml.cs#closecommandhandler)]
 [!code-vb[EnableCloseCommand#CloseCommandHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnableCloseCommand/VisualBasic/Window1.xaml.vb#closecommandhandler)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komut Vermeye Genel Bakış](../../../../docs/framework/wpf/advanced/commanding-overview.md)
